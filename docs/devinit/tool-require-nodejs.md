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
ms.openlocfilehash: 75690f85fb627140226242b476d70bfc4dac6ed2
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672304"
---
# <a name="require-nodejs"></a>require-nodejs

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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
