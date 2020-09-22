---
title: vcpkg — Zainstaluj
description: devinit narzędzie vcpkg — Zainstaluj.
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
ms.openlocfilehash: 2e6dcad778e89b112a8c851f2f27ac46330466af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810415"
---
# <a name="vcpkg-install"></a>vcpkg — Zainstaluj

To `vcpkg-install` Narzędzie służy do pozyskiwania bibliotek C/C++ (nazywanych portami) za pomocą [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                   |
| [**klawiatur**](#input)                              | ciąg | Yes      | Pakiety do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                       |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                        |

### <a name="input"></a>Dane wejściowe

Aby można było zainstalować `input` wiele pakietów, właściwość powinna być `name` częścią `vcpkg` instalacji lub zawierać listę nazw rozdzielonych spacjami. Listę dostępnych portów można znaleźć w [repozytorium GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane bezpośrednio do polecenia [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) i są udokumentowane w [repozytorium GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `vcpkg-install` narzędzia to błąd, zgodnie z `input` potrzebami.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
