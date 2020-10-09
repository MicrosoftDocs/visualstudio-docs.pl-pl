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
ms.openlocfilehash: 3324cf5faa1d9385adbbdf24a8125970c5db2c40
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862237"
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

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```