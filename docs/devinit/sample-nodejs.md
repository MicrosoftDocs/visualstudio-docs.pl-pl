---
title: Aplikacja platformy Node.js
description: Przykładowe repozytorium używające devinit do instalowania pakietów npm dla projektu Node.js Express.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 787bfc4b9959dcc5e6abab4737426e5a0a54b6a1
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402330"
---
# <a name="nodejs-app"></a>Aplikacja platformy Node.js

Zapoznaj się z repozytorium [devinit-EXAMPL-NodeJS](https://github.com/microsoft/devinit-example-nodejs) , aby zapoznać się z pełnym przykładem użycia devinit w celu zainstalowania pakietów npm dla projektu Node.js Express.

## <a name="devinitjson"></a>.devinit.json

Zawartość _.devinit.jsw_ pliku w katalogu głównym repozytorium.

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the body-parser package.",
      "tool": "npm-install",
      "input": "body-parser"
    },
    {
      "comments": "Installs the cookie-parser package.",
      "tool": "npm-install",
      "input": "cookier-parser"
    },
    {
      "comments": "Installs the debug package.",
      "tool": "npm-install",
      "input": "debug"
    },
    {
      "comments": "Installs the express package.",
      "tool": "npm-install",
      "input": "express"
    },
    {
      "comments": "Installs the morgan package.",
      "tool": "npm-install",
      "input": "morgan"
    },
    {
      "comments": "Installs the pug package.",
      "tool": "npm-install",
      "input": "pug"
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
