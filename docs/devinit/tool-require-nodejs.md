---
title: require-nodejs
description: Narzędzie devinit wymaga-NodeJS.
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
ms.openlocfilehash: ca1d5e48ab61926336aecebb1a2a4b794c704482
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842674"
---
# <a name="require-nodejs"></a>require-nodejs

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
Poniżej znajdują się przykłady sposobu uruchamiania programu `require-nodejs` przy użyciu programu `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.js, na którym zostanie zainstalowany LTS Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.js, na którym zostanie zainstalowana określona wersja Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
