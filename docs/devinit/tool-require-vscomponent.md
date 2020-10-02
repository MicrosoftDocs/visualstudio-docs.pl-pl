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
ms.openlocfilehash: 7c47c219fa0c0ef32946d6e0500bc37ce9aec0ff
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005038"
---
# <a name="require-vscomponent"></a>require-vscomponent

`require-vscomponent`Narzędzie służy do importowania konfiguracji programu Visual Studio do istniejącego programu Visual Studio. Przeczytaj więcej na `.vsconfig` [ten temat](https://docs.microsoft.com/visualstudio/install/import-export-installation-configurations).

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