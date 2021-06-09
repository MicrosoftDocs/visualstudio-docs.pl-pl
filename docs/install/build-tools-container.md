---
title: Instalowanie Visual Studio Build Tools w kontenerze
titleSuffix: ''
description: Dowiedz się, jak zainstalować Visual Studio Build Tools w kontenerze systemu Windows w celu obsługi przepływów pracy ciągłej integracji i ciągłego dostarczania (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dcf28f818760320b215cbff0d3a2eb5ad6d9f623
ms.sourcegitcommit: 55b99dbce29d19e493feae9b8d2fdac73718e4de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873071"
---
# <a name="install-build-tools-into-a-container"></a>Instalowanie narzędzi kompilacji w kontenerze

Możesz zainstalować Visual Studio Build Tools w kontenerze systemu Windows, aby obsługiwać przepływy pracy ciągłej integracji i ciągłego dostarczania (CI/CD). Ten artykuł zawiera instrukcje dotyczące wymaganych zmian [](workload-component-id-vs-build-tools.md) konfiguracji platformy Docker oraz obciążeń i składników, które można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) to doskonały sposób na spakowania spójnego systemu kompilacji, z których można korzystać nie tylko w środowisku serwera CI/CD, ale także w środowiskach deweloperskich. Na przykład możesz zainstalować kod źródłowy w kontenerze, który ma zostać s zbudowana przez dostosowane środowisko, podczas gdy będziesz nadal używać Visual Studio lub innych narzędzi do pisania kodu. Jeśli przepływ pracy ci/cd używa tego samego obrazu kontenera, możesz mieć pewność, że kod jest kompilowany spójnie. Kontenerów można również używać w celu zapewnienia spójności środowiska uruchomieniowego, co jest typowe w przypadku mikrousług korzystających z wielu kontenerów z systemem aranżacji; jednak wykracza poza zakres tego artykułu.

