---
title: Zaawansowany przykład dla kontenerów
description: Dowiedz się więcej na temat zaawansowanego przykładu dla kontenerów platformy Docker. W tym przykładzie plik Dockerfile używa określonego tagu wersji obrazu microsoft/dotnet-framework.
ms.custom: SEO-VS-2020
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2860a19592667008f585a4608eab23e0180dd2ac
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307703"
---
# <a name="advanced-example-for-containers"></a>Zaawansowany przykład dla kontenerów

::: moniker range="vs-2017"

Przykładowy plik Dockerfile w [narzędziu Install Build Tools w](build-tools-container.md) kontenerze zawsze używa obrazu [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) opartego na najnowszym obrazie microsoft/windowsservercore i najnowszym Visual Studio Build Tools instalatorze. Jeśli opublikujesz ten obraz w rejestrze [platformy Docker](https://azure.microsoft.com/services/container-registry) do ściągnięcie przez inne osoby, ten obraz może być w porządku w wielu scenariuszach. Jednak w praktyce częściej jest bardziej szczegółowe informacje o tym, jakiego obrazu podstawowego używasz, jakie pliki binarne pobierasz i które wersje narzędzi instalujesz.

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 jest obecnie w wersji zapoznawczej i nie [ma](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) licencji do użytku w środowiskach produkcyjnych.

::: moniker-end

::: moniker range=">=vs-2019"

Przykładowy plik Dockerfile w [narzędziu Install Build Tools w](build-tools-container.md) kontenerze zawsze używa obrazu [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) opartego na najnowszym obrazie microsoft/windowsservercore i najnowszym Visual Studio Build Tools instalatorze. Jeśli opublikujesz ten obraz w rejestrze [platformy Docker](https://azure.microsoft.com/services/container-registry) do ściągnięcie przez inne osoby, ten obraz może być w porządku w wielu scenariuszach. Jednak w praktyce częściej jest bardziej szczegółowe informacje o tym, jakiego obrazu podstawowego używasz, jakie pliki binarne pobierasz i które wersje narzędzi instalujesz.

::: moniker-end

W poniższym przykładzie plik Dockerfile używa określonego tagu wersji obrazu microsoft/dotnet-framework. Użycie określonego tagu dla obrazu podstawowego jest powszechnie spotykane i ułatwia zapamiętanie, że kompilowanie lub ponowne kompilowanie obrazów zawsze ma tę samą podstawę.

> [!NOTE]
> Nie można zainstalować programu Visual Studio na serwerze microsoft/windowsservercore:10.0.14393.1593 ani w żadnym opartym na nim obrazie, który ma znane problemy z uruchamianiem instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [Znane problemy dotyczące kontenerów](build-tools-container-issues.md).

Poniższy przykład pobiera najnowszą wersję narzędzi Build Tools. Jeśli chcesz użyć starszej wersji narzędzi kompilacji, którą można później zainstalować w kontenerze, musisz najpierw [utworzyć](create-an-offline-installation-of-visual-studio.md) i [zachować](update-a-network-installation-of-visual-studio.md) układ.

## <a name="install-script"></a>Instalowanie skryptu

Aby zbierać dzienniki w przypadku wystąpienia błędu instalacji, utwórz skrypt wsadowy o nazwie "Install.cmd" w katalogu roboczy, który zawiera następującą zawartość:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

W katalogu roboczy utwórz plik "Dockerfile" o następującej zawartości:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image.
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/runtime:4.8
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 w wersji 15.8 lub starszej (dowolny produkt) nie zostanie poprawnie zainstalowany w aplikacji mcr \. microsoft \. com windows \/ \/ servercore:1809 lub nowszej. Błąd nie jest wyświetlany.
   >
   > Aby [uzyskać więcej informacji, zobacz Znane problemy z kontenerami.](build-tools-container-issues.md)

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

::: moniker range=">=vs-2022"

>[!IMPORTANT]
> Visual Studio 2022 jest obecnie w wersji zapoznawczej i nie [ma](https://visualstudio.microsoft.com/license-terms/vs2022-prerelease/) licencji do użytku w środowiskach produkcyjnych.

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/17/preview/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/17/preview/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Uruchom następujące polecenie, aby skompilować obraz w bieżącym katalogu pracy:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
```

::: moniker-end

Opcjonalnie przekaż oba argumenty lub lub przy użyciu przełącznika wiersza polecenia, aby określić inny obraz podstawowy lub lokalizację układu wewnętrznego do `FROM_IMAGE` `CHANNEL_URL` obsługi `--build-arg` stałego obrazu.

> [!TIP]
> Aby uzyskać listę obciążeń i składników, zobacz [katalog Visual Studio Build Tools component](workload-component-id-vs-build-tools.md).
>

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

W tym przykładzie są pobierane określone narzędzia i sprawdza, czy skróty są zgodne. Pobiera również najnowsze narzędzie do zbierania dzienników Visual Studio i .NET, dzięki czemu w przypadku niepowodzenia instalacji można skopiować dzienniki na maszynę hosta w celu przeanalizowania błędu.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
> docker build -t buildtools2022:17.0 -t buildtools2022:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Po zakończeniu wykonywania ostatniego wiersza otwórz plik "%TEMP%\vslogs.zip" na swojej maszynie lub prześlij problem w Developer Community [internetowej.](https://aka.ms/feedback/suggest?space=8)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio Build Tools i identyfikatory składników](workload-component-id-vs-build-tools.md)
