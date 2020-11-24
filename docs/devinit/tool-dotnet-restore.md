---
title: dotnet-restore
description: Narzędzie devinit dotnet-Restore.
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
ms.openlocfilehash: 647748acc3eb45e2eca6ab4ca1e48a8bda3a563b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440396"
---
# <a name="dotnet-restore"></a>dotnet-restore

`dotnet-restore`Narzędzia przywracania zależności i narzędzi specyficznych dla projektu, które są określone w pliku projektu. Przeczytaj więcej na temat dotnet restore [tym miejscu](/dotnet/core/tools/dotnet-restore).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                |
| [**klawiatur**](#input)                              | ciąg | Nie       | Ścieżka do pliku projektu/rozwiązania do przywrócenia. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                     |

### <a name="input"></a>Dane wejściowe

Ścieżka do pliku projektu/rozwiązania do przywrócenia.

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane jako-do polecenia dotnet restore.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `dotnet-restore` narzędzia jest uruchamiane `dotnet restore` w bieżącym katalogu.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `dotnet-restore` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.js, na którym zostaną przywrócone zależności i narzędzia projektu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```