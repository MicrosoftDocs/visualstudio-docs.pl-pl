---
title: require-vscomponent
description: Narzędzie devinit wymaga-vscomponent.
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
ms.openlocfilehash: e88f1b58308d0c81d17f9337f0a1a1d5e253c6ba
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862824"
---
# <a name="require-vscomponent"></a>require-vscomponent

`require-vscomponent`Narzędzie służy do importowania konfiguracji programu Visual Studio do istniejącego programu Visual Studio. Przeczytaj więcej na `.vsconfig` [ten temat](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                     | Typ   | Wymagane | Wartość                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **komentarz**                             | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                |
| [**klawiatur**](#input)                      | ciąg | Nie       | Pełna ścieżka `.vsconfig` . Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [additionalOptions](#additional-options) | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.     |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia pełnej ścieżki `.vsconfig` pliku. Jeśli nie zostanie on wymieniony, narzędzie przeszuka `.vsconfig` w bieżącym katalogu i przekaże wartość do Instalator programu Visual Studio.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-vscomponent` Narzędzia polega na wyszukiwaniu `.vsconfig` pliku w bieżącym katalogu i uruchomieniu instalator programu Visual Studio z tymi szczegółami w trybie cichym. `require-vscomponent` obsługuje tylko modyfikowanie istniejącej instalacji programu Visual Studio.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "comments": "Imports .vsconfig file which is passed as input to Visual Studio.",
            "input": "C:\\.vsconfig"
        }
    ]
}
```