---
title: Prywatna wersja beta
description: Przykładowe dostosowania używane w repozytorium GitHub Codespaces programu Visual Studio w wersji zapoznawczej.
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
ms.openlocfilehash: c79206295615fc984d2a95b52e0ecc0f70814e6f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437102"
---
# <a name="private-beta"></a>Prywatna wersja beta

W tym przykładzie pokazano, jak dostosować codespace dla programu Visual Studio, aby miał te same funkcje co początkowy prywatny beta usługi [GitHub Codespaces](https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.json

Zawartość [`.devinit.json`](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Zawartość _.devcontainer.jsw_ pliku w katalogu głównym repozytorium.

```json
{
  "postCreateCommand": "devinit init"
}
```
