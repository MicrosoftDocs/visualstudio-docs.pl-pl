---
title: Wymagaj — npm
description: Narzędzie devinit wymaga-npm.
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
ms.openlocfilehash: 56c8bc0d277427d235396671f446a44125aa0165
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809680"
---
# <a name="require-npm"></a>Wymagaj — npm

`require-npm`Narzędzie służy do instalowania [npm](https://www.npmjs.com/).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                       |
| [**klawiatur**](#input)                              | ciąg | Yes      | Określa wersję NPM. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                           |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                  |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określania wersji npm.

### <a name="additional-options"></a>Opcje dodatkowe

Nieużywany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-nodejs` Narzędzia polega na zainstalowaniu najnowszej wersji LTS npm.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of NPM.",
            "tool": "require-npm"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```
