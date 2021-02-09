---
title: require-npm
description: Narzędzie devinit wymaga-npm.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 29ec1819317329985e0ea3210a56038fb2284c0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862263"
---
# <a name="require-npm"></a>require-npm

`require-npm`Narzędzie służy do instalowania [npm](https://www.npmjs.com/).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                       |
| [**klawiatur**](#input)                              | ciąg | Tak      | Określa wersję NPM. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                           |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                  |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określania wersji npm.

### <a name="additional-options"></a>Opcje dodatkowe

Nieużywany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-nodejs` Narzędzia polega na zainstalowaniu najnowszej wersji LTS npm.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `require-npm` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.js, na którym zostanie zainstalowany LTS npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.js, na którym zostanie zainstalowana określona wersja programu npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```