---
title: Identyfikatory GUID i identyfikatory Visual Studio narzędzi | Microsoft Docs
description: Wyświetl listę wartości identyfikatorów GUID i ID dla pasków narzędzi i grup, które zawierają, które znajdują się w Visual Studio zintegrowanego środowiska projektowego (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d2ba6c92a2913ec63a59751a4181454aa67fa67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898113"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identyfikatory GUID i identyfikatory Visual Studio paskach narzędzi
W tym temacie wyliczyliśmy wartości identyfikatorów GUID i ID pasków narzędzi, które znajdują się Visual Studio zintegrowanym środowisku projektowym (IDE) i grup, które zawierają. Te wartości są definiowane *w plikach vsct,* które są instalowane w ramach zestawu VISUAL STUDIO SDK. Aby uzyskać więcej informacji, zobacz [Polecenia, menu i](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)grupy zdefiniowane w idee .

> [!NOTE]
> Wiele pasków narzędzi dostępnych dla Visual Studio nie jest zdefiniowanych przez Visual Studio, a ich wartości identyfikatora GUID i ID nie są publiczne. W tym temacie wymieniono tylko paski narzędzi zdefiniowane w Visual Studio SDK *.vsct.*

 Aby uzyskać więcej informacji na temat pracy z obiektami IDE zdefiniowanymi w *plikach vsct,* zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Domyślne paski narzędzi udostępniane przez program Visual Studio IDE używają identyfikatora GUID , z wyjątkiem sytuacji, w których określono `guidSHLMainMenu` inaczej przy użyciu składni `GUID:ID` .

## <a name="ide-toolbars"></a>Paski narzędzi środowiska IDE
 Następujące paski narzędzi są udostępniane przez Visual Studio IDE. Paski narzędzi można wyświetlić, wybierając je w **podmenu** Paski narzędzi **menu** Narzędzia. Paski narzędzi w oknach narzędzi nie są uwzględnione w tej sekcji.

 Tylko grupy mogą maleć bezpośrednio z pasków narzędzi. Aby dodać grupę, ustaw jej element nadrzędny na identyfikator GUID i identyfikator paska narzędzi. Aby dodać przycisk do paska narzędzi, ustaw jego element nadrzędny na grupę na pasku narzędzi.

|Pasek narzędzi|ID (Identyfikator)|
|-------------|--------|
|Standardowa (Standard)|IDM_VS_TOOL_STANDARD|
|Kompilacja|IDM_VS_TOOL_BUILD|
|Edytor tekstu|IDM_VS_TOOL_TEXTEDITOR|
|Debugowanie|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Lokalizacja debugowania|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Specjalne paski narzędzi
 Te paski narzędzi są definiowane przez Visual Studio IDE, ale obsługują specjalne funkcje i nie hostują grup poleceń.

|Pasek narzędzi|ID (Identyfikator)|
|-------------|--------|
|Polecenie Add|IDM_VS_TOOL_ADDCOMMAND|
|Niezdefiniowane|IDM_VS_TOOL_UNDEFINED|
|Schemat XML|IDM_VS_TOOL_SCHEMA|
|Dane XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Grupy na paskach narzędzi ide
 Aby dodać przycisk do standardowego paska narzędzi, ustaw jedną z następujących grup jako element nadrzędny. Grupy są sortowane według nadrzędnego paska narzędzi.

### <a name="standard-toolbar-groups"></a>Standardowe grupy pasków narzędzi

|Nazwa|ID (Identyfikator)|
|----------|--------|
|Zapisywanie/otwieranie|IDG_VS_TOOLSB_SAVEOPEN|
|Wycinanie/kopiowanie|IDG_VS_TOOLSB_CUTCOPY|
|Cofanie/ponowne cofanie|IDG_VS_TOOLSB_UNDOREDO|
|Uruchamianie/kompilowanie|IDG_VS_TOOLSB_RUNBUILD|
|Wyszukaj|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nowe okna|IDG_VS_TOOLSB_NEWWINDOWS|
|Ładowanie/zapisywanie|IDG_VS_WINDOWUI_LOADSAVE|
|Miernik|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Tworzenie grup pasków narzędzi

|Nazwa|ID (Identyfikator)|
|----------|--------|
|Pasek kompilacji|IDG_VS_BUILDBAR|
|Anuluj|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Grupy pasków narzędzi edytora tekstu

|Nazwa|ID (Identyfikator)|
|----------|--------|
|Ukończenie|IDM_VS_TOOL_TEXTEDITOR|
|Wcięcie|IDG_VS_EDITTOOLBAR_INDENT|
|Komentarz|IDG_VS_EDITTOOLBAR_COMMENT|
|Zakładki|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Debugowanie grup pasków narzędzi

|Nazwa|ID (Identyfikator)|
|----------|--------|
|Wykonanie|IDM_DEBUG_TOOLBAR|
|Stepping|IDG_DEBUG_TOOLBAR_STEPPING|
|Zegarek|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Grupy paska narzędzi lokalizacji debugowania

|Nazwa|ID (Identyfikator)|
|----------|--------|
|Lokalizacja debugowania|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Paski narzędzi okna
 Paski narzędzi mogą być wyświetlane bezpośrednio w ide lub w oknach narzędzi, takich **jak Eksplorator rozwiązań**. Ponieważ okna narzędzi nie są zdefiniowane w *plikach vsct,* na paskach narzędzi nie zdefiniowano ich rodziców. Zamiast tego są one umieszczane w kodzie. W poniższej tabeli przedstawiono paski narzędzi wyświetlane w oknach narzędzi w idee oraz zawarte w nich grupy poleceń.

> [!NOTE]
> Paski narzędzi i grupy używają identyfikatora GUID , z wyjątkiem sytuacji, gdy określono inaczej `guidSHLMainMenu` przy użyciu składni IDENTYFIKATORA GUID:ID. Jeśli dla paska narzędzi określono identyfikator GUID, ma również zastosowanie do grup, które maleją z tego paska narzędzi.

|Okno narzędzi|Pasek narzędzi|Grupy|
|-----------------|-------------|------------|
|Eksplorator rozwiązań|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1. 5|
|Eksplorator serwera|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Właściwości|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Widok klas|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Widok klas|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Dane wyjściowe|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Znajdź i zamień|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Znajdowanie wyników 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Znajdowanie wyników 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Fragment kodu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Zakładki|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Lista zadań|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Zadania użytkownika|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Lista błędów|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Przeglądarka wywołań|IDM_VS_TOOL_CALLBROWSER1. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Punkty przerwania|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Demontażu|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Pamięć 1–4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1. 4<br /><br /> IDG_MEMORY_COLUMNS1. 4|
|Procesy|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Zobacz też
- [Dodawanie kontrolera menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Dodawanie paska narzędzi do okna narzędzi](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Identyfikatory GUID i identyfikatory Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
