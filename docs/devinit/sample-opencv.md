---
title: OpenCV
description: Przykładowe dostosowanie przy użyciu devinit dla systemu Linux i Windows dla repozytorium OpenCV.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: a2f284e1e464ab41391f60c546ce01d418ff377b
ms.sourcegitcommit: 8efe6b45d65f9db23f5575c15155fe363fa12cdb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92750118"
---
# <a name="opencv"></a>OpenCV

W tym przykładzie pokazano, jak dostosować [Codespaces GitHub](https://github.com/features/codespaces) , aby można było opracowywać projekty wieloplatformowe, takie jak [OpenCV/OpenCV](https://github.com/opencv/opencv).

Poniższe dostosowania są już stosowane w rozwidleniu [Microsoft/OpenCV](https://github.com/microsoft/opencv) i umożliwiają tworzenie elementów docelowych dla systemu Windows i Ubuntu.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Dostosowanie z devcontainer.jswłączony i devinit.jsna

`.devcontainer`Katalog musi zawierać następujące pliki:

* devcontainer.jsna
* devinit.jsna

### <a name="devcontainerjson"></a>devcontainer.jsna

Poniżej znajduje się zawartość _devcontainer.js_ pliku.

```json
{
  "postCreateCommand": "devinit init"
}
```

`postCreateCommand`Uruchamia narzędzie [devinit](devinit-and-codespaces.md) , które wykorzystuje _devinit.json_ .

### <a name="devinitjson"></a>devinit.jsna

Poniżej znajduje się zawartość [_devinit.js_](devinit-json.md) pliku.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

_devinit.json_ jest plikiem używanym przez narzędzie [devinit](devinit-and-codespaces.md) i musi znajdować się w tym samym katalogu _devcontainer.js_ on.

W tym przykładzie narzędzie [WSL-Install](tool-wsl-install.md) służy do tworzenia wystąpienia WSL z systemem Ubuntu 20,04 i udostępniania go za pomocą podstawowych narzędzi programistycznych języka C++.
## <a name="targeting-windows-or-linux"></a>Kierowanie dla systemu Windows lub Linux

Domyślna konfiguracja kompilacji dla systemu Windows jest zawsze tworzona o nazwie `x64-Debug` .

Po dodaniu powyższych plików, po utworzeniu wystąpienia Codespace, program Visual Studio Inicjuje nowe połączenie SSH w [Menedżerze połączeń](/cpp/linux/connect-to-your-remote-linux-computer)i tworzy nową konfigurację w selektorze konfiguracji, który jest przeznaczony dla wystąpienia Ubuntu za pośrednictwem połączenia SSH.

![Konfiguracja określania wartości docelowej Ubuntu](media/wsl-ssh-linux-configuration.png).

Wybierając wyróżnioną konfigurację, która jest przeznaczona dla WSL, możliwe jest skompilowanie i debugowanie obiektów docelowych kompilacji OpenCV.
