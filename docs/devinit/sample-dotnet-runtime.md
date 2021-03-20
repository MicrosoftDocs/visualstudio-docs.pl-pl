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
ms.openlocfilehash: d703e71b6f8ab57ab07c4143fdd5435585c6004c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672454"
---
# <a name="net-core-runtime"></a>Środowisko uruchomieniowe platformy .NET Core

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
