---
title: Dodawanie parametrów nazw do szablonów projektów i elementów
description: Dowiedz się, jak zmodyfikować parametry szablonu, aby zastąpić identyfikatory, takie jak nazwy klas i przestrzenie nazw.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6d7d0a6f45468759dc3ec2349764cf2677aa5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869235"
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

1. W pliku *vstemplate* szablonu Znajdź `ProjectItem` element, który zawiera ten plik.

1. Ustaw `ReplaceParameters` atrybut na `true` dla `ProjectItem` elementu:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
