---
title: Wymagaj — NodeJS
description: Narzędzie devinit wymaga-NodeJS.
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
ms.openlocfilehash: 6bc2de2e497bd58cfc036e74af3968a2f70d1f52
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808419"
---
# <a name="require-nodejs"></a>Wymagaj — NodeJS

`require-nodejs`Narzędzie służy do instalowania [Node.js](https://nodejs.org/) za pośrednictwem pliku MSI dystrybuowanego przez Node.js organizację.

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                     |
| [**klawiatur**](#input)                              | ciąg | Nie       | Wersja Node.JS do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) . |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.          |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określania wersji Node.js. Listę wersji można znaleźć na [ stronie pobieraniaNode.js](https://nodejs.org/en/download/). Pełny numer wersji jest wymagany dla elementu główna. pomocnicza. ścieżka (na przykład 14.4.0), jeśli którykolwiek z nich zostanie pominięty, instalacja zakończy się niepowodzeniem.

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do instalatora MSI dla Node.js.  

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-nodejs` Narzędzia polega na zainstalowaniu najnowszej LTS wersji węzła zgodnie z opisem w [witrynie sieci Web](https://nodejs.org/en/download/)Node.JS.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
