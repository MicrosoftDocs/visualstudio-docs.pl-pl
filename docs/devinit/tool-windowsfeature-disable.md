---
title: windowsfeature-disable
description: devinit narzędzie WindowsFeature-Wyłącz.
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
ms.openlocfilehash: cd06b3a3d063a2c209a901bbed1600570c31cd8e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672646"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
