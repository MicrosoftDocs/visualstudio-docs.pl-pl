---
title: windowsfeature-list
description: devinit narzędzie WindowsFeature-list.
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
ms.openlocfilehash: 43370389aaffdb4395248fed6ec83de39f16c86d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874506"
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
