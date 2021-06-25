---
title: Identyfikatory GUID i identyfikatory Visual Studio menu | Microsoft Docs
description: Wyświetl listę wartości identyfikatorów GUID i IDENTYFIKATORów menu i grup na pasku menu Visual Studio dostępnym w Visual Studio zintegrowanego środowiska projektowego (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898074"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identyfikatory GUID i identyfikatory Visual Studio menu
W tym artykule wyliczymy wartości identyfikatorów GUID i ID menu i grup na Visual Studio pasku menu. Te wartości są definiowane *w plikach vsct,* które są instalowane w ramach zestawu VISUAL STUDIO SDK. Aby uzyskać więcej informacji, zobacz [Polecenia, menu i](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)grupy zdefiniowane w idee .

 Aby uzyskać więcej informacji na temat pracy z obiektami zintegrowanego środowiska projektowego (IDE) zdefiniowanymi w plikach *vsct,* zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Menu i grupy na pasku Visual Studio używają identyfikatora GUID `guidSHLMainMenu` . Sam pasek menu ma identyfikator `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Grupy na pasku Visual Studio menu
 Aby dodać menu do paska menu, ustaw jedną z tych grup jako jej element nadrzędny.

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Plik/Edycja/Widok|IDG_VS_MM_FILEEDITVIEW|
|Refaktoryzacja|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Kompilacja|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Narzędzia|IDG_VS_MM_TOOLSADDINS|
|Okno/Pomoc/Społeczność|IDG_VS_MM_WINDOWHELP|
|Dodatki|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu na pasku Visual Studio menu
 Aby dodać grupę do istniejącego Visual Studio menu, ustaw jedno z następujących menu jako nadrzędne. Podmenu nie ma na tej liście.

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

## <a name="groups-on-visual-studio-menus"></a>Grupy w Visual Studio menu
 Poniższe listy pokazują grupy, które maleją bezpośrednio z menu na pasku Visual Studio menu. Najszybszym sposobem dodania polecenia do menu Visual Studio jest ustawienie jednej z tych grup jako nadrzędnej. Grupy, które pochodzą z podmenu, nie są wyświetlane w tej sekcji.

### <a name="file-menu-groups"></a>Grupy menu Plik

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Nowe/otwarte|IDG_VS_FILE_FILE|
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

### <a name="edit-menu-groups"></a>Edytowanie grup menu

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Cofanie/ponowne cofanie|IDG_VS_EDIT_UNDOREDO|
|Wycinanie/kopiowanie/wklejanie|IDG_VS_EDIT_CUTCOPY|
|Wybierz pozycję|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Znajdowanie|IDG_VS_EDIT_FIND|
|Obiekty|IDG_VS_EDIT_OBJECTS|
|Czasowniki OLE|IDG_VS_EDIT_OLEVERBS|
|Command Well|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Grupy menu Refaktoryzacja

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Wspólne|IDG_REFACTORING_COMMON|
|Zaawansowany|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Wyświetlanie grup menu

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Kod formularza|IDG_VS_VIEW_FORMCODE|
|Przeglądarka|IDG_VS_VIEW_BROWSER|
|Definiowanie widoków|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architekt systemu Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Okna organizacji|IDG_VS_VIEW_ORG_WINDOWS|
|Przeglądarka kodu|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Paski narzędzi|IDG_VS_VIEW_TOOLBARS|
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Nawigacja|IDG_VS_VIEW_NAVIGATE|
|Mały nawigowanie|IDG_VS_VIEW_SMALLNAVIGATE|
|Przeglądarka obiektów|IDG_VS_VIEW_OBJBRWSR|
|Command Well|IDG_VS_VIEW_COMMANDWELL|
|Strony właściwości|IDG_VS_VIEW_PROPPAGES|
|Odśwież|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Grupy menu projektu

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Dodawanie różne|IDG_VS_PROJ_MISCADD|
|Dodaj|IDG_VS_PROJ_ADD|
|Folder|IDG_VS_PROJ_FOLDER|
|Zwolnij/załaduj ponownie|IDG_VS_PROJ_UNLOADRELOAD|
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

### <a name="tools-menu-groups"></a>Grupy menu narzędzi

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
|Dokowanie/zamykanie|IDG_VS_DOCKCLOSE|
|Dokowanie/ukrywanie|IDG_VS_DOCKHIDE|
|Rozmieszczanie|IDG_VS_WINDOW_ARRANGE|
|Nawigacja|IDG_VS_WINDOW_NAVIGATION|
|Lista|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Grupy menu Pomoc

|Group (Grupa)|ID (Identyfikator)|
|-----------|--------|
|Samples|IDG_VS_HELP_SAMPLES|
|Pomoc techniczna|IDG_VS_HELP_SUPPORT|
|Informacje|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Podmenu Visual Studio menu
 W poniższej hierarchii przedstawiono podmenu skojarzone z menu na Visual Studio menu. Ponieważ tylko grupa może mieć menu jako element nadrzędny, każdy podmenu musi pochodzić z grupy w menu, a nie bezpośrednio z menu. Aby uzyskać więcej informacji na temat relacji między menu, grupami i podmenu, zobacz [Dodawanie podmenu do menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Nazwy menu na pasku menu programu Visual Studio nie są wyświetlane oddzielnie w tej hierarchii, ponieważ można je wywnioskować na podstawie konwencji nazewnictwa dla grup w idee w następujący sposób: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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
- [Identyfikatory GUID i identyfikatory Visual Studio paskach narzędzi](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Identyfikatory GUID i identyfikatory Visual Studio poleceń](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio plików tabeli poleceń (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
