---
title: require-choco
description: Narzędzie devinit wymaga-Choco.
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
ms.openlocfilehash: 68e944813e7084b13c15058e4f66aef4aadb9494
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900366"
---
# <a name="require-choco"></a>require-choco

`require-choco`Narzędzie może służyć do instalowania [czekolady](https://chocolatey.org/).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                      |
| [**klawiatur**](#input)                              | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                           |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej. |

### <a name="input"></a>Dane wejściowe

Nie używany.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem `require-choco` narzędzia jest zainstalowanie czekolady i dodanie go do programu `PATH` .

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `require-choco` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-install-chocolatey"></a>.devinit.js, na którym zostanie zainstalowana czekolada:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-choco"
        }
    ]
}
```