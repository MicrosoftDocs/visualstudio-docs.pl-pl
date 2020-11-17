---
title: enable-iis
description: devinit Enable-IIS.
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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671927"
---
# <a name="enable-iis"></a>enable-iis

To `enable-iis` Narzędzie służy do włączania funkcji usług IIS i instalowania [modułu ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) na potrzeby tworzenia aplikacji ASP.NET przy użyciu usług IIS.

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                               |
| [**klawiatur**](#input)                              | ciąg | Nie       | Nie używany.                                                                           |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany.                                                                           |

### <a name="input"></a>Dane wejściowe

Nie używany.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `enable-iis` narzędzia jest włączenie funkcji usług IIS: IIS-WebServer, IIS-WebServerRole, IIS-WebSockets i IIS-webauthentication, a następnie zainstalowanie najnowszej wersji pakietu hostingu ASP.NET zawierającego moduł ASP.NET Core. 

## <a name="example-usage"></a>Przykład użycia
Poniżej znajduje się przykład sposobu uruchamiania `enable-iis` przy użyciu `.devinit.json` . 

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.js, które umożliwią programowanie usług IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```