---
title: require-dotnetframeworksdk
description: Narzędzie devinit wymaga-dotnetframeworksdk.
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
ms.openlocfilehash: 0c40ebfd2a8b665a1421ba70c0f785774e97d3df
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672152"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
Poniżej znajdują się przykłady sposobu uruchamiania programu `require-dotnetframeworksdk` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>.devinit.js, na którym zostanie zainstalowana najnowsza .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.js, na którym zostanie zainstalowana określona wersja .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```