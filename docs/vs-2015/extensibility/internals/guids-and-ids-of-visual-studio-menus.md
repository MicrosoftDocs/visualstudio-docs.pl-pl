---
title: Identyfikatory GUID i identyfikatory menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3884097f24309b1f73e7e74bcecf0659352c1ab8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940961"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identyfikatory GUID i identyfikatory menu programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym temacie wylicza wartości Identyfikator GUID i identyfikator menu i grup na pasku menu programu Visual Studio. Te wartości są definiowane w .vsct — pliki, które są zainstalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami środowiska (IDE) zintegrowanego rozwoju, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Menu i grup na pasku menu programu Visual Studio, użyj identyfikatora GUID `guidSHLMainMenu`. Menu paska ma identyfikator równy `IDM_VS_TOOL_MAINMENU`.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupy na pasku Menu programu Visual Studio
 Aby dodać menu na pasku menu, należy ustawić jednej z tych grup jako klasy nadrzędnej.

|Grupa|ID|
|-----------|--------|
|Plik/Edycja/widok|IDG_VS_MM_FILEEDITVIEW|
|Refaktoryzacja|IDG_VS_MM_REFACTORING:|
|Projekt|IDG_VS_MM_PROJECT|
|Kompilacja|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Tools|IDG_VS_MM_TOOLSADDINS|
|Okno/Pomoc/Community|IDG_VS_MM_WINDOWHELP|
|Dodatki|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu na pasku Menu programu Visual Studio
 Aby dodać grupę do istniejącego menu programu Visual Studio, należy ustawić jedną z następujących menu jako klasy nadrzędnej. Podmenu nie znajdują się na tej liście.

|Menu|ID|
|----------|--------|
|Plik|IDM_VS_MENU_FILE|
|Edytowanie|IDM_VS_MENU_EDIT|
|Widok|IDM_VS_MENU_VIEW|
|Refaktoryzacja|IDM_VS_MENU_REFACTORING|
|Projekt|IDM_VS_MENU_PROJECT|
|Kompilacja|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Narzędzia|IDM_VS_MENU_TOOLS|
|Okno|IDM_VS_MENU_WINDOW|
|Dodatki|IDM_VS_MENU_ADDINS|
|Społeczność|IDM_VS_MENU_COMMUNITY|
|Pomoc|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Grupy menu programu Visual Studio
 Poniższej przedstawiono grupy, które jest elementem podrzędnym elementu bezpośrednio z poziomu menu na pasku menu programu Visual Studio. Najszybszym sposobem, aby dodać polecenie do menu programu Visual Studio jest do ustawienia jednej z tych grup jako element nadrzędny. Grupy, które jest elementem podrzędnym elementu menu podrzędne nie są wyświetlane w tej sekcji.

### <a name="file-menu-groups"></a>Grupy Menu Plik

|Grupa|ID|
|-----------|--------|
|Nowe/Otwórz|IDG_VS_FILE_FILE|
|Dodaj|IDG_VS_FILE_ADD|
|Rozwiązanie|IDG_VS_FILE_SOLUTION|
|Różne|IDG_VS_FILE_MISC|
|Zapisanie|IDG_VS_FILE_SAVE|
|Zmień nazwę|IDG_VS_FILE_RENAME|
|Przeglądarka|IDG_VS_FILE_BROWSER|
|Drukuj|IDG_VS_FILE_PRINT|
|Ostatnio używane|IDG_VS_FILE_MRU|
|Przenieś|IDG_VS_FILE_MOVE|
|Zakończ|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Edytuj grupy Menu

|Grupa|ID|
|-----------|--------|
|Cofnij/Ponów.|IDG_VS_EDIT_UNDOREDO|
|Wycinania/kopiowania/wklejania|IDG_VS_EDIT_CUTCOPY|
|Wybierz|IDG_VS_EDIT_SELECT|
|Przejdź do|IDG_VS_EDIT_GOTO|
|Znajdź|IDG_VS_EDIT_FIND|
|Obiekty|IDG_VS_EDIT_OBJECTS|
|Czasowniki OLE|IDG_VS_EDIT_OLEVERBS|
|Polecenie dobrze|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refaktoryzuj grupy Menu

