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
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671631"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

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