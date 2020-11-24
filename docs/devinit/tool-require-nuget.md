---
title: require-nuget
description: Narzędzie devinit wymaga — NuGet.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: dd5c85e6bff00433903a1e9e472f567401ada70c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440497"
---
# <a name="require-nuget"></a>require-nuget

`require-nuget`Narzędzie pobiera interfejs wiersza polecenia NuGet i dodaje go do programu `PATH` . Interfejs wiersza polecenia NuGet zapewnia pełen zakres funkcji NuGet do instalowania, tworzenia, publikowania i zarządzania pakietami bez wprowadzania żadnych zmian w plikach projektu. Więcej informacji o interfejsie wiersza polecenia NuGet można znaleźć [tutaj](/nuget/reference/nuget-exe-cli-reference).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                |
| [**klawiatur**](#input)                              | ciąg | Nie       | Wersja interfejsu wiersza polecenia NuGet do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                     |

### <a name="input"></a>Dane wejściowe

`input`Jest to opcjonalna właściwość używana do wybrania wersji interfejsu wiersza polecenia NuGet do zainstalowania. `input`W przypadku pominięcia zostanie zainstalowana najnowsza wersja interfejsu wiersza polecenia.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-nuget` narzędzia jest zainstalowanie najnowszej wersji interfejsu wiersza polecenia NuGet.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `require-nuget` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.js, na którym zostanie zainstalowana określona wersja programu NuGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```