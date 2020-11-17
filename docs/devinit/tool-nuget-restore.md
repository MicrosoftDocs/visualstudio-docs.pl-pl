---
title: nuget-restore
description: Narzędzie devinit narzędzia NuGet — przywracanie.
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
ms.openlocfilehash: 7d797e744b651eafd629ec83f20478f0142864e6
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672167"
---
# <a name="nuget-restore"></a>nuget-restore

`nuget-restore`Narzędzia przywracania zależności i narzędzi specyficznych dla projektu, które są określone w pliku projektu. Więcej informacji na temat przywracania NuGet można znaleźć [tutaj](/nuget/reference/cli-reference/cli-ref-restore).

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

Dodatkowe opcje są przesyłane w postaci-do polecenia NuGet Restore.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `nuget-restore` narzędzia jest uruchomienie elementu "NuGet Restore" w bieżącym katalogu.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `nuget-restore` przy użyciu `.devinit.json` . 

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.js, na którym zostaną przywrócone zależności i narzędzia projektu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```