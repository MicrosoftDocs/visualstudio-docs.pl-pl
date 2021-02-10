---
title: enable-iis
description: devinit Enable-IIS.
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
ms.openlocfilehash: 8af1a09ba16c1b51c0ebb443aed65e131bbc6b9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932807"
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