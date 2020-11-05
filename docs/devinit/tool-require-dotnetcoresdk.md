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
ms.openlocfilehash: 5c5b68b663d6ee4cd0294aa77bd89c2e778f8d2b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399607"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
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