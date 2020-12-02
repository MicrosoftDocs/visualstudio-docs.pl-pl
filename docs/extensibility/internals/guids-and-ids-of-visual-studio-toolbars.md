---
title: Identyfikatory GUID i identyfikator pasków narzędzi programu Visual Studio | Microsoft Docs
description: Wyświetl listę wartości identyfikatora GUID i identyfikatora dla pasków narzędzi i zawartych w nich grup, które znajdują się w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44cda401faa0d7e34bf9ce7579aa3cca026fa13
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480385"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identyfikatory GUID i identyfikator pasków narzędzi programu Visual Studio
W tym temacie przedstawiono identyfikatory GUID i identyfikator pasków narzędzi, które znajdują się w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, oraz zawartych w nich grup. Te wartości są zdefiniowane w plikach *. vsct* , które są instalowane w ramach zestawu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [polecenia, menu i grupy zdefiniowane przez środowisko IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Wiele pasków narzędzi dostępnych dla programu Visual Studio nie jest zdefiniowanych przez program Visual Studio, a ich identyfikatory GUID i identyfikatory nie są publiczne. W tym temacie wymieniono tylko paski narzędzi, które są zdefiniowane w plikach *vsct* zestawu SDK programu Visual Studio.

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami IDE zdefiniowanymi w plikach *. vsct* , zobacz sekcję [rozszerzając menu i polecenia](../../extensibility/extending-menus-and-commands.md).

 Domyślne paski narzędzi udostępniane przez środowisko IDE programu Visual Studio używają identyfikatora GUID `guidSHLMainMenu` , chyba że określono inaczej przy użyciu `GUID:ID` składni.

## <a name="ide-toolbars"></a>Paski narzędzi IDE
 Poniższe paski narzędzi są udostępniane przez środowisko IDE programu Visual Studio. Paski narzędzi można wyświetlić, zaznaczając je w podmenu **paski narzędzi** menu **Narzędzia** . Paski narzędzi w oknach narzędzi nie są uwzględnione w tej sekcji.

 Tylko grupy mogą być wyświetlane bezpośrednio z pasków narzędzi. Aby dodać grupę, ustaw jej element nadrzędny na identyfikator GUID i identyfikator paska narzędzi. Aby dodać przycisk do paska narzędzi, ustaw jego element nadrzędny na grupę na pasku narzędzi.

|Pasek narzędzi|ID|
|-------------|--------|
|Standardowa|IDM_VS_TOOL_STANDARD|
|Kompilacja|IDM_VS_TOOL_BUILD|
|Edytor tekstu|IDM_VS_TOOL_TEXTEDITOR|
|Debugowanie|guidVSDebugGroup: IDM_DEBUG_TOOLBAR|
|Lokalizacja debugowania|guidVSDebugGroup: IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Specjalne paski narzędzi
 Te paski narzędzi są definiowane przez środowisko IDE programu Visual Studio, ale obsługują funkcje wyspecjalizowane i nie obsługują grup poleceń.

|Pasek narzędzi|ID|
|-------------|--------|
|Polecenie Add|IDM_VS_TOOL_ADDCOMMAND|
|Niezdefiniowane|IDM_VS_TOOL_UNDEFINED|
|Schemat XML|IDM_VS_TOOL_SCHEMA|
|Dane XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Grupy na paskach narzędzi IDE
 Aby dodać przycisk do standardowego paska narzędzi, należy ustawić jedną z następujących grup jako nadrzędną. Grupy są sortowane według nadrzędnego paska narzędzi.

### <a name="standard-toolbar-groups"></a>Standardowe grupy paska narzędzi

|Nazwa|ID|
|----------|--------|
|Zapisz/Otwórz|IDG_VS_TOOLSB_SAVEOPEN|
|Wytnij/Kopiuj|IDG_VS_TOOLSB_CUTCOPY|
|Cofnij/ponów|IDG_VS_TOOLSB_UNDOREDO|
|Uruchom/Kompiluj|IDG_VS_TOOLSB_RUNBUILD|
|Wyszukiwanie|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nowe okna|IDG_VS_TOOLSB_NEWWINDOWS|
|Załaduj/Zapisz|IDG_VS_WINDOWUI_LOADSAVE|
|Miernik|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Tworzenie grup pasków narzędzi

|Nazwa|ID|
|----------|--------|
|Pasek kompilacji|IDG_VS_BUILDBAR|
|Anuluj|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Grupy paska narzędzi edytora tekstu

|Nazwa|ID|
|----------|--------|
|Ukończenie|IDM_VS_TOOL_TEXTEDITOR|
|Wyświetlane|IDG_VS_EDITTOOLBAR_INDENT|
|Komentarz|IDG_VS_EDITTOOLBAR_COMMENT|
|Zakładki|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Grupy paska narzędzi debugowania

|Nazwa|ID|
|----------|--------|
|Wykonanie|IDM_DEBUG_TOOLBAR|
|Wzmacnia|IDG_DEBUG_TOOLBAR_STEPPING|
|Zegarek|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Grupy paska narzędzi lokalizacji debugowania

|Nazwa|ID|
|----------|--------|
|Lokalizacja debugowania|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Paski narzędzi okna narzędzi
 Paski narzędzi mogą być wyświetlane bezpośrednio w środowisku IDE lub w oknach narzędzi, takich jak **Eksplorator rozwiązań**. Ponieważ okna narzędzi nie są zdefiniowane w plikach *. vsct* , paski narzędzi okna narzędzi nie mają zdefiniowanych elementów nadrzędnych. Zamiast tego są umieszczane w kodzie. W poniższej tabeli przedstawiono paski narzędzi, które znajdują się w oknach narzędzi w środowisku IDE, oraz grupy poleceń, które zawierają.

> [!NOTE]
> Paski narzędzi i grupy używają identyfikatora GUID `guidSHLMainMenu` , chyba że określono inaczej przy użyciu identyfikatora GUID: ID składni. Gdy identyfikator GUID jest określony dla paska narzędzi, ma również zastosowanie do grup, które są podrzędne od tego paska narzędzi.

|Okno narzędzia|Pasek narzędzi|Grupy|
|-----------------|-------------|------------|
|Eksplorator rozwiązań|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5000|
|Eksplorator serwera|guid_SE_MenuGroup: IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Właściwości|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Widok klas|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Widok klas|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Dane wyjściowe|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Znajdź i zamień|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Znajdź wyniki 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Wyniki wyszukiwania 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Fragment kodu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Zakładki|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Lista zadań|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Zadania użytkownika|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Lista błędów|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Przeglądarka wywołań|IDM_VS_TOOL_CALLBROWSER1.. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Punkty przerwania|guidVSDebugGroup: IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Dezasemblacji|guidVSDebugGroup: IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Pamięć 1-4|guidVSDebugGroup: IDM_MEMORY_WINDOW_TOOLBAR1... czwart|IDG_MEMORY_EXPRESSION1.. czwart<br /><br /> IDG_MEMORY_COLUMNS1.. czwart|
|Procesy|guidVSDebugGroup: IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Zobacz też
- [Dodawanie kontrolera menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Dodawanie paska narzędzi do okna narzędzi](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Identyfikator GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
