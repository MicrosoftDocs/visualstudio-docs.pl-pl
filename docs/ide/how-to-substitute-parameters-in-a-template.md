---
title: Dodawanie nazwy parametrów szablonów projektów i elementów
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 93e553338478bcdead9e283323348b02ac73eaac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031763"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Instrukcje: Zastępowanie parametrów w szablonie

Parametry szablonu pozwalają Zastąp identyfikatory, takie jak nazwy klas i przestrzenie nazw, gdy plik zostanie utworzony z szablonu. Dodawanie parametrów szablonu do istniejących szablonów lub tworzyć własne szablony za pomocą parametrów szablonu.

Parametry szablonu są zapisywane w formacie $*parametru*$. Aby uzyskać pełną listę parametrów szablonu, zobacz [parametry szablonu](../ide/template-parameters.md).

Poniższej sekcji pokazano, jak zmodyfikować szablon, aby zastąpić nazwę przestrzeni nazw "bezpieczna Nazwa projektu".

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Aby użyć parametru, aby zastąpić nazwę przestrzeni nazw

1. Wstaw parametr w co najmniej jeden z plików kodu w szablonie. Na przykład:

    ```csharp
    namespace $safeprojectname$
    ```

1. W *vstemplate* pliku szablonu, odszukaj `ProjectItem` element, który zawiera ten plik.

1. Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Projectitem — element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)