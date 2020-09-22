---
title: Wymagaj — psmodule
description: Narzędzie devinit wymaga-psmodule.
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
ms.openlocfilehash: f52483065c73f9d0e31f089f3d44aca74588d72f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809673"
---
# <a name="require-psmodule"></a>Wymagaj — psmodule

`require-psmodule`Narzędzie służy do instalowania [modułu programu PowerShell](https://docs.microsoft.com/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) z [Galeria programu PowerShell](https://www.powershellgallery.com/) za pośrednictwem programu [install-module] ( https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true , aby można go było używać w skryptach programu PowerShell.

>
>! Porada po zainstalowaniu modułu nadal trzeba go zaimportować do skryptu za pomocą polecenia [Import-Module](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).
>

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                   |
| [**klawiatur**](#input)                              | ciąg | Yes      | Pakiety do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                       |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.              |

### <a name="input"></a>Dane wejściowe

`input`Właściwość powinna być właściwością `Name` modułu programu PowerShell, która ma zostać zainstalowana. Listę dostępnych modułów programu PowerShell można znaleźć, wyszukując [Galeria programu PowerShell](https://www.powershellgallery.com/).

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje są przesyłane bezpośrednio do polecenia [Install-module](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) i są udokumentowane w [Microsoft docs](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `require-psmodule` narzędzia to błąd, zgodnie z `input` wymaganiami.

## <a name="builtin-options"></a>Wbudowane opcje

`require-psmodule`Narzędzie ustawia szereg `Install-Module` argumentów wiersza polecenia, aby zapewnić `Install-Module` możliwość uruchamiania bezobsługowego. Te argumenty są wymienione poniżej, a dokumentacja na nich znajduje się w [module Install](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true).

| Nazwa         | Opis                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Instaluje moduł i przesłania komunikaty ostrzegawcze dotyczące konfliktów instalacji modułu. Jeśli moduł o tej samej nazwie już istnieje na komputerze, Wymuś zainstalowanie wielu wersji. Spowoduje zastąpienie modułu, jeśli istnieje istniejący moduł o tej samej nazwie i wersji. Wymuś i AllowClobber można używać razem w poleceniu Install-module. |
| **-WhatIf**  | -WhatIf flaga jest dodawana, gdy przebiegu suchego jest przenoszona dla `devinit` polecenia.                                                                                                                                                                                                                                                                                                       |
| **-Verbose** | -Pełna flaga jest dodawana, gdy pełny jest przesyłany do `devinit` polecenia.                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```
