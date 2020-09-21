---
title: Prywatna wersja zapoznawcza
description: Przykładowe dostosowania używane w repozytorium GitHub Codespaces programu Visual Studio w wersji zapoznawczej.
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
ms.openlocfilehash: c240cee6595f060c5347cafc4379a7fc27c8d310
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809091"
---
# <a name="private-preview"></a>Prywatna wersja zapoznawcza

W tym przykładzie pokazano, jak dostosować codespace dla programu Visual Studio, aby miał te same funkcje co początkowy prywatny beta usługi [GitHub Codespaces](https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.jsna

Zawartość [_.devinit.js_](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

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
