---
title: Aplikacja platformy Node.js
description: Przykładowe repozytorium używające devinit do instalowania pakietów npm dla projektu Node.js Express.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 61e58109d98417e7b8b57a6c0fd23c64106413d7
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671758"
---
# <a name="nodejs-app"></a>Aplikacja platformy Node.js

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
