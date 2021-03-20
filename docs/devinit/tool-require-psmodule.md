---
title: require-psmodule
description: Narzędzie devinit wymaga-psmodule.
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
ms.openlocfilehash: cdb37bf4e714cfc25e5bf82354856fd4d3d63e87
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672701"
---
# <a name="require-psmodule"></a>require-psmodule

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.


`require-psmodule`Narzędzie to służy do instalowania [modułu programu PowerShell](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) z [Galeria programu PowerShell](https://www.powershellgallery.com/) za pomocą polecenia [Install-module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true), dzięki czemu można go używać w skryptach programu PowerShell.

> [!TIP]
> Po zainstalowaniu modułu nadal trzeba go zaimportować do skryptu za pomocą polecenia [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                   |
| [**klawiatur**](#input)                              | ciąg | Tak      | Pakiety do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                       |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.              |

### <a name="input"></a>Dane wejściowe

`input`Właściwość powinna być właściwością `Name` modułu programu PowerShell, która ma zostać zainstalowana. Listę dostępnych modułów programu PowerShell można znaleźć, wyszukując [Galeria programu PowerShell](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane bezpośrednio do polecenia [Install-module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) i są udokumentowane w [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7).

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-psmodule` narzędzia to błąd, zgodnie z `input` wymaganiami.

### <a name="built-in-options"></a>Wbudowane opcje

`require-psmodule`Narzędzie ustawia szereg `Install-Module` argumentów wiersza polecenia, aby zapewnić `Install-Module` możliwość uruchamiania bezobsługowego. Te argumenty są wymienione poniżej, a dokumentacja na nich znajduje się w [module Install](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nazwa         | Opis                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Wymuś**   | Instaluje moduł i przesłania komunikaty ostrzegawcze dotyczące konfliktów instalacji modułu. Jeśli moduł o tej samej nazwie już istnieje na komputerze, Wymuś zainstalowanie wielu wersji. Spowoduje zastąpienie modułu, jeśli istnieje istniejący moduł o tej samej nazwie i wersji. Polecenia Force i AllowClobber mogą być używane razem w Install-Module polecenie. |
| **-WhatIf**  | -WhatIf flaga jest dodawana, gdy przebiegu suchego jest przenoszona dla `devinit` polecenia.                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | -Pełna flaga jest dodawana, gdy pełny jest przesyłany do `devinit` polecenia.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `require-psmodule` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-powershellget-module"></a>.devinit.js, na którym zostanie zainstalowany moduł PowerShellGet:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-powershellget-module-from-a-specific-repository"></a>.devinit.js, na którym zostanie zainstalowany moduł PowerShellGet z określonego repozytorium:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```