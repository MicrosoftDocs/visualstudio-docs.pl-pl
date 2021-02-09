---
title: Instalowanie Visual Studio Build Tools w kontenerze
titleSuffix: ''
description: Dowiedz się, jak zainstalować Visual Studio Build Tools w kontenerze systemu Windows, aby obsługiwać przepływy pracy ciągłej integracji i ciągłego dostarczania (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 941a991e28a2d545bbc4da809a1e663c9fc41a5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902730"
---
# <a name="install-build-tools-into-a-container"></a>Instalowanie narzędzi kompilacji do kontenera

Visual Studio Build Tools można zainstalować w kontenerze systemu Windows w celu obsługi przepływów pracy ciągłej integracji i ciągłego dostarczania (CI/CD). W tym artykule opisano, jakie zmiany w konfiguracji platformy Docker są wymagane, a także jakie [obciążenia i składniki](workload-component-id-vs-build-tools.md) można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) są doskonałym sposobem na spakowanie spójnego systemu kompilacji, którego można użyć nie tylko w środowisku serwera ciągłej integracji/ciągłego wdrażania, ale również w środowiskach deweloperskich. Można na przykład zainstalować kod źródłowy w kontenerze, który ma zostać skompilowany przez dostosowane środowisko, podczas gdy nadal używasz programu Visual Studio lub innych narzędzi do pisania kodu. Jeśli przepływ pracy CI/CD korzysta z tego samego obrazu kontenera, możesz zapewnić spójność kodu. Kontenerów można również użyć do zapewnienia spójności środowiska uruchomieniowego, która jest powszechna dla mikrousług korzystających z wielu kontenerów z systemem aranżacji. jednak wykracza poza zakres tego artykułu.

