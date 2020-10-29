---
title: Aplikacja .NET Core
description: Przykładowe repozytorium używające devinit do zainstalowania określonego zestaw .NET Core SDK.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028148"
---
# <a name="net-core-app"></a>Aplikacja .NET Core

Aby zainstalować wymaganą wersję zestaw .NET Core SDK w Codespaces, zobacz repozytorium [DevinitExample](https://github.com/microsoft/DevinitExample) .

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