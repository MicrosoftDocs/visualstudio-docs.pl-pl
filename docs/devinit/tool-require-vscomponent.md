---
title: require-vscomponent
description: Narzędzie devinit wymaga-vscomponent.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 50172f96a49e2384553a372ded0c889b30a23fff
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006391"
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

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . 

| Nazwa                      | Typ      | Wymagane | Wartość                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | ciąg    | Nie       | Ścieżka instalacji wystąpienia programu Visual Studio, które chcesz zmodyfikować.                                                                                                                       |

Jeśli ścieżka instalacji nie zostanie określona, narzędzie zmodyfikuje najwcześniejszą instalację programu Visual Studio na komputerze, jeśli na maszynie istnieje wiele wystąpień. 

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-vscomponent` Narzędzia polega na wyszukiwaniu `.vsconfig` pliku w bieżącym katalogu i uruchomieniu instalator programu Visual Studio z tymi szczegółami w trybie cichym. `require-vscomponent` obsługuje tylko modyfikowanie istniejącej instalacji programu Visual Studio. 

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `require-vscomponent` przy użyciu `.devinit.json` .

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js, która spowoduje zaimportowanie konfiguracji danej ścieżki pliku. vsconfig:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.js, który zaimportuje konfiguracje danej ścieżki pliku. vsconfig do wystąpienia programu Visual Studio określonego za pośrednictwem ścieżki instalacji:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```