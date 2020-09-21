---
title: Środowisko uruchomieniowe platformy .NET Core
description: Przykładowe dostosowanie przy użyciu devinit dla repozytorium dotnet/Runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 477a498059be6d1ee5637a704512fd49b62e11b6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809112"
---
# <a name="net-core-runtime"></a>Środowisko uruchomieniowe platformy .NET Core

W tym przykładzie pokazano, jak dostosować środowisko uruchomieniowe programu .NET Core [/środowisko uruchomieniowe](https://github.com/dotnet/runtime) w celu automatycznego aprowizacji za pomocą usługi [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Ten skrypt jest wywoływany z _PostCloneSetup.ps1_ i może być również uruchamiany lokalnie w celu skonfigurowania repozytorium. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```batch
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Plik _packages.config_ jest plikiem [czekolady](https://chocolatey.org/) , który definiuje listę pakietów czekolady do zainstalowania. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.jsna

Zawartość [_.devinit.js_](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_ pliku.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Zawartość _.devcontainer.jsw_ pliku w katalogu głównym repozytorium.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
