---
title: Enable — IIS
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
ms.openlocfilehash: 245ea76f988b9a9e320a51ba6b2df01382668cc0
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127838"
---
# <a name="enable-iis"></a>Enable — IIS

To `enable-iis` Narzędzie służy do włączania funkcji usług IIS i instalowania [modułu ASP.NET Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module) na potrzeby tworzenia aplikacji ASP.NET przy użyciu usług IIS.

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
