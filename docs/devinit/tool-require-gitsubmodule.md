---
title: Wymagaj — gitsubmodule
description: Narzędzie devinit wymaga-gitsubmodule.
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
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810131"
---
# <a name="require-gitsubmodule"></a>Wymagaj — gitsubmodule

`require-gitsubmodule`Narzędzie przywraca moduły podrzędne git dla danego `.gitmodules` pliku. `.gitmodules`Jeśli nie zostanie przesłane żadne dane wejściowe, program używa lokalnego pliku w katalogu głównym. Więcej informacji na temat modułów podrzędnych usługi git można znaleźć [tutaj](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                                |
| [**klawiatur**](#input)                              | ciąg | Nie       | `.gitmodules` Pełna ścieżka pliku. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .               |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                     |

### <a name="input"></a>Dane wejściowe

Opcjonalne, służy `input` do pobierania `.gitmodules` ścieżki pliku do przywracania. `input`W przypadku pominięcia zostanie `.gitmodules` użyty plik katalogu głównego.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `require-gitsubmodule` narzędzia jest przywracanie modułów podrzędnych git wymienionych w `.gitmodules` pliku.

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
