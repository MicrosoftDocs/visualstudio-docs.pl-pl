---
title: Zaawansowany przykład dotyczący kontenerów
description: ''
ms.date: 04/18/2018
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fb273a54a89bb4c0339cac739b9dd0fe7fdd0afc
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415593"
---
# <a name="advanced-example-for-containers"></a>Zaawansowany przykład dotyczący kontenerów

Przykładowy plik Dockerfile w [Zainstaluj narzędzia kompilacji w kontenerze](build-tools-container.md) zawsze używa [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) obrazu na podstawie najnowszego obrazu microsoft/windowsservercore i wizualizacja Instalator programu Studio Build Tools. W przypadku publikowania tego obrazu na [rejestru platformy Docker](https://azure.microsoft.com/services/container-registry) innymi ściągania, ten obraz może być akceptowalne dla wielu scenariuszy. Jednak w praktyce jest to bardziej powszechne na konkretnym jakie podstawowy obrazu, należy użyć, z których plików binarnych, należy pobrać, i który narzędzi wersje, należy zainstalować.

Poniższy przykład pliku Dockerfile taga konkretną wersję obrazu microsoft/dotnet platformy. Używanie konkretny tag podstawowy obraz nie jest powszechne i umożliwia łatwe do zapamiętania ten budynek lub odbudowywania obrazów zawsze ma tej samej zasadzie.

> [!NOTE]
> Nie można zainstalować programu Visual Studio do microsoft/windowsservercore:10.0.14393.1593 lub dowolny obraz oparty na ich temat, istnieją znane problemy z uruchomieniem Instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md).

Poniższy przykład pobiera najnowszą wersję narzędzia Build Tools. Jeśli chcesz używać starszej wersji narzędzia kompilacji, który można zainstalować w kontenerze później, należy najpierw [tworzenie](create-an-offline-installation-of-visual-studio.md) i [Obsługa](update-a-network-installation-of-visual-studio.md) układu.

## <a name="install-script"></a>Skrypt instalacji

Aby zbierać dzienniki, gdy błąd instalacji wystąpi, Utwórz skrypt wsadowy, który nosi nazwę "Install.cmd" w katalogu roboczym, który zawiera następującą zawartością:

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

W katalogu roboczym należy utworzyć "Dockerfile" o następującej zawartości:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
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
   > Visual Studio 2017, wersja, należy zachować 15,8 lub starszym (dowolny produkt) nie zostaną prawidłowo zainstalowane na mcr\.microsoft\.com\/windows\/servercore:1809 lub nowszej. Nie jest wyświetlany błąd.
   >
   > Zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md) Aby uzyskać więcej informacji.

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
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

Opcjonalnie przekazać jednego lub obu tych `FROM_IMAGE` lub `CHANNEL_URL` argumentów za pomocą `--build-arg` przełącznik wiersza polecenia, aby określić inny obraz podstawowy lub lokalizacji wewnętrznych układu w celu zachowania stałego obrazu.

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

W tym przykładzie pobiera określone narzędzia i weryfikuje, czy skróty są zgodne. Również pobraniu najnowszy program Visual Studio i narzędzia kolekcji dziennika platformy .NET tak, aby w przypadku niepowodzenia instalacji, możesz skopiować dzienniki na komputer hosta do analizowania awarii.

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

::: moniker-end

After the last line finishes executing, open "%TEMP%\vslogs.zip" on your machine, or submit an issue on the [Developer Community](https://developercommunity.visualstudio.com) website.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## See also

* [Install Build Tools into a Container](build-tools-container.md)
* [Known Issues for Containers](build-tools-container-issues.md)
* [Visual Studio Build Tools workload and component IDs](workload-component-id-vs-build-tools.md)
