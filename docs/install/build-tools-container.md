---
title: Instalowanie narzędzi kompilacji programu Visual Studio w kontenerze
titleSuffix: ''
description: Dowiedz się, jak zainstalować narzędzia kompilacji programu Visual Studio w kontenerze systemu Windows w celu obsługi ciągłej integracji i ciągłego dostarczania (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 61ec972bd5e361c4417e49092de5976000a6da5f
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273897"
---
# <a name="install-build-tools-into-a-container"></a>Instalowanie narzędzi kompilacji w kontenerze

Narzędzia kompilacji programu Visual Studio można zainstalować w kontenerze systemu Windows w celu obsługi ciągłej integracji i ciągłego dostarczania (CI/CD). W tym artykule znajdziesz informacje o tym, jakie zmiany konfiguracji platformy Docker są wymagane, a także jakie [obciążenia i składniki](workload-component-id-vs-build-tools.md) można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) to świetny sposób na spakowanie spójnego systemu kompilacji, którego można używać nie tylko w środowisku serwera ciągłej integracji/ciągłego wdrażania, ale także w środowiskach programistów. Na przykład można zainstalować kod źródłowy w kontenerze, który ma być utworzony przez dostosowane środowisko, podczas gdy nadal używasz programu Visual Studio lub innych narzędzi do pisania kodu. Jeśli przepływ pracy ciągłej integracji/ciągłego wdrażania używa tego samego obrazu kontenera, można mieć pewność, że kod tworzy spójnie. Można również użyć kontenerów dla spójności środowiska uruchomieniowego, co jest typowe dla mikrousług przy użyciu wielu kontenerów z systemem aranżacji; jednak wykracza poza zakres tego artykułu.

