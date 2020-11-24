---
title: windowsfeature-disable
description: devinit narzędzie WindowsFeature-Wyłącz.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e48ba0a288aec76588e3d984d4c1577e053e35ae
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442160"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

To `windowsfeature-disable` Narzędzie służy do uzyskiwania funkcji systemu Windows.

## <a name="usage"></a>Użycie

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                  |
| [**klawiatur**](#input)                              | ciąg | Tak      | Funkcja systemu Windows do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.       |

### <a name="input"></a>Dane wejściowe

`input`Właściwość powinna być `name` typu `windows feature` do wyłączenia.

### <a name="additional-options"></a>Additional-Options

Brak.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `windowsfeature-disable` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `windowsfeature-disable` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.js, na którym zostanie wyłączona określona funkcja:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
