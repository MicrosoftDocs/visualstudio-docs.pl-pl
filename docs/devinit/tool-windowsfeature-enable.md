---
title: windowsfeature-enable
description: devinit narzędzie WindowsFeature-Enable.
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
ms.openlocfilehash: ea3716cfd244cb81d6c380d2787babf5845c490a
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672639"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

To `windowsfeature-enable` Narzędzie służy do włączania funkcji systemu Windows.

## <a name="usage"></a>Użycie

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                    |
| [**klawiatur**](#input)                              | ciąg | Tak      | Funkcja systemu Windows do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .   |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.         |

### <a name="input"></a>Dane wejściowe

`input`Właściwość powinna być `name` typu `windows feature` do zainstalowania. Listę dostępnych funkcji można znaleźć, uruchamiając `Get-WindowsFeature` polecenie cmd programu PowerShell.

### <a name="additional-options"></a>Additional-Options

Brak.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `windowsfeature-enable` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `windowsfeature-enable` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-iis"></a>.devinit.js, na którym zostaną zainstalowane usługi IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>.devinit.js, na którym zostanie zainstalowany .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.js, na którym zostanie zainstalowany program .NET Framework 4,5:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js, na którym zostanie zainstalowany podsystem Windows dla systemu Linux 2,0:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
