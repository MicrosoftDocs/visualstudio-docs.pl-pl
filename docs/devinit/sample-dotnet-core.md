---
title: Aplikacja .NET Core
description: Przykładowe repozytorium używające devinit do zainstalowania określonego zestaw .NET Core SDK.
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
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943586"
---
# <a name="net-core-app"></a>Aplikacja .NET Core

Aby zainstalować wymaganą wersję zestaw .NET Core SDK w Codespaces, zobacz repozytorium [devinit-example dotnet-Core](https://github.com/microsoft/devinit-example-dotnet-core) .

## <a name="devinitjson"></a>.devinit.json

Zawartość _.devinit.jsw_ pliku w katalogu głównym repozytorium.

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
