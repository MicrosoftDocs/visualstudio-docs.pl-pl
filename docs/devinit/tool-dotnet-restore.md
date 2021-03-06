---
title: dotnet-restore
description: Narzędzie devinit dotnet-Restore.
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
ms.openlocfilehash: 5beea84edce408acda7fc157f530c4a5f3253835
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672236"
---
# <a name="dotnet-restore"></a>dotnet-restore

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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