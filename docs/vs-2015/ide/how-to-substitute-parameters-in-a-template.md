---
title: 'Instrukcje: Zastępowanie parametrów w szablonie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be004820967f85de41b11c38031722b87a5af375
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039417"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Instrukcje: Zastępowanie parametrów w szablonie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zastąpić parametry szablonu, takich jak nazwy klasy, a przestrzenie nazw, gdy plik na podstawie szablonu zostanie utworzona. Aby uzyskać pełną listę parametrów szablonu, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Procedura  
 Po każdym utworzeniu projektu na podstawie tego szablonu można zastąpić parametry w plikach szablonu. Ta procedura wyjaśnia, jak utworzyć szablon, który zastępuje nazwę obszaru nazw, bezpieczna Nazwa projektu podczas tworzenia nowego projektu z szablonem.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Aby użyć parametru zastąpić nazwę przestrzeni nazw nazwa projektu  
  
1. Wstaw parametr w co najmniej jeden z plików kodu w szablonie. Na przykład:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Parametry szablonu są zapisywane w formacie $*parametru*$.  
  
2. W pliku .vstemplate szablonu zlokalizuj `ProjectItem` element, który zawiera ten plik.  
  
3. Ustaw `ReplaceParameters` atrybutu `true` dla `ProjectItem` elementu. Na przykład:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
