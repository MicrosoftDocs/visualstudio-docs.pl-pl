---
title: Środowisko uruchomieniowe platformy .NET Core
description: Przykładowe dostosowanie przy użyciu devinit dla repozytorium dotnet/Runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e2565a215ca97d2933dee14e639772f43da3f51f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943579"
---
# <a name="net-core-runtime"></a>Środowisko uruchomieniowe platformy .NET Core

W tym przykładzie pokazano, jak dostosować środowisko uruchomieniowe programu .NET Core [/środowisko uruchomieniowe](https://github.com/dotnet/runtime) w celu automatycznego aprowizacji za pomocą usługi [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Ten skrypt jest wywoływany z _PostCloneSetup.ps1_ i może być również uruchamiany lokalnie w celu skonfigurowania repozytorium. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```console
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

## <a name="devinitjson"></a>.devinit.json

Zawartość [`.devinit.json`](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_ pliku.

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
