---
title: Instalowanie narzędzia Visual Studio Build Tools do kontenera
titleSuffix: ''
description: Dowiedz się, jak zainstalować narzędzia Visual Studio Build Tools w kontenerze Windows do obsługi ciągłej integracji i przepływów pracy ciągłego dostarczania (CI/CD).
ms.date: 07/03/2019
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
ms.openlocfilehash: 53049d37f23a72adb337cdad629f4c689c83707e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114604"
---
# <a name="install-build-tools-into-a-container"></a>Zainstaluj narzędzia kompilacji do kontenera

Visual Studio Build Tools można zainstalować w kontenerze Windows do obsługi ciągłej integracji i przepływów pracy ciągłego dostarczania (CI/CD). Ten artykuł przeprowadzi Cię przez jakie zmiany konfiguracji platformy Docker są wymagane, a także co [obciążenia i składniki](workload-component-id-vs-build-tools.md) można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) to doskonały sposób do pakietu przez system kompilacji spójne, można użyć nie tylko w środowisku serwera ciągłej integracji/ciągłego wdrażania, ale również w środowiskach programowania. Na przykład można zainstalować kod źródłowy w kontenerze, który ma zostać utworzony przez dostosowane środowisko, gdy będziesz nadal używać programu Visual Studio lub innych narzędzi, należy napisać kod. Jeśli przepływ pracy ciągłej integracji/ciągłego wdrażania korzysta z tego samego obrazu kontenera, możesz mieć pewność, Twój kod się kompiluje spójne. Możesz używać kontenerów środowiska uruchomieniowego sprawdzania spójności, która jest często mikrousługi przy użyciu wielu kontenerów z systemem aranżacji; jednak wykracza poza zakres tego artykułu.

Jeśli program Visual Studio Build Tools nie ma wymagane do kompilowania swojego kodu źródłowego, można te same kroki dla innych produktów Visual Studio. Należy jednak pamiętać, że kontenery Windows nie obsługują interaktywny interfejs użytkownika, więc wszystkie polecenia, które muszą być zautomatyzowane.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Poniżej założono pewną znajomość [platformy Docker](https://www.docker.com/what-docker) . Jeśli nie znasz jeszcze programu Docker w systemie Windows, przeczytaj temat jak [zainstalować i skonfigurować aparat platformy Docker w systemie Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Poniższy obraz podstawowy jest przykładem i może nie zadziałać w systemie. Przeczytaj temat [zgodność wersji kontenera systemu Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) , aby określić, który obraz podstawowy ma być używany w danym środowisku.

## <a name="create-and-build-the-dockerfile"></a>Utwórz i skompiluj plik Dockerfile

Zapisz poniższy plik Dockerfile do nowego pliku na dysku. Jeśli plik nosi po prostu plik Dockerfile"", który jest rozpoznawany przez domyślny.

> [!WARNING]
> Ten przykład pliku dockerfile wyklucza tylko starsze zestawy Windows SDK, których nie można zainstalować w kontenerach. Wcześniejsze wersje powodują niepowodzenie polecenia kompilacji.

1. Otwórz wiersz polecenia.

1. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

1. Zmień katalogi do tego nowego katalogu:

   ```shell
   cd C:\BuildTools
   ```

1. Zapisz C:\BuildTools\Dockerfile następującą zawartością.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > W przypadku opierania się na obrazie bezpośrednio w usłudze Microsoft/windowsservercore lub mcr.microsoft.com/windows/servercore (Zobacz artykuł [Microsoft syndykats Catalog katalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)), .NET Framework może nie zostać poprawnie zainstalowany i nie jest wskazywany żaden błąd instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy oprzeć obraz na [platformie Microsoft/dotnet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszym. Należy również zauważyć, że obrazy otagowane w wersji 4.7.2 lub nowszej mogą używać programu PowerShell jako domyślnego `SHELL`, co spowoduje niepowodzenie wykonywania instrukcji `RUN` i `ENTRYPOINT`.
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

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > Jeśli zamierzasz oprzeć obraz bezpośrednio w firmie Microsoft/windowsservercore, .NET Framework może nie zostać zainstalowana prawidłowo i nie wskazano błędu instalacji. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy oprzeć obraz na [platformie Microsoft/dotnet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Należy również zauważyć, że obrazy oznaczone w wersji 4,8 lub nowszej mogą używać programu PowerShell jako domyślnego `SHELL`, co spowoduje niepowodzenie instrukcji `RUN` i `ENTRYPOINT`.
   >
   > Zobacz [zgodność wersji kontenera systemu Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) , aby sprawdzić, które wersje systemu operacyjnego kontenera są obsługiwane, w których wersjach systemu operacyjnego hosta i [znanych problemów dotyczących kontenerów](build-tools-container-issues.md) znanych problemów.

   ::: moniker-end
   
   > [!NOTE]
   > Kod błędu `3010` jest używany do wskazania sukcesu z wymaganym ponownym uruchomieniem. zobacz [komunikaty o błędach msiexec. exe](/windows/win32/msi/error-codes) , aby uzyskać więcej informacji.

1. Uruchom następujące polecenie, w tym katalogu.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślnie 1 GB nie wystarcza w przypadku zainstalowania niektórych obciążeń; Jednak może być możliwe skompilowanie tylko 1 GB pamięci, w zależności od wymagań dotyczących kompilacji.

   Finalnego obrazu jest oznakowany "buildtools2017:latest", aby można było łatwo uruchomić go w kontenerze jako "buildtools2017" od "najnowsza" tag jest domyślnie, jeśli jest określony żaden tag. Jeśli chcesz użyć określonej wersji programu Visual Studio kompilacji 2017 narzędzia w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), może być zamiast tego tagu kontener za pomocą określonego programu Visual Studio kompilacji numer, a także "najnowsza", więc kontenerów można użyć określonego Wersja spójne.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Domyślnie 1 GB nie wystarcza w przypadku zainstalowania niektórych obciążeń; Jednak może być możliwe skompilowanie tylko 1 GB pamięci, w zależności od wymagań dotyczących kompilacji.

   Obraz końcowy jest oznaczony jako "buildtools2019: Najnowsza", więc można go łatwo uruchomić w kontenerze jako "buildtools2019", ponieważ tag "Najnowsza" jest wartością domyślną, jeśli nie określono tagu. Jeśli chcesz użyć określonej wersji Visual Studio Build Tools 2019 w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), możesz zamiast tego oznaczyć kontener z konkretnym numerem kompilacji programu Visual Studio, a także "najnowszy", aby kontenery mogły korzystać z określonej wersji.

   ::: moniker-end

## <a name="using-the-built-image"></a>Przy użyciu wbudowanego obrazu

Teraz, po utworzeniu obrazu, możesz ją uruchomić w kontenerze celu zarówno interaktywny, jak i automatyczne kompilacje. W przykładzie użyto wiersza polecenia dewelopera, więc zmiennej PATH i inne zmienne środowiskowe są już skonfigurowane.

1. Otwórz wiersz polecenia.

1. Uruchom kontener, aby rozpoczynać Środowisko PowerShell dla wszystkich deweloperów zmiennych środowiskowych ustawionych:

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio Build Tools obciążenia i identyfikatory składników](workload-component-id-vs-build-tools.md)
