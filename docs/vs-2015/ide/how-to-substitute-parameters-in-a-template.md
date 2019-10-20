---
title: 'Instrukcje: zastępowanie parametrów w szablonie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670660"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Porady: parametry zastępcze w szablonie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zastąpić parametry szablonu, takie jak nazwy klas i przestrzenie nazw, gdy tworzony jest plik oparty na szablonie. Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

## <a name="procedure"></a>Procedura
 Parametry w plikach szablonu można zastąpić za każdym razem, gdy projekt jest tworzony na podstawie tego szablonu. W tej procedurze wyjaśniono, jak utworzyć szablon, który zastępuje nazwę przestrzeni nazw nazwą projektu bezpiecznej, gdy tworzony jest nowy projekt z szablonem.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Aby użyć parametru, aby zastąpić nazwę przestrzeni nazw nazwą projektu

1. Wstaw parametr w co najmniej jednym pliku kodu w szablonie. Na przykład:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Parametry szablonu są zapisywane w formacie $*Parameter*$.

2. W pliku. vstemplate szablonu Znajdź element `ProjectItem`, który zawiera ten plik.

3. Ustaw atrybut `ReplaceParameters` na `true` dla elementu `ProjectItem`. Na przykład:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Zobacz też
 [Tworzenie projektu i szablonów elementów](../ide/creating-project-and-item-templates.md) [Parametry szablonu](../ide/template-parameters.md) [programu Visual Studio szablon](../extensibility/visual-studio-template-schema-reference.md) [ProjectItem element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
