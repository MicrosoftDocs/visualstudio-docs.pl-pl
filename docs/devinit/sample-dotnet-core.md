---
title: Aplikacja .NET Core
description: Przykładowe repozytorium używające devinit do zainstalowania określonego zestaw .NET Core SDK.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 35971ac1fde5fc272f22579cc6640cbea6724db5
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344519"
---
# <a name="net-core-app"></a>Aplikacja .NET Core

Aby zainstalować wymaganą wersję zestaw .NET Core SDK w Codespaces, zobacz repozytorium [DotnetCoreDevinitExample](https://github.com/microsoft/DotnetCoreDevinitExample) .

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
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

## <a name="globaljson"></a>global.json

Zawartość _global.jsw_ pliku w katalogu głównym repozytorium.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
