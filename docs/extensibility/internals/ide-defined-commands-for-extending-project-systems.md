---
title: IDE-Defined polecenia rozszerzania systemów projektu | Microsoft Docs
description: Dowiedz się więcej o poleceniach i grupach poleceń zdefiniowanych Visual Studio zintegrowanym środowisku projektowym (IDE), które są używane do rozszerzania systemów projektów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4525802bf308d740ea5c468fac171e74bff2b34e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901165"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu
Jeśli chcesz rozszerzyć systemy projektów, możesz użyć poleceń i grup poleceń dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ideę IDE.

 W poniższych sekcjach przedstawiono elementy poleceń, które są szczególnie przydatne podczas rozszerzania systemów projektów.

## <a name="command-menus"></a>Menu poleceń
 W poniższej tabeli przedstawiono menu poleceń, które są przydatnymi lokalizacjami do umieszczania poleceń wysokiego poziomu, które wywołują rozszerzenie projektu.

|Menu polecenia|Opis|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Menu **najwyższego** poziomu Project (Projekt).|
|IDM_VS_TOOL_PROJWIN|Pasek **Eksplorator rozwiązań** narzędzi.|

## <a name="shortcut-menus"></a>Menu skrótów
 W poniższej tabeli przedstawiono menu skrótów, które mają zastosowanie w przypadku zaznaczenia pojedynczego węzła w programie **Eksplorator rozwiązań** lub gdy w programie Eksplorator rozwiązań istnieje wiele jednorodnych wyborów, **czyli** gdy wszystkie wybrane węzły są tego samego typu.

|Menu skrótów|Opis|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Ma zastosowanie po wybraniu węzła projektu.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Ma zastosowanie po wybraniu pliku.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Ma zastosowanie po wybraniu folderu.|
|IDM_VS_CTXT_WEBREFFOLDER|Ma zastosowanie po wybraniu folderu Web Reference.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Ma zastosowanie, gdy wybrano węzeł główny odwołań o nazwie "Odwołania".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Ma zastosowanie w przypadku wyboru węzłów odniesienia; Obejmują one tylko odwołania do zestawu, com i projektu. Nie zawiera odwołań internetowych.|

 W poniższej tabeli przedstawiono menu skrótów, które mają zastosowanie, gdy zaznaczenie w Eksplorator rozwiązań **obejmuje** wiele hierarchii,

|Menu skrótów|Opis|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Ma zastosowanie, gdy bieżący wybór zawiera węzeł rozwiązania i węzły projektu głównego.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Ma zastosowanie, gdy bieżący wybór zawiera węzeł rozwiązania i elementy projektu.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Ma zastosowanie, gdy bieżący wybór składa się tylko z wielu węzłów projektu głównego.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Ma zastosowanie, gdy bieżący wybór zawiera kombinację węzłów projektu głównego i elementów projektu. Ponadto wybór może zawierać węzeł rozwiązania.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Ma zastosowanie, gdy bieżące zaznaczenie zawiera elementy projektu z wielu projektów w rozwiązaniu lub gdy elementy różnych typów są wybrane w tym samym projekcie.|

## <a name="command-groups"></a>Grupy poleceń
 W poniższej tabeli przedstawiono grupy poleceń, których można używać podczas rozszerzania projektów i do których można uzyskać dostęp za pośrednictwem <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu skrótów.

|Grupa poleceń|Opis|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Polecenia do kompilowania, ponownego kompilowania i wdrażania projektu.|
|IDG_VS_CTXT_COMPILELINK|Polecenia do kompilowania i łączenia projektu.|
|IDG_VS_CTXT_PROJECT_CONFIG|Polecenia, które ustawiają konfigurację projektu i kolejność kompilacji.|
|IDG_VS_CTXT_PROJECT_ADD|Polecenia, które dodają elementy do projektu.|
|IDG_VS_CTXT_PROJECT_START|Polecenia, które ustawiają projekt startowy skojarzony z klawiszem F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Polecenia do zapisywania elementów projektu.|
|IDG_VS_CTXT_PROJECT_DEBUG|Polecenia debugowania.|
|IDG_VS_CTXT_PROJECT_SCC|Polecenia kontroli źródła.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Polecenia dla operacji wycinania, kopiowania i wklejania.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Polecenia, które zapewniają dostęp do **okna dialogowego Właściwości** projektu.|

## <a name="see-also"></a>Zobacz też

- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md)
