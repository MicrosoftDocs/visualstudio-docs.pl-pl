---
title: require-dotnetcoresdk
description: Narzędzie devinit wymaga-dotnetcoresdk.
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
ms.openlocfilehash: 1963ad8dfe1bd31eb3f98ec6fdf57524a274cfb6
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671792"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

`require-dotnetcoresdk`Narzędzie służy do instalowania [zestaw .NET Core SDK](https://dotnet.microsoft.com/) i udostępnionego środowiska uruchomieniowego za pośrednictwem skryptu [dotnet-Install](/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                               |
| [**klawiatur**](#input)                              | ciąg | Nie       | Wersja zestaw .NET Core SDK do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                    |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia wersji zestaw .NET Core SDK do zainstalowania. Listę wersji można znaleźć w [witrynie dotnet-Core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych w skrypcie [instalacji dotnet](/dotnet/core/tools/dotnet-install-script) . Więcej informacji o dostępnych parametrach można znaleźć w [dokumentacji](/dotnet/core/tools/dotnet-install-script) skryptu [dotnet-Install](/dotnet/core/tools/dotnet-install-script) . W przypadku korzystania z programu upewnij się `additionalOptions` , że używasz nazw i formatów argumentów programu PowerShell.

> [!NOTE]
> Każda dodatkowa wartość argumentu, który zawiera spację, musi zawierać dodatkową parę cudzysłowów ucieczki (przy użyciu ukośnika odwrotnego). Przykład można zobaczyć w [przykładzie użycia](#example-usage) przy użyciu `-InstallDir` .

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-dotnetcoresdk` narzędzia jest zainstalowanie wersji zestaw .NET Core SDK określonej w `global.json` pliku [(dokumentacji)](/dotnet/core/tools/global-json?tabs=netcore3x) w bieżącym katalogu roboczym. Jeśli `global.json` plik nie zostanie znaleziony, `require-dotnetcoresdk` program zainstaluje najnowszą bieżącą wersję zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `require-dotnetcoresdk` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.js, na którym zostanie zainstalowana najnowsza wersja programu .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.js, na którym zostanie zainstalowana określona wersja programu .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.js, na którym zostanie zainstalowana określona wersja programu .NET Core i ASP.NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.js, na którym zostanie zainstalowany program .NET Core w określonym katalogu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```