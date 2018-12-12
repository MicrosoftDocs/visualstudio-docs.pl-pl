---
title: Zaawansowany przykład dotyczący kontenerów
description: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: ''
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 408c66d87dbc932e09e1d5744ab5595672a00534
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307635"
---
# <a name="advanced-example-for-containers"></a>Zaawansowany przykład dotyczący kontenerów

Przykładowy plik Dockerfile w [Zainstaluj narzędzia kompilacji w kontenerze](build-tools-container.md) zawsze używa [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) obrazu na podstawie najnowszego obrazu microsoft/windowsservercore i wizualizacja Instalator programu Studio 2017 narzędzia kompilacji. W przypadku publikowania tego obrazu na [rejestru platformy Docker](https://azure.microsoft.com/services/container-registry) innymi ściągania, ten obraz może być akceptowalne dla wielu scenariuszy. Jednak w praktyce jest to bardziej powszechne na konkretnym jakie podstawowy obrazu, należy użyć, z których plików binarnych, należy pobrać, i który narzędzi wersje, należy zainstalować.

Poniższy przykład pliku Dockerfile taga konkretną wersję obrazu microsoft/dotnet platformy. Używanie konkretny tag podstawowy obraz nie jest powszechne i umożliwia łatwe do zapamiętania ten budynek lub odbudowywania obrazów zawsze ma tej samej zasadzie.

> [!NOTE]
> Nie można zainstalować programu Visual Studio do microsoft/windowsservercore:10.0.14393.1593 lub dowolny obraz oparty na ich temat, istnieją znane problemy z uruchomieniem Instalatora w kontenerze. Aby uzyskać więcej informacji, zobacz [znane problemy dotyczące](build-tools-container-issues.md).

Poniższy przykład pobiera najnowszą wersję kompilacji narzędzia 2017. Jeśli chcesz używać starszej wersji narzędzi Build Tools można zainstalować w kontenerze później, należy najpierw [tworzenie](create-an-offline-installation-of-visual-studio.md) i [Obsługa](update-a-network-installation-of-visual-studio.md) układu.

## <a name="install-script"></a>Skrypt instalacji

Aby dzienniki były zbierane, gdy wystąpi błąd instalacji, w katalogu roboczym, należy utworzyć skrypt wsadowy o nazwie "Install.cmd", o następującej zawartości:

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

## <a name="dockerfile"></a>Plik Dockerfile

W katalogu roboczym należy utworzyć "Dockerfile" o następującej zawartości:

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
   > Visual Studio 2017, wersja, należy zachować 15,8 lub starszym (dowolny produkt) nie zostaną prawidłowo zainstalowane na mcr<span></span>.microsoft\.com\/windows\/servercore:1809 lub nowszej. Nie jest wyświetlany błąd.
   >
   > Zobacz [znane problemy dotyczące kontenerów](build-tools-container-issues.md) Aby uzyskać więcej informacji.

Uruchom następujące polecenie, aby utworzyć obraz w bieżącym katalogu roboczym:

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

Opcjonalnie przekazać jednego lub obu tych `FROM_IMAGE` lub `CHANNEL_URL` argumentów za pomocą `--build-arg` przełącznik wiersza polecenia, aby określić inny obraz podstawowy lub lokalizacji wewnętrznych układu w celu zachowania stałego obrazu.

## <a name="diagnosing-install-failures"></a>Diagnozowanie błędów instalacji

W tym przykładzie pobiera określone narzędzia i weryfikuje, czy skróty są zgodne. Również pobraniu najnowszy program Visual Studio i narzędzia kolekcji dziennika platformy .NET tak, aby w przypadku niepowodzenia instalacji, możesz skopiować dzienniki na komputer hosta do analizowania awarii.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Po ukończeniu wykonywania ostatni wiersz Otwórz "% TEMP%\vslogs.zip" na komputerze lub Prześlij problem na [społeczności deweloperów](https://developercommunity.visualstudio.com) witryny sieci web.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie narzędzi do kompilacji w kontenerze](build-tools-container.md)
* [Znane problemy z kontenerami](build-tools-container-issues.md)
* [Visual Studio 2017 kompilacji narzędzia obciążeń i składników identyfikatorów](workload-component-id-vs-build-tools.md)
