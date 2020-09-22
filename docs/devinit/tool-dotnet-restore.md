---
title: dotnet-restore
description: Narzędzie devinit dotnet-Restore.
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
ms.openlocfilehash: 39324f3a14b631328f3f1189da7806e02fd1e076
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006030"
---
# <a name="dotnet-restore"></a>dotnet-restore

`dotnet-restore`Narzędzia przywracania zależności i narzędzi specyficznych dla projektu, które są określone w pliku projektu. Przeczytaj więcej na temat dotnet restore [tym miejscu](https://docs.microsoft.com/dotnet/core/tools/dotnet-restore).

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

Domyślnym zachowaniem tego `dotnet-restore` narzędzia jest uruchomienie "dotnet Restore" w bieżącym katalogu.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that builds the 'kitchen sink'",
    "run": [
        {
            "tool": "dotnet-restore",
            "comments": "Restores the dependencies and tools of a project using dotnet core.",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```
