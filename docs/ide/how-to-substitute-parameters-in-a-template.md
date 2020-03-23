---
title: Dodawanie parametrów nazw do szablonów projektów i elementów
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591414"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Jak: Zastępowanie parametrów w szablonie

Parametry szablonu umożliwiają zastępowanie identyfikatorów, takich jak nazwy klas i przestrzenie nazw, gdy plik jest tworzony na podstawie szablonu. Można dodać parametry szablonu do istniejących szablonów lub utworzyć własne szablony z parametrami szablonu.

Parametry szablonu są zapisywane w formacie $*parametr*$. Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

W poniższej sekcji pokazano, jak zmodyfikować szablon, aby zastąpić nazwę obszaru nazw "bezpieczną nazwą projektu".

## <a name="example---namespace-name"></a>Przykład - nazwa obszaru nazw

1. Wstaw parametr w jednym lub więcej plików kodu w szablonie. Przykład:

    ```csharp
    namespace $safeprojectname$
    ```

1. W pliku *vstemplate* dla szablonu `ProjectItem` znajdź element, który zawiera ten plik.

1. Ustaw `ReplaceParameters` atrybut `true` dla `ProjectItem` elementu:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Element ProjectItem (szablony elementów programu Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
