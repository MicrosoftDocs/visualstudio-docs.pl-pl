---
title: vcpkg-install
description: devinit narzędzie vcpkg — Zainstaluj.
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
ms.openlocfilehash: 8a4cbe6bd1da12985da87d2f872dc74f988ef213
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672653"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

To `vcpkg-install` Narzędzie służy do pozyskiwania bibliotek C/C++ (nazywanych portami) za pomocą [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                   |
| [**klawiatur**](#input)                              | ciąg | Tak      | Pakiety do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                       |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                        |

### <a name="input"></a>Dane wejściowe

Aby można było zainstalować `input` wiele pakietów, właściwość powinna być `name` częścią `vcpkg` instalacji lub zawierać listę nazw rozdzielonych spacjami. Listę dostępnych portów można znaleźć w [repozytorium GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane bezpośrednio do polecenia [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) i są udokumentowane w [repozytorium GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `vcpkg-install` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `vcpkg-install` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.js, na którym zostanie zainstalowany port SDL2:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>.devinit.js, na którym zostanie zainstalowana wiele portów:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```