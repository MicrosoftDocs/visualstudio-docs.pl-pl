---
title: Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5964dbbd6851adc1ccf209575dc9867cd18bf1ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953149"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu
Gdy chcesz rozszerzyć systemy projektu, można użyć poleceń i polecenia grupy udostępniane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 W poniższych sekcjach wymieniono elementy polecenia, które są szczególnie przydatne do rozszerzania systemów projektu.  
  
## <a name="command-menus"></a>Polecenia menu  
 W poniższej tabeli przedstawiono menu poleceń, które są przydatne w lokalizacjach na przetestowanie wysokiego poziomu poleceń, które wywołują rozszerzenia projektu.  
  
|Polecenia menu|Opis|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Projektu** menu najwyższego poziomu.|  
|IDM_VS_TOOL_PROJWIN|**Eksploratora rozwiązań** paska narzędzi.|  
  
## <a name="shortcut-menus"></a>Menu skrótów  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane po wybraniu jednego węzła w **Eksploratora rozwiązań**, lub gdy występują jednorodnego wielokrotny w **Eksploratora rozwiązań**, czyli kiedy wszystkie wybrane węzły są tego samego typu.  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Ma zastosowanie, gdy zaznaczony jest węzeł projektu.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Ma zastosowanie, gdy plik jest zaznaczony.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Ma zastosowanie przy wybraniu folderu.|  
|IDM_VS_CTXT_WEBREFFOLDER|Ma zastosowanie przy wybraniu folderu odwołań sieci Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Ma zastosowanie, gdy wybrano węzeł główny odwołania, które są nazywane "Odwołaniami".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Ma zastosowanie, gdy wybrano węzły odwołanie; należą do zestawu modelu COM i tylko odwołania do projektu. Nie ma odwołań sieci Web.|  
  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane podczas wyboru w **Eksploratora rozwiązań** obejmuje wiele hierarchii  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i węzłów projektu głównego.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy węzła i projektu rozwiązania.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Ma zastosowanie, gdy bieżące zaznaczenie składa się z wielu projektów węzłów głównych tylko.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera główny węzły projektów i elementów projektu. Ponadto zaznaczenie może zawierać węzła rozwiązania.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy projektu z wielu projektów w rozwiązaniu lub wybranie elementów różnego typu w tym samym projekcie.|  
  
## <a name="command-groups"></a>Grup poleceń  
 W poniższej tabeli przedstawiono grupy poleceń, używane podczas rozszerzania projektów, a dostępny za pośrednictwem <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu skrótów.  
  
|Grupa poleceń|Opis|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Polecenia służące do tworzenia, ponownie skompilować i wdrażania projektu.|  
|IDG_VS_CTXT_COMPILELINK|Polecenia służące do kompilowania i łączenia projektu.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Polecenia, które ustawienia konfiguracji projektu i kolejność kompilacji.|  
|IDG_VS_CTXT_PROJECT_ADD|Polecenia, które umożliwia dodanie elementów do projektu.|  
|IDG_VS_CTXT_PROJECT_START|Polecenia, które Ustaw projekt uruchamiania skojarzone z klawisz F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Polecenia zapisywanie elementów projektu.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Polecenia służące do debugowania.|  
|IDG_VS_CTXT_PROJECT_SCC|Polecenia służące do kontroli źródła.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Polecenia Wytnij, operacje kopiowania i wklejania.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Polecenia, które zapewniają dostęp do **właściwości projektu** okno dialogowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands programu Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md)