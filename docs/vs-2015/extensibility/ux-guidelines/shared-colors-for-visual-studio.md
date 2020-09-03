---
title: Udostępnione kolory
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154602"
---
# <a name="shared-colors-for-visual-studio"></a>Udostępnione kolory dla programu Visual Studio

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas projektowania interfejsu użytkownika, który używa typowych elementów programu Visual Studio Shell lub chcesz, aby element interfejsu był spójny z podobnymi funkcjami, Użyj istniejących nazw tokenów w plikach definicji pakietów, aby wybrać i przypisać kolory. Dzięki temu interfejs użytkownika pozostaje spójny z ogólnym środowiskiem programu Visual Studio i jest aktualizowany automatycznie po dodaniu lub zaktualizowaniu motywów.

W tym artykule opisano typowe elementy interfejsu użytkownika i używane przez nie nazwy tokenów, które można przywołać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje na temat uzyskiwania dostępu do tych tokenów kolorów, zobacz [usługę VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Upewnij się, że nazwy tokenów są poprawnie używane:

- **Używaj nazw tokenów opartych na funkcjach, a nie na samym kolorze.** Wspólne kolory udostępnione są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko dla tych samych lub podobnych funkcji. Na przykład nie należy ponownie używać koloru naciśniętego pola kombi dla obracającej animacji postępu, tak samo jak kolor. Funkcje pola kombi i animacji są różne i jeśli kolor skojarzony z polem kombi zmieni się, może to nie być już odpowiedni kolor elementu animacji. Spójne użycie koloru pozwala na ukierunkowanie użytkowników i zapobieganie niepomyleniu.

- **Używaj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które mają być używane z tekstem, będą mieć skojarzony kolor tekstu. Nie używaj kolorów tekstu innych niż określone dla danego tła. Jeśli nie ma skojarzonego koloru tekstu, nie używaj tego koloru tła dla każdej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą spowodować nieczytelny interfejs.

- **Użyj kolorów kontroli odpowiednich dla ich lokalizacji.** W niektórych stanach niektóre kontrolki programu Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego wybierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów, które są odpowiednie dla lokalizacji, w której umieszczasz formant.

> [!IMPORTANT]
> Nie można używać tokenów znajdujących się w kategorii "Strona początkowa" lub "jabłecznik".

## <a name="command-structures"></a>Struktury poleceń

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menu

Menu mogą wystąpić w kilku miejscach w programie Visual Studio: główny pasek menu, osadzony w dokumencie lub narzędziu, lub po kliknięciu prawym przyciskiem myszy w różnych lokalizacjach w środowisku IDE. Implementacje menu skojarzonych z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiedniego elementu. Należy zawsze używać standardowej implementacji menu dostarczanej przez środowisko programu Visual Studio. Jednak w niektórych rzadkich przypadkach może nie mieć dostępu do standardowych menu programu Visual Studio. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w programie Visual Studio.

![Menu Redline](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 — 000_MenuRedline")

Użyj...
- zawsze, gdy trzeba utworzyć niestandardowe menu.

- gdy masz nowy składnik interfejsu użytkownika, który chcesz dopasować do menu programu Visual Studio.

Nie używaj...
sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu w określony sposób.

#### <a name="menu-title"></a>Tytuł menu

Tytuły menu składają się z tła, obramowania i tekstu tytułu, a także symbolu opcjonalnego, zazwyczaj gdy menu znajduje się na pasku poleceń.

![Tytuł menu Redline](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 — 001_MenuTitleRedline")

Użyj...
za każdym razem, gdy tworzysz tytuł menu niestandardowego.

Nie używaj...
- dla wszystkich elementów, które nie powinny być zawsze zgodne z tytułem menu.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Domyślny tytuł menu](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 — 002_MenuTitleDefault")

  **Tytuł menu**

  Tło

  Brak

  Pierwszy plan (tekst)

  `Environment.CommandBarTextActive`

  ![Tytuł menu z wartością domyślną glifu](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")

  **Tytuł menu z glifem**

  Pierwszy plan (symbol)

  `Environment.CommandBarMenuGlyph`

  Obramowanie

  Brak

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Tytuł menu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 — 004_MenuTitleHover")

  **Tytuł menu**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextHover`

  ![Tytuł menu z symbolem po aktywowaniu](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")

  **Tytuł menu z glifem**

  Pierwszy plan (symbol)

  `Environment.CommandBarMenuMouseOverGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto tytuł menu](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 — 006_MenuTitlePressed")

  **Tytuł menu**

  Tło

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextActive`

  ![Tytuł menu z naciśniętym symbolem](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")

  **Tytuł menu z glifem**

  Pierwszy plan (symbol)

  `Environment.CommandBarMenuMouseDownGlyph`

  Obramowanie

  `Environment.CommandBarMenuBorder`

  Tylko lewe, górne i prawe.

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Tytuł menu z wyłączonym glifem](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")

  **Tytuł menu z glifem**

  Tło

  Brak

  Pierwszy plan (tekst)

  `Environment.CommandBarTextInactive`

  Pierwszy plan (symbol)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

#### <a name="menu"></a>Menu

Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub symbolu podmenu. Zmiana koloru tła i tekstu przy aktywowaniu. Ten token koloru to para tła/pierwszego planu.

![Elementy menu Redline](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 — 009_MenuItemRedline")

Użyj...
dla każdej listy rozwijanej, która jest uruchamiana z paska menu lub paska poleceń.

Nie używaj...
- dla każdej listy rozwijanej, która występuje w innym kontekście.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Domyślne menu](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")

  **Menu**

  Tło

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextActive`

  Pierwszy plan (symbol podmenu)

  `Environment.CommandBarMenuSubmenuGlyph`

  Obramowanie

  `Environment.CommandBarMenuBorder`

  Tło ikony kanału

  `Environment.CommandBarMenuIconBackground`

  Separator

  `Environment.CommandBarMenuSeparator`

  W tle

  `Environment.DropShadowBackground`

  ![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 — 011_MenuChecked")

  **Dane**

  Znacznik wyboru

  `Environment.CommandBarCheckBox`

  Znacznik wyboru tła

  `Environment.CommandBarSelectedIcon`

  ![Wybrano menu](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 — 012_MenuSelected")

  **Wybrane**

  Tło ikony

  `Environment.CommandBarSelected`

  Obramowanie ikony

  `Environment.CommandBarSelectedBorder`

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Aktywowanie menu](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 — 013_MenuHover")

  **Element menu**

  Tło

  `Environment.CommandBarMenuItemMouseOver`

  Pierwszy plan (tekst)

  `Environment.CommandBarMenuItemMouseOver`

  Pierwszy plan (symbol podmenu)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Zaznaczono aktywowany menu](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 — 014_MenuHoverChecked")

  **Dane**

  Znacznik wyboru

  `Environment.CommandBarCheckBoxMouseOver`

  Znacznik wyboru tła

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Wybrano aktywowany menu](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 — 015_MenuHoverSelected")

  **Wybrane**

  Tło ikony

  `Environment.CommandBarHoverOverSelected`

  Obramowanie ikony

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 — 016_MenuDisabled")

  Element menu

  Pierwszy plan (tekst)

  `Environment.CommandBarTextInactive`

  Pierwszy plan (symbol podmenu)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Wyłączono zaznaczenie opcji menu](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 — 017_MenuDisabledChecked")

  Zaznaczono

  Znacznik wyboru

  `Environment.CommandBarCheckBoxDisabled`

  Znacznik wyboru tła

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Pasek poleceń

Pasek poleceń może pojawić się w wielu miejscach w środowisku IDE programu Visual Studio, w szczególności z półkami poleceń i osadzonych w oknach narzędzi lub dokumentów.

Ogólnie rzecz biorąc zawsze używaj standardowej implementacji paska poleceń dostarczonej przez środowisko programu Visual Studio. Zastosowanie mechanizmu standardowego gwarantuje, że wszystkie szczegóły wizualizacji będą wyświetlane poprawnie i że te elementy interaktywne będą stale działać z innymi kontrolkami paska poleceń programu Visual Studio. Jeśli jednak jest to konieczne, aby skompilować własny pasek poleceń, upewnij się, że styl jest poprawnie używany przy użyciu następujących nazw tokenów.

![Pasek poleceń Redline](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 — 018_CommandBarRedline")

![Przycisk przepełnienia Redline](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 — 019_OverflowButtonRedline")

Użyj...
w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.

Nie używaj...
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.

#### <a name="command-bar-group"></a>Grupa paska poleceń

Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przyciski podzielone, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów są regulowane przez oddzielne nazwy tokenów i są omawiane osobno w innym miejscu w tym przewodniku. Linia separatora służy do dzielenia grupy paska poleceń na powiązane podgrupy.

![Redline grupy paska poleceń](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 — 020_CommandBarGroupRedline")

Użyj...
w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.

Nie używaj...
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.

  **Domyślne** (nie inne Stany)

  Element

  Nazwa tokenu: Category. Color

  Tło

  `Environment.CommandBarGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Obramowanie

  `Environment.CommandBarToolBarBorder`

  Przeciągnij uchwyt

  `Environment.CommandBarDragHandle`

  Separator

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Ikony poleceń

![Ikona polecenia Redline](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 — 021_CommandIconRedline1")

![Ikona polecenia Redline](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 — 022_CommandIconRedline2")

Użyj...
dla każdego przycisku, który zostanie umieszczony na pasku poleceń.

Nie używaj...
- dla kontrolek mających własne nazwy tokenów.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Domyślna ikona polecenia](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 — 023_CommandIconDefault")

  **Wartooć**

  Tło

  Nie dotyczy (dziedziczy z poziomu tła paska poleceń)

  Pierwszy plan (tekst)

  `Environment.CommandBarTextActive`

  Obramowanie

  Brak

  ![Wybrana domyślnie ikona polecenia](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")

  **Wybrane**

  Tło

  `Environment.CommandBarSelected`

  Pierwszy plan (tekst)

  `Environment.CommandBarTextSelected`

  Obramowanie

  `Environment.CommandBarSelectedBorder`

  **Aktywowanie i klawiatura ukierunkowana**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Ikona polecenia — Umieść kursor](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 — 025_CommandIconHover")

  **Standardowy przy aktywowaniu**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextHover`

  Obramowanie

  `Environment.CommandBarBorder`

  ![Ikona polecenia — Wybierz kursor](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")

  **Wybrane przy aktywowaniu**

  Tło

  `Environment.CommandBarHoverOverSelected`

  Pierwszy plan (tekst)

  `Environment.CommandBarTextHoverOverSelected`

  Obramowanie

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto ikonę polecenia](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 — 027_CommandIconPressed")

  **Ikona polecenia naciśniętego**

  Tło

  `Environment.CommandBarMouseDownBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextMouseDown`

  Obramowanie

  `Environment.CommandBarBorder`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Ikona polecenia wyłączona](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 — 028_CommandIconDisabled")

  **Ikona polecenia wyłączonego**

  Tło

  Nie dotyczy (dziedziczy z poziomu tła paska poleceń)

  Pierwszy plan (tekst)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

#### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a> Pole kombi

> [!IMPORTANT]
> Pola kombi są podobne do list rozwijanych, ale zawierają edytowalny region tekstu. Jeśli lista rozwijana nie zawiera regionu tekstu edytowalnego, użyj tokenów kolorów znalezionych w obszarze [listy rozwijanej](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Pole kombi Redline](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 — 029_ComboBoxRedline")

Użyj...
- podczas kompilowania niestandardowych pól kombi.

- podczas tworzenia kontrolki paska poleceń, która jest podobna do pola kombi.

  Nie używaj...
  - dla wszystkich elementów, które nie zawsze pasują do interfejsu użytkownika paska poleceń.

- gdy masz dostęp do pola kombi z stylem.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Pole kombi pola wejściowego](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")

  **Pole wejściowe**

  Tło

  `Environment.ComboBoxBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxText`

  Obramowanie

  `Environment.ComboBoxBorder`

  Separator

  Brak separatora

  ![Pole kombi upuść&#45;przycisk w dół](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")

  **Przycisk listy rozwijanej**

  Tło

  Nie dotyczy (dziedziczy)

  Pierwszy plan (symbol)

  `Environment.ComboBoxGlyph`

  ![Pole kombi&#47;upuść&#45;lista](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")

  **Lista rozwijana**

  Tło

  `Environment.ComboBoxPopupBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.ComboBoxItemText`

  Obramowanie

  `Environment.ComboBoxPopupBorder`

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Pole kombi pola wejściowego przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")

  **Pole wejściowe**

  Tło

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.ComboBoxMouseOverText`

  Obramowanie

  `Environment.ComboBoxMouseOverBorder`

  Separator

  `Environment.ComboBoxMouseOverSeparator`

  ![Pole kombi&#47;upuść&#45;przycisk w dół na przycisku aktywowany](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxButtonMouseOverBackground`

  Pierwszy plan (symbol)

  `Environment.ComboBoxMouseOverGlyph`

  ![Pole kombi&#47;upuść&#45;listy przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")

  **Lista rozwijana**

  Tło (element menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxItemMouseOverText`

  Obramowanie (element menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Ustawiono fokus**

  Składnik

  Element

  Nazwa tokenu: Color. Category

  ![Pole kombi pola wejściowego z fokusem](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")

  **Pole wejściowe**

  Tło

  `Environment.ComboBoxFocusedBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxFocusedText`

  Obramowanie

  `Environment.ComboBoxFocusedBorder`

  Separator

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Pole kombi&#47;upuść&#45;przycisk w dół](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxFocusedButtonBackground`

  Pierwszy plan (symbol)

  `Environment.ComboBoxFocusedGlyph`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Color. Category

  ![Naciśnięto pole wejściowe pola kombi](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")

  **Pole wejściowe**

  Tło

  `Environment.ComboBoxMouseDownBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxMouseDownText`

  Obramowanie

  `Environment.ComboBoxMouseDownBorder`

  Separator

  `Environment.ComboBoxMouseDownSeparator`

  ![Pole kombi&#47;naciśnięcie przycisku upuść&#45;w dół](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxButtonMouseDownBackground`

  Pierwszy plan (symbol)

  `Environment.ComboBoxMouseDownGlyph`

  **Wyłączone**

  ![Pole wejściowe pola kombi jest wyłączone](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")

  **Pole wejściowe**

  Tło

  `Environment.ComboBoxDisabledBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxDisabledText`

  Obramowanie

  `Environment.ComboBoxDisabledBorder`

  Separator

  Brak separatora

  ![Pole kombi&#47;upuść&#45;przycisk w dół wyłączone](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszy plan (symbol)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a> Lista rozwijana

> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale brak edytowalnych regionów tekstu. Jeśli lista rozwijana zawiera region tekstu edytowalnego, użyj tokenów kolorów znajdujących się w [polu kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Porzuć&#45;w dół Redline](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 — 042_DropdownRedline")

Użyj...
podczas tworzenia niestandardowych kontrolek listy rozwijanej.

Nie używaj...
- dla wszystkich elementów, które nie są podobne do listy rozwijanej.

- dla pól kombi lub przycisków podziału.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść pole wyboru&#45;w dół](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")

  **Pole wyboru**

  Tło

  `Environment.DropDownBackground`

  Pierwszy plan (tekst)

  `DropDownText`

  Obramowanie

  `DropDownBorder`

  Separator

  Brak separatora

  ![Przycisk Porzuć&#45;w dół](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 — 044_DropdownButton")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszy plan (symbol)

  `Environment.DropDownGlyph`

  ![Upuść&#45;ą listę](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")

  **Lista rozwijana**

  Tło

  `Environment.DropDownPopupBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.ComboBoxItemText`

  Obramowanie

  `Environment.DropDownPopupBorder`

  W tle

  `Environment.DropShadowBackground`

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść pole wyboru&#45;w dół na aktywowaniu](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")

  **Pole wyboru**

  Tło

  `Environment.DropDownMouseOverBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.DropDownMouseOverText`

  Obramowanie

  `Environment.DropDownMouseOverBorder`

  Separator

  `Environment.DropDownButtonMouseOverSeparator`

  ![Przycisk Porzuć&#45;w dół na aktywowaniu](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.DropDownButtonMouseOverBackground`

  Pierwszy plan (symbol)

  `Environment.DropDownMouseOverGlyph`

  ![Upuść&#45;ą listę przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 — 048_DropdownListHover")

  **Lista rozwijana**

  Tło (element menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Pierwszy plan (tekst)

  `Environment.ComboBoxItemMouseOverText`

  Obramowanie (element menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto pole wyboru&#45;w dół](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")

  **Pole wyboru**

  Tło

  `Environment.DropDownMouseDownBackground`

  Pierwszy plan (tekst)

  `Environment.DropDownMouseDownText`

  Obramowanie

  `Environment.DropDownMouseDownBorder`

  Separator

  `Environment.DropDownButtonMouseDownSeparator`

  ![Naciśnięto przycisk Porzuć&#45;w dół](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.DropDownButtonMouseDownBackground`

  Pierwszy plan (symbol)

  `Environment.DropDownMouseDownGlyph`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść pole wyboru&#45;wyłączone](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")

  Tło

  `Environment.DropDownDisabledBackground`

  Pierwszy plan (tekst)

  `Environment.DropDownDisabledText`

  Obramowanie

  `Environment.DropDownDisabledBorder`

  Separator

  Brak separatora

  ![Przycisk usuwania&#45;w dół jest wyłączony](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")

  Tło

  Brak

  Pierwszy plan (symbol)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Przycisk podziału

Przyciski podziału współdzielą wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne nazwy tokenów przycisku akcji i listy rozwijanej są powtarzane w tym miejscu dla wygody. Lista rozwijana przycisku podziału to implementacje [menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)paska poleceń.

![Przycisk podziału Redline](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 — 053_SplitButtonRedline")

Użyj...
podczas tworzenia niestandardowego przycisku podziału.

Nie używaj...
- dla innych rodzajów przycisków.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk podziału](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")

  **Przycisk podziału (wartość domyślna)**

  Tło

  Brak

  Pierwszy plan (tekst)

  `Environment.CommandBarTextActive`

  Pierwszy plan (symbol)

  `Environment.CommandBarSplitButtonGlyph`

  Obramowanie

  Brak

  Separator

  Brak

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk podziału po aktywowaniu](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")

  **Przycisk podziału (przy aktywowaniu)**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextHover`

  Pierwszy plan (symbol)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  Separator

  `Environment.CommandBarSplitButtonSeparator`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto przycisk podziału](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")

  **Przycisk podziału (naciśnięto)**

  Tło

  `Environment.CommandBarMouseDownBackgroundBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `Environment.CommandBarTextMouseDown`

  Pierwszy plan (symbol)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  Separator

  Brak

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk podziału wyłączony](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")

  **Przycisk podziału (wyłączony)**

  Tło

  Brak

  Pierwszy plan (tekst)

  `Environment.ComboBoxItemTextInactive`

  Pierwszy plan (symbol)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

  Separator

  Brak

#### <a name="more-options-and-overflow-buttons"></a>Przyciski "więcej opcji" i "overflow"
 Przycisk "więcej opcji" jest używany, gdy grupy paska poleceń można dostosowywać przez dodawanie lub usuwanie powiązanych przycisków paska poleceń. Przycisk "przepełnienie" pojawia się, gdy pasek poleceń został obcięty z powodu braku miejsca w poziomie, a w obszarze kliknij Pokaż menu zawierające przyciski paska poleceń, których nie można wyświetlić. Kolory tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.

 ![Więcej opcji Redline](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 — 058_MoreOptionsRedline")

 Użyj...
dla niestandardowych przycisków "więcej opcji" lub "overflow".

 Nie używaj...
przyciski, które nie mają podobnej funkcjonalności, do przycisku "więcej opcji" lub "overflow".

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Więcej opcji](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 — 059_MoreOptions")

 **Więcej opcji**

 ![Przycisk przepełnienia](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 — 060_Overflow")

 **Przepływ**

 Tło

 `Environment.CommandBarOptionsBackground`

 Pierwszy plan (symbol)

 `Environment.CommandBarOptionsGlyph`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Więcej opcji przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 — 061_MoreOptionsHover")

 **Więcej opcji**

 ![Przepełnienie przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 — 062_OverflowOptions")

 **Przepływ**

 Tło

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (symbol)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto więcej opcji](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 — 063_MoreOptionsPressed")

 **Więcej opcji**

 ![Naciśnięto przepełnienie](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 — 064_OverflowPressed")

 **Przepływ**

 Tło

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (symbol)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Okna dokumentów
 Nie ma potrzeby replikowania okien dokumentów, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach dokumentów, aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.

 W przypadku używania tokenów kolorów okna dokumentu należy zachować ostrożność, aby użyć ich tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, będziesz mieć nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frame"></a>Ramka okna dokumentu
 Okna dokumentów mogą być zadokowane w środowisku IDE lub przestawne jako oddzielne okno. Gdy okno dokumentu jest przepływające poza IDE, nadal znajduje się w dokumencie i ma kolory tła, obramowania, tekstu i karty, które są takie same, jak gdy jest częścią IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne kolory tła, obramowania i tekstu. Gdy okna narzędzi są zadokowane w tym dokumencie, dziedziczą one zachowanie i kolor ich kart z nazw tokenów okna dokumentu.

 ![Okno zadokowanego dokumentu Redline](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 — 065_DockedDocumentWindowRedline")

 **Okno zadokowanego dokumentu**

 ![Przestawne okno dokumentu Redline](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 — 066_FloatingDocumentWindowRedline")

 **Przestawne okno dokumentu**

 Użyj...
wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okna dokumentu.

 Nie używaj...
dla każdego interfejsu użytkownika, którego nie chcesz automatycznie zmieniać, jeśli powłoka ma aktualizację motywu.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 Dokument: zadokowane lub przestawne

 Tło

 Zależy od typu dokumentu

 Pierwszy plan (tekst)

 Zależy od typu dokumentu

 Obramowanie

 `Environment.ToolWindowBorder`

 ![Ramka skoncentrowana](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")

 **Ramka: zmiennoprzecinkowe, ukierunkowane**

 Tło

 `Environment.ToolWindowFloatingFrame`

 Pierwszy plan (tekst)

 `Environment.ToolWindowFloatingFrame`

 Pierwszy plan (symbol)

 `Environment.RaftedWindowButtonActiveGlyph`

 Obramowanie

 `Environment.MainWindowActiveDefaultBorder`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonActiveBorder`

 Ustaw jako przezroczysty

 ![Ramka nieskoncentrowana](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")

 **Ramka: zmiennoprzecinkowe, nieskoncentrowane**

 Tło

 `Environment.ToolWindowFloatingFrameInactive`

 Pierwszy plan (tekst)

 `Environment.ToolWindowFloatingFrameInactive`

 Pierwszy plan (symbol)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Obramowanie

 `Environment.MainWindowInactiveBorder`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonInactiveBorder`

 Ustaw jako przezroczysty

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Ramka skoncentrowana na aktywowaniu](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 — 069_FrameFocusedHover")

 **Ramka: zmiennoprzecinkowe, ukierunkowane**

 Tło (symbol)

 `Environment.RaftedWindowButtonHoverActive`

 Pierwszy plan (symbol)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Ramka nieskoncentrowana na aktywowaniu](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")

 **Ramka: zmiennoprzecinkowe, nieskoncentrowane**

 Tło (symbol)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Pierwszy plan (symbol)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto fokus ramki](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 — 071_FrameFocusedPressed")

 **Ramka: zmiennoprzecinkowe, ukierunkowane**

 Tło (symbol)

 `Environment.RaftedWindowButtonDown`

 Pierwszy plan (symbol)

 `Environment.RaftedWindowButtonDownGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Karty dokumentów
 Karty dokumentów znajdują się w kanale karty, aby wskazać, które dokumenty są obecnie otwarte, wraz z których jeden jest bieżącym zaznaczonym lub aktywnym dokumentem. Okna narzędzi można także zadokować w kanale karty dokumentu, jeśli użytkownik umieści je w tym miejscu. W takiej sytuacji używają tych samych kolorów karty co okna dokumentu. Jeśli tworzysz interfejs użytkownika, który chcesz zawsze dopasować kolory okna dokumentu (w tym aktualizacje motywu lub zainstalować nowe motywy), odwołując się do tych tokenów kolorów.

 ![Karta dokumentu Redline](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 — 072_DocumentTabRedline")

 Użyj...
w dowolnym miejscu tworzysz interfejs użytkownika, który chcesz dopasować do kart dokumentów i automatycznie pobrać aktualizacje motywu lub nowe kolory motywu.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, gdy powłoka ma aktualizację motywu.

#### <a name="open-document-tabs"></a>Otwórz karty dokumentów
 Każdy otwarty dokument zawiera kartę w kanale karty dokumentu, który wyświetla jego nazwę. Dokumenty mogą być wybierane lub otwierane w tle, a ich karty odzwierciedlają te stany:

- Wybrana karta przedstawia dokument, który jest aktualnie wyświetlany w dokumencie. Wybrana karta zawiera obramowanie dokumentu, które rozciąga się między górną krawędzią dokumentu.

- Karty w tle to karty dokumentów, które nie są obecnie wybrane. Po kliknięciu stają się one wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.

  ![Otwórz Redline karty dokumentu](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 — 073_OpenDocumentTabRedline")

  Użyj...
  podczas tworzenia niestandardowych kart dokumentów.

  Nie używaj...
  - dla kart tymczasowych (Podgląd).

- dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

#### <a name="selected-tab"></a>Wybrana karta
 **Ustawiono fokus**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Wybrana karta skoncentrowana](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")

 **Karta wybrany dokument z fokusem**

 Tło

 `Environment.FileTabSelectedGradientTop`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.FileTabSelectedText`

 Obramowanie

 `Environment.FileTabSelectedBorder`

 Ustaw na ten sam kolor, co tło.

 Obramowanie dokumentu

 `Environment.FileTabDocumentBorderBackground`

 **Bez fokusu**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Wybrana karta nieskoncentrowana](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")

 **Karta wybrany dokument z fokusem**

 Tło

 `Environment.FileTabInactiveGradientTop`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.FileTabInactiveText`

 Obramowanie

 `Environment.FileTabInactiveBorder`

 Ustaw na ten sam kolor, co tło.

 Obramowanie dokumentu

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Karta tło
 **Wartooć**

 ![Karta tło](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 — 076_BackgroundTab")

 **Domyślna karta tła**

 Tło

 `Environment.FileTabBackground`

 Pierwszy plan (tekst)

 `Environment.FileTabText`

 Obramowanie

 `Environment.FileTabBorder`

 Ustaw na ten sam kolor, co tło.

 **Aktywowane**

 ![Karta tła na aktywowaniu](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 — 077_BackgroundTabHover")

 **Karta tła na aktywowaniu**

 Tło

 `Environment.FileTabHotGradientTop`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.FileTabHotText`

 Obramowanie

 `Environment.FileTabHotBorder`

 Ustaw na ten sam kolor, co tło.

#### <a name="preview-tab"></a>Karta Podgląd

Karta Podgląd zostanie wyświetlona po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksplorator rozwiązań. Działa jako wersja zapoznawcza dokumentu, a także daje użytkownikowi możliwość otwarcia dokumentu po lewej stronie kanału karty dokumentu. Tylko jedna otwarta karta podglądu może być otwarta w danym momencie. Karty podglądu mają Stany tła i wybrane, takie jak otwarte karty i mogą być skoncentrowane lub nieskoncentrowane w stanie aktywnym.

![Redline karty podglądu](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 — 078_PreviewTabRedline")

Użyj...
w dowolnym miejscu tworzysz tymczasową wersję zapoznawczą i chcesz, aby część elementu była zgodna z bieżącym kolorem karty podglądu.

Nie używaj...
- dla dowolnego rodzaju dokumentu lub karty, która nie jest tymczasowa (wersja zapoznawcza).

- dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

  **Wybrana karta podglądu: skoncentrowana**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Zakładka zapoznawcza](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")

  **Karta ukierunkowana wersja zapoznawcza**

  Tło

  `Environment.FileTabProvisionalSelectedActive`

  Pierwszy plan (tekst)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Ustaw na ten sam kolor, co tło.

  Obramowanie dokumentu

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Wybrana karta podglądu: nieskoncentrowany**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Nieskoncentrowana karta podglądu](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")

  **Nieskoncentrowana karta podglądu**

  Tło

  `Environment.FileTabProvisionalSelectedInactive`

  Pierwszy plan (tekst)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Obramowanie dokumentu

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Karta Podgląd w tle: domyślna**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Karta tła podglądu](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")

  **Karta tła karty podglądu**

  Tło

  `Environment.FileTabProvisionalInactive`

  Pierwszy plan (tekst)

  `Environment.FileTabProvisionalInactiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalInactiveBorder`

  Ustaw na ten sam kolor, co tło.

  **Karta Podgląd w tle: aktywowanie**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Karta tła podglądu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")

  **Karta tła karty podglądu przy aktywowaniu**

  Tło

  `Environment.FileTabProvisionalHover`

  Pierwszy plan (tekst)

  `Environment.FileTabProvisionalHoverForeground`

  Obramowanie

  `Environment.FileTabProvisionalHoverBorder`

  Ustaw na ten sam kolor, co tło.

#### <a name="document-overflow-button"></a>Przycisk przepełnienia dokumentu

Przycisk przepełnienia dokumentu jest obecny, jeśli istnieje co najmniej jeden otwarty dokument, bez względu na to, czy w bieżącej konfiguracji znajduje się odstęp w pionie, aby dopasować wszystkie karty dokumentu. Menu rozwijane przepełnienie dokumentu, które jest kontrolowane przez kolory **CommandBarMenu** (zobacz [menu](../../misc/shared-colors.md#BKMK_CommandMenus)), wyświetla listę wszystkich otwartych dokumentów, zarówno widocznych, jak i ukrytych, oraz zmiany glifu przepełnienia w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale karty.

![Przepełnienie Redline](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 — 083_OverflowRedline")

Użyj...
podczas tworzenia niestandardowego przycisku przepełnienia dokumentu.

Nie używaj...
- dla interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia.

- dla przycisków przepełnienia paska poleceń.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przepływ](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 — 084_Overflow")

  **Przycisk przepełnienia dokumentu**

  Tło

  `Environment.DocWellOverflowButtonBackground`

  Pierwszy plan (symbol)

  `Environment.DocWellOverflowButtonGlyph`

  Obramowanie

  Brak

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przepełnienie przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 — 085_OverflowHover")

  **Przycisk przepełnienia dokumentu po aktywowaniu**

  Tło

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Pierwszy plan (symbol)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Obramowanie

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto przepełnienie](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 — 086_OverflowPressed")

  **Przycisk przepełnienia naciśniętego dokumentu**

  Tło

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Pierwszy plan (symbol)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Obramowanie

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Okna narzędzi
 Nie ma potrzeby replikowania okien narzędzi, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach narzędzi, tak aby interfejs użytkownika zawsze pojawiał się w spójny sposób z tą częścią środowiska programu Visual Studio.

 ![Okno narzędzi Redline](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 — 087_ToolWindowRedline")

 Użyj...
wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

### <a name="tool-window-frame"></a>Ramka okna narzędzi
 Okna narzędzi w programie Visual Studio są używane dla wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzi jest otwarte, można je przypisać do dowolnej z czterech boków obszaru dokumentu. Okna narzędzi można również przepływać poza IDE, co umożliwia ich zmianę położenia w dowolnym miejscu na ekranie użytkownika. Przestawne okna zawsze znajdują się na wierzchu IDE. Na koniec okna narzędzi mogą być zadokowane jako okna dokumentu i wyświetlane jako karta w obszarze dokumentu. Okna narzędzi, które zostały zadokowane jako okna dokumentów, są kolorowe w części przy użyciu nazw tokenów okna dokumentu.

 ![Ramka okna narzędzia Redline](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 — 088_ToolWindowFrameRedline")

 Użyj...
wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

 **Zadokowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Okno narzędzia zostało zadokowane](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 — 089_ToolWindowDocked")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.ToolWindowBorder`

 **Przestawne: skoncentrowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Okno narzędzia z fokusem](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 — 090_ToolWindowFocused")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.MainWindowActiveDefaultBorder`

 **Zmiennoprzecinkowe: nieskoncentrowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Okno narzędzia bez fokusu](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi
 Obramowanie paska tytułu nie jest obramowaniem o wartości true, ale jest to linia pogrubiona w górnej części paska tytułu. Nie ma nazwy tokenu dla stanu nieskoncentrowanego.

 ![Pasek tytułu okna narzędzi Redline](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 — 092_ToolWindowTitleBarRedline")

 Użyj...
wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

 **Ustawiono fokus**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pasek tytułu skoncentrowany](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")

 **Priorytetowy pasek tytułu**

 Tło

 `Environment.TitleBarActiveGradientBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.TitleBarActiveText`

 Obramowanie

 `Environment.TitleBarActiveBorder`

 Ustaw na ten sam kolor, co tło.

 Przeciągnij uchwyt

 `Environment.TitleBarDragHandleActive`

 **Bez fokusu**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pasek tytułu bez fokusu](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")

 **Nieskoncentrowany pasek tytułu**

 Tło

 `Environment.TitleBarInactiveGradientBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.TitleBarInactiveText`

 Obramowanie

 Brak

 Przeciągnij uchwyt

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Przyciski paska tytułu

![Przycisk paska tytułu Redline](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 — 095_TitleBarButtonRedline")

Użyj...
w przypadku przycisków, które są wyświetlane w interfejsie użytkownika, które używają tokenów kolorów z pasków tytułu okna narzędzi.

Nie używaj...
- w przypadku przycisków, które są wyświetlane w innych lokalizacjach.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk paska tytułu — fokus](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")

  **Ustawiono fokus**

  Tło

  Brak

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonActiveGlyph`

  Obramowanie

  Brak

  ![Przycisk paska tytułu bez fokusu](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")

  **Bez fokusu**

  Tło

  Brak

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonInactiveGlyph`

  Obramowanie

  Brak

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk paska tytułu skoncentrowany na aktywowaniu](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")

  **Ustawiono fokus**

  Tło

  `Environment.ToolWindowButtonHoverActive`

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Przycisk paska tytułu bez fokusu po aktywowaniu](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")

  **Bez fokusu**

  Tło

  `Environment.ToolWindowButtonHoverInactive`

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Przycisk paska tytułu skoncentrowany i wciśnięty](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")

  **Ustawiono fokus**

  Tło

  `Environment.ToolWindowButtonDown`

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonDownBorder`

  ![Przycisk paska tytułu bez fokusu i został naciśnięty](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")

  **Bez fokusu**

  Tło

  `Environment.ToolWindowButtonDown`

  Pierwszy plan (symbol)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Karty okna narzędzi
 ![Karta okna narzędzi Redline](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 — 102_ToolWindowTabRedline")

 Użyj...
wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

 **Wybrana karta**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Karta okna narzędzi ukierunkowana](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")

 **Zaznaczona, ukierunkowana Karta okna narzędzi**

 Tło

 `Environment.ToolWindowTabSelectedTab`

 Pierwszy plan (tekst)

 `Environment.ToolWindowTabSelectedActiveText`

 Obramowanie

 `Environment.ToolWindowTabSelectedBorder`

 Ustaw na ten sam kolor, co tło.

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Karta okna narzędzi bez fokusu](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")

 **Zaznaczona, Karta okna narzędzia nieskoncentrowanego**

 Tło

 `Environment.ToolWindowTabSelectedTab`

 Pierwszy plan (tekst)

 `Environment.ToolWindowTabSelectedText`

 Obramowanie

 `Environment.ToolWindowTabSelectedBorder`

 Ustaw na ten sam kolor, co tło.

 **Karta tło**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Karta tła okna narzędzi](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")

 **Karta okna narzędzia tła**

 Tło

 `Environment.ToolWindowTabGradientBegin`

 Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.

 `Environment.ToolWindowTabGradientEnd`

 Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.

 Pierwszy plan (tekst)

 `Environment.ToolWindowTabText`

 Obramowanie

 `Environment.ToolWindowTabBorder`

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Karta tła okna narzędzi przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")

 **Karta okna narzędzia tła na aktywowaniu**

 Tło

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.

 Pierwszy plan (tekst)

 `Environment.ToolWindowTabMouseOverText`

 Obramowanie

 `Environment.ToolWindowTabMouseOverBorder`

 Ustaw na ten sam kolor, co tło.

### <a name="auto-hide-tabs"></a>Autoukrywanie kart
 ![Auto&#45;Ukryj Redline](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 — 107_AutoHideRedline")

 Użyj...
w dowolnym miejscu tworzysz interfejs użytkownika, który chcesz dopasować do kart okna z autoukrywaniem.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Auto&#45;Ukryj kartę](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 — 108_AutoHideTab")

 **Domyślna karta Autoukrywanie**

 Tło

 `Environment.AutoHideTabBackgroundBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.AutoHideTabText`

 Obramowanie

 `Environment.AutoHideTabBorder`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Auto&#45;Ukryj kartę przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 — 109_AutoHideTabHover")

 **Autoukrywanie karty przy aktywowaniu**

 Tło

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

 Pierwszy plan (tekst)

 `Environment.AutoHideTabMouseOverText`

 Obramowanie

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Wspólne formanty udostępnione
 Jeśli używasz standardowego paska poleceń programu Visual Studio w funkcji, będziesz mieć dostęp do kontrolek powłoki z stylami i nie należy ich powtarzać. Jeśli jednak trzeba utworzyć niestandardowy pasek poleceń, może być konieczne także skompilowanie niestandardowych kontrolek. W takim przypadku upewnij się, że używasz prawidłowych nazw tokenów dla każdej z następujących kontrolek, aby interfejs użytkownika był spójny z pozostałą częścią programu Visual Studio.

### <a name="search-box"></a>Pole wyszukiwania
 Jeśli to możliwe, użyj typowej kontrolki wyszukiwania dostarczonej przez środowisko programu Visual Studio. Kolory pola wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors. pkgdef** , który zawiera nazwy tokenów pola wejściowego, akcji przycisku, listy rozwijanej i menu rozwijanego.

 Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wykluczają się wzajemnie:

- "Skoncentrowane" lub "bez fokusu" odnosi się do tego, czy kursor znajduje się w polu tekstowym.

- "Aktywne" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadza zapytanie wyszukiwania w polu tekstowym.

- "Aktywowany" oznacza, że użytkownik przeznaczył mysz nad polem wyszukiwania za pomocą myszy (ten stan zastępuje wszystkie inne Stany).

- Wartość "wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.

  ![Redline pola wyszukiwania](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 — 110_SearchBoxRedline")

  Użyj...
  podczas projektowania niestandardowego pola wyszukiwania.

  Nie używaj...
  - dla wszystkich elementów, które nie są polem wyszukiwania.

- dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika pola wyszukiwania.

  **Ustawiono fokus**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Pole wejściowe wyszukiwania skoncentrowane](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")

  **Pole wejściowe**

  Tło

  `SearchControl.FocusedBackground`

  Pierwszy plan (tekst)

  `SearchControl.FocusedBackground`

  Obramowanie

  `SearchControl.FocusedBorder`

  Separator

  `SearchControl.FocusedDropDownSeparator`

  ![Przycisk akcji wyszukiwania — fokus](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")

  **Przycisk akcji**

  Tło

  Brak

  Pierwszy plan (symbol wyszukiwania)

  `SearchControl.SearchGlyph`

  Pierwszy plan (symbol STOP)

  `SearchControl.StopGlyph`

  Pierwszy plan (czysty symbol)

  `SearchControl.ClearGlyph`

  Obramowanie

  Brak

  ![Przycisk wyszukiwania Porzuć&#45;w dół](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.FocusedDropDownButton`

  Pierwszy plan (symbol)

  `SearchControl.FocusedDropDownButtonGlyph`

  Obramowanie

  `SearchControl.FocusedDropDownButtonBorder`

  **Bez fokusu**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")

  **Aktywne pole wejściowe**

  Tło

  `SearchControl.SearchActiveBackground`

  Pierwszy plan (tekst)

  `SearchControl.SearchActiveBackground`

  Obramowanie

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Wyszukiwanie pola wejściowego, które nie jest skoncentrowane i nieaktywne](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Nieaktywne pole wejściowe**

  Tło

  `SearchControl.Unfocused`

  Pierwszy plan (tekst)

  `SearchControl.Unfocused`

  Obramowanie

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Przycisk akcji wyszukiwania — nieskoncentrowany](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")

  **Przycisk akcji**

  Tło

  Brak

  Pierwszy plan (symbol wyszukiwania)

  `SearchControl.SearchGlyph`

  Pierwszy plan (symbol STOP)

  `SearchControl.StopGlyph`

  Pierwszy plan (czysty symbol)

  `SearchControl.ClearGlyph`

  Obramowanie

  Brak

  ![Przycisk wyszukiwania Porzuć&#45;w dół nieskoncentrowany](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.UnfocusedDropDownButton`

  Pierwszy plan (symbol)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Obramowanie

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto przycisk akcji wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Przycisk akcji**

  Tło

  `SearchControl.ActionButtonMouseDown`

  Pierwszy plan (symbol)

  `SearchControl.ActionButtonMouseDownGlyph`

  Obramowanie

  `SearchControl.ActionButtonMouseDownBorder`

  ![Naciśnięto przycisk wyszukiwania&#45;w dół](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.MouseDownDropDownButton`

  Pierwszy plan (symbol)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Obramowanie

  `SearchControl.MouseDownDropDownButtonBorder`

  **Wyróżniony (tylko tekst)**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Wyróżnij pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")

  **Pole wejściowe z wyróżnionym tekstem**

  Tło

  `SearchControl.Selection`

  Pierwszy plan (tekst)

  `SearchControl.FocusedBackground`

  Obramowanie

  Brak

  Separator

  `SearchControl.FocusedDropDownSeparator`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Pole wejściowe wyszukiwania wyłączone](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")

  **Pole wejściowe**

  Tło

  `SearchControl.Disabled`

  Pierwszy plan (tekst)

  `SearchControl.Disabled`

  Obramowanie

  `SearchControl.DisabledBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Przycisk akcji wyszukiwania jest wyłączony](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")

  **Przycisk akcji**

  Tło

  Brak

  Pierwszy plan (symbol)

  `SearchControl.ActionButtonDisabledGlyph`

  Obramowanie

  Brak

  ![Przycisk wyszukiwania Porzuć&#45;w dół wyłączone](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszy plan (symbol)

  `SearchControl.DisabledDownButtonGlyph`

  Obramowanie

  Brak

#### <a name="search-drop-down-lists"></a>Lista rozwijana wyszukiwania

Menu rozwijane pola wyszukiwania może być nieco bardziej skomplikowane niż inne menu rozwijane w programie Visual Studio. Sekcje "sugerowane wyszukiwania" i "Opcje wyszukiwania" mogą występować samodzielnie lub razem w menu, a każdy z nich jest kolorowy osobno. Linia oddziela również te dwie sekcje, gdy pojawiają się razem, a obramowanie otacza całe menu rozwijane.

![Wyszukaj Porzuć&#45;w dół Redline](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 — 124_SearchDropdownRedline")

Użyj...
- podczas tworzenia listy rozwijanej wyszukiwania niestandardowego.

- poprawne nazwy tokenów dla poprawnych składników listy.

  Nie używaj...
  - dla list rozwijanych, które są wyświetlane w innych kontekstach.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Domyślne (nie inne Stany)**

  Element

  Nazwa tokenu: Category. Color

  Obramowanie

  `SearchControl.PopupBorder`

  Separator

  `SearchControl.PopupSectionHeaderSeparator`

  W tle

  `Environment.DropShadowBackground`

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Wyszukaj sugerowane](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 — 125_SearchSuggested")

  **Sugerowane wyszukiwania**

  Tło

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `SearchControl.PopupItemText`

  ![Pole wyboru wyszukiwania](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")

  **Opcje wyszukiwania (pole wyboru)**

  ![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")

  **Opcje wyszukiwania (link)**

  Tło

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst pola wyboru)

  `SearchControl.PopupCheckboxText`

  Pierwszy plan (tekst linku)

  `SearchControl.PopupButtonText`

  Tło nagłówka

  `SearchControl.PopupSectionHeaderGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst nagłówka)

  `SearchControl.PopupSectionHeaderText`

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Wyszukiwanie sugerowane przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")

  **Sugerowane wyszukiwania**

  Tło

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst)

  `SearchControl.PopupMouseOverItemText`

  Obramowanie

  `SearchControl.PopupControlMouseOverBorder`

  ![Pole wyboru wyszukiwania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")

  **Sugerowane wyszukiwania (pole wyboru)**

  ![Opcje wyszukiwania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")

  **Opcje wyszukiwania**

  Tło

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst pola wyboru)

  `SearchControl.PopupCheckboxMouseDownText`

  Pierwszy plan (tekst linku)

  `SearchControl.PopupButtonMouseDownText`

  Obramowanie

  `SearchControl.PopupControlMouseOverBorder`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Zaciskaj sugerowane wyszukiwanie](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")

  **Sugerowane wyszukiwania (pole wyboru)**

  ![Naciśnięto opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")

  **Opcje wyszukiwania**

  Tło pola wyboru

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst pola wyboru)

  `SearchControl.PopupCheckboxMouseDownText`

  Tło łącza

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.

  Pierwszy plan (tekst linku)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Hyperlink
 Hiperłącze jest jednym formantem, który nie ma pary pierwszego planu/tła. We wszystkich przypadkach Użyj koloru hiperlinku pierwszego planu, który będzie wyświetlany prawidłowo na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu koloru dla kontrolki hiperłącze, zobaczysz domyślny kolor systemowy dla "naciśniętego", który będzie miał lampę błyskową czerwony. Jest to sygnał, że formant nie używa poprawnego tokenu koloru środowiska.

 ![Redline hiperlinków](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 — 133_HyperlinkRedline")

 Użyj...
gdy musisz utworzyć niestandardowe hiperłącze.

 Nie używaj...
dla wszystkich elementów, które nie są hiperłączem.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Domyślne hiperłącze](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 — 134_Hyperlink")

 Pierwszy plan (tekst)

 `Environment.PanelHyperlink`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Hiperłącze przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 — 135_HyperlinkHover")

 Pierwszy plan (tekst)

 `Environment.PanelHyperlinkHover`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto hiperłącze](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 — 136_HyperlinkPressed")

 Pierwszy plan (tekst)

 `Environment.PanelHyperlinkPressed`

 **Wyłączone**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Hiperłącze wyłączone](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 — 137_HyperlinkDisabled")

 Pierwszy plan (tekst)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Powiadomienie
 Infobars są używane do udostępniania więcej informacji na temat danego kontekstu i są zawsze wyświetlane w górnej części okna dokumentu lub okna narzędzi.

 ![Pasek informacyjny Redline](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 — 138_InfobarRedline")

 Użyj...
podczas tworzenia niestandardowej infobars.

 Nie używaj...
dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego.

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Powiadomienie](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 — 139_Infobar")

 **Powiadomienie**

 Tło

 `Environment.InfoBackground`

 Pierwszy plan (tekst)

 `Environment.InfoText`

 Obramowanie

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Pasek przewijania
 Paski przewijania są zgodne ze środowiskiem programu Visual Studio i nie będą potrzebne. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w paskach przewijania, tak aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.

 ![Pasek przewijania Redline](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 — 140_ScrollbarRedline")

 Użyj...
podczas tworzenia interfejsu użytkownika, który chcesz dopasować do pasków przewijania programu Visual Studio.

 Nie używaj... dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika paska przewijania.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pasek przewijania](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 — 141_Scrollbar")

 **Paski**

 Paski

 `Environment.ScrollBarBackground`

 Pierwszy plan (kciuk)

 `Environment.ScrollBarThumbBackground`

 ![Strzałka paska przewijania](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 — 142_ScrollbarArrow")

 **Strzałka przewijania**

 Tło

 `Environment.ScrollBarArrowBackground`

 Ustaw na taki sam kolor jak pasek przewijania.

 Pierwszy plan (symbol)

 `Environment.ScrollBarArrowGlyph`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pasek przewijania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 — 143_ScrollbarHover")

 **Paski**

 Paski

 `Environment.ScrollBarBackground`

 Pierwszy plan (kciuk)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Strzałka paska przewijania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")

 **Strzałka przewijania**

 Tło

 `Environment.ScrollBarArrowMouseOverBackground`

 Ustaw na taki sam kolor jak pasek przewijania.

 Pierwszy plan (symbol)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto pasek przewijania](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 — 145_ScrollbarPressed")

 **Paski**

 Paski

 `Environment.ScrollBarBackground`

 Pierwszy plan (kciuk)

 `Environment.ScrollBarThumbPressedBackground`

 ![Naciśnięto strzałkę paska przewijania](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")

 **Strzałka przewijania**

 Tło

 `Environment.ScrollBarArrowPressedBackground`

 Ustaw ten sam kolor jako pasek przewijania.

 Pierwszy plan (symbol)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="tree-view"></a><a name="BKMK_TreeView"></a> Widok drzewa

Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwera i Widok klasy, Implementuj hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w kategorii TreeView. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy z zagnieżdżonymi elementami podrzędnymi również mają glify wskazujące, czy element jest rozwinięty, czy zwinięty.

![Widok drzewa Redline](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 — 147_TreeViewRedline")

Użyj...
wszędzie tam, gdzie trzeba zaimplementować hierarchiczny widok organizacyjny.

Nie używaj...
- dla wszystkich elementów, które nie są podobne do widoku drzewa.

- w każdej kombinacji tła/pierwszego planu poza określoną.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Widok drzewa](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")

  Tło

  `TreeView.Background`

  Pierwszy plan (tekst)

  `TreeView.Background`

  Pierwszy plan (symbol)

  `TreeView.Glyph`

  Obramowanie

  Brak

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Widok drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")

  Tło

  `TreeView.Background`

  Pierwszy plan (tekst)

  `TreeView.Background`

  Pierwszy plan (symbol)

  `TreeView.GlyphMouseOver`

  Obramowanie

  Brak

  **Przeciągnij nad**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Widok drzewa DragOver](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")

  Tło

  `TreeView.DragOverItem`

  Pierwszy plan (tekst)

  `TreeView.DragOverItem`

  Pierwszy plan (symbol)

  `TreeView.DragOverItemGlyph`

  Obramowanie

  Brak

  **Wybrane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Widok drzewa z fokusem](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")

  **Ustawiono fokus**

  Tło

  `TreeView.SelectedItemActive`

  Pierwszy plan (tekst)

  `TreeView.SelectedItemActive`

  Pierwszy plan (symbol)

  `TreeView.SelectedItemActiveGlyph`

  Obramowanie

  `TreeView.FocusVisualBorder`

  ![Widok drzewa nieskoncentrowany](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")

  **Bez fokusu**

  Tło

  `TreeView.SelectedItemInactive`

  Pierwszy plan (tekst)

  `TreeView.SelectedItemInactive`

  Pierwszy plan (symbol)

  `TreeView.SelectedItemInactiveGlyph`

  Obramowanie

  Brak

  **Umieść kursor nad wybranym**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Widok drzewa skoncentrowany na aktywowaniu](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")

  **Ustawiono fokus**

  Tło

  `TreeView.SelectedItemActive`

  Pierwszy plan (tekst)

  `TreeView.SelectedItemActive`

  Pierwszy plan (symbol)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Obramowanie

  Brak`TreeView.FocusVisualBorder`

  ![Widok drzewa nieskoncentrowany po aktywowaniu](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")

  **Bez fokusu**

  Tło

  `TreeView.SelectedItemInactive`

  Pierwszy plan (tekst)

  `TreeView.SelectedItemInactive`

  Pierwszy plan (symbol)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Obramowanie

  Brak

### <a name="button-controls"></a>formanty przycisków
 ![Button — formant Redline](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 — 155_ButtonControlRedline")

 Użyj...
w przypadku przycisków w dokumencie, które chcesz zintegrować z motywami programu Visual Studio (jasnym, ciemniejszym, niebieskim lub duży kontrastm systemu).

 Nie używaj...
w przypadku przycisków, które będą wyświetlane na tle niestandardowym, które nie jest częścią motywu programu Visual Studio.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Przycisk](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 — 156_Button")

 Przycisk

 `CommonControls.Button`

 Obramowanie przycisku

 `CommonControls.ButtonBorder`

 **Wyłączone**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Przycisk wyłączony](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 — 157_ButtonDisabled")

 Przycisk

 `CommonControls.ButtonDisabled`

 Obramowanie przycisku

 `CommonControls.ButtonBorderDisabled`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Przycisk po aktywowaniu](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 — 158_ButtonHover")

 Przycisk

 `CommonControls.ButtonHover`

 Obramowanie przycisku

 `CommonControls.ButtonBorderHover`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto przycisk](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 — 159_ButtonPressed")

 Przycisk

 `CommonControls.ButtonPressed`

 Obramowanie przycisku

 `CommonControls.ButtonBorderPressed`

 **Ustawiono fokus**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Przycisk skoncentrowany](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 — 160_ButtonFocused")

 Przycisk

 `CommonControls.ButtonFocused`

 Obramowanie przycisku

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Kontrolki pola wyboru
 ![Pole wyboru Redline](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 — 161_CheckboxRedline")

 Użyj...
dla kontrolek pola wyboru zawartych w tym dokumencie.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie jest kontrolką pola wyboru.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")

 Tło

 `CommonControls.CheckBoxBackground`

 Obramowanie

 `CommonControls.CheckBoxBorder`

 Tekst

 `CommonControls.CheckBoxText`

 Symbol

 `CommonControls.CheckBoxGlyph`

 **Wyłączone**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pole wyboru wyłączone](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")

 Tło

 `CommonControls.CheckBoxBackgroundDisabled`

 Obramowanie

 `CommonControls.CheckBoxBorderDisabled`

 Tekst

 `CommonControls.CheckBoxTextDisabled`

 Symbol

 `CommonControls.CheckBoxGlyphDisabled`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pole wyboru przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")

 Tło

 `CommonControls.CheckBoxBackgroundHover`

 Obramowanie

 `CommonControls.CheckBoxBorderHover`

 Tekst

 `CommonControls.CheckBoxTextHover`

 Symbol

 `CommonControls.CheckBoxGlyphHover`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pole wyboru zostało naciśnięte](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")

 Tło

 `CommonControls.CheckBoxBackgroundPressed`

 Obramowanie

 `CommonControls.CheckBoxBorderPressed`

 Tekst

 `CommonControls.CheckBoxTextPressed`

 Symbol

 `CommonControls.CheckBoxGlyphPressed`

 **Ustawiono fokus**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Pole wyboru ukierunkowane](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")

 Tło

 `CommonControls.CheckBoxBackgroundFocused`

 Obramowanie

 `CommonControls.CheckBoxBorderFocused`

 Tekst

 `CommonControls.CheckBoxTextFocused`

 Symbol

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Kontrolki pola kombi/pola rozwijalnego

![Upuść&#45;w dół&#47;pole kombi Redline](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 — 167_DropDownComboBoxRedline")

Użyj...
dla listy rozwijanej i pól kombi, które są częścią dokumentu.

Nie używaj...
- dla każdego interfejsu użytkownika, który nie jest polem listy rozwijanej ani pola kombi.

- dla [listy rozwijanej](../../misc/shared-colors.md#BKMK_CommandDropDown) lub [pola kombi](../../misc/shared-colors.md#BKMK_CommandComboBox) na pasku poleceń.

  **Wartooć**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Pole kombi Porzuć&#45;w dół&#47;](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")

  Tło

  `CommonControls.ComboBoxBackground`

  Obramowanie

  `CommonControls.ComboBoxBorder`

  Tekst

  `CommonControls.ComboBoxText`

  Separator

  `CommonControls.ComboBoxSeparator`

  Symbol

  `CommonControls.ComboBoxGlyph`

  Tło symbolu

  `CommonControls.ComboBoxGlyphBackground`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![&#45;upuść&#47;pole kombi wyłączone](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")

  Tło

  `CommonControls.ComboBoxBackgroundDisabled`

  Obramowanie

  `CommonControls.ComboBoxBorderDisabled`

  Tekst

  `CommonControls.ComboBoxTextDisabled`

  Separator

  `CommonControls.ComboBoxSeparatorDisabled`

  Symbol

  `CommonControls.ComboBoxGlyphDisabled`

  Tło symbolu

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Aktywowane**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")

  Tło

  `CommonControls.ComboBoxBackgroundHover`

  Obramowanie

  `CommonControls.ComboBoxBorderHover`

  Tekst

  `CommonControls.ComboBoxTextHover`

  Separator

  `CommonControls.ComboBoxSeparatorHover`

  Symbol

  `CommonControls.ComboBoxGlyphHover`

  Tło symbolu

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Naciśnięte**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Naciśnięto pole kombi&#47;&#45;w dół](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")

  Tło

  `CommonControls.ComboBoxBackgroundPressed`

  Obramowanie

  `CommonControls.ComboBoxBorderPressed`

  Tekst

  `CommonControls.ComboBoxTextPressed`

  Separator

  `CommonControls.ComboBoxSeparatorPressed`

  Symbol

  `CommonControls.ComboBoxGlyphPressed`

  Tło symbolu

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Ustawiono fokus**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść&#45;w dół&#47;pole kombi](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")

  Tło

  `CommonControls.ComboBoxBackgroundFocused`

  Obramowanie

  `CommonControls.ComboBoxBorderFocused`

  Tekst

  `CommonControls.ComboBoxTextFocused`

  Separator

  `CommonControls.ComboBoxSeparatorFocused`

  Symbol

  `CommonControls.ComboBoxGlyphFocused`

  Tło symbolu

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Wprowadzanie tekstu**

  Składnik

  Element

  Nazwa tokenu: Category. Color

  ![Upuść&#45;w dół&#47;wprowadzanie tekstu w polu kombi](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 — 173_DropDownComboBoxTextInput")

  Wyróżnij

  `CommonControls.ComboBoxTextInputSelection`

  **Naciśnięto — widok elementu listy**

  ![Porzuć&#45;w dół&#47;widok listy pola kombi](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")

  Tło

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Obramowanie

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Tekst elementu

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Cień tła

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelarycznych (siatka)
 Kontrolki danych tabelarycznych, znane także jako kontrolki siatki, są typowymi kontrolkami dla programu Visual Studio, których można użyć do prezentowania dużych ilości danych w wielu kolumnach. Standardowe kontrolki danych tabelarycznych można znaleźć w wielu miejscach w programie Visual Studio: okno narzędzia Lista błędów, raporty IntelliTrace i widok sterty pamięci, między innymi. Należy zawsze używać standardowych formantów danych tabelarycznych. W niektórych rzadkich przypadkach może nie mieć dostępu do standardowych formantów danych tabelarycznych. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelarycznych w programie Visual Studio.

 ![Dane tabelaryczne &#40;formancie siatki&#41; Redline](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 — 197_TabularDataGridControlRedline")

 Użyj...
dla kontrolek tabelarycznych lub siatki.

 Nie używaj...
dla każdego interfejsu użytkownika, który nie jest kontrolką tabelaryczną lub siatką.

#### <a name="column-headers"></a>Nagłówki kolumn
 Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego symbolu zwykle używane, gdy siatka jest posortowana według tej kolumny.

 Stan

 Element

 Nazwa tokenu: Category. Color

 Domyślne

 Tło

 `Header.Default`

 Pierwszy plan (tekst)

 `Environment.CommandBarTextActive`

 Pierwszy plan (symbol)

 `Header.Glyph`

 Obramowanie

 `Header.SeparatorLine`

 Aktywowane

 Tło

 `Header.MouseOver`

 Pierwszy plan (tekst)

 `Environment.CommandBarTextHover`

 Pierwszy plan (symbol)

 `Header.MouseOverGlyph`

 Obramowanie

 `Header.SeparatorLine`

 Naciśnięte

 Tło

 `CommonControls.CheckBoxBackgroundPressed`

 Pierwszy plan (tekst)

 `CommonControls.CheckBoxBorderPressed`

 Pierwszy plan (symbol)

 `CommonControls.CheckBoxTextPressed`

 Obramowanie

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Wyświetl listę elementów
 Elementy widoku listy składają się z tła i zawartości. Zawartość może być tekstem, ikoną lub obu.

 Stan

 Element

 Nazwa tokenu: Category. Color

 Domyślne

 Tło

 Przezroczyste

 Pierwszy plan (tekst)

 `Environment.CommandBarTextActive`

 Obramowanie

 Brak

 Wybrane (aktywne)

 Tło

 `TreeView.SelectedItemActive`

 Pierwszy plan (tekst)

 `TreeView.SelectedItemActiveText`

 Obramowanie

 Brak

 Wybrane (nieaktywne)

 Tło

 `TreeView.SelectedItemInactive`

 Pierwszy plan (tekst)

 `TreeView.SelectedItemInactiveText`

 Obramowanie

 Brak

## <a name="manifest-designer"></a>Manifest Designer

Projektant manifestu został zaprojektowany jako sposób ułatwiający edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Chociaż nie jest dostępna żadna udostępniona architektura do użycia, może być odpowiednie dopasowanie układu projektu i kolorów na kartach Orientacja/Nawigacja i ogólna struktura. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Redline projektanta manifestu](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 — 175_ManifestDesignerRedline")

Użyj...
- dla projektantów, które są podobne do projektanta manifestu.

- zamiast używania wspólnych kontrolek kart w górnej części edytora w obszarze dokumentu.

Nie używaj...
- Jeśli masz więcej niż sześć kart.

- dla każdego interfejsu użytkownika, który nie jest uporządkowany jak projektant manifestu.

  Stan

  Składnik

  Element

  Nazwa tokenu: Category. Color

  Domyślne (wybrane)

  Tab

  Tło

  `ManifestDesigner.TabActive`

  Obramowanie

  Brak

  Okienko opisu

  Tło

  `ManifestDesigner.DescriptionPane`

  Strona zawartości

  Tło

  `ManifestDesigner.Background`

  Tekst pomocnika okna dialogowego

  `ManifestDesigner.WatermarkText`

  Ta nazwa tokenu nie jest zgodna z jej funkcją.

  Nie wybrano

  Tab

  Tło

  `ManifestDesigner.Tab.Inactive`

  Aktywowane

  Tab

  Tło

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Znakowanie
 Program Visual Studio obsługuje tagowanie, dzięki czemu użytkownik może zadeklarować słowa kluczowe do przeszukiwania do celów śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać Team Foundation Server (TFS) do tagowania elementów roboczych. Poniższe tabele zawierają nazwy kolorów zarówno dla samego tagu, jak i symboli "Close Icon", które pojawiają się w Stanach aktywowania i wybrane.

 ![Redline tagowania](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 — 176_TaggingRedline")

 Użyj...
dla interfejsu użytkownika obsługującego tagowanie.

 Nie używaj...
dla każdego innego typu interfejsu użytkownika.

### <a name="tag"></a>Tag
 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 — 177_Tag")

 **Wartooć**

 Tło

 `Tag.Background`

 Pierwszy plan (tekst)

 `Tag.Background`

 ![Oznacz przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 — 178_TagHover")

 **Aktywowane**

 Tło

 `Tag.HoverBackground`

 Pierwszy plan (tekst)

 `Tag.HoverBackgroundText`

 ![Naciśnięto tag](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 — 179_TagPressed")

 **Naciśnięte**

 Tło

 `Tag.PressedBackground`

 Pierwszy plan (tekst)

 `Tag.PressedBackgroundText`

 ![Wybrany tag](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 — 180_TagSelected")

 **Wybrane**

 Tło

 `Tag.SelectedBackground`

 Pierwszy plan (tekst)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Symbol (ikona zamknięcia)
 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Oznacz symbol &#40;symbolu&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 — 181_TagGlyph")

 **Default (tag domyślny)**

 Tło

 Brak

 Pierwszy plan (symbol)

 `Tag.TagHoverGlyph`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Oznacz symbol &#40;symbolu&#41; przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 — 182_TagGlyphHover")

 **Aktywuj (domyślny tag)**

 Tło

 `Tag.TagHoverGlyphHoverBackground`

 Pierwszy plan (symbol)

 `Tag.TagHoverGlyphHover`

 Obramowanie

 `Tag.TagHoverGlyphHoverBorder`

 **Naciśnięte**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Naciśnięto &#40;znacznika&#41; symbolu](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 — 183_TagGlyphPressed")

 **Naciśnięto (domyślny tag)**

 Tło

 `Tag.TagHoverGlyphPressedBackground`

 Pierwszy plan (symbol)

 `Tag.TagHoverGlyphPressed`

 Obramowanie

 `Tag.TagHoverGlyphPressedBorder`

 **Zaznaczony tag/domyślny symbol**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Wybrany tag](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 — 184_TagSelected")

 **Default (wybrany tag)**

 Tło

 Brak

 Pierwszy plan (symbol)

 `Tag.TagSelectedGlyph`

 **Zaznaczony znacznik/aktywowany symbol**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Znacznik wybrany przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 — 185_TagSelectedHover")

 **Aktywuj (zaznaczony tag)**

 Tło

 `Tag.TagSelectedGlyphHoverBackground`

 Pierwszy plan (symbol)

 `Tag.TagSelectedGlyphHover`

 Obramowanie

 `Tag.TagSelectedGlyphHoverBorder`

 **Naciśnięto zaznaczony znacznik/Symbol**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Wybrano tag](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 — 186_TagSelectedPressed")

 **Naciśnięto (tag wybrany)**

 Tło

 `Tag.TagSelectedGlyphPressedBackground`

 Pierwszy plan (symbol)

 `Tag.TagSelectedGlyphPressed`

 Obramowanie

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Powłoka

### <a name="background"></a>Tło

Tło środowiska składa się z dwóch warstw. Warstwa dolna to pełny kolor, który obejmuje całe środowisko IDE. Górna warstwa dopasowuje się do półki poleceń i między oknem narzędzia a ukrywanie kanałów po lewej i prawej stronie IDE. Począwszy od Visual Studio 2013, górny i dolny warstw tła są ustawione na ten sam kolor w jasnych i ciemnych motywach.

![Redline w tle powłoki](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 — 187_ShellBackgroundRedline")

Użyj...
dla miejsc, które chcesz dopasować do tła środowiska programu Visual Studio.

Nie używaj...
- jako wypełnienie miejsc, które nie są powierzchniami tła.

- jako tło, w którym chcesz umieścić elementy pierwszego planu.

  Składnik

  Element

  Nazwa tokenu: Category. Color

  Warstwa dolna

  Tło

  `Environment.EnvironmentBackground`

  Składnik

  Element

  Nazwa tokenu: Category. Color

  Warstwa najwyższej warstwy

  Tło

  *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Półka polecenia

Dwa zestawy nazw tokenów są używane na potrzeby tła półki poleceń: jeden zestaw dla miejsca, w którym znajduje się pasek menu, i jeden dla miejsca, w którym znajdują się paski poleceń. Pojedyncza grupa pasków poleceń ma własne wartości koloru tła, które zostały omówione bardziej szczegółowo w sekcji "pasek poleceń". Tekst paska menu i paska poleceń jest omówiony odpowiednio w sekcji menu i paska poleceń.

![Redline półki polecenia](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 — 188_CommandShelfRedline")

Użyj...
- w przypadku obszarów, w których są umieszczane menu lub paski narzędzi.

- z poprawną kombinacją nazw tokenów w tle/?

Nie używaj...
w przypadku obszarów, które nie są podobne do półki poleceń.

  Składnik

  Element

  Nazwa tokenu: Category. Color

  Pasek menu

  Tło

  *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Pasek poleceń

  Tło

  *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Przybornik
 Przybornik jest jednym z popularnych okien narzędzi, które są najczęściej używane w programie Visual Studio. Jest to zasadniczo formant drzewa z zastosowaniem specjalnego motywu i stylu.

 ![Redline przybornika](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 — 189_ToolboxRedline")

 Użyj...
podczas projektowania okna narzędzi, które chcesz zawsze zachować spójność z przybornikiem powłoki.

 Nie używaj...
dla wszystkich elementów, które nie są podobne do interfejsu użytkownika przybornika, lub jeśli nie masz pewności, czy interfejs użytkownika będzie miał problemy, jeśli zmienią się kolory przybornika powłoki.

 **Wartooć**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")

 **Węzeł nadrzędny**

 ![Węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")

 **Węzeł podrzędny**

 Tło

 `Environment.ToolboxContent`

 Nagłówki

 `Environment.ToolWindowBackground`

 Poszczególne elementy lub całe okno, jeśli nie ma dostępnych kontrolek

 Obramowanie

 Brak

 Pierwszy plan (symbol)

 `Environment.ToolboxContent`

 Pierwszy plan (tekst)

 `Environment.ToolboxContent`

 **Aktywowane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Węzeł podrzędny przybornika przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")

 **Umieść kursor w węźle podrzędnym**

 Tło

 `Environment.ToolboxContentMouseOver`

 Tylko pojedyncze elementy

 Obramowanie

 Brak

 Pierwszy plan (tekst)

 `Environment.ToolboxContentMouseOver`

 Tylko pojedyncze elementy

 **Wybrane**

 Składnik

 Element

 Nazwa tokenu: Category. Color

 ![Węzeł nadrzędny przybornika z fokusem](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")

 **Fokus węzła nadrzędnego**

 ![Węzeł podrzędny przybornika — fokus](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")

 **Priorytetowy węzeł podrzędny**

 Tło

 `TreeView.SelectedItemActive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Obramowanie

 `TreeView.FocusVisualBorder`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Pierwszy plan (symbol)

 `TreeView.SelectedItemActive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Pierwszy plan (tekst)

 `TreeView.SelectedItemActive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 ![Węzeł nadrzędny przybornika bez fokusu](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")

 **Węzeł nadrzędny nieskoncentrowany**

 ![Węzeł podrzędny przybornika z fokusem](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")

 **Węzeł podrzędny nieskoncentrowany**

 Tło

 `TreeView.SelectedItemInactive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Obramowanie

 Brak

 Pierwszy plan (symbol)

 `TreeView.SelectedItemInactive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Pierwszy plan (tekst)

 `TreeView.SelectedItemInactive`

 Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)