Jeśli Visual Studio Build Tools nie ma tego, czego potrzebujesz do skompilowania kodu źródłowego, te same kroki mogą być używane dla innych Visual Studio produktów. Należy jednak pamiętać, że kontenery systemu Windows nie obsługują interaktywnego interfejsu użytkownika, dlatego wszystkie polecenia muszą być zautomatyzowane.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Poniżej przyjęto założenie, że [znajomość platformy Docker](https://www.docker.com/what-docker) jest nieco znana. Jeśli nie znasz jeszcze uruchamiania platformy Docker w systemie Windows, przeczytaj o instalowania i konfigurowaniu aparatu [platformy Docker w systemie Windows.](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)

Poniższy obraz podstawowy jest przykładowy i może nie działać dla Twojego systemu. Przeczytaj [informacje o zgodności wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby określić, którego obrazu podstawowego należy użyć dla środowiska.

## <a name="create-and-build-the-dockerfile"></a>Tworzenie i kompilowanie pliku Dockerfile

Zapisz następujący przykładowy plik Dockerfile w nowym pliku na dysku. Jeśli plik ma nazwę po prostu "Dockerfile", jest rozpoznawany domyślnie.

> [!WARNING]
> W tym przykładzie plik Dockerfile wyklucza tylko wcześniejsze zestawy SDK systemu Windows, których nie można zainstalować w kontenerach. Wcześniejsze wersje powodują niepowodzenie polecenia kompilacji.

1. Otwórz wiersz polecenia.

1. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

1. Zmień katalogi na ten nowy katalog:

   ```shell
   cd C:\BuildTools
   ```

1. Zapisz następującą zawartość w folderze C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

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
   > Aby uzyskać listę obciążeń i składników, zobacz [katalog Visual Studio Build Tools component](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Jeśli obraz bazuje bezpośrednio na bazie microsoft/windowsservercore lub mcr.microsoft.com/windows/servercore (zobacz katalog kontenerów syndykatów firmy [Microsoft),](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)program .NET Framework może nie zostać zainstalowany prawidłowo i nie jest wyświetlany błąd instalacji. Kod zarządzany może nie zostać uruchomiony po zakończeniu instalacji. Zamiast tego należy bazować obraz na [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Należy również pamiętać, że obrazy oznaczone tagiem w wersji 4.7.2 lub nowszej mogą używać programu PowerShell jako domyślnego polecenia , co spowoduje niepowodzenie instrukcji `SHELL` `RUN` i `ENTRYPOINT` .
   >
   > Visual Studio 2017 w wersji 15.8 lub starszej (dowolny produkt) nie zostanie poprawnie zainstalowany na mcr.microsoft.com/windows/servercore:1809 lub nowszym. Błąd nie jest wyświetlany.
   >
   > Zobacz [Zgodność wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby zobaczyć, które wersje systemu operacyjnego kontenera są obsługiwane w których wersjach systemu operacyjnego hosta, i Znane problemy dotyczące [kontenerów w](build-tools-container-issues.md) przypadku znanych problemów.
   
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
   > Aby uzyskać listę obciążeń i składników, zobacz [katalog Visual Studio Build Tools component](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Jeśli obraz bazuje bezpośrednio na bazie microsoft/windowsservercore, .NET Framework instalacja może nie być prawidłowo i nie jest wyświetlany błąd instalacji. Kod zarządzany może nie zostać uruchomiony po zakończeniu instalacji. Zamiast tego należy bazować obraz na [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Należy również zauważyć, że obrazy oznaczone tagiem w wersji 4.8 lub nowszej mogą używać programu PowerShell jako domyślnego polecenia , co spowoduje niepowodzenie `SHELL` `RUN` instrukcji i `ENTRYPOINT` .
   >
   > Zobacz [Zgodność wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby zobaczyć, które wersje systemu operacyjnego kontenera są obsługiwane w których wersjach systemu operacyjnego hosta, i Znane problemy dotyczące [kontenerów w](build-tools-container-issues.md) przypadku znanych problemów.

   ::: moniker-end
   
   > [!NOTE]
   > Kod błędu służy do wskazywania powodzenia z wymaganym ponownym uruchomieniem. Aby uzyskać więcej `3010` informacji, [zobaczMsiExec.exe komunikatów o błędach.](/windows/win32/msi/error-codes)

1. Uruchom następujące polecenie w tym katalogu.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślny rozmiar 1 GB nie jest wystarczający, jeśli są zainstalowane niektóre obciążenia. Jednak w zależności od wymagań kompilacji można utworzyć tylko 1 GB pamięci.

   Końcowy obraz jest oznaczony tagiem "buildtools2017:latest", dzięki czemu można łatwo uruchomić go w kontenerze jako "buildtools2017", ponieważ tag "latest" jest domyślny, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji programu Visual Studio Build Tools 2017 [](advanced-build-tools-container.md)w bardziej zaawansowanym scenariuszu, możesz zamiast tego otagować kontener określonym numerem kompilacji Visual Studio oraz "najnowszą", aby kontenery mogły spójnie używać określonej wersji.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślny rozmiar 1 GB nie jest wystarczający, jeśli są zainstalowane niektóre obciążenia. Jednak w zależności od wymagań kompilacji można utworzyć tylko 1 GB pamięci.

   Końcowy obraz jest oznaczony tagiem "buildtools2019:latest", dzięki czemu można łatwo uruchomić go w kontenerze jako "buildtools2019", ponieważ tag "latest" jest domyślny, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji programu Visual Studio Build Tools 2019 [](advanced-build-tools-container.md)w bardziej zaawansowanym scenariuszu, możesz zamiast tego otagować kontener określonym numerem kompilacji Visual Studio oraz "najnowszą", aby kontenery mogły spójnie używać określonej wersji.

   ::: moniker-end

## <a name="using-the-built-image"></a>Korzystanie z obrazu wbudowanego

Teraz, po utworzeniu obrazu, możesz uruchomić go w kontenerze w celu tworzenia interaktywnych i zautomatyzowanych kompilacji. W przykładzie użyto wiersz polecenia dla deweloperów, więc ścieżka i inne zmienne środowiskowe są już skonfigurowane.

1. Otwórz wiersz polecenia.

1. Uruchom kontener, aby uruchomić środowisko programu PowerShell z ustawionymi wszystkimi zmiennymi środowiskowym dewelopera:

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

Aby użyć tego obrazu na potrzeby przepływu pracy ci/CD, możesz opublikować go we własnym Azure Container Registry lub w innym wewnętrznym rejestrze [platformy Docker,](https://docs.docker.com/registry/deploying) aby serwery musiały tylko go ściągnąć. [](https://azure.microsoft.com/services/container-registry)

   > [!NOTE]
   > Jeśli nie można uruchomić kontenera platformy Docker, prawdopodobnie występuje Visual Studio instalacji. Możesz zaktualizować plik Dockerfile, aby usunąć krok, który wywołuje polecenie Visual Studio batch. Dzięki temu można uruchomić kontener platformy Docker i odczytać dzienniki błędów instalacji.
   >
   > W pliku Dockerfile usuń parametry `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` i `&&` z polecenia `ENTRYPOINT` . Polecenie powinno teraz mieć 1.0. `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` Następnie ponownie skompilować plik Dockerfile i wykonać `run` polecenie w celu uzyskania dostępu do plików kontenera. Aby zlokalizować dzienniki błędów instalacji, przejdź do `$env:TEMP` katalogu i znajdź plik `dd_setup_<timestamp>_errors.log` .
   >
   > Po zidentyfikowaniu i naprawieniu problemu z instalacją możesz dodać parametry i z powrotem do polecenia i `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` ponownie `ENTRYPOINT` skompilować plik Dockerfile.
   >
   > Aby uzyskać więcej informacji, zobacz [Znane problemy dotyczące kontenerów](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio Build Tools i identyfikatory składników](workload-component-id-vs-build-tools.md)
