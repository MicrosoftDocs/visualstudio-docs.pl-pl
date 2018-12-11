---
title: Instalowanie narzędzia Visual Studio Build Tools do kontenera
titleSuffix: ''
description: Dowiedz się, jak zainstalować narzędzia Visual Studio Build Tools w kontenerze Windows do obsługi ciągłej integracji i przepływów pracy ciągłego dostarczania (CI/CD).
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37ce2fc60ac2a57baddf62e68a900349ed072f4d
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160091"
---
# <a name="install-build-tools-into-a-container"></a>Zainstaluj narzędzia kompilacji do kontenera

Visual Studio Build Tools można zainstalować w kontenerze Windows do obsługi ciągłej integracji i przepływów pracy ciągłego dostarczania (CI/CD). Ten artykuł przeprowadzi Cię przez jakie zmiany konfiguracji platformy Docker są wymagane, a także co [obciążenia i składniki](workload-component-id-vs-build-tools.md) można zainstalować w kontenerze.

[Kontenery](https://www.docker.com/what-container) to doskonały sposób do pakietu przez system kompilacji spójne, można użyć nie tylko w środowisku serwera ciągłej integracji/ciągłego wdrażania, ale również w środowiskach programowania. Na przykład można zainstalować kod źródłowy w kontenerze, który ma zostać utworzony przez dostosowane środowisko, gdy będziesz nadal używać programu Visual Studio lub innych narzędzi, należy napisać kod. Jeśli przepływ pracy ciągłej integracji/ciągłego wdrażania korzysta z tego samego obrazu kontenera, możesz mieć pewność, Twój kod się kompiluje spójne. Możesz używać kontenerów środowiska uruchomieniowego sprawdzania spójności, która jest często mikrousługi przy użyciu wielu kontenerów z systemem aranżacji; jednak wykracza poza zakres tego artykułu.

Jeśli program Visual Studio Build Tools nie ma wymagane do kompilowania swojego kodu źródłowego, można te same kroki dla innych produktów Visual Studio. Należy jednak pamiętać, że kontenery Windows nie obsługują interaktywny interfejs użytkownika, więc wszystkie polecenia, które muszą być zautomatyzowane.

## <a name="overview"></a>Omówienie

Za pomocą [Docker](https://www.docker.com/what-docker) tworzenia obrazu, z której możesz tworzyć kontenery, które są kompilowane w kodzie źródłowym. Przykład pliku Dockerfile instaluje najnowszy program Visual Studio kompilacji narzędzia 2017 i innych programach przydatna często używane do tworzenia kodu źródłowego. Można dalej modyfikować, własny plik Dockerfile, aby uwzględnić inne narzędzia i skrypty, aby uruchomić testy, opublikuj dane wyjściowe kompilacji i nie tylko.

Jeśli zainstalowano już Docker for Windows, możesz przejść do kroku 3.

## <a name="step-1-enable-hyper-v"></a>Krok 1. Włączanie funkcji Hyper-V

Funkcji Hyper-V nie jest włączona domyślnie. Musi być włączone, można uruchomić aparatu Docker for Windows, ponieważ obecnie tylko izolacji funkcji Hyper-V jest obsługiwana w przypadku systemu Windows 10.

* [Włączanie funkcji Hyper-V w systemie Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Włączanie funkcji Hyper-V w systemie Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> Wirtualizacja musi być włączona na tym komputerze. Zazwyczaj jest włączona domyślnie Jednak jeśli niepowodzenia instalacji funkcji Hyper-V, zapoznaj się z dokumentacją systemu, jak włączyć wirtualizację.

## <a name="step-2-install-docker-for-windows"></a>Krok 2. Zainstalować platformę Docker for Windows

Jeśli używasz systemu Windows 10, możesz [Pobierz i zainstaluj platformę Docker Community Edition](https://docs.docker.com/docker-for-windows/install). Jeśli używasz systemu Windows Server 2016, postępuj zgodnie z [instrukcjami, aby zainstalować platformę Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Krok 3. Przełącz się do Windows kontenery

Tworzenie narzędzi 2017 można zainstalować tylko na Windows, co wymaga [przełączyć się do kontenerów Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Kontenery Windows w systemie Windows 10 obsługują tylko [izolacji funkcji Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), podczas gdy kontenery Windows w systemie Windows Server 2016 obsługuje zarówno funkcji Hyper-V i izolację procesów.

## <a name="step-4-expand-maximum-container-disk-size"></a>Krok 4. Rozwiń kontener maksymalny rozmiar dysku

Program Visual Studio Build Tools — i w większym stopniu, w programie Visual Studio — wymagają dużej ilości miejsca na dysku wszystkie narzędzia, które mają zostać zainstalowane. Mimo, że przykładowy plik Dockerfile powoduje wyłączenie pamięci podręcznej pakietu, rozmiar dysku obrazów kontenerów musisz zwiększyć miejsce wymagane. Obecnie w Windows, możesz tylko zwiększyć rozmiar dysku, zmieniając konfigurację platformy Docker.

**W systemie Windows 10**:

1. [Kliknij prawym przyciskiem myszy ikonę platformy Docker for Windows](https://docs.docker.com/docker-for-windows/#docker-settings) na pasku zadań i kliknij przycisk **ustawienia**.
2. [Kliknij pozycję demona](https://docs.docker.com/docker-for-windows/#docker-daemon) sekcji.
3. [Przełącz **podstawowe** ](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) przycisk, aby **zaawansowane**.
4. Dodaj następującą właściwość JSON w tablicy w celu zwiększenia miejsca na dysku do 120 GB (więcej niż wystarczająca dla narzędzia Build Tools możliwości rozbudowy).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Ta właściwość jest dodawany do niczego, którą już posiadasz. Na przykład za pomocą tych zmian dotyczy domyślny plik konfiguracji demona, powinien zostać wyświetlony:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Kliknij przycisk **zastosować**.

**W systemie Windows Server 2016**:

1. Zatrzymaj usługę "docker":

   ```shell
   sc.exe stop docker
   ```

2. W wierszu polecenia z podwyższonym poziomem uprawnień należy edytować "% ProgramData%\Docker\config\daemon.json" (lub niezależnie od rodzaju określony do `dockerd --config-file`).
3. Dodaj następującą właściwość JSON w tablicy w celu zwiększenia miejsca na dysku do 120 GB (więcej niż wystarczająca dla narzędzia Build Tools możliwości rozbudowy).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Ta właściwość jest dodawany do niczego, którą już posiadasz.
4. Zapisz i zamknij plik.
5. Uruchom usługę "docker":

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Krok 5. Utwórz i skompiluj plik Dockerfile

Zapisz poniższy plik Dockerfile do nowego pliku na dysku. Jeśli plik nosi po prostu plik Dockerfile"", który jest rozpoznawany przez domyślny.

> [!NOTE]
> W tym przykładzie plik Dockerfile tylko wyklucza starszych zestawów SDK Windows, której nie można zainstalować w kontenerach. Starsze wersje spowodować, że polecenie kompilacji, aby zakończyć się niepowodzeniem.

1. Otwórz wiersz polecenia.
2. Utwórz nowy katalog (zalecane):

   ```shell
   mkdir C:\BuildTools
   ```

3. Zmień katalogi do tego nowego katalogu:

   ```shell
   cd C:\BuildTools
   ```

3. Zapisz C:\BuildTools\Dockerfile następującą zawartością.

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
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

   > [!NOTE]
   > Jeśli obraz jest oparty bezpośrednio na microsoft/windowsservercore, .NET Framework nie może być poprawnie zainstalowany i błąd instalacji nie zostanie zgłoszony. Kod zarządzany może nie działać po zakończeniu instalacji. Zamiast tego należy utworzyć obraz na [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) lub nowszej. Należy również zauważyć, nowsze obrazów może używać programu PowerShell jako domyślny `SHELL` co spowoduje `RUN` i `ENTRYPOINT` instrukcjami, aby zakończyć się niepowodzeniem.

4. Uruchom następujące polecenie, w tym katalogu.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   To polecenie tworzy plik Dockerfile w bieżącym katalogu przy użyciu 2 GB pamięci. Wartość domyślna 1 GB nie wystarcza podczas instalowania niektórych obciążeń; jednak może być zdolny do skompilowania z tylko 1 GB pamięci, w zależności od wymagań dotyczących kompilacji.

   Finalnego obrazu jest oznakowany "buildtools2017:latest", aby można było łatwo uruchomić go w kontenerze jako "buildtools2017" od "najnowsza" tag jest domyślnie, jeśli jest określony żaden tag. Jeśli chcesz użyć określonej wersji programu Visual Studio kompilacji 2017 narzędzia w bardziej [zaawansowanym scenariuszu](advanced-build-tools-container.md), może być zamiast tego tagu kontener za pomocą określonego programu Visual Studio kompilacji numer, a także "najnowsza", więc kontenerów można użyć określonego Wersja spójne.

## <a name="step-6-using-the-built-image"></a>Krok 6. Przy użyciu wbudowanego obrazu

Teraz, po utworzeniu obrazu, możesz ją uruchomić w kontenerze celu zarówno interaktywny, jak i automatyczne kompilacje. W przykładzie użyto wiersza polecenia dewelopera, więc zmiennej PATH i inne zmienne środowiskowe są już skonfigurowane.

1. Otwórz wiersz polecenia.
2. Uruchom kontener, aby rozpoczynać Środowisko PowerShell dla wszystkich deweloperów zmiennych środowiskowych ustawionych:

   ```shell
   docker run -it buildtools2017
   ```

Aby użyć tego obrazu dla przepływu pracy ciągłej integracji/ciągłego wdrażania, można opublikować ją w ramach swojej własnej [usługi Azure Container Registry](https://azure.microsoft.com/services/container-registry) lub innych wewnętrznych [rejestru platformy Docker](https://docs.docker.com/registry/deploying) tak serwerów wystarczy wyciągniesz go.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Zaawansowany przykład dotyczący kontenerów](advanced-build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio 2017 kompilacji narzędzia obciążeń i składników identyfikatorów](workload-component-id-vs-build-tools.md)
