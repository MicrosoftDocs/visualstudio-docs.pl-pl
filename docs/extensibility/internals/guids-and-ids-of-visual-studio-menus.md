---
title: Identyfikator GUID i identyfikatory menu programu Visual Studio | Microsoft Docs
description: Wyświetl listę wartości identyfikatora GUID i identyfikatora dla menu i grup na pasku menu programu Visual Studio, które znajdują się w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9f5066c5ae5c9fa57517406b8eca388747979c4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082091"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identyfikator GUID i identyfikatory menu programu Visual Studio
W tym artykule jest wyliczany identyfikator GUID i wartości identyfikatorów menu i grup na pasku menu programu Visual Studio. Te wartości są zdefiniowane w plikach *. vsct* , które są instalowane w ramach zestawu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [polecenia, menu i grupy zdefiniowane przez środowisko IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami zintegrowanego środowiska programistycznego (IDE), które są zdefiniowane w plikach *. vsct* , zobacz sekcję [rozszerzającą menu i polecenia](../../extensibility/extending-menus-and-commands.md).

 Menu i grupy na pasku menu programu Visual Studio używają identyfikatora GUID `guidSHLMainMenu` . Pasek menu ma identyfikator `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupy na pasku menu programu Visual Studio
 Aby dodać menu do paska menu, Ustaw jedną z tych grup jako nadrzędną.

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Plik/Edycja/Widok|IDG_VS_MM_FILEEDITVIEW|
|Refaktoryzacja|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Kompilacja|IDG_VS_MM_BUILDDEBUGRUN|
|Format/narzędzia|IDG_VS_MM_TOOLSADDINS|
|Okno/Pomoc/społeczność|IDG_VS_MM_WINDOWHELP|
|Dodatki|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu na pasku menu programu Visual Studio
 Aby dodać grupę do istniejącego menu programu Visual Studio, należy ustawić jeden z następujących menu jako jego element nadrzędny. Podmenu nie znajdują się na tej liście.

|Menu|ID (Identyfikator)|
|----------|--------|
|Plik|IDM_VS_MENU_FILE|
|Edytuj|IDM_VS_MENU_EDIT|
|Widok|IDM_VS_MENU_VIEW|
|Refaktoryzacja|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Kompilacja|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|narzędzia|IDM_VS_MENU_TOOLS|
|Rozszerzenia|IDM_VS_MENU_EXTENSIONS|
|Okno|IDM_VS_MENU_WINDOW|
|Dodatki|IDM_VS_MENU_ADDINS|
|Społeczność|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Grupy w menu programu Visual Studio
 Na poniższych listach przedstawiono grupy, które pozostały bezpośrednio z menu na pasku menu programu Visual Studio. Najszybszym sposobem dodawania polecenia do menu programu Visual Studio jest ustawienie jednej z tych grup jako nadrzędnej. Grupy, których nie ma w podmenu, nie są wyświetlane w tej sekcji.

### <a name="file-menu-groups"></a>Grupy menu plików

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Nowy/otwarty|IDG_VS_FILE_FILE|
|Dodaj|IDG_VS_FILE_ADD|
|Rozwiązanie|IDG_VS_FILE_SOLUTION|
|Różne|IDG_VS_FILE_MISC|
|Zapisz|IDG_VS_FILE_SAVE|
|Zmień nazwę|IDG_VS_FILE_RENAME|
|Przeglądarka|IDG_VS_FILE_BROWSER|
|Drukuj|IDG_VS_FILE_PRINT|
|Ostatnio używane|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Zakończ|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Edytuj grupy menu

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Cofnij/ponów|IDG_VS_EDIT_UNDOREDO|
|Wytnij/Kopiuj/Wklej|IDG_VS_EDIT_CUTCOPY|
|Wybierz pozycję|IDG_VS_EDIT_SELECT|
|Chodzenie|IDG_VS_EDIT_GOTO|
|Znajdowanie|IDG_VS_EDIT_FIND|
|Obiekty|IDG_VS_EDIT_OBJECTS|
|Zlecenia OLE|IDG_VS_EDIT_OLEVERBS|
|Źródło polecenia|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Grupy menu refaktoryzacji

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Wspólne|IDG_REFACTORING_COMMON|
|Zaawansowany|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Grupy menu Widok

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Kod formularza|IDG_VS_VIEW_FORMCODE|
|Przeglądarka|IDG_VS_VIEW_BROWSER|
|Definiowanie widoków|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Okna architekta|IDG_VS_VIEW_ARCH_WINDOWS|
|Okna organizacji|IDG_VS_VIEW_ORG_WINDOWS|
|Przeglądarka kodu|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Okna deweloperskie|IDG_VS_VIEW_DEV_WINDOWS|
|Paski narzędzi|IDG_VS_VIEW_TOOLBARS|
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Nawigacja|IDG_VS_VIEW_NAVIGATE|
|Mała Nawigacja|IDG_VS_VIEW_SMALLNAVIGATE|
|Przeglądarka obiektów|IDG_VS_VIEW_OBJBRWSR|
|Źródło polecenia|IDG_VS_VIEW_COMMANDWELL|
|Strony właściwości|IDG_VS_VIEW_PROPPAGES|
|Odśwież|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupy menu projektu

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Różne Dodawanie|IDG_VS_PROJ_MISCADD|
|Dodaj|IDG_VS_PROJ_ADD|
|Folder|IDG_VS_PROJ_FOLDER|
|Zwolnij/Załaduj ponownie|IDG_VS_PROJ_UNLOADRELOAD|
|Odwołanie|IDG_VS_PROJ_REFERENCE|
|Opcje|IDG_VS_PROJ_OPTIONS|
|Ustawienia|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Grupy menu kompilacji

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Rozwiązanie|IDG_VS_BUILD_SOLUTION|
|Wybór|IDG_VS_BUILD_SELECTION|
|Optymalizacja sterowana profilem|IDG_VS_PGO_SELECTION|
|Różne|IDG_VS_BUILD_MISC|
|Anuluj|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Grupy menu Narzędzia

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Wiersz polecenia|IDG_VS_TOOLS_CMDLINE|
|Fragmenty kodu|IDG_VS_TOOLS_SNIPPETS|
|Podzestaw obiektów|IDG_VS_TOOLS_OBJSUBSET|
|Opcje|IDG_VS_TOOLS_OPTIONS|
|Inne 2|IDG_VS_TOOLS_OTHER2|
|Narzędzia zewnętrzne|IDG_VS_TOOLS_EXT_TOOLS|
|Dostosowania zewnętrzne|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Grupy menu okna

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Nowy|IDG_VS_WINDOW_NEW|
|Zadokuj/Zamknij|IDG_VS_DOCKCLOSE|
|Zadokuj/Ukryj|IDG_VS_DOCKHIDE|
|Rozmieszczanie|IDG_VS_WINDOW_ARRANGE|
|Nawigacja|IDG_VS_WINDOW_NAVIGATION|
|Lista|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupy menu Pomoc

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Samples|IDG_VS_HELP_SAMPLES|
|Pomoc techniczna|IDG_VS_HELP_SUPPORT|
|Informacje|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Podmenu menu programu Visual Studio
 W poniższej hierarchii przedstawiono podmenu, które są skojarzone z menu na pasku menu programu Visual Studio. Ponieważ tylko Grupa może mieć menu jako jego element nadrzędny, każde podmenu musi mieć wartość z grupy w menu, a nie bezpośrednio z menu. Aby uzyskać więcej informacji na temat relacji między menu, grupami i podmenumi, zobacz [Dodawanie podmenu do menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Nazwy menu na pasku menu programu Visual Studio nie są odrębnie wyświetlane w tej hierarchii, ponieważ mogą być wywnioskowane z konwencji nazewnictwa dla grup w IDE w następujący sposób: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

|Grupa nadrzędna|Podmenu|Grupy podrzędne|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... ust|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Zobacz też
- [Identyfikatory GUID i identyfikator pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Identyfikator GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
