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
ms.openlocfilehash: f6946afa0138dc27a61f5665a9172c231392acc1
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862240"
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