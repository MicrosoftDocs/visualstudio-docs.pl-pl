---
title: Współdzielone kolory | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302407"
---
# <a name="shared-colors"></a>Kolory udostępnione
Tutaj wstaw wprowadzenie.  
  
## <a name="shared-colors"></a>Kolory udostępnione  
 Podczas projektowania interfejsu użytkownika, który używa wspólnych elementów powłoki programu Visual Studio lub chcesz, aby element interfejsu był zgodny z podobnymi funkcjami, użyj istniejących nazw tokenów w plikach definicji pakietu, aby wybrać i przypisać kolory. Gwarantuje to, że interfejs użytkownika pozostaje zgodny z ogólnym środowisku programu Visual Studio i że aktualizuje się automatycznie po dodaniu lub zaktualizowaniu motywów.  
  
 W tym artykule opisano typowe elementy interfejsu użytkownika i nazwy tokenów, których używają, do których można się odwoływać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje dotyczące uzyskiwania dostępu do tych tokenów kolorów, zobacz [Usługa VSColor](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Upewnij się, że nazwy tokenów są używane poprawnie:  
  
- **Użyj nazw tokenów opartych na funkcji, a nie na samym kolorze.** Typowe kolory udostępnione są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko do użycia dla tych samych lub podobnych funkcji. Na przykład nie należy ponownie używać koloru wciśniętym polu kombi dla animacji postępu wirowania tylko dlatego, że podoba Ci się kolor. Funkcje pola kombi i animacji są różne, a jeśli kolor skojarzony z polem kombi ulegnie zmianie, może nie być już odpowiedni kolor dla elementu animacji. Konsekwentne korzystanie z kolorów pomaga zorientować użytkowników i zapobiec pomyłce.  
  
- **Użyj kolorów tła i tekstu w odpowiedniej kombinacji.** Kolory tła, które mają być używane z tekstem, będą miały skojarzony kolor tekstu. Nie używaj kolorów tekstowych innych niż określone dla tego tła. Jeśli nie ma skojarzonego koloru tekstu, nie należy używać tego koloru tła dla dowolnej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą powodować nieczytelny interfejs.  
  
- **Użyj kolorów formantów, które są odpowiednie dla ich lokalizacji.** W niektórych stanach niektóre formanty programu Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego zbierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów, które są odpowiednie dla lokalizacji, w której umieszczasz formant.  
  
> [!IMPORTANT]
> Nie używaj tokenów znalezionych w kategoriach "Strona startowa" lub "Cydr"!  
  
### <a name="command-structures"></a>Struktury poleceń  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menu  
 Menu może występować w kilku miejscach w programie Visual Studio 2013: pasek menu głównego, osadzone w oknach dokumentu lub narzędzia lub po kliknięciu prawym przyciskiem myszy w różnych lokalizacjach w całej IDE. Implementacje menu skojarzone z innymi elementami interfejsu użytkownika są omówione w sekcji dla odpowiedniego elementu. Należy zawsze używać implementacji menu standardowego dostarczonych przez środowisko programu Visual Studio. Jednak w niektórych rzadkich przypadkach może nie mieć dostępu do standardowych menu programu Visual Studio. W takich sytuacjach należy użyć następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w programie Visual Studio.  
  
 ![Menu redline](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Używać...  
- gdy trzeba utworzyć menu niestandardowe.  
  
- gdy masz nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.  
  
Nie używaj ...  
sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu, jak określono.  
  
##### <a name="menu-title"></a>Tytuł menu  
 Tytuły menu składają się z tła, obramowania i tekstu tytułowego, a także opcjonalnego glifu, zwykle gdy menu znajduje się na pasku poleceń.  
  
 ![Czerwony pasek tytułu menu](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Używać...  
przy każdym tworzeniu niestandardowego tytułu menu.  
  
Nie używaj...  
- na wszystko, czego nie chcesz zawsze pasować do tytułu menu.  
  
- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Tło|Brak|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z domyślnym glifem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (Glif)|`Environment.CommandBarMenuGlyph`|  
|![Tytuł menu z domyślnym glifem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifem**|Obramowanie|Brak|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Tytuł menu po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Tytuł menu z glifem po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (Glif)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Tytuł menu z glifem po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifem**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty tytuł menu](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięty tytuł menu](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z wciśniętym glifem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (Glif)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Tytuł menu z wciśniętym glifem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifem**|Obramowanie|`Environment.CommandBarMenuBorder`<br /><br /> Tylko po lewej, górnej i prawej stronie.|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Tło|Brak|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (Glif)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Obramowanie|Brak|  
  
##### <a name="menu"></a>Menu  
 Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub glifu podmenu. Jego tło i kolor tekstu zmieniają się po najechaniu kursorem. Ten token kolorów jest parą tła/pierwszego planu.  
  
 ![Elementy menu redline](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Używać...  
 dla każdej listy rozwijanej uruchamianej z paska menu lub paska poleceń.  
  
Nie używaj...  
- dla każdej listy rozwijanej, która występuje w innym kontekście.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Pierwszy plan (glif podmenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Obramowanie|`Environment.CommandBarMenuBorder`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Tło kanału ikony|`Environment.CommandBarMenuIconBackground`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|Separator|`Environment.CommandBarMenuSeparator`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menu**|W tle|`Environment.DropShadowBackground`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Zaznaczone**|Sprawdź znacznik|`Environment.CommandBarCheckBox`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Zaznaczone**|Sprawdzanie tła znacznika|`Environment.CommandBarSelectedIcon`|  
|![Wybrane menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Wybrano**|Tło ikony|`Environment.CommandBarSelected`|  
|![Wybrane menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Wybrano**|Obramowanie ikony|`Environment.CommandBarSelectedBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Najechać menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Pozycja menu**|Tło|`Environment.CommandBarMenuItemMouseOver`|  
|![Najechać menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Pozycja menu**|Pierwszy plan (tekst)|`Environment.CommandBarMenuItemMouseOver`|  
|![Najechać menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Pozycja menu**|Pierwszy plan (glif podmenu)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menu poleć wskaźnik myszy](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Zaznaczone**|Sprawdź znacznik|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menu poleć wskaźnik myszy](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Zaznaczone**|Sprawdzanie tła znacznika|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Wybrano opcję Najechajnie](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Wybrano**|Tło ikony|`Environment.CommandBarHoverOverSelected`|  
|![Wybrano opcję Najechajnie](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Wybrano**|Obramowanie ikony|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Pozycja menu|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Pozycja menu|Pierwszy plan (glif podmenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menu wyłączone zaznaczone](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Zaznaczone|Sprawdź znacznik|`Environment.CommandBarCheckBoxDisabled`|  
|![Menu wyłączone zaznaczone](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Zaznaczone|Sprawdzanie tła znacznika|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Pasek poleceń  
 Pasek poleceń może pojawić się w wielu miejscach w środowisku IDE programu Visual Studio, w szczególności na półce poleceń i osadzony w oknach narzędzi lub dokumentów.  
  
 Ogólnie rzecz biorąc należy zawsze używać implementacji standardowego paska poleceń dostarczonych przez środowisko programu Visual Studio. Za pomocą standardowego mechanizmu zapewnia, że wszystkie szczegóły wizualne będą wyświetlane poprawnie i że elementy interaktywne będą zachowywać się zgodnie z innymi formantami paska poleceń programu Visual Studio. Jeśli jednak konieczne jest zbudowanie własnego paska poleceń, upewnij się, że styl poprawnie używasz następujących nazw tokenów.  
  
 ![Czerwona linia paska poleceń](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Czerwony przycisk przepełnienia](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Używać...  
 w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.  
  
Nie używaj...  
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.  
  
##### <a name="command-bar-group"></a>Grupa paska poleceń  
 Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przycisków podziału, menu rozwijanych, pól kombi lub menu. Kolory dla tych formantów są regulowane przez oddzielne nazwy tokenów i są omawiane indywidualnie w innym miejscu w tym przewodniku. Linia separatora służy do dzielenia grupy pasków poleceń na powiązane podgrupy.  
  
 ![Czerwona linia grupy paska polecenia](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Używać...  
 w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.  
  
Nie używaj...  
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.  
  
  **Domyślnie** (bez innych stanów)  
  
|Element|Nazwa tokenu: Category.color|  
|-------------|--------------------------------|  
|Tło|`Environment.CommandBarGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|Obramowanie|`Environment.CommandBarToolBarBorder`|  
|Przeciągnij uchwyt|`Environment.CommandBarDragHandle`|  
|Separator|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ikony poleceń  
 ![Czerwona linia ikony polecenia](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Czerwona linia ikony polecenia](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Używać...  
 dla wszystkich przycisków, które zostaną umieszczone na pasku poleceń.  
  
Nie używaj...  
- formanty, które mają własne nazwy tokenów.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Domyślny**|Tło|Nie dotyczy (dziedziczy z tła paska poleceń)|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Domyślny**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Domyślny**|Obramowanie|Nie dotyczy|  
|![Domyślna ikona polecenia zaznaczona](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Tło|`Environment.CommandBarSelected`|  
|![Domyślna ikona polecenia zaznaczona](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Pierwszy plan (tekst)|`Environment.CommandBarTextSelected`|  
|![Domyślna ikona polecenia zaznaczona](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Obramowanie|`Environment.CommandBarSelectedBorder`|  
  
 **Najedź kursorem i z naciskem na klawiaturę**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Najechać kursorem myszy na ikon](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard po najechaniu kursorem**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Najechać kursorem myszy na ikon](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard po najechaniu kursorem**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Najechać kursorem myszy na ikon](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standard po najechaniu kursorem**|Obramowanie|`Environment.CommandBarBorder`|  
|![Wybrano ikonę polecenia](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu kursorem myszy**|Tło|`Environment.CommandBarHoverOverSelected`|  
|![Wybrano ikonę polecenia](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu kursorem myszy**|Pierwszy plan (tekst)|`Environment.CommandBarTextHoverOverSelected`|  
|![Wybrano ikonę polecenia](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu kursorem myszy**|Obramowanie|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona wciśnięty polecenia**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięty ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona wciśnięty polecenia**|Pierwszy plan (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Wciśnięty ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona wciśnięty polecenia**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona polecenia Wyłączone**|Tło|Nie dotyczy (dziedziczy z tła paska poleceń)|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona polecenia Wyłączone**|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona polecenia Wyłączone**|Obramowanie|Nie dotyczy|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Pudełko kombi  
  
> [!IMPORTANT]
> Pola kombi są podobne do rozwijanych, ale zawierają edytowalny region tekstu. Jeśli twoja rozwijana pozycja nie zawiera edytowalnyego regionu tekstowego, użyj tokenów kolorów znalezionych w obszarze [Rozwijane](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Czerwona linia pola kombi](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Używać...  
- podczas tworzenia niestandardowych skrzynek kombi.  

- podczas tworzenia formantu paska poleceń, który jest podobny do pola kombi.  

Nie używaj ...  
- dla wszystkiego, czego nie chcesz zawsze pasować do interfejsu użytkownika paska poleceń.  

- gdy masz dostęp do stylizowanego pola kombi.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxBackground`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxText`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxBorder`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Separator|Brak separatora|  
|![Przycisk upuszczania pola kombi&#45;w dół](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|Nie dotyczy (dziedziczy)|  
|![Przycisk upuszczania pola kombi&#45;w dół](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.ComboBoxGlyph`|  
|![Pole kombi&#47;lista&#45;w dół](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Tło|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pole kombi&#47;lista&#45;w dół](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemText`|  
|![Pole kombi&#47;lista&#45;w dół](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Obramowanie|`Environment.ComboBoxPopupBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pole wejściowe pola kombi po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxMouseOverText`|  
|![Pole wejściowe pola kombi po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxMouseOverBorder`|  
|![Pole wejściowe pola kombi po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxMouseOverSeparator`|  
|![Pole kombi&#47;przycisk upuszczania&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Pole kombi&#47;przycisk upuszczania&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.ComboBoxMouseOverGlyph`|  
|![Pole kombi&#47;lista&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Tło (pozycja menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Pole kombi&#47;lista&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Pole kombi&#47;lista&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Obramowanie (pozycja menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi koncentruje](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxFocusedBackground`|  
|![Pole wejściowe pola kombi koncentruje](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxFocusedText`|  
|![Pole wejściowe pola kombi koncentruje](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxFocusedBorder`|  
|![Pole wejściowe pola kombi koncentruje](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Pole kombi&#47;przycisk upuszczania&#45;w dół](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxFocusedButtonBackground`|  
|![Pole kombi&#47;przycisk upuszczania&#45;w dół](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Wciśnięte pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxMouseDownBackground`|  
|![Wciśnięte pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxMouseDownText`|  
|![Wciśnięte pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxMouseDownBorder`|  
|![Wciśnięte pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxMouseDownSeparator`|  
|![Pole kombi&#47;wciśnięty przycisk upuszczania&#45;w dół](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Pole kombi&#47;wciśnięty przycisk upuszczania&#45;w dół](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxDisabledBackground`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxDisabledText`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxDisabledBorder`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Separator|Brak separatora|  
|![Pole kombi&#47;przycisk upuszczenia&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Pole kombi&#47;przycisk upuszczenia&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Z listy rozwijanej  
  
> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale brakuje edytowalnych regionów tekstowych. Jeśli twoja rozwijana liczba zawiera edytowalny region tekstowy, użyj tokenów kolorów znalezionych w [polu Kombi](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Upuść&#45;w dół czerwonej linii](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Używać...  
 podczas tworzenia niestandardowych formantów listy rozwijanej.  
  
Nie używaj ...  
- dla wszystkiego, co nie jest podobne do listy rozwijanej.  

- dla skrzynek kombi lub przycisków dzielonych.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownBackground`|  
|![Pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`DropDownText`|  
|![Pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Obramowanie|`DropDownBorder`|  
|![Pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Separator|Brak separatora|  
|![Przycisk upuść&#45;w dół](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Przycisk upuść&#45;w dół](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.DropDownGlyph`|  
|![Lista&#45;w dół](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista rozwijana**|Tło|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Lista&#45;w dół](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemText`|  
|![Lista&#45;w dół](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista rozwijana**|Obramowanie|`Environment.DropDownPopupBorder`|  
|![Lista&#45;w dół](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Lista rozwijana**|W tle|`Environment.DropShadowBackground`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść pole wyboru&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Upuść pole wyboru&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`Environment.DropDownMouseOverText`|  
|![Upuść pole wyboru&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseOverBorder`|  
|![Upuść pole wyboru&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseOverSeparator`|  
|![Przycisk upuść&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseOverBackground`|  
|![Przycisk upuść&#45;w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.DropDownMouseOverGlyph`|  
|![Lista&#45;upuszczania w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista rozwijana**|Tło (pozycja menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Lista&#45;upuszczania w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Lista&#45;upuszczania w dół po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Lista rozwijana**|Obramowanie (pozycja menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięte pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseDownBackground`|  
|![Wciśnięte pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`Environment.DropDownMouseDownText`|  
|![Wciśnięte pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseDownBorder`|  
|![Wciśnięte pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseDownSeparator`|  
|![Przycisk upuszczenia&#45;w dół](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseDownBackground`|  
|![Przycisk upuszczenia&#45;w dół](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`Environment.DropDownMouseDownGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Tło|`Environment.DropDownDisabledBackground`|  
|![Pole wyboru&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Pierwszy plan (tekst)|`Environment.DropDownDisabledText`|  
|![Pole wyboru&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Obramowanie|`Environment.DropDownDisabledBorder`|  
|![Pole wyboru&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Separator|Brak separatora|  
|![Przycisk upuszczenia&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Tło|Nie dotyczy|  
|![Przycisk upuszczenia&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Pierwszy plan (Glif)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Przycisk Podziału  
 Przyciski podziału współużytkują wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne działania i nazwy tokenów przycisku rozwijane są powtarzane tutaj dla wygody. Listy rozwijane przycisków podziału są implementacjami paska poleceń [Menu](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Czerwony przycisk Podziału](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Używać...  
 podczas tworzenia niestandardowego przycisku podziału.  
  
Nie używaj ...  
- dla innych rodzajów przycisków.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk Podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Przycisk Podziału (domyślnie)**|Tło|Brak|  
|![Przycisk Podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Przycisk Podziału (domyślnie)**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Przycisk Podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Przycisk Podziału (domyślnie)**|Pierwszy plan (Glif)|`Environment.CommandBarSplitButtonGlyph`|  
|![Przycisk Podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Przycisk Podziału (domyślnie)**|Obramowanie|Nie dotyczy|  
|![Przycisk Podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Przycisk Podziału (domyślnie)**|Separator|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk Podziału po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Przycisk Podziału (po najechaniu kursorem)**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Przycisk Podziału po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Przycisk Podziału (po najechaniu kursorem)**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Przycisk Podziału po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Przycisk Podziału (po najechaniu kursorem)**|Pierwszy plan (Glif)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Przycisk Podziału po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Przycisk Podziału (po najechaniu kursorem)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Przycisk Podziału po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Przycisk Podziału (po najechaniu kursorem)**|Separator|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty przycisk Podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Przycisk Podziału (wciśnięty)**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięty przycisk Podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Przycisk Podziału (wciśnięty)**|Pierwszy plan (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Wciśnięty przycisk Podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Przycisk Podziału (wciśnięty)**|Pierwszy plan (Glif)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Wciśnięty przycisk Podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Przycisk Podziału (wciśnięty)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Wciśnięty przycisk Podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Przycisk Podziału (wciśnięty)**|Separator|Nie dotyczy|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk Podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Przycisk Podziału (wyłączony)**|Tło|Nie dotyczy|  
|![Przycisk Podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Przycisk Podziału (wyłączony)**|Pierwszy plan (tekst)|`Environment.ComboBoxItemTextInactive`|  
|![Przycisk Podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Przycisk Podziału (wyłączony)**|Pierwszy plan (Glif)|`Environment.CommandBarTextInactive`|  
|![Przycisk Podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Przycisk Podziału (wyłączony)**|Obramowanie|Nie dotyczy|  
|![Przycisk Podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Przycisk Podziału (wyłączony)**|Separator|Nie dotyczy|  
  
##### <a name="more-options-and-overflow-buttons"></a>Przyciski "Więcej opcji" i "Przepełnienie"  
 Przycisk "Więcej opcji" jest używany, gdy grupa paska poleceń można dostosować, dodając lub usuwając powiązane przyciski paska poleceń. Przycisk "Przepełnienie" pojawia się, gdy pasek poleceń jest obcinany z powodu braku miejsca w poziomie, a po kliknięciu pokazuje menu zawierające przyciski paska poleceń, które nie mogą być wyświetlane. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.  
  
 ![Więcej opcji redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Używać...  
 dla niestandardowych przycisków "Więcej opcji" lub "Przepełnienie".  
  
 Nie używaj ...  
 dla przycisków, które nie mają podobnych funkcji do przycisku "Więcej opcji" lub "Przepełnienie".  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Więcej opcji**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsGlyph`|  
|![Przycisk Przepełnienie](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Przepełnienie**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Przycisk Przepełnienie](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Przepełnienie**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Więcej opcji po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Przepełnienie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Przepełnienie**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Przepełnienie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Przepełnienie**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Więcej wciśniętych opcji](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Więcej wciśniętych opcji](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Przepełnienie wciśnięte](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Przepełnienie**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Przepełnienie wciśnięte](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Przepełnienie**|Pierwszy plan (Glif)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Okna dokumentów  
 Nie ma potrzeby replikowania okien dokumentów, ponieważ są one dostarczane przez środowisko programu Visual Studio. Jednak można zdecydować, że chcesz wykorzystać kolory używane w oknach dokumentów, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.  
  
 Podczas korzystania z tokenów kolorów okna dokumentu, należy uważać, aby używać ich tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, będziesz mieć nieoczekiwane wyniki w interfejsie użytkownika.  
  
#### <a name="document-window-frame"></a>Ramka okna dokumentu  
 Okna dokumentu mogą być zadokowane w IDE lub pływające jako oddzielne okno. Gdy okno dokumentu jest przestawne poza IDE, nadal znajduje się w dokumencie dobrze i ma tła, obramowania, tekstu i kolorów kart, które są takie same, jak wtedy, gdy jest częścią IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne kolory tła, obramowania i tekstu. Gdy okna narzędzi są dobrze zadokowane w dokumencie, dziedziczą zachowanie i kolor ich kart z nazw tokenów okna dokumentu.  
  
 ![Zadokowany czerwony kolor okna dokumentu](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Zadokowane okno dokumentu**  
  
 ![Przestawna czerwona linia okna dokumentu](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Okno dokumentu przestawnego**  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w tym interfejsu użytkownika, który ma być zgodny z oknem dokumentu.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być automatycznie zmieniany, jeśli powłoka ma aktualizację motywu.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Dokument: zadokowany lub przestawny|Tło|Zależy od typu dokumentu|  
|Dokument: zadokowany lub przestawny|Pierwszy plan (tekst)|Zależy od typu dokumentu|  
|Dokument: zadokowany lub przestawny|Obramowanie|`Environment.ToolWindowBorder`|  
|![Skoncentrowana ramka](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rama: pływająca, skupiona**|Tło|`Environment.ToolWindowFloatingFrame`|  
|![Skoncentrowana ramka](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rama: pływająca, skupiona**|Pierwszy plan (tekst)|`Environment.ToolWindowFloatingFrame`|  
|![Skoncentrowana ramka](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rama: pływająca, skupiona**|Pierwszy plan (Glif)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Skoncentrowana ramka](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rama: pływająca, skupiona**|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
|![Skoncentrowana ramka](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rama: pływająca, skupiona**|Obramowanie (Glif)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Ustawiona na przezroczysta|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Tło|`Environment.ToolWindowFloatingFrameInactive`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Pierwszy plan (tekst)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Pierwszy plan (Glif)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Obramowanie|`Environment.MainWindowInactiveBorder`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Obramowanie (Glif)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Ustawiona na przezroczysta|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ramka skupiona na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rama: pływająca, skupiona**|Tło (Glif)|`Environment.RaftedWindowButtonHoverActive`|  
|![Ramka skupiona na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rama: pływająca, skupiona**|Pierwszy plan (Glif)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Ramka skupiona na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rama: pływająca, skupiona**|Obramowanie (Glif)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Ramka nieskoncentrowana po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Tło (Glif)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Ramka nieskoncentrowana po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Pierwszy plan (Glif)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Ramka nieskoncentrowana po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rama: pływająca, nieskoncentrowana**|Obramowanie (Glif)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty klawisz frame](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rama: pływająca, skupiona**|Tło (Glif)|`Environment.RaftedWindowButtonDown`|  
|![Wciśnięty klawisz frame](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rama: pływająca, skupiona**|Pierwszy plan (Glif)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Wciśnięty klawisz frame](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rama: pływająca, skupiona**|Obramowanie (Glif)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Karty dokumentów  
 Karty dokumentów znajdują się w kanale kart, aby wskazać, które dokumenty są aktualnie otwarte, wraz z tym, który z nich jest bieżącym wybranym lub aktywnym dokumentem. Okna narzędzi można również zadokować w kanale karty dokumentu, jeśli użytkownik je tam umieszcza. W tej sytuacji używają tych samych kolorów kart, co okna dokumentu. Jeśli tworzysz interfejs użytkownika, który ma być zawsze zgodny z kolorami okna dokumentu (w tym aktualizacjami motywu lub jeśli są zainstalowane nowe motywy), odwoł się do tych tokenów kolorów.  
  
 ![Czerwony zakładka Dokument](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Używać...  
 w dowolnym miejscu tworzenia interfejsu użytkownika, który ma być zgodny z kartami dokumentów i automatycznie odbiera aktualizacje motywów lub nowe kolory motywu.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, gdy powłoka ma aktualizację motywu.  
  
##### <a name="open-document-tabs"></a>Otwieranie kart dokumentów  
 Każdy otwarty dokument ma kartę w kanale kart dokumentu, na których wyświetlana jest jego nazwa. Dokumenty można wybierać lub otwierać w tle, a ich karty odzwierciedlają następujące stany:  
  
- Wybrana karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie. Wybrana karta ma obramowanie dokumentu, które dobrze rozciąga się na górną krawędź dokumentu.  
  
- Karty tła to wszystkie karty dokumentów, które nie są aktualnie zaznaczoną kartą. Po kliknięciu stają się one wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.  
  
  ![Otwórz czerwoną linię karty dokumentu](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Używać...  
  podczas tworzenia niestandardowych kart dokumentów.  
  
  Nie używaj ...  
  - dla tymczasowych (podgląd) kart.  
  
- dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
##### <a name="selected-tab"></a>Karta Zaznaczone  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaznaczone fokus karty](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Karta Wybrany dokument, fokus**|Tło|`Environment.FileTabSelectedGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Zaznaczone fokus karty](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Karta Wybrany dokument, fokus**|Pierwszy plan (tekst)|`Environment.FileTabSelectedText`|  
|![Zaznaczone fokus karty](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Karta Wybrany dokument, fokus**|Obramowanie|`Environment.FileTabSelectedBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
|![Zaznaczone fokus karty](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Karta Wybrany dokument, fokus**|Obramowanie dokumentu|`Environment.FileTabDocumentBorderBackground`|  
  
 **Unfocused**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaznaczona karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Karta Zaznaczony dokument, nieskoncentrowana**|Tło|`Environment.FileTabInactiveGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Zaznaczona karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Karta Zaznaczony dokument, nieskoncentrowana**|Pierwszy plan (tekst)|`Environment.FileTabInactiveText`|  
|![Zaznaczona karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Karta Zaznaczony dokument, nieskoncentrowana**|Obramowanie|`Environment.FileTabInactiveBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
|![Zaznaczona karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Karta Zaznaczony dokument, nieskoncentrowana**|Obramowanie dokumentu|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Karta Tło  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta Tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Domyślna karta Tło**|Tło|`Environment.FileTabBackground`|  
|![Karta Tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Domyślna karta Tło**|Pierwszy plan (tekst)|`Environment.FileTabText`|  
|![Karta Tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Domyślna karta Tło**|Obramowanie|`Environment.FileTabBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta Tło po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Tło po najechaniu kursorem myszy**|Tło|`Environment.FileTabHotGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Karta Tło po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Tło po najechaniu kursorem myszy**|Pierwszy plan (tekst)|`Environment.FileTabHotText`|  
|![Karta Tło po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Tło po najechaniu kursorem myszy**|Obramowanie|`Environment.FileTabHotBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
##### <a name="preview-tab"></a>Karta Podgląd  
 Karta podglądu pojawi się po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksploratora rozwiązań. Działa jako podgląd dokumentu, a także daje użytkownikowi możliwość utrzymania dokumentu otwartego po lewej stronie kanału karty dokumentu. W ciągu jednego czasu można otworzyć tylko jedną kartę podglądu. Karty podglądu mają zarówno tło, jak i wybrane stany, takie jak otwarte karty, i mogą być skoncentrowane lub nieskoncentrowane w ich aktywnym stanie.  
  
 ![Czerwony kolor karty Podgląd](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Używać...  
 gdziekolwiek tworzysz tymczasowy podgląd i chcesz, aby jakiś element pasował do bieżącego koloru karty podglądu.  
  
Nie używaj ...  
- dla każdego rodzaju dokumentu lub karty, która nie jest tymczasowa (podgląd).  

- dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
  **Wybrana karta podglądu: skupiona**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus karty Podgląd](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Podgląd z punktem skupienia**|Tło|`Environment.FileTabProvisionalSelectedActive`|  
|![Fokus karty Podgląd](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Podgląd z punktem skupienia**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Fokus karty Podgląd](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Podgląd z punktem skupienia**|Obramowanie|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
|![Fokus karty Podgląd](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Podgląd z punktem skupienia**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Wybrana karta podglądu: Nieskoncentrowana**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Podgląd nieskoncentrowana](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Podgląd nieskoncentrowany**|Tło|`Environment.FileTabProvisionalSelectedInactive`|  
|![Karta Podgląd nieskoncentrowana](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Podgląd nieskoncentrowany**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Karta Podgląd nieskoncentrowana](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Podgląd nieskoncentrowany**|Obramowanie|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Karta Podgląd nieskoncentrowana](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Podgląd nieskoncentrowany**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Karta Podgląd tła: Domyślna**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Podgląd tła](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Tła karty Podgląd**|Tło|`Environment.FileTabProvisionalInactive`|  
|![Karta Podgląd tła](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Tła karty Podgląd**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Karta Podgląd tła](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Tła karty Podgląd**|Obramowanie|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
 **Karta Podgląd tła: Kursoruj kursorem**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Podgląd tła po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty Podgląd po najechaniu kursorem myszy**|Tło|`Environment.FileTabProvisionalHover`|  
|![Karta Podgląd tła po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty Podgląd po najechaniu kursorem myszy**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalHoverForeground`|  
|![Karta Podgląd tła po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty Podgląd po najechaniu kursorem myszy**|Obramowanie|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
##### <a name="document-overflow-button"></a>Przycisk Przepełnienie dokumentu  
 Przycisk przepełnienia dokumentu jest obecny, jeśli jest otwarty jeden lub więcej dokumentów, niezależnie od tego, czy w bieżącej konfiguracji jest miejsce w pionie, aby zmieścić wszystkie karty dokumentu. Menu rozwijane przepełnienie dokumentu, które jest kontrolowane przez kolory **CommandBarMenu** (patrz [Menu),](../misc/shared-colors.md#BKMK_CommandMenus)wyświetla listę wszystkich otwartych dokumentów, zarówno widocznych, jak i ukrytych, a glif przepełnienia zmienia się w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale kart.  
  
 ![Przepełnienie czerwonej linii](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Używać...  
podczas tworzenia niestandardowego przycisku przepełnienia dokumentu.  

Nie używaj ...  
- dla interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia.  

- dla przycisków przepełnienia paska poleceń.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przepełnienie](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Przycisk Przepełnienie dokumentu**|Tło|`Environment.DocWellOverflowButtonBackground`|  
|![Przepełnienie](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Przycisk Przepełnienie dokumentu**|Pierwszy plan (Glif)|`Environment.DocWellOverflowButtonGlyph`|  
|![Przepełnienie](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Przycisk Przepełnienie dokumentu**|Obramowanie|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przepełnienie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Przycisk Przepełnienie dokumentu po najechaniu kursorem myszy**|Tło|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Przepełnienie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Przycisk Przepełnienie dokumentu po najechaniu kursorem myszy**|Pierwszy plan (Glif)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Przepełnienie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Przycisk Przepełnienie dokumentu po najechaniu kursorem myszy**|Obramowanie|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przepełnienie wciśnięte](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Wciśnięty przycisk przepełnienia dokumentu**|Tło|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Przepełnienie wciśnięte](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Wciśnięty przycisk przepełnienia dokumentu**|Pierwszy plan (Glif)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Przepełnienie wciśnięte](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Wciśnięty przycisk przepełnienia dokumentu**|Obramowanie|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Okna narzędzi  
 Nie ma potrzeby replikowania okien narzędzi, ponieważ są one dostarczane przez środowisko programu Visual Studio. Jednak można zdecydować, że chcesz wykorzystać kolory używane w oknach narzędzi, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.  
  
 ![Czerwona linia okna narzędzia](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w tym interfejsu użytkownika, który ma być zgodny z oknami narzędzi.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
#### <a name="tool-window-frame"></a>Ramka okna narzędzia  
 Okna narzędzi w programie Visual Studio są używane dla wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzia jest otwarte, można je przypisać do dowolnej z czterech stron obszaru dokumentu. Okna narzędzi można również unosić się poza IDE, co pozwala na ich zmianę położenia w dowolnym miejscu na ekranie użytkownika. Okna przestawne zawsze znajdują się na szczycie IDE. Na koniec okna narzędzi mogą być zadokowane jako okna dokumentów i dobrze wyświetlane jako karta w dokumencie. Okna narzędzi, które zostały zadokowane jako okna dokumentów, są częściowo barwione przy użyciu nazw tokenów okna dokumentu.  
  
 ![Ramka okna narzędzia czerwona linia](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w tym interfejsu użytkownika, który ma być zgodny z oknami narzędzi.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Zadokowany**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Okno narzędzia zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Tło|`Environment.ToolWindowBackground`|  
|![Okno narzędzia zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Obramowanie|`Environment.ToolWindowBorder`|  
  
 **Pływające: koncentruje się**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Skupione okno narzędzia](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Tło|`Environment.ToolWindowBackground`|  
|![Skupione okno narzędzia](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Pływające: nieskoncentrowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Okno narzędzia nieskoncentrowane](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Tło|`Environment.ToolWindowBackground`|  
|![Okno narzędzia nieskoncentrowane](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Obramowanie|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzia  
 Obramowanie paska tytułu nie jest prawdziwym obramowaniem, ale grubą linią w górnej części paska tytułu. Nie ma nazwy tokenu dla jego stan nieskoncentrowany.  
  
 ![Czerwony pasek tytułu okna narzędzia](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w tym interfejsu użytkownika, który ma być zgodny z oknami narzędzi.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pasek tytułu skupiony](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Ostry pasek tytułu**|Tło|`Environment.TitleBarActiveGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pasek tytułu skupiony](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Ostry pasek tytułu**|Pierwszy plan (tekst)|`Environment.TitleBarActiveText`|  
|![Pasek tytułu skupiony](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Ostry pasek tytułu**|Obramowanie|`Environment.TitleBarActiveBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
|![Pasek tytułu skupiony](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Ostry pasek tytułu**|Przeciągnij uchwyt|`Environment.TitleBarDragHandleActive`|  
  
 **Unfocused**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pasek tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Tło|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pasek tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Pierwszy plan (tekst)|`Environment.TitleBarInactiveText`|  
|![Pasek tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Obramowanie|Nie dotyczy|  
|![Pasek tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Przeciągnij uchwyt|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Przyciski paska tytułu  
 ![Czerwony pasek tytułu](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Używać...  
 dla przycisków, które pojawiają się w interfejsie użytkownika, który używa tokenów kolorów z pasków tytułów okna narzędzia.  
  
Nie używaj ...  
- dla przycisków wyświetlanych w innych lokalizacjach.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu koncentruje się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Tło|Nie dotyczy|  
|![Przycisk paska tytułu koncentruje się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Przycisk paska tytułu koncentruje się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Obramowanie|Nie dotyczy|  
|![Przycisk paska tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Unfocused**|Tło|Nie dotyczy|  
|![Przycisk paska tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Unfocused**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Przycisk paska tytułu nieskoncentrowany](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Unfocused**|Obramowanie|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu na skupić się na najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Tło|`Environment.ToolWindowButtonHoverActive`|  
|![Przycisk paska tytułu na skupić się na najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Przycisk paska tytułu na skupić się na najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Obramowanie|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Przycisk paska tytułu nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Unfocused**|Tło|`Environment.ToolWindowButtonHoverInactive`|  
|![Przycisk paska tytułu nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Unfocused**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Przycisk paska tytułu nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Unfocused**|Obramowanie|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu nakoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Tło|`Environment.ToolWindowButtonDown`|  
|![Przycisk paska tytułu nakoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Przycisk paska tytułu nakoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
|![Przycisk paska tytułu nieskoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Unfocused**|Tło|`Environment.ToolWindowButtonDown`|  
|![Przycisk paska tytułu nieskoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Unfocused**|Pierwszy plan (Glif)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Przycisk paska tytułu nieskoncentrowany i naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Unfocused**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Karty okna narzędzia  
 ![Karta okno narzędzia czerwony](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w tym interfejsu użytkownika, który ma być zgodny z oknami narzędzi.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Karta Zaznaczone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus okna narzędzia](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta Okno zaznaczone, skupione narzędzie**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Fokus okna narzędzia](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta Okno zaznaczone, skupione narzędzie**|Pierwszy plan (tekst)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Fokus okna narzędzia](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta Okno zaznaczone, skupione narzędzie**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta okna narzędzia nieskoncentrowana](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta okno narzędzia zaznaczone, nieskoncentrowane**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna narzędzia nieskoncentrowana](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta okno narzędzia zaznaczone, nieskoncentrowane**|Pierwszy plan (tekst)|`Environment.ToolWindowTabSelectedText`|  
|![Karta okna narzędzia nieskoncentrowana](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta okno narzędzia zaznaczone, nieskoncentrowane**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
 **Karta Tło**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta tło okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta Okno narzędzia Tło**|Tło|`Environment.ToolWindowTabGradientBegin`<br /><br /> Gradient zatrzymuje ustawioną na tę samą wartość koloru w programie Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Gradient zatrzymuje ustawioną na tę samą wartość koloru w programie Visual Studio 2013.|  
|![Karta tło okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta Okno narzędzia Tło**|Pierwszy plan (tekst)|`Environment.ToolWindowTabText`|  
|![Karta tło okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta Okno narzędzia Tło**|Obramowanie|`Environment.ToolWindowTabBorder`|  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta tła okna narzędzia po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okno narzędzia tło po najechaniu kursorem myszy**|Tło|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Gradient zatrzymuje ustawioną na tę samą wartość koloru w programie Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Gradient zatrzymuje ustawioną na tę samą wartość koloru w programie Visual Studio 2013.|  
|![Karta tła okna narzędzia po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okno narzędzia tło po najechaniu kursorem myszy**|Pierwszy plan (tekst)|`Environment.ToolWindowTabMouseOverText`|  
|![Karta tła okna narzędzia po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okno narzędzia tło po najechaniu kursorem myszy**|Obramowanie|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Ustaw ten sam kolor co tło.|  
  
#### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart  
 ![Automatyczna&#45;ukryć czerwoną linię](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Używać...  
 w dowolnym miejscu tworzenia interfejsu użytkownika, który ma być zgodny z automatycznie ukrytymi kartami okna narzędzia.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Automatyczna&#45;ukrywanie](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Domyślna karta automatycznego ukrywania**|Tło|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Karta Automatyczna&#45;ukrywanie](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Domyślna karta automatycznego ukrywania**|Pierwszy plan (tekst)|`Environment.AutoHideTabText`|  
|![Karta Automatyczna&#45;ukrywanie](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Domyślna karta automatycznego ukrywania**|Obramowanie|`Environment.AutoHideTabBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Automatyczne&#45;ukryj kartę po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatyczne ukrywanie karty po najechaniu kursorem myszy**|Tło|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Automatyczne&#45;ukryj kartę po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatyczne ukrywanie karty po najechaniu kursorem myszy**|Pierwszy plan (tekst)|`Environment.AutoHideTabMouseOverText`|  
|![Automatyczne&#45;ukryj kartę po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automatyczne ukrywanie karty po najechaniu kursorem myszy**|Obramowanie|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Typowe kontrolki współużytkowane  
 Korzystając ze standardowego paska poleceń programu Visual Studio w funkcji, będziesz mieć dostęp do formantów powłoki w stylu i nie należy ponownie szablon tych typowych formantów. Jednak jeśli trzeba utworzyć pasek poleceń niestandardowe, może być konieczne tworzenie formantów niestandardowych, jak również. W takim przypadku należy pamiętać, aby użyć poprawne nazwy tokenów dla każdego z następujących formantów, tak aby interfejs użytkownika jest zgodny z resztą programu Visual Studio.  
  
#### <a name="search-box"></a>Pole wyszukiwania  
 Jeśli to możliwe, należy użyć wspólnego formantu wyszukiwania dostarczonego przez środowisko programu Visual Studio. Kolory pól wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors.pkgdef,** który zawiera nazwy tokenów dla pola wejściowego, przycisku akcji, przycisku rozwijanego i menu rozwijanego.  
  
 Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wzajemnie się wykluczają:  
  
- "Koncentruje się" lub "nieskoncentrowane" odnosi się do tego, czy kursor znajduje się w polu tekstowym.  
  
- "Aktywny" lub "nieaktywny" odnosi się do tego, czy użytkownik ma wprowadzić zapytanie wyszukiwania w polu tekstowym.  
  
- "Hover" oznacza, że użytkownik ma myszy nad polem wyszukiwania za pomocą myszy (ten stan zastępuje wszystkie inne stany).  
  
- "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.  
  
  ![Czerwony kolor pola wyszukiwania](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Używać...  
  podczas projektowania niestandardowego pola wyszukiwania.  
  
  Nie używaj ...  
  - dla wszystkiego, co nie jest polem wyszukiwania.  
  
- dla wszystkiego, co nie chcesz zawsze pasować do interfejsu użytkownika pola wyszukiwania.  
  
  **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Tło|`SearchControl.FocusedBackground`|  
|![Pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.FocusedBackground`|  
|![Pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Obramowanie|`SearchControl.FocusedBorder`|  
|![Pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Separator|`SearchControl.FocusedDropDownSeparator`|  
|![Przycisk akcji wyszukiwania koncentruje](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Przycisk Akcja**|Tło|Brak|  
|![Przycisk akcji wyszukiwania koncentruje](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (glif wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Przycisk akcji wyszukiwania koncentruje](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (stop glif)|`SearchControl.StopGlyph`|  
|![Przycisk akcji wyszukiwania koncentruje](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (przezroczysty glif)|`SearchControl.ClearGlyph`|  
|![Przycisk akcji wyszukiwania koncentruje](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Przycisk Akcja**|Obramowanie|Nie dotyczy|  
|![Przycisk rozwijania wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.FocusedDropDownButton`|  
|![Przycisk rozwijania wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Przycisk rozwijania wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Unfocused**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wyszukiwanie pola wejściowego nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Tło|`SearchControl.SearchActiveBackground`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.SearchActiveBackground`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowanego i nieaktywnego](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Tło|`SearchControl.Unfocused`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowanego i nieaktywnego](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.Unfocused`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowanego i nieaktywnego](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Wyszukiwanie pola wejściowego nieskoncentrowanego i nieaktywnego](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Przycisk akcji wyszukiwania nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Przycisk Akcja**|Tło|Nie dotyczy|  
|![Przycisk akcji wyszukiwania nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (glif wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Przycisk akcji wyszukiwania nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (stop glif)|`SearchControl.StopGlyph`|  
|![Przycisk akcji wyszukiwania nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Przycisk Akcja**|Pierwszy plan (przezroczysty glif)|`SearchControl.ClearGlyph`|  
|![Przycisk akcji wyszukiwania nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Przycisk Akcja**|Obramowanie|Nie dotyczy|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.UnfocusedDropDownButton`|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk Akcja**|Tło|`SearchControl.ActionButtonMouseDown`|  
|![Wciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk Akcja**|Pierwszy plan (Glif)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Wciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk Akcja**|Obramowanie|`SearchControl.ActionButtonMouseDownBorder`|  
|![Wciśnięty przycisk upuszczenia wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.MouseDownDropDownButton`|  
|![Wciśnięty przycisk upuszczenia wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Wciśnięty przycisk upuszczenia wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Wyróżnione (tylko tekst)**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Podświetl pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Pole wprowadzania z wyróżnionym tekstem**|Tło|`SearchControl.Selection`|  
|![Podświetl pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Pole wprowadzania z wyróżnionym tekstem**|Pierwszy plan (tekst)|`SearchControl.FocusedBackground`|  
|![Podświetl pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Pole wprowadzania z wyróżnionym tekstem**|Obramowanie|Brak|  
|![Podświetl pole wprowadzania wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Pole wprowadzania z wyróżnionym tekstem**|Separator|`SearchControl.FocusedDropDownSeparator`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wprowadzania wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Tło|`SearchControl.Disabled`|  
|![Pole wprowadzania wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.Disabled`|  
|![Pole wprowadzania wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Obramowanie|`SearchControl.DisabledBorder`|  
|![Pole wprowadzania wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Przycisk akcji wyszukiwania wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Przycisk Akcja**|Tło|Brak|  
|![Przycisk akcji wyszukiwania wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Przycisk Akcja**|Pierwszy plan (Glif)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Przycisk akcji wyszukiwania wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Przycisk Akcja**|Obramowanie|Brak|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (Glif)|`SearchControl.DisabledDownButtonGlyph`|  
|![Przycisk upuszczenia wyszukiwania&#45;w dół wyłączony](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|Brak|  
  
##### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania  
 Menu rozwijane pola wyszukiwania ma potencjał, aby być nieco bardziej złożone niż inne menu rozwijane w programie Visual Studio. Sekcje "sugerowane wyszukiwania" i "opcje wyszukiwania" mogą pojawić się samodzielnie lub razem w menu, a każda z nich jest kolorowana oddzielnie. Linia oddziela również te dwie sekcje, gdy pojawiają się razem, a obramowanie otacza całe menu rozwijane.  
  
 ![Wyszukaj&#45;w dół czerwonej linii](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Używać...  
- podczas tworzenia niestandardowej listy rozwijanej wyszukiwania.  

- poprawne nazwy tokenów dla składników listy poprawne.  

Nie używaj ...  
- dla list rozwijanych, które pojawiają się w innych kontekstach.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślnie (bez innych stanów)**  
  
|Element|Nazwa tokenu: Category.color|  
|-------------|--------------------------------|  
|Obramowanie|`SearchControl.PopupBorder`|  
|Separator|`SearchControl.PopupSectionHeaderSeparator`|  
|W tle|`Environment.DropShadowBackground`|  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Pierwszy plan (tekst)|`SearchControl.PopupItemText`|  
|![Pole wyboru Wyszukaj](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pole wyboru Wyszukaj](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxText`|  
|![Pole wyboru Wyszukaj](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonText`|  
|![Pole wyboru Wyszukaj](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pole wyboru Wyszukaj](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sugerowane wyszukiwanie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Sugerowane wyszukiwanie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Pierwszy plan (tekst)|`SearchControl.PopupMouseOverItemText`|  
|![Sugerowane wyszukiwanie po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Pole wyboru Wyszukaj po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Pole wyboru Wyszukaj po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opcje wyszukiwania po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Pole wyboru Wyszukaj po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Opcje wyszukiwania po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Pole wyboru Wyszukaj po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Opcje wyszukiwania po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Sugerowane wyszukiwanie wciśnięte](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięte opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Sugerowane wyszukiwanie wciśnięte](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięte opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Sugerowane wyszukiwanie wciśnięte](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Wciśnięte opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Sugerowane wyszukiwanie wciśnięte](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Wciśnięte opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnym interfejsie użytkownika tematyce, istnieją przystanki gradientu i wartości dla tego tła.|  
|![Sugerowane wyszukiwanie wciśnięte](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Wciśnięte opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 Hiperłącze jest jednym formancie, który nie ma pary pierwszego planu/tła. We wszystkich przypadkach należy użyć koloru hiperłącza pierwszego planu, który będzie wyświetlany poprawnie na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu kolorów dla formantu hiperłącza, zobaczysz domyślny kolor systemu dla "wciśnięty", który będzie migać na czerwono. Jest to sygnał, że formant nie używa poprawnego tokenu kolor środowiska.  
  
 ![Hiperłącze czerwona](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Używać...  
 gdy trzeba utworzyć niestandardowe hiperłącze.  
  
 Nie używaj ...  
 dla wszystkiego, co nie jest hiperłączem.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Domyślne hiperłącze](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Pierwszy plan (tekst)|`Environment.PanelHyperlink`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty hiperłącze](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkPressed`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze wyłączone](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Pasek informacyjny  
 Paski informacyjne są używane w celu zapewnienia więcej informacji o danym kontekście i zawsze pojawiają się w górnej części okna dokumentu lub okna narzędzia.  
  
 ![Czerwona linia paska informacyjnego](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Używać...  
 podczas tworzenia niestandardowych pasków informacyjnych.  
  
 Nie używaj ...  
 dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego.  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Pasek informacyjny**|Tło|`Environment.InfoBackground`|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Pasek informacyjny**|Pierwszy plan (tekst)|`Environment.InfoText`|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Pasek informacyjny**|Obramowanie|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Pasek przewijania  
 Paski przewijania są stylizowane przez środowisko programu Visual Studio i nie muszą być tematyce. Jednak można zdecydować, że chcesz wykorzystać kolory używane w paski przewijania, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.  
  
 ![Czerwony pasek przewijania](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Używać...  
 podczas tworzenia interfejsu użytkownika, który chcesz dopasować paski przewijania programu Visual Studio.  
  
 Nie używaj ...  
 dla wszystkiego, czego nie chcesz zawsze pasować do interfejsu użytkownika paska przewijania.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbBackground`|  
|![Strzałka paska przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowBackground`<br /><br /> Ustaw ten sam kolor co pasek przewijania.|  
|![Strzałka paska przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Strzałka przewijania**|Pierwszy plan (Glif)|`Environment.ScrollBarArrowGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Pasek przewijania po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Strzałka paska przewijania po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Ustaw ten sam kolor co pasek przewijania.|  
|![Strzałka paska przewijania po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Strzałka przewijania**|Pierwszy plan (Glif)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięty pasek przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Wciśnięty pasek przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbPressedBackground`|  
|![Wciśnięte strzałki paska przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Ustaw ten sam kolor co pasek przewijania.|  
|![Wciśnięte strzałki paska przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Strzałka przewijania**|Pierwszy plan (Glif)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Widok drzewa  
 Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwerów i Widok klasy, implementuje hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w kategorii TreeView. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy, które mają zagnieżdżone elementy podrzędne mają również glify, które wskazują, czy element jest rozwinięty lub zwinięty.  
  
 ![Widok drzewa czerwony](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Używać...  
 w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, aby zaimplementować hierarchiczny widok organizacyjny.  
  
Nie używaj ...  
- dla wszystkiego, co nie jest podobne do widoku drzewa.  

- w dowolnej kombinacji tła/pierwszego planu innej niż określona.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Tło|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Pierwszy plan (tekst)|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Pierwszy plan (Glif)|`TreeView.Glyph`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Obramowanie|Brak|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Tło|`TreeView.Background`|  
|![Widok drzewa po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Pierwszy plan (tekst)|`TreeView.Background`|  
|![Widok drzewa po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Pierwszy plan (Glif)|`TreeView.GlyphMouseOver`|  
|![Widok drzewa po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Obramowanie|Brak|  
  
 **Przeciągnij nad**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przeciąganie widoku drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Tło|`TreeView.DragOverItem`|  
|![Przeciąganie widoku drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Pierwszy plan (tekst)|`TreeView.DragOverItem`|  
|![Przeciąganie widoku drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Pierwszy plan (Glif)|`TreeView.DragOverItemGlyph`|  
|![Przeciąganie widoku drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Obramowanie|Brak|  
  
 **Wybrano**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa skoncentrowany](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Widok drzewa skoncentrowany](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`|  
|![Widok drzewa skoncentrowany](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (Glif)|`TreeView.SelectedItemActiveGlyph`|  
|![Widok drzewa skoncentrowany](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Obramowanie|`TreeView.FocusVisualBorder`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Unfocused**|Tło|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Unfocused**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Unfocused**|Pierwszy plan (Glif)|`TreeView.SelectedItemInactiveGlyph`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Unfocused**|Obramowanie|Brak|  
  
 **Umieść wskaźnik myszy na zaznaczonym**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa skupiony na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Widok drzewa skupiony na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`|  
|![Widok drzewa skupiony na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (Glif)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Widok drzewa skupiony na najechaniu kursorem](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Obramowanie|Brak`TreeView.FocusVisualBorder`|  
|![Widok drzewa nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Unfocused**|Tło|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Unfocused**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Unfocused**|Pierwszy plan (Glif)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Widok drzewa nieskoncentrowany po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Unfocused**|Obramowanie|Brak|  
  
#### <a name="button-controls"></a>formanty przycisków  
 ![Czerwona linia sterowania przyciskami](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Używać...  
 dla przycisków w dokumencie dobrze, że chcesz zintegrować z motywami programu Visual Studio (Jasny, Ciemny, Niebieski lub system wysoki kontrast motywu).  
  
 Nie używaj ...  
 dla przycisków, które będą wyświetlane na niestandardowym tle, który nie jest częścią motywu programu Visual Studio.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Button|`CommonControls.Button`|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Obramowanie przycisków|`CommonControls.ButtonBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk wyłączony](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Button|`CommonControls.ButtonDisabled`|  
|![Przycisk wyłączony](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Obramowanie przycisków|`CommonControls.ButtonBorderDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Przycisk po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Button|`CommonControls.ButtonHover`|  
|![Przycisk po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Obramowanie przycisków|`CommonControls.ButtonBorderHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Button|`CommonControls.ButtonPressed`|  
|![Naciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Obramowanie przycisków|`CommonControls.ButtonBorderPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nacisk na przycisk](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Button|`CommonControls.ButtonFocused`|  
|![Nacisk na przycisk](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Obramowanie przycisków|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Kontrolki pola wyboru  
 ![Pole wyboru redline](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Używać...  
 dla formantów pola wyboru zawartych w dokumencie dobrze.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie jest formantem pola wyboru.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Tło|`CommonControls.CheckBoxBackground`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Obramowanie|`CommonControls.CheckBoxBorder`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Tekst|`CommonControls.CheckBoxText`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glifów|`CommonControls.CheckBoxGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Tło|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Obramowanie|`CommonControls.CheckBoxBorderDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Tekst|`CommonControls.CheckBoxTextDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glifów|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Tło|`CommonControls.CheckBoxBackgroundHover`|  
|![Pole wyboru po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Obramowanie|`CommonControls.CheckBoxBorderHover`|  
|![Pole wyboru po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Tekst|`CommonControls.CheckBoxTextHover`|  
|![Pole wyboru po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glifów|`CommonControls.CheckBoxGlyphHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięte pole wyboru](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|![Wciśnięte pole wyboru](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Obramowanie|`CommonControls.CheckBoxBorderPressed`|  
|![Wciśnięte pole wyboru](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Tekst|`CommonControls.CheckBoxTextPressed`|  
|![Wciśnięte pole wyboru](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glifów|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru z fokusem](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Tło|`CommonControls.CheckBoxBackgroundFocused`|  
|![Pole wyboru z fokusem](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Obramowanie|`CommonControls.CheckBoxBorderFocused`|  
|![Pole wyboru z fokusem](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Tekst|`CommonControls.CheckBoxTextFocused`|  
|![Pole wyboru z fokusem](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glifów|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Kontrolki skrzynki/pola kombi  
 ![Upuść&#45;w dół&#47;pole kombi redline](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Używać...  
dla rozwijanych i pól kombi, które są częścią dokumentu dobrze.  

Nie używaj ...  
- dla dowolnego interfejsu użytkownika, który nie jest polem rozwijanym ani kombi.  

- dla pola [rozwijanego](../misc/shared-colors.md#BKMK_CommandDropDown) lub [kombi](../misc/shared-colors.md#BKMK_CommandComboBox) na pasku poleceń.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Tło|`CommonControls.ComboBoxBackground`|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Obramowanie|`CommonControls.ComboBoxBorder`|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Tekst|`CommonControls.ComboBoxText`|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Separator|`CommonControls.ComboBoxSeparator`|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glifów|`CommonControls.ComboBoxGlyph`|  
|![Upuść&#45;w dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Tło glifów|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Tło|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Obramowanie|`CommonControls.ComboBoxBorderDisabled`|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Tekst|`CommonControls.ComboBoxTextDisabled`|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Separator|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glifów|`CommonControls.ComboBoxGlyphDisabled`|  
|![Upuść&#45;w dół&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Tło|`CommonControls.ComboBoxBackgroundHover`|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Obramowanie|`CommonControls.ComboBoxBorderHover`|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Tekst|`CommonControls.ComboBoxTextHover`|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Separator|`CommonControls.ComboBoxSeparatorHover`|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glifów|`CommonControls.ComboBoxGlyphHover`|  
|![Upuść&#45;w dół&#47;pole kombi po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Tło|`CommonControls.ComboBoxBackgroundPressed`|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Obramowanie|`CommonControls.ComboBoxBorderPressed`|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Tekst|`CommonControls.ComboBoxTextPressed`|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Separator|`CommonControls.ComboBoxSeparatorPressed`|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glifów|`CommonControls.ComboBoxGlyphPressed`|  
|![Upuść&#45;w dół&#47;wciśnięty pole kombi](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Tło|`CommonControls.ComboBoxBackgroundFocused`|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Obramowanie|`CommonControls.ComboBoxBorderFocused`|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Tekst|`CommonControls.ComboBoxTextFocused`|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Separator|`CommonControls.ComboBoxSeparatorFocused`|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glifów|`CommonControls.ComboBoxGlyphFocused`|  
|![Upuść&#45;w dół&#47;pole kombi koncentruje](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Wybór wprowadzania tekstu**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Wprowadzanie tekstu pola kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Wyróżnij|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Naciśnięty — widok elementu listy**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackground`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackgroundHover`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorder`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderHover`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderPressed`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderFocused`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemText`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextHover`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextPressed`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextFocused`|  
|![Upuść&#45;w dół&#47;widok listy pól kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Cień tła|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelaryczne (siatki)  
 Kontrolki danych tabelaryczne, znane również jako formanty siatki, są typowymi formantami programu Visual Studio, które mogą być używane do prezentowania dużych ilości danych w wielu kolumnach. Standardowe kontrole danych tabelaryczne można znaleźć w wielu miejscach w programie Visual Studio: okno narzędzia lista błędów, raporty IntelliTrace i widok sterty pamięci, między innymi. Zawsze używaj standardowych kontroli danych tabelaryczne. W niektórych rzadkich przypadkach może nie mieć dostępu do standardowych kontroli danych tabelaryczne. W takich sytuacjach należy użyć następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelaryczne w programie Visual Studio.  
  
 ![Tabelaryczne dane &#40;sterowanie siatką&#41; czerwoną](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Używać...  
 dla kontrolek tabelaryczne lub siatki.  
  
 Nie używaj ...  
 dla dowolnego interfejsu użytkownika, który nie jest formantem tabelarycznym ani siatki.  
  
##### <a name="column-headers"></a>Nagłówki kolumn  
 Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego glifów zwykle używanych, gdy siatka jest sortowana według tej kolumny.  
  
|Stan|Element|Nazwa tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Domyślne|Tło|`Header.Default`|  
|Domyślne|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|Domyślne|Pierwszy plan (Glif)|`Header.Glyph`|  
|Domyślne|Obramowanie|`Header.SeparatorLine`|  
|Aktywowane|Tło|`Header.MouseOver`|  
|Aktywowane|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|Aktywowane|Pierwszy plan (Glif)|`Header.MouseOverGlyph`|  
|Aktywowane|Obramowanie|`Header.SeparatorLine`|  
|Naciśnięte|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|Naciśnięte|Pierwszy plan (tekst)|`CommonControls.CheckBoxBorderPressed`|  
|Naciśnięte|Pierwszy plan (Glif)|`CommonControls.CheckBoxTextPressed`|  
|Naciśnięte|Obramowanie|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Elementy widoku listy  
 Elementy widoku listy składają się z tła i zawartości. Zawartość może być tekstem, ikoną lub obiema.  
  
|Stan|Element|Nazwa tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Domyślne|Tło|Przezroczyste|  
|Domyślne|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|Domyślne|Obramowanie|Brak|  
|Zaznaczone (aktywne)|Tło|`TreeView.SelectedItemActive`|  
|Zaznaczone (aktywne)|Pierwszy plan (tekst)|`TreeView.SelectedItemActiveText`|  
|Zaznaczone (aktywne)|Obramowanie|Brak|  
|Zaznaczone (nieaktywne)|Tło|`TreeView.SelectedItemInactive`|  
|Zaznaczone (nieaktywne)|Pierwszy plan (tekst)|`TreeView.SelectedItemInactiveText`|  
|Zaznaczone (nieaktywne)|Obramowanie|Brak|  
  
### <a name="manifest-designer"></a>Manifest Designer  
 Projektant manifestu został zaprojektowany jako sposób na ułatwienie edytowania pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Chociaż nie ma żadnej udostępnionej struktury dostępnej do użycia, może być odpowiedni dla ciebie, aby dopasować układ projektu i kolory kart orientacji/nawigacji i ogólnej struktury. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [Układ programu Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Czerwona linia projektanta manifestu](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Używać...  
- dla projektantów, które są podobne do Projektanta manifestu.  

- zamiast używania wspólnych kontrolek kart w górnej części edytora w dokumencie.  

Nie używaj ...  
- jeśli masz więcej niż sześć kart.  

- dla dowolnego interfejsu użytkownika, który nie jest skonstruowany jak Projektant manifestu.  
  
|Stan|Składnik|Element|Nazwa tokenu: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Domyślnie (zaznaczone)|Tab|Tło|`ManifestDesigner.TabActive`|  
|Domyślnie (zaznaczone)|Tab|Obramowanie|Brak|  
|Domyślnie (zaznaczone)|Okienko opisu|Tło|`ManifestDesigner.DescriptionPane`|  
|Domyślnie (zaznaczone)|Strona zawartości|Tło|`ManifestDesigner.Background`|  
|Domyślnie (zaznaczone)|Strona zawartości|Tekst pomocnika okna dialogowego|`ManifestDesigner.WatermarkText`<br /><br /> Ta nazwa tokenu nie pasuje do jego funkcji.|  
|Niewybrane|Tab|Tło|`ManifestDesigner.Tab.Inactive`|  
|Aktywowane|Tab|Tło|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Znakowanie  
 Visual Studio obsługuje tagowanie, co pozwala użytkownikowi zadeklarować słowa kluczowe z wyszukuj do celów śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać team foundation server (TFS) do oznaczania elementów roboczych. Poniższe tabele podają nazwy kolorów zarówno dla samego tagu, jak i glifu "zamknij ikonę", który pojawia się w stanach myszy i wybranych.  
  
 ![Oznaczanie czerwonej linii](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Używać...  
 dla interfejsu użytkownika, który obsługuje tagowanie.  
  
 Nie używaj ...  
 dla innego typu interfejsu użytkownika.  
  
#### <a name="tag"></a>Tag  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Domyślny**|Tło|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Domyślny**|Pierwszy plan (tekst)|`Tag.Background`|  
|![Tag po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Aktywowane**|Tło|`Tag.HoverBackground`|  
|![Tag po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Aktywowane**|Pierwszy plan (tekst)|`Tag.HoverBackgroundText`|  
|![Wciśnięty znacznik](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Naciśnięte**|Tło|`Tag.PressedBackground`|  
|![Wciśnięty znacznik](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Naciśnięte**|Pierwszy plan (tekst)|`Tag.PressedBackgroundText`|  
|![Znacznik zaznaczony](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Wybrano**|Tło|`Tag.SelectedBackground`|  
|![Znacznik zaznaczony](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Wybrano**|Pierwszy plan (tekst)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glif (ikona zamknięcia)  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Oznacz &#40;&#41;glifów](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Domyślny (domyślny tag)**|Tło|Nie dotyczy|  
|![Oznacz &#40;&#41;glifów](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Domyślny (domyślny tag)**|Pierwszy plan (Glif)|`Tag.TagHoverGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Oznacz &#40;&#41; glifów po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wskaźnik myszy (domyślny znacznik)**|Tło|`Tag.TagHoverGlyphHoverBackground`|  
|![Oznacz &#40;&#41; glifów po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wskaźnik myszy (domyślny znacznik)**|Pierwszy plan (Glif)|`Tag.TagHoverGlyphHover`|  
|![Oznacz &#40;&#41; glifów po najechaniu kursorem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Wskaźnik myszy (domyślny znacznik)**|Obramowanie|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Znacznik &#40;&#41; glifów wciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Wciśnięty (tag domyślny)**|Tło|`Tag.TagHoverGlyphPressedBackground`|  
|![Znacznik &#40;&#41; glifów wciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Wciśnięty (tag domyślny)**|Pierwszy plan (Glif)|`Tag.TagHoverGlyphPressed`|  
|![Znacznik &#40;&#41; glifów wciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Wciśnięty (tag domyślny)**|Obramowanie|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Znacznik zaznaczony/domyślny glif**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Znacznik zaznaczony](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Domyślny (zaznaczony tag)**|Tło|Nie dotyczy|  
|![Znacznik zaznaczony](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Domyślny (zaznaczony tag)**|Pierwszy plan (Glif)|`Tag.TagSelectedGlyph`|  
  
 **Znacznik zaznaczony/aktywowanie glifów**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Znacznik wybrany po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Wskaźnik myszy (zaznaczony znacznik)**|Tło|`Tag.TagSelectedGlyphHoverBackground`|  
|![Znacznik wybrany po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Wskaźnik myszy (zaznaczony znacznik)**|Pierwszy plan (Glif)|`Tag.TagSelectedGlyphHover`|  
|![Znacznik wybrany po najechaniu kursorem myszy](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Wskaźnik myszy (zaznaczony znacznik)**|Obramowanie|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Znacznik wybrany/wciśnięty glif**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Znacznik wciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Wciśnięty (zaznaczony znacznik)**|Tło|`Tag.TagSelectedGlyphPressedBackground`|  
|![Znacznik wciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Wciśnięty (zaznaczony znacznik)**|Pierwszy plan(Glif)|`Tag.TagSelectedGlyphPressed`|  
|![Znacznik wciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Wciśnięty (zaznaczony znacznik)**|Obramowanie|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Powłoka  
  
#### <a name="background"></a>Tło  
 Tło środowiska składa się z dwóch warstw. Dolna warstwa jest jednolity kolor, który obejmuje cały IDE. Górna warstwa mieści się pod półką poleceń i między oknem narzędzia automatycznie ukrywaj kanały po lewej i prawej krawędzi IDE. Od programu Visual Studio 2013 górne i dolne warstwy tła są ustawione na ten sam kolor w motywach Jasne i Ciemne.  
  
 ![Czerwona linia tła powłoki](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Używać...  
 dla miejsc, które mają być zgodne z tłem środowiska programu Visual Studio.  
  
Nie używaj ...  
- jako wypełnienie dla miejsc, które nie są powierzchniami tła.  

- jako tło, na którym chcesz umieścić elementy pierwszego planu.  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Warstwa dolna|Tło|`Environment.EnvironmentBackground`|  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Warstwa górna|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Warstwa górna|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Warstwa górna|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Warstwa górna|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Półka poleceń  
 Dwa zestawy nazw tokenów są używane dla tła półki poleceń: jeden zestaw, dla którego znajduje się pasek menu i jeden dla miejsca, w którym znajdują się paski poleceń. Indywidualna grupa paska poleceń ma własne wartości kolorów tła, które są omówione bardziej szczegółowo w sekcji "pasek poleceń". Pasek menu i tekst paska poleceń są omawiane odpowiednio w sekcjach menu i paska poleceń.  
  
 ![Czerwona linia półki poleceń](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Używać...  
- dla obszarów, w których umieszczasz menu lub paski narzędzi.  

- z prawidłową kombinacją nazw tokenów tła/pierwszego planu.  
  
  Nie używaj ...  
  dla obszarów, które nie są podobne do półki poleceń.  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Pasek menu|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Pasek menu|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Pasek menu|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Pasek poleceń|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Pasek poleceń|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Pasek poleceń|Tło<br /><br /> *Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Przybornik  
 Przybornik jest jednym z typowych okien narzędzi, który jest najczęściej używany w programie Visual Studio. Jest to zasadniczo kontrola drzewa ze specjalnym motywem i zastosowanej stylizacji.  
  
 ![Czerwony pasek narzędzi](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Używać...  
 podczas projektowania okna narzędzia, które ma być zawsze zgodne z przybornikami powłoki.  
  
 Nie używaj ...  
 dla wszystkiego, co nie jest podobne do interfejsu użytkownika przybornika lub jeśli nie masz pewności, czy interfejs użytkownika będzie miał problemy, jeśli zmienią się kolory przybornika powłoki.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Węzeł nadrzędny przybornika przybornika przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli nie ma dostępnych formantów|  
|![Węzeł podrzędny przybornika przyborniku](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli nie ma dostępnych formantów|  
|![Węzeł nadrzędny przybornika przybornika przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika przyborniku](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł nadrzędny przybornika przybornika przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszy plan (Glif)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika przyborniku](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszy plan (Glif)|`Environment.ToolboxContent`|  
|![Węzeł nadrzędny przybornika przybornika przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszy plan (tekst)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika przyborniku](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszy plan (tekst)|`Environment.ToolboxContent`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Węzeł podrzędny przyborniku przy najechaniu kursorem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Przybornik najechać kursorem na węzeł podrzędny**|Tło|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedyncze przedmioty|  
|![Węzeł podrzędny przyborniku przy najechaniu kursorem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Przybornik najechać kursorem na węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przyborniku przy najechaniu kursorem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Przybornik najechać kursorem na węzeł podrzędny**|Pierwszy plan (tekst)|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedyncze przedmioty|  
  
 **Wybrano**  
  
|Składnik|Element|Nazwa tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Skupiono się na węźle nadrzędnym przybornika przyborniku](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Skoncentrowany węzeł nadrzędny**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle podrzędnym przybornika](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Skoncentrowany węzeł podrzędny**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle nadrzędnym przybornika przyborniku](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Skoncentrowany węzeł nadrzędny**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle podrzędnym przybornika](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Skoncentrowany węzeł podrzędny**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle nadrzędnym przybornika przyborniku](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Skoncentrowany węzeł nadrzędny**|Pierwszy plan (Glif)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle podrzędnym przybornika](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Skoncentrowany węzeł podrzędny**|Pierwszy plan (Glif)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle nadrzędnym przybornika przyborniku](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Skoncentrowany węzeł nadrzędny**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Skupiono się na węźle podrzędnym przybornika](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Skoncentrowany węzeł podrzędny**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł nadrzędny**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł podrzędny**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł nadrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł nadrzędny przybornika przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł nadrzędny**|Pierwszy plan (Glif)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł podrzędny**|Pierwszy plan (Glif)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł nadrzędny**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika nieskoncentrowany](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nieskoncentrowany węzeł podrzędny**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widok drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Odwołanie do wartości koloru  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Składnik|Część|Element|Stan|Jasny|Ciemny|Blue|Wysoki kontrast|  
|Linie podziału|||Domyślne|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark ( ControlDark )|  
|Glif ekspandera||Pierwszy plan|Domyślne|||||  
|Glif ekspandera||Pierwszy plan|Aktywowane|||||  
|Glif ekspandera||Tło|Domyślne|||||  
|Glif ekspandera||Tło|Aktywowane|||||  
|Glif ekspandera||Obramowanie|Domyślne|||||  
|Glif ekspandera||Obramowanie|Aktywowane|||||