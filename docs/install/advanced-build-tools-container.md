---
title: Zaawansowany przykład dla kontenerów
description: ''
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 92d0e984d4ccf595af2821dff9c02d069b16404d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80273845"
---
# <a name="advanced-example-for-containers"></a>Zaawansowany przykład dla kontenerów

::: moniker range="vs-2017"

Przykład pliku dockerfile w [narzędziu do tworzenia kompilacji do kontenera](build-tools-container.md) zawsze używa obrazu [Microsoft/dotnet-Framework: 4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) na podstawie najnowszego obrazu Microsoft/windowsservercore i najnowszego Instalatora Visual Studio Build Tools. Jeśli opublikujesz ten obraz w [rejestrze platformy Docker](https://azure.microsoft.com/services/container-registry) dla innych użytkowników, ten obraz może być poprawny w wielu scenariuszach. Jednak w rzeczywistości jest to bardziej powszechne, aby określić, jaki podstawowy obraz jest używany, jakie dane binarne są pobierane i które instalowane wersje narzędzi.

::: moniker-end

::: moniker range="vs-2019"

Przykład pliku dockerfile w [narzędziu do tworzenia kompilacji do kontenera](build-tools-container.md) zawsze używa obrazu [Microsoft/dotnet-Framework: 4.8](https://hub.docker.com/r/microsoft/dotnet-framework) na podstawie najnowszego obrazu Microsoft/windowsservercore i najnowszego Instalatora Visual Studio Build Tools. Jeśli opublikujesz ten obraz w [rejestrze platformy Docker](https://azure.microsoft.com/services/container-registry) dla innych użytkowników, ten obraz może być poprawny w wielu scenariuszach. Jednak w rzeczywistości jest to bardziej powszechne, aby określić, jaki podstawowy obraz jest używany, jakie dane binarne są pobierane i które instalowane wersje narzędzi.

::: moniker-end

W poniższym przykładzie pliku dockerfile używa określonego znacznika wersji obrazu Microsoft/dotnet-Framework. Użycie określonego tagu dla obrazu podstawowego to commonplace i ułatwia zapamiętanie, że Kompilowanie lub rekompilowanie obrazów zawsze jest takie samo.

> [!NOTE]
> Nie można zainstalować programu Visual Studio w programie Microsoft/windowsservercore: 10.0.14393.1593 ani na podstawie jego obrazu, który ma znane problemy z uruchamianiem Instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md).

Poniższy przykład Pobiera najnowszą wersję narzędzi kompilacji. Jeśli chcesz użyć wcześniejszej wersji narzędzi do kompilacji, którą można zainstalować w kontenerze później, musisz najpierw [utworzyć](create-an-offline-installation-of-visual-studio.md) i [zachować](update-a-network-installation-of-visual-studio.md) układ.

## <a name="install-script"></a>Zainstaluj skrypt

Aby zbierać dzienniki w przypadku wystąpienia błędu instalacji, Utwórz skrypt wsadowy o nazwie "Install. cmd" w katalogu roboczym, który zawiera następującą zawartość:

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

W katalogu roboczym Utwórz "pliku dockerfile" z następującą zawartością:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
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
   > Program Visual Studio 2017 w wersji 15,8 lub starszej (dowolny produkt) nie zostanie prawidłowo zainstalowany na MCR \. Microsoft \. com \/ Windows \/ ServerCore: 1809 lub nowszy. Nie jest wyświetlany żaden błąd.
   >
   > Aby uzyskać więcej informacji, zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md) .

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

Uruchom następujące polecenie, aby skompilować obraz w bieżącym katalogu roboczym:

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

Opcjonalnie Przekaż jeden lub oba `FROM_IMAGE` lub `CHANNEL_URL` argumenty przy użyciu `--build-arg` przełącznika wiersza polecenia, aby określić inny obraz podstawowy lub lokalizację układu wewnętrznego w celu utrzymania stałego obrazu.

   > [!TIP]
   > Aby zapoznać się z listą obciążeń i składników, zobacz [katalog składników Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

Ten przykład pobiera określone narzędzia i sprawdza, czy skróty pasują do siebie. Pobiera również najnowsze narzędzie do zbierania dzienników programu Visual Studio i programu .NET, dzięki czemu w przypadku wystąpienia błędu instalacji można skopiować dzienniki na maszynę hosta w celu przeanalizowania błędu.

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

Po zakończeniu ostatniego wiersza Otwórz pozycję "% TEMP% \vslogs.zip" na swojej maszynie lub Prześlij problem do witryny internetowej [społeczności deweloperów](https://developercommunity.visualstudio.com) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio Build Tools obciążenia i identyfikatory składników](workload-component-id-vs-build-tools.md)
