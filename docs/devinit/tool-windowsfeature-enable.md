---
title: WindowsFeature — Włącz
description: devinit narzędzie WindowsFeature-Enable.
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
ms.openlocfilehash: 679f8599516cc63aa56d327f69164612db8bb3ca
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810401"
---
# <a name="windowsfeature-enable"></a>WindowsFeature — Włącz

To `windowsfeature-enable` Narzędzie służy do włączania funkcji systemu Windows.

## <a name="usage"></a>Użycie

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                    |
| [**klawiatur**](#input)                              | ciąg | Yes      | Funkcja systemu Windows do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .   |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.         |

### <a name="input"></a>Dane wejściowe

`input`Właściwość powinna być `name` typu `windows feature` do zainstalowania. Listę dostępnych funkcji można znaleźć, uruchamiając `Get-WindowsFeature` polecenie cmd programu PowerShell.

### <a name="additional-options"></a>Dodatkowe opcje

Brak.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `windowsfeature-enable` narzędzia to błąd, zgodnie z `input` potrzebami.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
