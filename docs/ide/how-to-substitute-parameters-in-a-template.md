---
title: Dodawanie parametrów nazw do szablonów projektów i elementów
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09d86c52fcd9ddce3c986e0bfa6c9c96f746c663
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656563"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Instrukcje: zastępowanie parametrów w szablonie

Parametry szablonu umożliwiają zastępowanie identyfikatorów, takich jak nazwy klas i przestrzenie nazw, gdy plik jest tworzony na podstawie szablonu. Można dodawać parametry szablonu do istniejących szablonów lub tworzyć własne szablony z parametrami szablonu.

Parametry szablonu są zapisywane w formacie $*Parameter*$. Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

W poniższej sekcji pokazano, jak zmodyfikować szablon, aby zastąpić nazwę przestrzeni nazw nazwą "bezpieczny projekt".

## <a name="example---namespace-name"></a>Przykład — nazwa przestrzeni nazw

1. Wstaw parametr w co najmniej jednym pliku kodu w szablonie. Na przykład:

    ```csharp
    namespace $safeprojectname$
    ```

1. W pliku *vstemplate* szablonu znajdź element `ProjectItem`, który zawiera ten plik.

1. Ustaw atrybut `ReplaceParameters` na `true` dla elementu `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)