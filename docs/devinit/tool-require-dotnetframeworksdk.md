---
title: Wymagaj — dotnetframeworksdk
description: Narzędzie devinit wymaga-dotnetframeworksdk.
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
ms.openlocfilehash: c9e27883bda455794429221af436af1fe39229fc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809687"
---
# <a name="require-dotnetframeworksdk"></a>Wymagaj — dotnetframeworksdk

`require-dotnetframeworksdk`Narzędzie służy do instalowania [zestawu SDK .NET Framework](https://dotnet.microsoft.com/) za pośrednictwem [podanych instalatorów](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane  | Wartość                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie        | Opcjonalna Właściwość komentarzy. Nie używany.                                                    |
| [**klawiatur**](#input)                              | ciąg | Nie        | Wersja zestawu SDK .NET Framework do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie        | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.               |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określania wersji zestawu SDK .NET Framework, która ma zostać zainstalowana. Listę wersji można znaleźć w [witrynie programu dotnet-Framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-dotnetframeworksdk` narzędzia jest zainstalowanie najnowszej wersji. Zapoznaj się z [dostarczonymi instalatorami](https://dotnet.microsoft.com/download/visual-studio-sdks) w celu uzyskania najnowszej wersji.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install a specific version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        },
        {
            "comments": "Example that will install the latest version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```
