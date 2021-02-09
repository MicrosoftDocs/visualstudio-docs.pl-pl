---
title: dotnet-toolinstall
description: Narzędzie devinit dotnet-toolinstall.
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
ms.openlocfilehash: ae8f58224e5e4e1d6f8bed7bb810dafe0f0ed54a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882263"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

`dotnet-toolinstall`Narzędzie służy do instalowania [narzędzi .NET Core](https://dotnet.microsoft.com/) za pomocą `dotnet tool update` polecenia.

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                 |
| [**klawiatur**](#input)                              | ciąg | Tak      | Narzędzie .NET Core do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.      |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia narzędzia .NET Core do zainstalowania. W programie znajduje się nieoficjalna lista narzędzi [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) polecenie.

`dotnet tool update`Polecenie jest używane do bezpiecznego obsługi przypadku, gdy narzędzie jest już zainstalowane.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `dotnet-toolinstall` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `dotnet-toolinstall` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.js, na którym zostanie zainstalowane narzędzie do śledzenia dotnet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.js, na którym zostanie zainstalowane narzędzie do śledzenia dotnet jako narzędzie globalne:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```