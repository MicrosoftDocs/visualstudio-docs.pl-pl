---
title: Zaawansowany przykład kontenerów
description: ''
ms.date: 07/03/2019
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0a88815c4a2853270b539a3e012297b681af62e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114944"
---
# <a name="advanced-example-for-containers"></a>Zaawansowany przykład kontenerów

::: moniker range="vs-2017"

Przykładowy plik Dockerfile w [instalacji narzędzi kompilacji w kontenerze](build-tools-container.md) zawsze używa obrazu [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) na podstawie najnowszego obrazu microsoft/windowsservercore i najnowszego instalatora narzędzi kompilacji programu Visual Studio. Jeśli publikujesz ten obraz w [rejestrze platformy Docker](https://azure.microsoft.com/services/container-registry) dla innych do ciągnięcia, ten obraz może być w porządku dla wielu scenariuszy. Jednak w praktyce częściej można dokłdnąć, jakiego obrazu podstawowego używasz, pobieranych plików binarnych i instalowanych wersji narzędzi.

::: moniker-end

::: moniker range="vs-2019"

Przykładowy plik Dockerfile w [instalacji narzędzi kompilacji w kontenerze](build-tools-container.md) zawsze używa obrazu [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) na podstawie najnowszego obrazu microsoft/windowsservercore i najnowszego instalatora narzędzi kompilacji programu Visual Studio. Jeśli publikujesz ten obraz w [rejestrze platformy Docker](https://azure.microsoft.com/services/container-registry) dla innych do ciągnięcia, ten obraz może być w porządku dla wielu scenariuszy. Jednak w praktyce częściej można dokłdnąć, jakiego obrazu podstawowego używasz, pobieranych plików binarnych i instalowanych wersji narzędzi.

::: moniker-end

Poniższy przykład Dockerfile używa określonego tagu wersji obrazu microsoft/dotnet-framework. Używanie określonego znacznika dla obrazu podstawowego jest powszechne i ułatwia zapamiętanie, że tworzenie lub odbudowywanie obrazów ma zawsze tę samą podstawę.

> [!NOTE]
> Nie można zainstalować programu Visual Studio w programie Microsoft/windowsservercore:10.0.14393.1593 lub na jego podstawie dowolnego obrazu, który ma znane problemy z uruchomieniem instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [Znane problemy dla kontenerów](build-tools-container-issues.md).

Poniższy przykład pobiera najnowszą wersję narzędzi kompilacji. Jeśli chcesz użyć wcześniejszej wersji narzędzi kompilacji, które można zainstalować w kontenerze później, należy najpierw [utworzyć](create-an-offline-installation-of-visual-studio.md) i [obsługiwać](update-a-network-installation-of-visual-studio.md) układ.

## <a name="install-script"></a>Instalowanie skryptu

Aby zbierać dzienniki po wystąpieniu błędu instalacji, utwórz skrypt wsadowy o nazwie "Install.cmd" w katalogu roboczym, który zawiera następującą zawartość:

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

## <a name="dockerfile"></a>Plik dockerfile

W katalogu roboczym utwórz "Dockerfile" z następującą zawartością:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Program Visual Studio 2017 w wersji 15.8 lub nowszej\.\.(dowolny produkt) nie zostanie poprawnie zainstalowany w programie mcr microsoft com\/windows\/servercore:1809 lub nowszym. Nie jest wyświetlany żaden błąd.
   >
   > Aby uzyskać więcej [informacji, zobacz Znane problemy dla kontenerów.](build-tools-container-issues.md)

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Uruchom następujące polecenie, aby utworzyć obraz w bieżącym katalogu roboczym:

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

Opcjonalnie przekaż jeden `FROM_IMAGE` lub `CHANNEL_URL` oba `--build-arg` lub argumenty za pomocą przełącznika wiersza polecenia, aby określić inny obraz podstawowy lub lokalizację układu wewnętrznego w celu utrzymania stałego obrazu.

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

W tym przykładzie pobiera określone narzędzia i sprawdza, czy skróty są zgodne. Pobiera również najnowsze narzędzie do zbierania dzienników programu Visual Studio i .NET, dzięki czemu w przypadku wystąpienia błędu instalacji można skopiować dzienniki do komputera hosta w celu przeanalizowania błędu.

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

Po zakończeniu wykonywania ostatniego wiersza otwórz "%TEMP%\vslogs.zip" na komputerze lub prześlij problem w witrynie [społeczności deweloperów.](https://developercommunity.visualstudio.com)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Obciążenie i identyfikatory składników narzędzi kompilacji programu Visual Studio](workload-component-id-vs-build-tools.md)
