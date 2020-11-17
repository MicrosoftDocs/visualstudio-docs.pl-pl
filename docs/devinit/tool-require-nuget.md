---
title: require-nuget
description: Narzędzie devinit wymaga — NuGet.
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
ms.openlocfilehash: e4f08e8c3f5967eb2e9db53633a12b304ac23bfb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671761"
---
# <a name="require-nuget"></a>require-nuget

`require-nuget`Narzędzie do pobierania interfejsu wiersza polecenia NuGet i dodaje do zmiennej PATH. Interfejs wiersza polecenia NuGet zapewnia pełen zakres funkcji NuGet do instalowania, tworzenia, publikowania i zarządzania pakietami bez wprowadzania żadnych zmian w plikach projektu. Więcej informacji o interfejsie wiersza polecenia NuGet można znaleźć [tutaj](/nuget/reference/nuget-exe-cli-reference).

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