|Grupa|ID|
|-----------|--------|
|Wspólne|IDG_REFACTORING_COMMON|
|Zaawansowane|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Grupy Menu Widok

|Grupa|ID|
|-----------|--------|
|Kod formularza|IDG_VS_VIEW_FORMCODE|
|Przeglądarka|IDG_VS_VIEW_BROWSER|
|Definiowanie widoków|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architekt Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Windows organizacji|IDG_VS_VIEW_ORG_WINDOWS|
|Przeglądarka kodu|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Windows Dev|IDG_VS_VIEW_DEV_WINDOWS|
|Paski narzędzi|IDG_VS_VIEW_TOOLBARS|
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Przejdź|IDG_VS_VIEW_NAVIGATE|
|Przejdź w małych|IDG_VS_VIEW_SMALLNAVIGATE|
|Przeglądarka obiektów|IDG_VS_VIEW_OBJBRWSR|
|Polecenie dobrze|IDG_VS_VIEW_COMMANDWELL|
|Strony właściwości|IDG_VS_VIEW_PROPPAGES|
|Odśwież|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupy Menu projektu

|Grupa|ID|
|-----------|--------|
|Różne Dodaj|IDG_VS_PROJ_MISCADD|
|Dodaj|IDG_VS_PROJ_ADD|
|Folder|IDG_VS_PROJ_FOLDER|
|Zwolnienie/ponowne załadowanie|IDG_VS_PROJ_UNLOADRELOAD|
|Tematy pomocy|IDG_VS_PROJ_REFERENCE|
|Opcje|IDG_VS_PROJ_OPTIONS|
|Ustawienia|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Tworzenie grupy Menu

|Grupa|ID|
|-----------|--------|
|Rozwiązanie|IDG_VS_BUILD_SOLUTION|
|Wybór|IDG_VS_BUILD_SELECTION|
|Optymalizacja sterowana profilem|IDG_VS_PGO_SELECTION|
|Różne|IDG_VS_BUILD_MISC|
|Anuluj|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Grupy Menu narzędzia

|Grupa|ID|
|-----------|--------|
|Wiersz polecenia|IDG_VS_TOOLS_CMDLINE|
|Fragmenty kodu|IDG_VS_TOOLS_SNIPPETS|
|Podzbiór obiektów|IDG_VS_TOOLS_OBJSUBSET|
|Opcje|IDG_VS_TOOLS_OPTIONS|
|Inne 2|IDG_VS_TOOLS_OTHER2|
|Narzędzia zewnętrzne|IDG_VS_TOOLS_EXT_TOOLS|
|Dostosowania zewnętrznych|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Grupy Menu okna

|Grupa|ID|
|-----------|--------|
|New|IDG_VS_WINDOW_NEW|
|Zadokuj/zamykającego|IDG_VS_DOCKCLOSE|
|Ukryj/Dock|IDG_VS_DOCKHIDE|
|Rozmieść|IDG_VS_WINDOW_ARRANGE|
|Nawigacja|IDG_VS_WINDOW_NAVIGATION|
|Lista|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupy Menu Pomoc

|Grupa|ID|
|-----------|--------|
|Przykłady|IDG_VS_HELP_SAMPLES|
|Obsługa|IDG_VS_HELP_SUPPORT|
|Informacje|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Podmenu menu programu Visual Studio
 Następującej hierarchii zawiera podmenu, które są skojarzone z menu na pasku menu programu Visual Studio. Ponieważ tylko grupa może mieć menu jako klasy nadrzędnej, co podmenu musi jest elementem podrzędnym elementu z grupy menu, zamiast bezpośrednio z menu. Aby uzyskać więcej informacji na temat relacji między menu, grup i podmenu, zobacz [dodawanie podmenu do Menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
>  Nazwy menu na pasku menu programu Visual Studio nie są oddzielnie wyświetlane w tej hierarchii, ponieważ ich można wywnioskować na podstawie konwencji nazewnictwa dla grup w IDE, w następujący sposób: IDG_VS_*nazwy Menu*_*nazwę grupy*.

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
|||IDG_VS_WNDO_OTRWNDWS1... 6|
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
 [Identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md) [identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md) [tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