Jeśli Visual Studio Build Tools nie ma potrzebnych do skompilowania kodu źródłowego, te same kroki mogą być używane dla innych produktów Visual Studio. Należy jednak pamiętać, że kontenery systemu Windows nie obsługują interaktywnego interfejsu użytkownika, więc wszystkie polecenia muszą być zautomatyzowane.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Poniżej założono pewną znajomość [platformy Docker](https://www.docker.com/what-docker) . Jeśli nie znasz jeszcze programu Docker w systemie Windows, przeczytaj temat jak [zainstalować i skonfigurować aparat platformy Docker w systemie Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Poniższy obraz podstawowy jest przykładem i może nie zadziałać w systemie. Przeczytaj temat [zgodność wersji kontenera systemu Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) , aby określić, który obraz podstawowy ma być używany w danym środowisku.

## <a name="create-and-build-the-dockerfile"></a>Tworzenie i Kompilowanie pliku dockerfile

Zapisz Poniższy przykład pliku dockerfile do nowego pliku na dysku. Jeśli plik ma nazwę "pliku dockerfile", jest rozpoznawany domyślnie.

> [!WARNING]
> Ten przykład pliku dockerfile wyklucza tylko starsze zestawy Windows SDK, których nie można zainstalować w kontenerach. Wcześniejsze wersje powodują niepowodzenie polecenia kompilacji.

1. Otwórz wiersz polecenia.

1. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

1. Zmień katalogi na ten nowy katalog:

   ```shell
   cd C:\BuildTools
   ```

1. Zapisz poniższą zawartość w usłudze C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN start /wait C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Aby zapoznać się z listą obciążeń i składników, zobacz [katalog składników Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > W przypadku opierania się na obrazie bezpośrednio w usłudze Microsoft/windowsservercore lub mcr.microsoft.com/windows/servercore (Zobacz artykuł [Microsoft syndykats Catalog katalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)), .NET Framework może nie zostać poprawnie zainstalowany i nie jest wskazywany żaden błąd instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy oprzeć obraz na [platformie Microsoft/dotnet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszym. Należy również zauważyć, że obrazy otagowane w wersji 4.7.2 lub nowszej mogą używać programu PowerShell jako domyślnego `SHELL` , co spowoduje `RUN` `ENTRYPOINT` Niepowodzenie wykonywania instrukcji i.
   >
   > Program Visual Studio 2017 w wersji 15,8 lub starszej (dowolny produkt) nie zostanie poprawnie zainstalowany w systemie mcr.microsoft.com/windows/servercore:1809 lub nowszym. Nie jest wyświetlany żaden błąd.
   >
   > Zobacz [zgodność wersji kontenera systemu Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) , aby sprawdzić, które wersje systemu operacyjnego kontenera są obsługiwane, w których wersjach systemu operacyjnego hosta i [znanych problemów dotyczących kontenerów](build-tools-container-issues.md) znanych problemów.
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Aby zapoznać się z listą obciążeń i składników, zobacz [katalog składników Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Jeśli zamierzasz oprzeć obraz bezpośrednio w firmie Microsoft/windowsservercore, .NET Framework może nie zostać zainstalowana prawidłowo i nie wskazano błędu instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy oprzeć obraz na [platformie Microsoft/dotnet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Należy również zauważyć, że obrazy oznaczone w wersji 4,8 lub nowszej mogą używać programu PowerShell jako domyślnego `SHELL` , co spowoduje `RUN` `ENTRYPOINT` Niepowodzenie wykonywania instrukcji i.
   >
   > Zobacz [zgodność wersji kontenera systemu Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) , aby sprawdzić, które wersje systemu operacyjnego kontenera są obsługiwane, w których wersjach systemu operacyjnego hosta i [znanych problemów dotyczących kontenerów](build-tools-container-issues.md) znanych problemów.

   ::: moniker-end
   
   > [!NOTE]
   > Kod błędu `3010` jest używany do wskazania sukcesu z wymaganym ponownym uruchomieniem, zobacz [MsiExec.exe komunikaty o błędach](/windows/win32/msi/error-codes) , aby uzyskać więcej informacji.

1. Uruchom następujące polecenie w tym katalogu.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie kompiluje pliku dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślnie 1 GB nie wystarcza w przypadku zainstalowania niektórych obciążeń; Jednak może być możliwe skompilowanie tylko 1 GB pamięci, w zależności od wymagań dotyczących kompilacji.

   Obraz końcowy jest oznaczony jako "buildtools2017: Najnowsza", więc można go łatwo uruchomić w kontenerze jako "buildtools2017", ponieważ tag "Najnowsza" jest wartością domyślną, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji Visual Studio Build Tools 2017 w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), możesz zamiast tego oznaczyć kontener z konkretnym numerem kompilacji programu Visual Studio, a także "najnowszy", aby kontenery mogły korzystać z określonej wersji.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   To polecenie kompiluje pliku dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślnie 1 GB nie wystarcza w przypadku zainstalowania niektórych obciążeń; Jednak może być możliwe skompilowanie tylko 1 GB pamięci, w zależności od wymagań dotyczących kompilacji.

   Obraz końcowy jest oznaczony jako "buildtools2019: Najnowsza", więc można go łatwo uruchomić w kontenerze jako "buildtools2019", ponieważ tag "Najnowsza" jest wartością domyślną, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji Visual Studio Build Tools 2019 w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), możesz zamiast tego oznaczyć kontener z konkretnym numerem kompilacji programu Visual Studio, a także "najnowszy", aby kontenery mogły korzystać z określonej wersji.

   ::: moniker-end

## <a name="using-the-built-image"></a>Korzystanie z skompilowanego obrazu

Teraz, po utworzeniu obrazu, można go uruchomić w kontenerze, aby wykonać kompilacje interaktywne i zautomatyzowane. W przykładzie zastosowano wiersz polecenia dla deweloperów, więc ścieżka i inne zmienne środowiskowe są już skonfigurowane.

1. Otwórz wiersz polecenia.

1. Uruchom kontener, aby uruchomić środowisko PowerShell ze wszystkimi ustawionymi zmiennymi środowiskowymi dla deweloperów:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Aby użyć tego obrazu dla przepływu pracy ciągłej integracji/ciągłego dostarczania, możesz opublikować go we własnym [Azure Container Registry](https://azure.microsoft.com/services/container-registry) lub innym wewnętrznym [rejestrze platformy Docker](https://docs.docker.com/registry/deploying) , aby serwery musiały je tylko ściągnąć.

   > [!NOTE]
   > Jeśli nie można uruchomić kontenera platformy Docker, prawdopodobnie wystąpił problem z instalacją programu Visual Studio. Możesz zaktualizować pliku dockerfile, aby usunąć krok wywołujący polecenie programu Visual Studio Batch. Dzięki temu można uruchomić kontener platformy Docker i odczytać dzienniki błędów instalacji.
   >
   > W pliku pliku dockerfile Usuń `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` Parametry i z `ENTRYPOINT` polecenia. Polecenie powinno teraz być `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` . Następnie ponownie skompiluj pliku dockerfile i wykonaj polecenie, `run` Aby uzyskać dostęp do plików kontenerów. Aby zlokalizować dzienniki błędów instalacji, przejdź do `$env:TEMP` katalogu i Znajdź `dd_setup_<timestamp>_errors.log` plik.
   >
   > Po zidentyfikowaniu i usunięciu problemu z instalacją można dodać `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` Parametry i z `&&` powrotem do `ENTRYPOINT` polecenia i ponownie skompilować pliku dockerfile.
   >
   > Aby uzyskać więcej informacji, zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio Build Tools obciążenia i identyfikatory składników](workload-component-id-vs-build-tools.md)
