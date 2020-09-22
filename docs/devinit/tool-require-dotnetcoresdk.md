---
title: require-dotnetcoresdk
description: Narzędzie devinit wymaga-dotnetcoresdk.
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
ms.openlocfilehash: 201ee0a7384b5dce502151fc9d34d73bc19424a5
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005785"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

`require-dotnetcoresdk`Narzędzie służy do instalowania [zestaw .NET Core SDK](https://dotnet.microsoft.com/) i udostępnionego środowiska uruchomieniowego za pośrednictwem skryptu [dotnet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) .

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

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych w skrypcie [instalacji dotnet](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) . Więcej informacji o dostępnych parametrach można znaleźć w [dokumentacji](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) skryptu [dotnet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) . W przypadku korzystania z programu upewnij się `additionalOptions` , że używasz nazw i formatów argumentów programu PowerShell.

Uwaga: wszelkie dodatkowe wartości argumentu, który zawiera spację, muszą zawierać dodatkową parę cudzysłowów ucieczki (przy użyciu ukośnika odwrotnego). Przykład można zobaczyć w [przykładzie użycia](#example-usage) przy użyciu `-InstallDir` .

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-dotnetcoresdk` narzędzia jest zainstalowanie wersji zestaw .NET Core SDK określonej w `global.json` pliku [(dokumentacji)](https://docs.microsoft.com/dotnet/core/tools/global-json?tabs=netcore3x) w bieżącym katalogu roboczym. Jeśli `global.json` plik nie zostanie znaleziony, `require-dotnetcoresdk` program zainstaluje najnowszą bieżącą wersję zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```
