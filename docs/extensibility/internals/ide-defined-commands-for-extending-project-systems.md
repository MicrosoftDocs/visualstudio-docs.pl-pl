---
title: Polecenia zdefiniowane przez IDE dla rozszerzania systemów projektowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707734"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu
Aby rozszerzyć systemy projektów, można użyć poleceń i grup [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poleceń dostarczonych przez IDE.

 W poniższych sekcjach listy elementów polecenia, które są szczególnie przydatne do rozszerzania systemów projektu.

## <a name="command-menus"></a>Menu poleceń
 W poniższej tabeli przedstawiono menu poleceń, które są przydatne lokalizacje do umieszczania poleceń wysokiego poziomu, które wywołują extender projektu.

|Menu polecenia|Opis|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menu **projektu** najwyższego poziomu.|
|IDM_VS_TOOL_PROJWIN|Pasek narzędzi **Eksploratora rozwiązań.**|

## <a name="shortcut-menus"></a>Menu skrótów
 W poniższej tabeli przedstawiono menu skrótów, które mają zastosowanie, gdy pojedynczy węzeł jest zaznaczony w **Eksploratorze rozwiązań**lub gdy w **Eksploratorze rozwiązań**znajduje się wiele jednorodnych zaznaczeń, czyli wtedy, gdy wszystkie wybrane węzły są tego samego typu.

|Menu skrótów|Opis|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Ma zastosowanie, gdy węźle projektu jest zaznaczone.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Ma zastosowanie, gdy plik jest zaznaczony.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Ma zastosowanie, gdy folder jest zaznaczony.|
|IDM_VS_CTXT_WEBREFFOLDER|Ma zastosowanie po zaznaczeniu folderu Odwołanie do sieci Web.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Ma zastosowanie, gdy wybrano węzeł główny odwołań o nazwie "Odwołania".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Ma zastosowanie, gdy wybrano węzły odniesienia; obejmują one tylko odwołania do zestawu, com i projektu. Nie zawiera odwołań do sieci Web.|

 W poniższej tabeli przedstawiono menu skrótów, które mają zastosowanie, gdy zaznaczenie w **Eksploratorze rozwiązań** obejmuje wiele hierarchii,

|Menu skrótów|Opis|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i węzły projektu głównego.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera węzeł rozwiązania i elementy projektu.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Ma zastosowanie, gdy bieżące zaznaczenie składa się tylko z wielu węzłów projektu głównego.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera kombinację węzłów projektu głównego i elementów projektu. Ponadto zaznaczenie może zawierać węzeł rozwiązania.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy projektu z wielu projektów w rozwiązaniu lub gdy elementy różnych typów są zaznaczone w tym samym projekcie.|

## <a name="command-groups"></a>Grupy poleceń
 W poniższej tabeli przedstawiono grupy poleceń, których można używać <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> podczas rozszerzania projektów, oraz które można uzyskać do nich dostęp za pośrednictwem menu skrótów.

|Grupa poleceń|Opis|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Polecenia dotyczące tworzenia, przebudowy i wdrażania projektu.|
|IDG_VS_CTXT_COMPILELINK|Polecenia do kompilowania i łączenia projektu.|
|IDG_VS_CTXT_PROJECT_CONFIG|Polecenia, które ustawiają konfigurację projektu i kolejność kompilacji.|
|IDG_VS_CTXT_PROJECT_ADD|Polecenia, które dodają elementy do projektu.|
|IDG_VS_CTXT_PROJECT_START|Polecenia, które ustawiają projekt uruchamiania skojarzony z kluczem F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Polecenia służące do zapisywania elementów projektu.|
|IDG_VS_CTXT_PROJECT_DEBUG|Polecenia do debugowania.|
|IDG_VS_CTXT_PROJECT_SCC|Polecenia do kontroli źródła.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Polecenia do operacji wycinania, kopiowania i wklejania.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Polecenia zapewniające dostęp do okna dialogowego **Właściwości projektu.**|

## <a name="see-also"></a>Zobacz też

- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md)
