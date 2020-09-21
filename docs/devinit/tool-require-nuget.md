---
title: Wymagaj — NuGet
description: Narzędzie devinit wymaga — NuGet.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c926bc146a7d85d67c49281effe88958f2031695
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810450"
---
# <a name="require-nuget"></a>Wymagaj — NuGet

`require-nuget`Narzędzie do pobierania interfejsu wiersza polecenia NuGet i dodaje do zmiennej PATH. Interfejs wiersza polecenia NuGet zapewnia pełen zakres funkcji NuGet do instalowania, tworzenia, publikowania i zarządzania pakietami bez wprowadzania żadnych zmian w plikach projektu. Więcej informacji o interfejsie wiersza polecenia NuGet można znaleźć [tutaj](https://docs.microsoft.com/nuget/reference/nuget-exe-cli-reference).

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that downloads NuGet CLI and adds to PATH variable.'",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
            "comments": "Installs NuGet for given input version. If no input given, then installs latest."
        }
    ]
}
```
