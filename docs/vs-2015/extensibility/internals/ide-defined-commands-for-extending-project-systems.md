---
title: Polecenia zdefiniowane w środowisku IDE służące do rozszerzania systemów projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b5de061449844b87d60d7a700b1e1c22e1e1282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195038"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy chcesz rozciągnąć systemy projektów, możesz użyć poleceń i grup poleceń dostarczonych przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 W poniższych sekcjach wymieniono elementy poleceń, które są szczególnie przydatne w przypadku rozszerzania systemów projektów.  
  
## <a name="command-menus"></a>Menu poleceń  
 W poniższej tabeli przedstawiono menu poleceń, które są przydatne do umieszczania poleceń wysokiego poziomu, które wywołują rozszerzenie projektu.  
  
|Menu poleceń|Opis|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Menu najwyższego poziomu **projektu** .|  
|IDM_VS_TOOL_PROJWIN|Pasek narzędzi **Eksplorator rozwiązań** .|  
  
## <a name="shortcut-menus"></a>Menu skrótów  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane w przypadku wybrania jednego węzła w **Eksplorator rozwiązań**lub gdy w **Eksplorator rozwiązań**znajduje się wiele opcji jednorodnych, co oznacza, że wszystkie wybrane węzły są tego samego typu.  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Stosuje się, gdy wybrano węzeł projektu.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Stosuje się, gdy plik jest zaznaczony.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Stosuje się, gdy wybrano folder.|  
|IDM_VS_CTXT_WEBREFFOLDER|Stosuje się, gdy wybrano folder odwołania sieci Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Stosuje się, gdy wybrano węzeł główny odwołań o nazwie "References".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Stosuje się, gdy są wybrane węzły odwołań; są to m.in. zestawy, COM i odwołania do projektu. Nie zawiera odwołań sieci Web.|  
  
 W poniższej tabeli przedstawiono menu skrótów, które są stosowane, gdy zaznaczenie w **Eksplorator rozwiązań** obejmuje wiele hierarchii,  
  
|Menu skrótów|Opis|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i węzły głównego projektu.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i elementy projektu.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Stosuje się, gdy bieżące zaznaczenie składa się tylko z wielu węzłów głównego projektu.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Stosuje się, gdy bieżące zaznaczenie zawiera kombinację głównych węzłów projektu i elementów projektu. Ponadto zaznaczenie może zawierać węzeł rozwiązania.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Stosuje się, gdy bieżące zaznaczenie zawiera elementy projektu z wielu projektów w rozwiązaniu lub gdy w tym samym projekcie wybrano elementy różnych typów.|  
  
## <a name="command-groups"></a>Grupy poleceń  
 W poniższej tabeli przedstawiono grupy poleceń, których można użyć podczas rozszerzając projekty i można uzyskać do nich dostęp za pomocą <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu skrótów.  
  
|Grupa poleceń|Opis|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Polecenia do kompilowania, ponownego kompilowania i wdrażania projektu.|  
|IDG_VS_CTXT_COMPILELINK|Polecenia do kompilowania i łączenia projektu.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Polecenia, które ustawiają konfigurację projektu i kolejność kompilacji.|  
|IDG_VS_CTXT_PROJECT_ADD|Polecenia, które dodają elementy do projektu.|  
|IDG_VS_CTXT_PROJECT_START|Polecenia, które ustawiają projekt startowy skojarzony z klawiszem F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Polecenia do zapisywania elementów projektu.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Polecenia do debugowania.|  
|IDG_VS_CTXT_PROJECT_SCC|Polecenia dla kontroli źródła.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Polecenia dla operacji wycinania, kopiowania i wklejania.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Polecenia, które zapewniają dostęp do okna dialogowego **właściwości projektu** .|  
  
## <a name="see-also"></a>Zobacz też  
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md)
