---
title: windowsfeature-list
description: devinit narzędzie WindowsFeature-list.
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
ms.openlocfilehash: 07b92e8783393fa19e5c09344a396a6c5c4fc011
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442127"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

To `windowsfeature-list` Narzędzie służy do wyświetlania stanu Włącz/Wyłącz dla wszystkich funkcji systemu Windows.

| Nazwa                                             | Typ   | Wymagane | Wartość                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.      |
| [**klawiatur**](#input)                              | ciąg | Nie       | Nie używany. Ignorowane.                         |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Ignorowane.                         |

### <a name="input"></a>Dane wejściowe

Nie używany. Ignorowane.

#### <a name="additional-options"></a>Opcje dodatkowe

Nie używany. Ignorowane.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `windowsfeature-list` narzędzia jest wyświetlenie stanu Włącz/Wyłącz dla wszystkich funkcji systemu Windows.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `windowsfeature-list` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.js, w którym zostanie wystawiony stan wszystkich funkcji systemu Windows:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
