---
title: dotnet-toolinstall
description: Narzędzie devinit dotnet-toolinstall.
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
ms.openlocfilehash: cb19cab0c03b87894029a18f682f05def6a2197c
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005546"
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

`input`Właściwość służy do określania instalacji narzędzia .NET Core. W programie znajduje się nieoficjalna lista narzędzi [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez [`dotnet tool update`](https://docs.microsoft.com/dotnet/core/tools/global-tools#update-a-tool) polecenie. 

`dotnet tool update`Polecenie jest używane do bezpiecznego obsługi przypadku, gdy narzędzie jest już zainstalowane.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `dotnet-toolinstall` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install the dotnet-trace tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        },
        {
            "comments": "Example that will install the dotnet-trace tool as a global tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```