Jeśli narzędzia kompilacji programu Visual Studio nie mają tego, czego potrzebujesz do utworzenia kodu źródłowego, te same kroki mogą być używane dla innych produktów programu Visual Studio. Należy jednak pamiętać, że kontenery systemu Windows nie obsługują interaktywnego interfejsu użytkownika, więc wszystkie polecenia muszą być zautomatyzowane.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Poniżej przyjęto pewną znajomość platformy [Docker.](https://www.docker.com/what-docker) Jeśli nie znasz jeszcze aplikacji Docker w systemie Windows, przeczytaj o tym, jak [zainstalować i skonfigurować aparat](/virtualization/windowscontainers/manage-docker/configure-docker-daemon)platformy Docker w systemie Windows .

Poniższy obraz podstawowy jest próbką i może nie działać w twoim systemie. Przeczytaj [zgodność wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby określić, który obraz podstawowy należy użyć w swoim środowisku.

## <a name="create-and-build-the-dockerfile"></a>Tworzenie i tworzenie pliku dockerfile

Zapisz poniższy przykład Dockerfile do nowego pliku na dysku. Jeśli plik nosi nazwę po prostu "Dockerfile", jest rozpoznawany domyślnie.

> [!WARNING]
> W tym przykładzie dockerfile wyklucza tylko wcześniejsze pakiety SDK systemu Windows, których nie można zainstalować w kontenerach. Wcześniejsze wersje powodują, że polecenie kompilacji nie powiedzie się.

1. Otwórz wiersz polecenia.

1. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

1. Zmień katalogi na ten nowy katalog:

   ```shell
   cd C:\BuildTools
   ```

1. Zapisz następującą zawartość w pliku C:\BuildTools\Dockerfile.
 
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
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
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
   > Aby uzyskać listę obciążeń i składników, zobacz [katalog składników Narzędzia kompilacji programu Visual Studio](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Jeśli obraz jest podstawą bezpośrednio na microsoft/windowsservercore lub mcr.microsoft.com/windows/servercore (zobacz [katalog kontenerów syndykatów firmy Microsoft), program](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/).NET Framework może nie zostać poprawnie zainstalowany i nie zostanie wskazany błąd instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego oprzeć obraz na [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszych. Należy również pamiętać, że obrazy oznaczone w wersji 4.7.2 lub `SHELL`nowszej `RUN` mogą `ENTRYPOINT` używać programu PowerShell jako domyślnego programu PowerShell, co spowoduje niepowodzenie i instrukcje.
   >
   > Visual Studio 2017 w wersji 15.8 lub wcześniejszej (dowolny produkt) nie zostanie poprawnie zainstalowany w mcr.microsoft.com/windows/servercore:1809 lub nowszych. Nie jest wyświetlany żaden błąd.
   >
   > Zobacz [zgodność wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby zobaczyć, które wersje systemu operacyjnego kontenera są obsługiwane na których wersjach systemu operacyjnego hosta i [znane problemy dla kontenerów](build-tools-container-issues.md) znanych problemów.
   
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
   > Aby uzyskać listę obciążeń i składników, zobacz [katalog składników Narzędzia kompilacji programu Visual Studio](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Jeśli obraz jest podstawą bezpośrednio na microsoft/windowsservercore, program .NET Framework może nie zostać poprawnie zainstalowany i nie jest wskazany błąd instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego oprzeć obraz na [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszym. Należy również pamiętać, że obrazy oznaczone w wersji 4.8 lub `SHELL`nowszej `RUN` mogą `ENTRYPOINT` używać programu PowerShell jako domyślnego , co spowoduje niepowodzenie i instrukcje.
   >
   > Zobacz [zgodność wersji kontenera systemu Windows,](/virtualization/windowscontainers/deploy-containers/version-compatibility) aby zobaczyć, które wersje systemu operacyjnego kontenera są obsługiwane na których wersjach systemu operacyjnego hosta i [znane problemy dla kontenerów](build-tools-container-issues.md) znanych problemów.

   ::: moniker-end
   
   > [!NOTE]
   > Kod `3010` błędu służy do wskazania sukcesu z wymaganym ponownym uruchomieniem, zobacz [MsiExec.exe komunikaty o błędach,](/windows/win32/msi/error-codes) aby uzyskać więcej informacji.

1. Uruchom następujące polecenie w tym katalogu.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślna wartość 1 GB nie jest wystarczająca, gdy są zainstalowane niektóre obciążenia; jednak może być w stanie skompilować tylko 1 GB pamięci w zależności od wymagań kompilacji.

   Ostateczny obraz jest oznaczony jako "buildtools2017:latest", dzięki czemu można go łatwo uruchomić w kontenerze jako "buildtools2017", ponieważ tag "najnowsze" jest domyślny, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji programu Visual Studio Build Tools 2017 w bardziej [zaawansowanym scenariuszu,](advanced-build-tools-container.md)możesz zamiast tego oznaczyć kontener z określonym numerem kompilacji programu Visual Studio, a także "najnowszym", aby kontenery mogły konsekwentnie używać określonej wersji.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślna wartość 1 GB nie jest wystarczająca, gdy są zainstalowane niektóre obciążenia; jednak może być w stanie skompilować tylko 1 GB pamięci w zależności od wymagań kompilacji.

   Ostateczny obraz jest oznaczony jako "buildtools2019:latest", dzięki czemu można go łatwo uruchomić w kontenerze jako "buildtools2019", ponieważ tag "ostatni" jest domyślny, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji programu Visual Studio Build Tools 2019 w bardziej [zaawansowanym scenariuszu,](advanced-build-tools-container.md)możesz zamiast tego oznaczyć kontener z określonym numerem kompilacji programu Visual Studio, a także "najnowszym", aby kontenery mogły konsekwentnie używać określonej wersji.

   ::: moniker-end

## <a name="using-the-built-image"></a>Korzystanie z wbudowanego obrazu

Teraz, gdy utworzono obraz, można go uruchomić w kontenerze, aby wykonać zarówno kompilacje interaktywne, jak i zautomatyzowane. W przykładzie użyto wiersza polecenia dewelopera, więc ścieżka i inne zmienne środowiskowe są już skonfigurowane.

1. Otwórz wiersz polecenia.

1. Uruchom kontener, aby uruchomić środowisko programu PowerShell ze wszystkimi ustawionymi zmiennymi środowiskowymi deweloperów:

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

Aby użyć tego obrazu dla przepływu pracy ciągłej integracji/ciągłego wdrażania, można opublikować go we własnym [rejestrze kontenerów platformy Azure](https://azure.microsoft.com/services/container-registry) lub innym wewnętrznym [rejestrze platformy Docker,](https://docs.docker.com/registry/deploying) aby serwery musiały go tylko pobierać.

   > [!NOTE]
   > Jeśli uruchomienie kontenera platformy Docker nie powiedzie się, prawdopodobnie wystąpi problem z instalacją programu Visual Studio. Można zaktualizować Dockerfile, aby usunąć krok, który wywołuje polecenie wsadowe programu Visual Studio. Dzięki temu można uruchomić kontener platformy Docker i odczytać dzienniki błędów instalacji.
   >
   > W pliku Dockerfile usuń `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` parametry i `ENTRYPOINT` parametry z polecenia. Polecenie powinno być `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]`teraz . Następnie odbuduj plik Dockerfile i wykonaj polecenie, `run` aby uzyskać dostęp do plików kontenera. Aby zlokalizować dzienniki błędów `$env:TEMP` instalacji, przejdź `dd_setup_<timestamp>_errors.log` do katalogu i znajdź plik.
   >
   > Po zidentyfikowaniu i rozwiązaniu problemu `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` z `&&` instalacją `ENTRYPOINT` można dodać parametry i parametry z powrotem do polecenia i odbudować plik Dockerfile.
   >
   > Aby uzyskać więcej informacji, zobacz [Znane problemy dla kontenerów](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Obciążenie i identyfikatory składników narzędzi kompilacji programu Visual Studio](workload-component-id-vs-build-tools.md)
