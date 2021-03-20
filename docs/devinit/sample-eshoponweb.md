---
title: eShopOnWeb
description: Przykładowe dostosowanie przy użyciu devinit dla repozytorium dotnet-Architecture/eShopOnWeb.
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
ms.openlocfilehash: 1356cf2654adfb78fcff61c9f9dab95f1fdbe913
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672447"
---
# <a name="eshoponweb"></a>eShopOnWeb

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

W tym przykładzie pokazano, jak dostosować przykład architektury dotnet [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) do automatycznej obsługi administracyjnej za pomocą usługi [GitHub Codespaces](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Ten skrypt jest wywoływany z _PostCloneSetup.ps1_ i może być uruchamiany lokalnie w celu skonfigurowania repozytorium. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Zawartość [`.devinit.json`](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
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
