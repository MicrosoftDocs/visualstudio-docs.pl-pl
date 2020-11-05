---
title: windowsfeature-list
description: devinit narzędzie WindowsFeature-list.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400199"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
