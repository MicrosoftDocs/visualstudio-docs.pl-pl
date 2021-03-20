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
ms.openlocfilehash: 3225e67db734e02abce96820d44ca1515ddc348f
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672632"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
