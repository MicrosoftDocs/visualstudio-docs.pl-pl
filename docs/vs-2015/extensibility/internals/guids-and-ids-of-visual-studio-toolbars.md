---
title: Identyfikatory GUID i identyfikatory pasków narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 183baec1e0170f9c34a100cbf64257a3e7fa45e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061858"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym temacie wylicza wartości Identyfikator GUID i identyfikator pasków narzędzi, które są zawarte w programie Visual Studio zintegrowane środowisko programistyczne (IDE) i grupy mogą zawierać. Te wartości są definiowane w .vsct — pliki, które są zainstalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
>  Wiele pasków narzędzi dostępnych w programie Visual Studio nie są zdefiniowane przez program Visual Studio i ich identyfikatorów GUID i identyfikator wartości nie są publiczne. Ten temat zawiera tylko paski narzędzi, które są zdefiniowane w programie Visual Studio SDK .vsct — pliki.

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami środowiska IDE, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Domyślne paski narzędzi dostarczonych przez program Visual Studio IDE Użyj identyfikatora GUID `guidSHLMainMenu`, z wyjątkiem w przypadku, gdy określono inaczej, używając składni GUID:ID.

## <a name="ide-toolbars"></a>Paski narzędzi IDE
 Następujące paski narzędzi są dostarczane przez program Visual Studio IDE. Paski narzędzi mogą być wyświetlane, wybierając je na **pasków narzędzi** podmenu **narzędzia** menu. Paski narzędzi w oknach narzędzi nie znajdują się w tej sekcji.

 Tylko grupy można jest elementem podrzędnym elementu bezpośrednio pasków narzędzi. Aby dodać grupę, ustaw jego element nadrzędny identyfikator GUID i identyfikator, na pasku narzędzi. Aby dodać przycisk do paska narzędzi, należy ustawić jego elementu nadrzędnego z grupą na pasku narzędzi.

|Pasek narzędzi|ID|
|-------------|--------|
|Standardowa|IDM_VS_TOOL_STANDARD|
|Kompilacja|IDM_VS_TOOL_BUILD|
|Edytor tekstu|IDM_VS_TOOL_TEXTEDITOR|
|Debugowanie|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Lokalizacja debugowania|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Specjalne pasków narzędzi
 Te paski narzędzi są definiowane przez program Visual Studio IDE, ale obsługiwać wyspecjalizowane funkcje i nie jest hostem grup poleceń.

|Pasek narzędzi|ID|
|-------------|--------|
|Polecenie Add|IDM_VS_TOOL_ADDCOMMAND|
|Niezdefiniowane|IDM_VS_TOOL_UNDEFINED|
|schemat XML|IDM_VS_TOOL_SCHEMA|
|Dane XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Grupy na paskach narzędzi IDE
 Aby dodać przycisk do standardowego paska narzędzi, należy ustawić jedną z następujących grup jako klasy nadrzędnej. Grupy są sortowane przez nadrzędne paska narzędzi.

### <a name="standard-toolbar-groups"></a>Standardowy pasek narzędzi grup

|Nazwa|ID|
|----------|--------|
|Zapisywanie i otwieranie|IDG_VS_TOOLSB_SAVEOPEN|
|Wytnij/Kopiuj|IDG_VS_TOOLSB_CUTCOPY|
|Cofnij/Ponów.|IDG_VS_TOOLSB_UNDOREDO|
|Uruchom/Build|IDG_VS_TOOLSB_RUNBUILD|
|Wyszukaj|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nowy Windows|IDG_VS_TOOLSB_NEWWINDOWS|
|Ładowania/zapisu|IDG_VS_WINDOWUI_LOADSAVE|
|Miernik|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Tworzenie grup paska narzędzi

|Nazwa|ID|
|----------|--------|
|Pasek kompilacji|IDG_VS_BUILDBAR|
|Anuluj|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Pasek narzędzi edytora tekstu grupy

|Nazwa|ID|
|----------|--------|
|Uzupełnianie|IDM_VS_TOOL_TEXTEDITOR|
|Zwiększ wcięcie|IDG_VS_EDITTOOLBAR_INDENT|
|Komentarz|IDG_VS_EDITTOOLBAR_COMMENT|
|Zakładki|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Debugowanie grup paska narzędzi

|Nazwa|ID|
|----------|--------|
|Wykonanie|IDM_DEBUG_TOOLBAR|
|Przechodzenie krok po kroku|IDG_DEBUG_TOOLBAR_STEPPING|
|Wyrażenie kontrolne|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Grupy pasek narzędzi lokalizacji debugowania

|Nazwa|ID|
|----------|--------|
|Lokalizacja debugowania|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Paskach narzędzi okna
 Paski narzędzi mogą być wyświetlane bezpośrednio w środowisku IDE lub w oknach narzędzi takich jak **Eksploratora rozwiązań**. Ponieważ okna narzędzi nie są zdefiniowane w plikach vsct, paskach narzędzi okna nie mają zdefiniowanych elementów nadrzędnych. Zamiast tego są umieszczane w kodzie. W poniższej tabeli przedstawiono pasków narzędzi, które pojawiają się na okien narzędzi w IDE i grup poleceń, które zawierają.

> [!NOTE]
>  Paski narzędzi i grup Użyj identyfikatora GUID `guidSHLMainMenu`, z wyjątkiem w przypadku, gdy określono inaczej, używając składni GUID:ID. W przypadku, gdy identyfikator GUID jest określony dla paska narzędzi, ma również zastosowanie do grupy, które jest elementem podrzędnym elementu tego paska narzędzi.

|Okna narzędzi|Pasek narzędzi|Grupy|
|-----------------|-------------|------------|
|Eksplorator rozwiązań|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|
|Server Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Właściwości|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Widok klas|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Widok klas|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Przeglądarka obiektów|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Dane wyjściowe|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Znajdź i zamień|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Znajdź wyniki 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Znajdź wyniki 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Fragment kodu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Zakładki|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Lista zadań|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Zadania użytkownika|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Lista błędów|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Przeglądarka wywołań|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Punkty przerwania|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Dezasemblacji|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Pamięć 1 – 4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|
|Procesy|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Zobacz też
 [Dodawanie kontrolera Menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md) [Dodawanie paska narzędzi do okna narzędzi](../../extensibility/adding-a-toolbar-to-a-tool-window.md) [identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
