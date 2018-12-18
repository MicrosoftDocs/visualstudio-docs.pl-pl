---
title: Udostępnione kolory
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03cfcf2b4ea2b3a0b4773e9c2632c84091819f45
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063226"
---
# <a name="shared-colors-for-visual-studio"></a>Udostępnione kolory dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas projektowania interfejsu użytkownika, który używa wspólnych elementów powłoki programu Visual Studio lub chcesz, aby Twoje element interfejsu, aby były zgodne z podobne funkcje, umożliwia już istniejącymi nazwami tokenu w plikach definicji pakietu wybierz i przypisania kolorów. Gwarantuje to, że Twój interfejs użytkownika pozostaje zgodny z całego środowiska programu Visual Studio i że jest aktualizowana automatycznie po motywy są dodawane lub aktualizowane.

 W tym artykule opisano typowe elementy interfejsu użytkownika i token nazwy które używają, które można odwoływać się podczas kompilowania z podobnym interfejsem użytkownika. Dla określonych informacji dotyczących tych kolorów tokeny dostępu, zobacz [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

 Upewnij się, że prawidłowo używać nazw tokenu:

-   **Użyj tokenu nazw na podstawie funkcji, nie na samego koloru.** Typowe udostępnione kolory są skojarzone z elementami określonego interfejsu i są przeznaczone wyłącznie do użytku takie same lub podobne funkcje. Na przykład nie używaj ponownie plików kolor po naciśnięciu kombi dla Animacja postępu rotowania tylko dlatego, jak kolor. Funkcje pola kombi i animacji są różne, a Jeśli kolor skojarzony z zmiany pola kombi, mogą już być odpowiedni kolor w odniesieniu do danego elementu animacji. Spójnego używania koloru pomaga w poznaniu użytkowników i uniknąć pomyłek.

-   **Użyj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które są przeznaczone do użycia z tekstem będzie miał kolor tekstu. Nie używaj kolorów tekstu innego niż został określony dla w tle. Jeśli nie jest kolorem skojarzony tekst, nie należy używać tego kolor tła dla dowolnego powierzchni, w którym oczekujesz, że do wyświetlania tekstu. Inne kombinacje kolorów tekstu i tła może spowodować w interfejsie nie można go odczytać.

-   **Użyj kolorów kontrolki, które są odpowiednie dla ich lokalizacji.** W określonych stanach niektóre formanty programu Visual Studio nie mają osobne obramowania i kolory tła. Zamiast tego przejmą ich te kolory z powierzchni spodem. Upewnij się, zawsze używaj tokenów nazwy, które są odpowiednie dla lokalizacji, w którym umieszcza się kontrolka.

> [!IMPORTANT]
>  Nie używaj tokenów w kategorii "Stronę startową" lub "Jabłecznik."

## <a name="command-structures"></a>Polecenie struktury

###  <a name="BKMK_CommandMenus"></a> Menu
 Menu może wystąpić w kilku miejscach w programie Visual Studio: główny pasek menu, osadzony w dokumencie lub narzędzia systemu windows lub kliknij prawym przyciskiem myszy w różnych miejscach w całej IDE. Implementacje menu skojarzone z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiednich elementów. Zawsze należy używać implementacji standardowe menu oferowanych przez środowisko Visual Studio. Jednak w sporadycznych przypadkach możesz utracić dostęp do standardowego menu programu Visual Studio. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika są spójne z innych menu w programie Visual Studio.

 ![Menu poprawek](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")

 Użyj...
 -   Kiedy należy utworzyć niestandardowe menu.

- Jeśli masz nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.

  Nie używaj...
  kolor tła samodzielnie. Zawsze użyj kombinacji tła/pierwszego planu, jak określono.

#### <a name="menu-title"></a>Tytuł menu
 Tytuły menu składają się z tła, obramowania i tekst tytułu, a także opcjonalnie symbol, zwykle w przypadku, gdy menu znajduje się na pasku poleceń.

 ![Tytuł menu poprawek](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")

 Użyj...
zawsze, gdy tworzysz tytuł menu niestandardowe.

 Nie używaj...
 -   dla wszystkich elementów, które nie chcesz zawsze odpowiada tytuł menu.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Domyślny tytuł menu](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")

  **Tytuł menu**

  Tło

  Brak

  Pierwszego planu (tekst)

  `Environment.CommandBarTextActive`

  ![Tytuł menu z domyślną symbol](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")

  **Tytuł menu z glifów**

  Pierwszego planu (symbol)

  `Environment.CommandBarMenuGlyph`

  Obramowanie

  Brak

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Tytuł menu, po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")

  **Tytuł menu**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextHover`

  ![Tytuł menu z symbol po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")

  **Tytuł menu z glifów**

  Pierwszego planu (symbol)

  `Environment.CommandBarMenuMouseOverGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Tytuł menu naciśnięty](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")

  **Tytuł menu**

  Tło

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextActive`

  ![Tytuł menu z naciśnięto symbol](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")

  **Tytuł menu z glifów**

  Pierwszego planu (symbol)

  `Environment.CommandBarMenuMouseDownGlyph`

  Obramowanie

  `Environment.CommandBarMenuBorder`

  Tylko po lewej stronie, górnej i prawej stronie.

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Tytuł menu przy użyciu symbolu wyłączone](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")

  **Tytuł menu z glifów**

  Tło

  Brak

  Pierwszego planu (tekst)

  `Environment.CommandBarTextInactive`

  Pierwszego planu (symbol)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

#### <a name="menu"></a>Menu
 Element menu poszczególnych składa się z tekst menu i opcjonalnej ikony, pole wyboru lub symbol podmenu. Jego tekstu i tła kolorów zmiana po najechaniu wskaźnikiem. Token ten kolor to para tła/pierwszego planu.

 ![Elementy menu poprawek](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")

 Użyj...
Aby uzyskać wszystkie listy rozwijanej, który jest uruchamiany z paska menu i paska poleceń.

 Nie używaj...
 -   Aby uzyskać wszystkie listy rozwijanej, która występuje w kontekście innego.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Domyślne menu](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")

  **Menu**

  Tło

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextActive`

  Pierwszego planu (podmenu symbol)

  `Environment.CommandBarMenuSubmenuGlyph`

  Obramowanie

  `Environment.CommandBarMenuBorder`

  Tło kanału ikony

  `Environment.CommandBarMenuIconBackground`

  Separator

  `Environment.CommandBarMenuSeparator`

  W tle

  `Environment.DropShadowBackground`

  ![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")

  **Zaznaczone**

  Znacznik wyboru

  `Environment.CommandBarCheckBox`

  Znacznik wyboru tła

  `Environment.CommandBarSelectedIcon`

  ![Wybrane menu](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")

  **Wybrane**

  Tło ikony

  `Environment.CommandBarSelected`

  Ikona obramowania

  `Environment.CommandBarSelectedBorder`

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Po wskazaniu wskaźnikiem menu](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")

  **Element menu**

  Tło

  `Environment.CommandBarMenuItemMouseOver`

  Pierwszego planu (tekst)

  `Environment.CommandBarMenuItemMouseOver`

  Pierwszego planu (podmenu symbol)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Po wskazaniu wskaźnikiem menu zaznaczone](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")

  **Zaznaczone**

  Znacznik wyboru

  `Environment.CommandBarCheckBoxMouseOver`

  Znacznik wyboru tła

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Po wskazaniu wskaźnikiem menu wybrane](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")

  **Wybrane**

  Tło ikony

  `Environment.CommandBarHoverOverSelected`

  Ikona obramowania

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")

  Element menu

  Pierwszego planu (tekst)

  `Environment.CommandBarTextInactive`

  Pierwszego planu (podmenu symbol)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Zaznaczone wyłączone menu](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")

  Zaznaczone

  Znacznik wyboru

  `Environment.CommandBarCheckBoxDisabled`

  Znacznik wyboru tła

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Pasek poleceń
 Na pasku poleceń może znajdować się w wielu miejscach w programie Visual Studio IDE, głównie półki polecenia i narzędzia embedded na platformie lub okna dokumentu.

 Ogólnie rzecz biorąc należy zawsze używać implementacja paska poleceń standardowych, które są dostarczane przez środowisko Visual Studio. Przy użyciu standardowego mechanizmu zapewnia, są poprawnie wyświetlane wszystkie szczegóły visual i że elementów interaktywnych będą zachowywać się spójne z innymi formantami paska poleceń programu Visual Studio. Jednak jeśli jest to niezbędne do tworzenia własnego paska poleceń, upewnij się, że poprawnie za pomocą następujących nazw tokenu stylu.

 ![Pasek poleceń poprawek](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")

 ![Przycisk przepełnienie poprawek](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")

 Użyj...
w miejscach osadzone polecenia pasek ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio.

 Nie używaj...
 -   dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.

-   Aby uzyskać inne niż te, dla których token nazwy zostały określone składniki paska poleceń.

#### <a name="command-bar-group"></a>Grupy pasek poleceń
 Grupy pasek poleceń zawiera zestaw powiązanych formantów paska poleceń i może zawierać dowolną liczbę przyciski, Podziel przyciski, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów jest regulowane przez oddzielne nazwy tokenu i są omówione oddzielnie w innym miejscu, w tym przewodniku. Linii separatora jest używane do dzielenia grupy pasek poleceń do powiązanych podgrupy.

 ![Grupa paska poleceń poprawek](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")

 Użyj...
w miejscach osadzone polecenia pasek ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio.

 Nie używaj...
 -   dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.

- Aby uzyskać inne niż te, dla których token nazwy zostały określone składniki paska poleceń.

  **Domyślne** (nie innych Państw)

  Element

  Nazwa tokenu: Category.color

  Tło

  `Environment.CommandBarGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Obramowanie

  `Environment.CommandBarToolBarBorder`

  Przeciągnij uchwyt

  `Environment.CommandBarDragHandle`

  Separator

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Ikony poleceń
 ![Ikona polecenia poprawek](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")

 ![Ikona polecenia poprawek](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")

 Użyj...
dla przycisków, które zostaną umieszczone na pasku poleceń.

 Nie używaj...
 -   dla formantów, które mają własne nazwy tokenu.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Polecenie domyślną ikonę](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")

  **Default**

  Tło

  N/d (dziedziczy tło paska poleceń)

  Pierwszego planu (tekst)

  `Environment.CommandBarTextActive`

  Obramowanie

  Brak

  ![Polecenie ikonę domyślnie wybrana](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")

  **Wybrane**

  Tło

  `Environment.CommandBarSelected`

  Pierwszego planu (tekst)

  `Environment.CommandBarTextSelected`

  Obramowanie

  `Environment.CommandBarSelectedBorder`

  **Aktywowanie i fokus klawiatury**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Polecenie ikony po wskazaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")

  **Standardowa po najechaniu wskaźnikiem**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextHover`

  Obramowanie

  `Environment.CommandBarBorder`

  ![Polecenie ikony po wskazaniu wskaźnikiem, wybrane](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")

  **Wybrane po najechaniu wskaźnikiem**

  Tło

  `Environment.CommandBarHoverOverSelected`

  Pierwszego planu (tekst)

  `Environment.CommandBarTextHoverOverSelected`

  Obramowanie

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Ikona polecenia naciśnięty](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")

  **Ikona po naciśnięciu polecenia**

  Tło

  `Environment.CommandBarMouseDownBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextMouseDown`

  Obramowanie

  `Environment.CommandBarBorder`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Ikona polecenia wyłączone](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")

  **Ikona polecenia wyłączenia**

  Tło

  N/d (dziedziczy tło paska poleceń)

  Pierwszego planu (tekst)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

####  <a name="BKMK_CommandComboBox"></a> Pole kombi

> [!IMPORTANT]
>  Pola kombi są podobne do list rozwijanych, ale zawierają region tekst do edycji. Jeśli z listy rozwijanej nie obejmuje regionu tekst do edycji, należy użyć tokenów kolor, znajdującym się [listy rozwijanej](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

 ![Pole kombi poprawek](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")

 Użyj...
 -   Podczas tworzenia pola kombi niestandardowych.

- Podczas tworzenia formantu paska poleceń, która jest podobna do pola kombi.

  Nie używaj...
  -   dla wszystkich elementów, nie należy zawsze dopasować polecenia paska.

- Jeśli masz dostęp do pola kombi ze stylem.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Pole wejściowe pola kombi](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")

  **Pola wejściowego**

  Tło

  `Environment.ComboBoxBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxText`

  Obramowanie

  `Environment.ComboBoxBorder`

  Separator

  Nie separatora

  ![Listy pola kombi&#45;naciśnięty przycisk](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")

  **Przycisk listy rozwijanej**

  Tło

  N/d (dziedziczy)

  Pierwszego planu (symbol)

  `Environment.ComboBoxGlyph`

  ![Pole kombi&#47;porzucić&#45;listy rozwijanej](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")

  **Listy rozwijanej**

  Tło

  `Environment.ComboBoxPopupBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.ComboBoxItemText`

  Obramowanie

  `Environment.ComboBoxPopupBorder`

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Pole kombi pola wejściowego po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")

  **Pola wejściowego**

  Tło

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.ComboBoxMouseOverText`

  Obramowanie

  `Environment.ComboBoxMouseOverBorder`

  Separator

  `Environment.ComboBoxMouseOverSeparator`

  ![Pole kombi&#47;porzucić&#45;przycisku po umieszczeniu na](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxButtonMouseOverBackground`

  Pierwszego planu (symbol)

  `Environment.ComboBoxMouseOverGlyph`

  ![Pole kombi&#47;porzucić&#45;listy po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")

  **Listy rozwijanej**

  W tle (element Menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxItemMouseOverText`

  Obramowanie (element Menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Fokus**

  Składnik

  Element

  Nazwa tokenu: Color.category

  ![Pole wejściowe pola kombi skupia się](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")

  **Pola wejściowego**

  Tło

  `Environment.ComboBoxFocusedBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxFocusedText`

  Obramowanie

  `Environment.ComboBoxFocusedBorder`

  Separator

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Pole kombi&#47;porzucić&#45;naciśnięty przycisk skupia się](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxFocusedButtonBackground`

  Pierwszego planu (symbol)

  `Environment.ComboBoxFocusedGlyph`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Color.category

  ![Pole wejściowe pola kombi naciśnięty](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")

  **Pola wejściowego**

  Tło

  `Environment.ComboBoxMouseDownBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxMouseDownText`

  Obramowanie

  `Environment.ComboBoxMouseDownBorder`

  Separator

  `Environment.ComboBoxMouseDownSeparator`

  ![Pole kombi&#47;porzucić&#45;dół wciśnięcie przycisku](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.ComboBoxButtonMouseDownBackground`

  Pierwszego planu (symbol)

  `Environment.ComboBoxMouseDownGlyph`

  **Wyłączone**

  ![Pole wejściowe pola kombi wyłączone](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")

  **Pola wejściowego**

  Tło

  `Environment.ComboBoxDisabledBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxDisabledText`

  Obramowanie

  `Environment.ComboBoxDisabledBorder`

  Separator

  Nie separatora

  ![Pole kombi&#47;porzucić&#45;naciśnięty przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszego planu (symbol)

  `Environment.ComboBoxDisabledGlyph`

####  <a name="BKMK_CommandDropDown"></a> Lista rozwijana

> [!IMPORTANT]
>  Listy rozwijane są podobne do pola kombi, ale brak regionów tekst do edycji. Jeśli z listy rozwijanej zawiera tekst do edycji regionu, należy użyć tokenów kolor, znajdującym się [pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

 ![Upuść&#45;poprawek w dół](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")

 Użyj...
Podczas tworzenia kontrolki niestandardowej listy rozwijanej.

 Nie używaj...
 -   dla wszystkich elementów, który nie jest podobna do listy rozwijanej.

- dla pola kombi lub przyciski dzielone.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;w dół do pola wyboru](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")

  **Pole wyboru**

  Tło

  `Environment.DropDownBackground`

  Pierwszego planu (tekst)

  `DropDownText`

  Obramowanie

  `DropDownBorder`

  Separator

  Nie separatora

  ![Upuść&#45;naciśnięty przycisk](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszego planu (symbol)

  `Environment.DropDownGlyph`

  ![Upuść&#45;listy rozwijanej](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")

  **Listy rozwijanej**

  Tło

  `Environment.DropDownPopupBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.ComboBoxItemText`

  Obramowanie

  `Environment.DropDownPopupBorder`

  W tle

  `Environment.DropShadowBackground`

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;w dół do pola wyboru po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")

  **Pole wyboru**

  Tło

  `Environment.DropDownMouseOverBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.DropDownMouseOverText`

  Obramowanie

  `Environment.DropDownMouseOverBorder`

  Separator

  `Environment.DropDownButtonMouseOverSeparator`

  ![Upuść&#45;przycisku po umieszczeniu na](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.DropDownButtonMouseOverBackground`

  Pierwszego planu (symbol)

  `Environment.DropDownMouseOverGlyph`

  ![Upuść&#45;listy po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")

  **Listy rozwijanej**

  W tle (element Menu)

  `Environment.ComboBoxItemMouseOverBackground`

  Pierwszego planu (tekst)

  `Environment.ComboBoxItemMouseOverText`

  Obramowanie (element Menu)

  `Environment.ComboBoxItemMouseOverBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;w dół do pola wyboru naciśnięty](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")

  **Pole wyboru**

  Tło

  `Environment.DropDownMouseDownBackground`

  Pierwszego planu (tekst)

  `Environment.DropDownMouseDownText`

  Obramowanie

  `Environment.DropDownMouseDownBorder`

  Separator

  `Environment.DropDownButtonMouseDownSeparator`

  ![Upuść&#45;dół wciśnięcie przycisku](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `Environment.DropDownButtonMouseDownBackground`

  Pierwszego planu (symbol)

  `Environment.DropDownMouseDownGlyph`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;w dół do pola wyboru wyłączone](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")

  Tło

  `Environment.DropDownDisabledBackground`

  Pierwszego planu (tekst)

  `Environment.DropDownDisabledText`

  Obramowanie

  `Environment.DropDownDisabledBorder`

  Separator

  Nie separatora

  ![Upuść&#45;naciśnięty przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")

  Tło

  Brak

  Pierwszego planu (symbol)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Przycisk podziału
 Przyciski dzielone udostępniać wiele tokenów nazwy inne kontrolki paska poleceń, takich jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne działania i przycisk listy rozwijanej token nazwy są powtarzane tutaj dla wygody. Listy rozwijane w przycisku podziału stanowią implementacje paska poleceń [menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

 ![Przycisk podziału poprawek](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")

 Użyj...
Kiedy tworzysz przycisku podziału niestandardowych.

 Nie używaj...
 -   dla innych rodzajów przycisków.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Przycisk podziału](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")

  **Przycisk podziału (ustawienie domyślne)**

  Tło

  Brak

  Pierwszego planu (tekst)

  `Environment.CommandBarTextActive`

  Pierwszego planu (symbol)

  `Environment.CommandBarSplitButtonGlyph`

  Obramowanie

  Brak

  Separator

  Brak

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Przycisk podziału po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")

  **Przycisk podziału (po najechaniu wskaźnikiem)**

  Tło

  `Environment.CommandBarMouseOverBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextHover`

  Pierwszego planu (symbol)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  Separator

  `Environment.CommandBarSplitButtonSeparator`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Wciśnięcie przycisku podziału](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")

  **Przycisk podziału (po naciśnięciu)**

  Tło

  `Environment.CommandBarMouseDownBackgroundBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `Environment.CommandBarTextMouseDown`

  Pierwszego planu (symbol)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Obramowanie

  `Environment.CommandBarBorder`

  Separator

  Brak

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Przycisk podziału wyłączone](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")

  **Przycisk podziału (wyłączony)**

  Tło

  Brak

  Pierwszego planu (tekst)

  `Environment.ComboBoxItemTextInactive`

  Pierwszego planu (symbol)

  `Environment.CommandBarTextInactive`

  Obramowanie

  Brak

  Separator

  Brak

#### <a name="more-options-and-overflow-buttons"></a>Przyciski "Overflow ma wartość" i więcej opcji
 Przycisk "Więcej opcji" jest używany, gdy grupy pasek poleceń jest możliwe do dostosowania, albo dodając lub usuwając przyciski paska poleceń powiązanych. Przycisk "Overflow" jest wyświetlany, gdy pasek poleceń zostały obcięte ze względu na Brak miejsca w poziomie, a po kliknięciu pokazuje menu zawierające przyciski paska poleceń nie może być wyświetlany. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw tokenów nazwy.

 ![Więcej opcji poprawek](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")

 Użyj...
niestandardowe "więcej opcji" lub "Overflow" przycisków.

 Nie używaj...
dla przycisków, które nie mają podobne funkcje do bardziej opcji lub przycisku "Overflow".

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Więcej opcji](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")

 **Więcej opcji**

 ![Przycisk przepełnienie](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")

 **przepełnienia**

 Tło

 `Environment.CommandBarOptionsBackground`

 Pierwszego planu (symbol)

 `Environment.CommandBarOptionsGlyph`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Więcej opcji po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")

 **Więcej opcji**

 ![Overflow po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")

 **przepełnienia**

 Tło

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (symbol)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Więcej opcji naciśnięty](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")

 **Więcej opcji**

 ![Przepełnienie naciśnięty](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")

 **przepełnienia**

 Tło

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (symbol)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Okna dokumentów
 Nie ma potrzeby replikowanie okna dokumentu, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolory używane w oknach dokumentów, tak, aby Twój interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

 Korzystając z tokenów kolor okna dokumentu, należy uważać, aby używać ich tylko dla podobnych elementów oraz zawsze par. Jeśli nie zrobisz, będziesz mieć nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frame"></a>Ramka okna dokumentu
 Okna dokumentów może być zadokowane w IDE lub zmiennoprzecinkową jako oddzielne okno. Gdy okno dokumentu jest liczb zmiennoprzecinkowych poza IDE, ona nadal znajduje się w źródle dokumentu i ma tła, obramowania, tekstu i kolorów karty, które są takie same jak, gdy jest on częścią środowiska IDE. Jednak dokumentu znajduje się wewnątrz ramki, który ma swój własny tło obramowania i kolorów tekstu. Gdy okna narzędziowe są zadokowane w źródle dokumentu, dziedziczą zachowanie i koloru dla swoich kart z nazwy tokenu okien dokumentu.

 ![Okno zadokowane dokumentu poprawek](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")

 **Okno zadokowane dokumentu**

 ![Przestawne okna dokumentu poprawek](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")

 **Przestawne okna dokumentu.**

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okno dokumentu.

 Nie używaj...
dla dowolnego interfejsu użytkownika, których nie chcesz automatycznie umożliwia zmianę powłoki ma aktualizacji motywu.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 Dokument: zadokowany lub liczb zmiennoprzecinkowych

 Tło

 Zależy od typu dokumentu

 Pierwszego planu (tekst)

 Zależy od typu dokumentu

 Obramowanie

 `Environment.ToolWindowBorder`

 ![Ramka skupia się](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")

 **Ramka: Opływanie, fokus**

 Tło

 `Environment.ToolWindowFloatingFrame`

 Pierwszego planu (tekst)

 `Environment.ToolWindowFloatingFrame`

 Pierwszego planu (symbol)

 `Environment.RaftedWindowButtonActiveGlyph`

 Obramowanie

 `Environment.MainWindowActiveDefaultBorder`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonActiveBorder`

 Ustaw przezroczyste

 ![Po przeniesieniu fokusu ramki](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")

 **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**

 Tło

 `Environment.ToolWindowFloatingFrameInactive`

 Pierwszego planu (tekst)

 `Environment.ToolWindowFloatingFrameInactive`

 Pierwszego planu (symbol)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Obramowanie

 `Environment.MainWindowInactiveBorder`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonInactiveBorder`

 Ustaw przezroczyste

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Ramka koncentruje się na przesunięciu](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")

 **Ramka: Opływanie, fokus**

 Tło (symbol)

 `Environment.RaftedWindowButtonHoverActive`

 Pierwszego planu (symbol)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Po przeniesieniu fokusu po najechaniu wskaźnikiem ramki](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")

 **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**

 Tło (symbol)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Pierwszego planu (symbol)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Ramka skupia się po naciśnięciu](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")

 **Ramka: Opływanie, fokus**

 Tło (symbol)

 `Environment.RaftedWindowButtonDown`

 Pierwszego planu (symbol)

 `Environment.RaftedWindowButtonDownGlyph`

 Obramowanie (symbol)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Karty dokumentów
 Karty dokumentów znajdują się w kanale kartę, aby wskazać, które dokumenty są obecnie otwarte, oraz które z nich jest bieżąca wybrane lub aktywnego dokumentu. Okna narzędzi również może być zadokowane w kanale kartę dokumentu, jeśli użytkownik przełączy je ma. W takiej sytuacji używają takich samych kolorów karty jako okna dokumentu. Czy tworzenie interfejsu użytkownika chcesz zawsze odpowiada kolory okna dokumentu (w tym aktualizacje motywu lub jeśli są zainstalowane nowe motywy), a następnie odwoływać się do tych tokenów kolorów.

 ![Karty dokumentów poprawek](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować karty dokumentów i automatycznie pobierał kompozycję aktualizacje lub nowe kolory motywu.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, gdy powłoka ma motyw aktualizacji.

#### <a name="open-document-tabs"></a>Otwórz dokument karty
 Każdy otwarty dokument ma kartę w kanale kartę dokumentu, który wyświetla jego nazwę. Dokumenty można albo wybrać lub otworzyć w tle, a ich karty odzwierciedlać te stany:

- Wybrane karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie dobrze. Kartę wybraną ma obramowanie dokumentu, które dobrze rozszerza między górną krawędzią dokumentu.

- Karty w tle są żadnych kart dokumentu, które nie są aktualnie wybrana karta. Po kliknięciu stają się wybranej karty i uzyskania wszystkich obramowania, tekstu i tła kolorów z tymi nazwami tokenu.

  ![Karta otwartym dokumencie poprawek](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")

  Użyj...
  Podczas tworzenia karty niestandardowego dokumentu.

  Nie używaj...
  -   dla karty tymczasowe (wersja zapoznawcza).

- dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

#### <a name="selected-tab"></a>Wybranej karty
 **Fokus**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Kartę wybraną skupia się](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")

 **Karcie wybrany dokument skupia się**

 Tło

 `Environment.FileTabSelectedGradientTop`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.FileTabSelectedText`

 Obramowanie

 `Environment.FileTabSelectedBorder`

 Ustaw kolor tła.

 Obramowanie dokumentu

 `Environment.FileTabDocumentBorderBackground`

 **Po przeniesieniu fokusu**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Po przeniesieniu fokusu kartę wybraną](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")

 **Karta wybrany dokument, po przeniesieniu fokusu**

 Tło

 `Environment.FileTabInactiveGradientTop`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.FileTabInactiveText`

 Obramowanie

 `Environment.FileTabInactiveBorder`

 Ustaw kolor tła.

 Obramowanie dokumentu

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Karta tła
 **Default**

 ![Karta tła](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")

 **Domyślna karta tła**

 Tło

 `Environment.FileTabBackground`

 Pierwszego planu (tekst)

 `Environment.FileTabText`

 Obramowanie

 `Environment.FileTabBorder`

 Ustaw kolor tła.

 **Po wskazaniu wskaźnikiem**

 ![Karta tło po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")

 **Karta tło po najechaniu wskaźnikiem**

 Tło

 `Environment.FileTabHotGradientTop`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.FileTabHotText`

 Obramowanie

 `Environment.FileTabHotBorder`

 Ustaw kolor tła.

#### <a name="preview-tab"></a>Karta (wersja zapoznawcza)
 Karta (wersja zapoznawcza) pojawia się po prawej stronie kanału kartę dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksploratora rozwiązań. On działa w wersji zapoznawczej dokumentu, a także zapewnia możliwość nie zamykaj dokumentu po lewej stronie kanału karty dokumentu. Otwórz kartę tylko jeden (wersja zapoznawcza) może być otwarty naraz. Podgląd karty mają zarówno w tle i wybranych stanów, takie jak karty i może być ukierunkowane lub po przeniesieniu fokusu w ich stanie aktywnym.

 ![Karta Podgląd poprawek](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")

 Użyj...
dowolne miejsce tworzenia tymczasowych (wersja zapoznawcza) i ma pewien element, aby dopasować bieżący kolor karcie podglądu.

 Nie używaj...
 -   dla każdego rodzaju dokumentu lub kartę, która nie jest tymczasowe (wersja zapoznawcza).

- dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

  **Karta podgląd wybranych: fokus**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Karta (wersja zapoznawcza) koncentruje się](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")

  **Karta specjalistyczny (wersja zapoznawcza)**

  Tło

  `Environment.FileTabProvisionalSelectedActive`

  Pierwszego planu (tekst)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Ustaw kolor tła.

  Obramowanie dokumentu

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Karta podgląd wybranych: po przeniesieniu fokusu**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Karta (wersja zapoznawcza) po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")

  **Karta po przeniesieniu fokusu (wersja zapoznawcza)**

  Tło

  `Environment.FileTabProvisionalSelectedInactive`

  Pierwszego planu (tekst)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Obramowanie dokumentu

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Tło karcie podglądu: domyślna**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Karta tła w wersji zapoznawczej](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")

  **W wersji zapoznawczej zarządzania tab tab tła**

  Tło

  `Environment.FileTabProvisionalInactive`

  Pierwszego planu (tekst)

  `Environment.FileTabProvisionalInactiveForeground`

  Obramowanie

  `Environment.FileTabProvisionalInactiveBorder`

  Ustaw kolor tła.

  **Tło karcie podglądu: Zatrzymaj wskaźnik myszy**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Karta tła (wersja zapoznawcza) po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")

  **W wersji zapoznawczej zarządzania tab tab tło po najechaniu wskaźnikiem**

  Tło

  `Environment.FileTabProvisionalHover`

  Pierwszego planu (tekst)

  `Environment.FileTabProvisionalHoverForeground`

  Obramowanie

  `Environment.FileTabProvisionalHoverBorder`

  Ustaw kolor tła.

#### <a name="document-overflow-button"></a>Przycisk przepełnienie dokument
 Przycisk przepełnienie dokument jest obecny, jeśli istnieje jeden lub więcej dokumentów otworzyć, niezależnie od tego, czy brak miejsca w pionie w bieżącej konfiguracji, aby dopasować wszystkich kartach dokumentów. Menu rozwijanego przepełnienie dokumentu, które są kontrolowane przez **CommandBarMenu** kolory (zobacz [menu](../../misc/shared-colors.md#BKMK_CommandMenus)), zostanie wyświetlona lista wszystkich otwartych dokumentach widoczna i ukryta, i zmienia się glif przepełnienia w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale kartę.

 ![Przepełnienie poprawek](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")

 Użyj...
Podczas tworzenia niestandardowego dokumentu przycisku przepełnienia.

 Nie używaj...
 -   dla interfejsu użytkownika, który nie jest podobne do przycisku przepełnienia.

- dla przycisków przepełnienie paska poleceń.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")

  **Przycisk przepełnienie dokument**

  Tło

  `Environment.DocWellOverflowButtonBackground`

  Pierwszego planu (symbol)

  `Environment.DocWellOverflowButtonGlyph`

  Obramowanie

  Brak

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Overflow po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")

  **Przycisk przepełnienie dokument po najechaniu wskaźnikiem**

  Tło

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Pierwszego planu (symbol)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Obramowanie

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Przepełnienie naciśnięty](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")

  **Naciśnięty przycisk przepełnienie dokument**

  Tło

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Pierwszego planu (symbol)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Obramowanie

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Okna narzędzi
 Nie ma potrzeby replikowanie okien narzędziowych, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolorów używanych w oknach narzędzi, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

 ![Okno narzędzia poprawek](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

### <a name="tool-window-frame"></a>Ramki okna narzędzi
 Okna narzędzi w programie Visual Studio są używane w przypadku wielu różnych zadań, a może znajdować się w jednej z kilku różnych stanów. Jeśli okno narzędzi jest otwarty, można przypisać do dowolnego z czterech bokach obszar dokumentu. Okna narzędzi można również liczb zmiennoprzecinkowych poza IDE, co pozwala na można zmieniać pozycji w dowolnym miejscu w ramach ekranu użytkownika. Zmiennoprzecinkowe systemu windows zawsze znajdują się na górze IDE. Na koniec okna narzędzi może być zadokowane jako okien dokumentu i są wyświetlane na karcie w dokumencie dobrze. Okna narzędzi, które zostały zadokowane jako okien dokumentu mają kolor w części za pomocą nazwy tokenu okien dokumentu.

 ![Ramka okna narzędzia poprawek](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

 **Zadokowane**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Okno zadokowane](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.ToolWindowBorder`

 **Zmiennoprzecinkowa: fokus**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Okna narzędzi, które skupia się](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.MainWindowActiveDefaultBorder`

 **Zmiennoprzecinkowa: po przeniesieniu fokusu**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Po przeniesieniu fokusu okna narzędzi](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")

 Tło

 `Environment.ToolWindowBackground`

 Obramowanie

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi
 Obramowania paska tytułu nie jest PRAWDA obramowanie, ale Gruba linia wzdłuż górnej krawędzi paska tytułu. Nie ma w Nazwa tokenu dla jego stanu po przeniesieniu fokusu.

 ![Pasek tytułu okna narzędzia poprawek](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

 **Fokus**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pasek tytułu skupia się](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")

 **Pasek tytułu fokusem**

 Tło

 `Environment.TitleBarActiveGradientBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.TitleBarActiveText`

 Obramowanie

 `Environment.TitleBarActiveBorder`

 Ustaw kolor tła.

 Przeciągnij uchwyt

 `Environment.TitleBarDragHandleActive`

 **Po przeniesieniu fokusu**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Po przeniesieniu fokusu paska tytułu](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")

 **Pasek tytułu po przeniesieniu fokusu**

 Tło

 `Environment.TitleBarInactiveGradientBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.TitleBarInactiveText`

 Obramowanie

 Brak

 Przeciągnij uchwyt

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Przyciski paska tytułu
 ![Przycisk paska tytułu poprawek](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")

 Użyj...
przycisków, które są wyświetlane w interfejs użytkownika, który używa tokenów kolor z paski tytułu okna narzędzia.

 Nie używaj...
 -   w przypadku przycisków, które pojawiają się w innych lokalizacjach.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Tytuł paska przycisk skupia się](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")

  **Fokus**

  Tło

  Brak

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonActiveGlyph`

  Obramowanie

  Brak

  ![Tytuł paska przycisku po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")

  **Po przeniesieniu fokusu**

  Tło

  Brak

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonInactiveGlyph`

  Obramowanie

  Brak

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Przycisk paska tytułu, który skupia się na przesunięciu](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")

  **Fokus**

  Tło

  `Environment.ToolWindowButtonHoverActive`

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Tytuł paska przycisku po przeniesieniu fokusu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")

  **Po przeniesieniu fokusu**

  Tło

  `Environment.ToolWindowButtonHoverInactive`

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Tytuł paska przycisk fokus i naciśnięciu](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")

  **Fokus**

  Tło

  `Environment.ToolWindowButtonDown`

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonDownBorder`

  ![Przycisk paska tytułu, po przeniesieniu fokusu i po naciśnięciu](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")

  **Po przeniesieniu fokusu**

  Tło

  `Environment.ToolWindowButtonDown`

  Pierwszego planu (symbol)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Obramowanie

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Karty okna narzędzi
 ![Karta okna narzędzia poprawek](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

 **Wybranej karty**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Karta okna narzędzia skupia się](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")

 **Karta okna narzędzia wybrane, ukierunkowane**

 Tło

 `Environment.ToolWindowTabSelectedTab`

 Pierwszego planu (tekst)

 `Environment.ToolWindowTabSelectedActiveText`

 Obramowanie

 `Environment.ToolWindowTabSelectedBorder`

 Ustaw kolor tła.

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Karta w oknie narzędzia po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")

 **Karta okna narzędzia zaznaczona, po przeniesieniu fokusu**

 Tło

 `Environment.ToolWindowTabSelectedTab`

 Pierwszego planu (tekst)

 `Environment.ToolWindowTabSelectedText`

 Obramowanie

 `Environment.ToolWindowTabSelectedBorder`

 Ustaw kolor tła.

 **Karta tła**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Karta tła okna narzędzia](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")

 **Karta okna narzędzia do tła**

 Tło

 `Environment.ToolWindowTabGradientBegin`

 Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.

 `Environment.ToolWindowTabGradientEnd`

 Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.

 Pierwszego planu (tekst)

 `Environment.ToolWindowTabText`

 Obramowanie

 `Environment.ToolWindowTabBorder`

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Karta tła okna narzędzia po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")

 **Karta okna narzędzia tło po najechaniu wskaźnikiem**

 Tło

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.

 Pierwszego planu (tekst)

 `Environment.ToolWindowTabMouseOverText`

 Obramowanie

 `Environment.ToolWindowTabMouseOverBorder`

 Ustaw kolor tła.

### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart
 ![Automatyczne&#45;ukrywanie poprawek](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")

 Użyj...
dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować karty okna ukryte automatycznie narzędzi.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Automatyczne&#45;Ukrywanie karty](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")

 **Domyślną kartę autoukrywanie**

 Tło

 `Environment.AutoHideTabBackgroundBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.AutoHideTabText`

 Obramowanie

 `Environment.AutoHideTabBorder`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Automatyczne&#45;Ukrywanie karty po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")

 **Autoukrywanie kartę po najechaniu wskaźnikiem**

 Tło

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

 Pierwszego planu (tekst)

 `Environment.AutoHideTabMouseOverText`

 Obramowanie

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Typowe kontrolki udostępnionego
 Używając standardowego paska poleceń programu Visual Studio w Twojej funkcji, będziesz mieć dostęp do formantów powłoki ze stylem, a powinien nie re szablonu tych wspólnych formantów. Jednak jeśli potrzebujesz do tworzenia paska poleceń niestandardowych, może być konieczne do tworzenia kontrolek niestandardowych również. W takim przypadku upewnij się, że Użyj poprawne nazwy tokenu dla każdego z następujących formantów interfejsu użytkownika jest zgodne z pozostałą częścią programu Visual Studio.

### <a name="search-box"></a>Pole wyszukiwania
 Możliwe, używaj wspólnej kontroli wyszukiwania oferowanych przez środowisko Visual Studio. Kolory pole wyszukiwania znajdują się w kategorii "SearchControl" **ShellColors.pkgdef** pliku, który zawiera token nazwy pola wejściowego, przycisk akcji, przycisk listy rozwijanej i menu rozwijanego.

 Pole wyszukiwania może być jednym z kilku Państw, z których niektóre są wzajemnie wykluczających się:

- "Skupia się" lub "po przeniesieniu fokusu" odnosi się do czy kursor znajduje się w polu tekstowym.

- "Active" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadził zapytania wyszukiwania w polu tekstowym.

- "Aktywowaniu" oznacza, że użytkownik ma moused w polu wyszukiwania za pomocą myszy (ten stan zastępuje inne stany).

- "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączone dla bieżącego kontekstu.

  ![Pole wyszukiwania poprawek](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")

  Użyj...
  Podczas projektowania pole wyszukiwania niestandardowego.

  Nie używaj...
  -   dla wszystkich elementów, który nie jest pole wyszukiwania.

- dla każdego elementu, który nie ma zawsze do dopasowania wyszukiwania polu interfejsu użytkownika.

  **Fokus**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Pole wejściowe wyszukiwania skupia się](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")

  **Pola wejściowego**

  Tło

  `SearchControl.FocusedBackground`

  Pierwszego planu (tekst)

  `SearchControl.FocusedBackground`

  Obramowanie

  `SearchControl.FocusedBorder`

  Separator

  `SearchControl.FocusedDropDownSeparator`

  ![Fokus przycisku akcji Wyszukaj](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")

  **Akcja przycisku**

  Tło

  Brak

  Pierwszego planu (symbol wyszukiwania)

  `SearchControl.SearchGlyph`

  Pierwszego planu (Zatrzymaj symbol)

  `SearchControl.StopGlyph`

  Pierwszego planu (Wyczyść symbol)

  `SearchControl.ClearGlyph`

  Obramowanie

  Brak

  ![Listy wyszukiwania&#45;naciśnięty przycisk skupia się](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.FocusedDropDownButton`

  Pierwszego planu (symbol)

  `SearchControl.FocusedDropDownButtonGlyph`

  Obramowanie

  `SearchControl.FocusedDropDownButtonBorder`

  **Po przeniesieniu fokusu**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")

  **Aktywne pola wejściowego**

  Tło

  `SearchControl.SearchActiveBackground`

  Pierwszego planu (tekst)

  `SearchControl.SearchActiveBackground`

  Obramowanie

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Pole wejściowe wyszukiwania po przeniesieniu fokusu i nieaktywnych](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Nieaktywne pola wejściowego**

  Tło

  `SearchControl.Unfocused`

  Pierwszego planu (tekst)

  `SearchControl.Unfocused`

  Obramowanie

  `SearchControl.UnfocusedBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")

  **Akcja przycisku**

  Tło

  Brak

  Pierwszego planu (symbol wyszukiwania)

  `SearchControl.SearchGlyph`

  Pierwszego planu (Zatrzymaj symbol)

  `SearchControl.StopGlyph`

  Pierwszego planu (Wyczyść symbol)

  `SearchControl.ClearGlyph`

  Obramowanie

  Brak

  ![Listy wyszukiwania&#45;naciśnięty przycisk po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.UnfocusedDropDownButton`

  Pierwszego planu (symbol)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Obramowanie

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Naciśnięty przycisk akcji wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Akcja przycisku**

  Tło

  `SearchControl.ActionButtonMouseDown`

  Pierwszego planu (symbol)

  `SearchControl.ActionButtonMouseDownGlyph`

  Obramowanie

  `SearchControl.ActionButtonMouseDownBorder`

  ![Listy wyszukiwania&#45;dół wciśnięcie przycisku](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Przycisk listy rozwijanej**

  Tło

  `SearchControl.MouseDownDropDownButton`

  Pierwszego planu (symbol)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Obramowanie

  `SearchControl.MouseDownDropDownButtonBorder`

  **Wyróżnione (tylko tekst)**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Wyróżnij pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")

  **Pole wejściowe tekst wyróżniony**

  Tło

  `SearchControl.Selection`

  Pierwszego planu (tekst)

  `SearchControl.FocusedBackground`

  Obramowanie

  Brak

  Separator

  `SearchControl.FocusedDropDownSeparator`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Pole wejściowe wyszukiwania wyłączone](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")

  **Pola wejściowego**

  Tło

  `SearchControl.Disabled`

  Pierwszego planu (tekst)

  `SearchControl.Disabled`

  Obramowanie

  `SearchControl.DisabledBorder`

  Separator

  `SearchControl.DropDownSeparator`

  ![Wyszukiwanie akcji przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")

  **Akcja przycisku**

  Tło

  Brak

  Pierwszego planu (symbol)

  `SearchControl.ActionButtonDisabledGlyph`

  Obramowanie

  Brak

  ![Listy wyszukiwania&#45;naciśnięty przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")

  **Przycisk listy rozwijanej**

  Tło

  Brak

  Pierwszego planu (symbol)

  `SearchControl.DisabledDownButtonGlyph`

  Obramowanie

  Brak

#### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania
 Menu rozwijane pole wyszukiwania ma być nieco bardziej skomplikowane niż inne menu rozwijanych w programie Visual Studio. "Sugerowane wyszukiwania" i sekcje "Opcje wyszukiwania" może występować samodzielnie, lub ze sobą w menu, a każdy z nich jest kolorowe oddzielnie. Wiersz również oddziela te dwie sekcje, gdy pojawiają się ze sobą i obramowanie wokół menu rozwijane całego.

 ![Listy wyszukiwania&#45;poprawek w dół](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")

 Użyj...
 -   Podczas tworzenia listy rozwijanej wyszukiwania niestandardowego.

- Prawidłowe nazwy tokenu dla składników poprawnej listy.

  Nie używaj...
  -   Aby uzyskać listy rozwijane, które pojawiają się w innych kontekstach.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Domyślne (nie innych Państw)**

  Element

  Nazwa tokenu: Category.color

  Obramowanie

  `SearchControl.PopupBorder`

  Separator

  `SearchControl.PopupSectionHeaderSeparator`

  W tle

  `Environment.DropShadowBackground`

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Wyszukaj sugerowane](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")

  **Sugerowane wyszukiwania**

  Tło

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `SearchControl.PopupItemText`

  ![Pole wyboru wyszukiwania](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")

  **Opcje wyszukiwania (pole)**

  ![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")

  **Opcje wyszukiwania (link)**

  Tło

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (pole tekstowe)

  `SearchControl.PopupCheckboxText`

  Pierwszego planu (tekst łącza)

  `SearchControl.PopupButtonText`

  Tło nagłówka

  `SearchControl.PopupSectionHeaderGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst nagłówka)

  `SearchControl.PopupSectionHeaderText`

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Wyszukaj sugerowane po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")

  **Sugerowane wyszukiwania**

  Tło

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst)

  `SearchControl.PopupMouseOverItemText`

  Obramowanie

  `SearchControl.PopupControlMouseOverBorder`

  ![Pole wyboru wyszukiwania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")

  **Sugerowane wyszukiwania (pole)**

  ![Opcje po najechaniu wskaźnikiem wyszukiwania](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")

  **Opcje wyszukiwania**

  Tło

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (pole tekstowe)

  `SearchControl.PopupCheckboxMouseDownText`

  Pierwszego planu (tekst łącza)

  `SearchControl.PopupButtonMouseDownText`

  Obramowanie

  `SearchControl.PopupControlMouseOverBorder`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Wyszukaj sugerowane naciśnięty](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")

  **Sugerowane wyszukiwania (pole)**

  ![Opcje naciśnięty wyszukiwania](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")

  **Opcje wyszukiwania**

  Tło pola wyboru

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (pole tekstowe)

  `SearchControl.PopupCheckboxMouseDownText`

  Tło łącza

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.

  Pierwszego planu (tekst łącza)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Hyperlink
 Hiperlink jest jeden formant, który nie ma parę tła/na pierwszym planie. We wszystkich przypadkach należy użyć hiperłącze kolor pierwszego planu, który pojawi się prawidłowo na ciemny i symulowanych map bitowych białe tło. Jeśli nie używa tokenu kolor kontrolki hiperlinku, pojawią się domyślny kolor systemu dla "naciśnięty", "który będzie flash czerwony. To sygnał, formant nie używa tokenu kolor odpowiednie środowisko.

 ![Hiperłącze poprawek](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")

 Użyj...
Kiedy należy utworzyć niestandardowy hiperlink.

 Nie używaj...
dla wszystkich elementów, które nie są hiperłączem.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Domyślne hiperłącze](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")

 Pierwszego planu (tekst)

 `Environment.PanelHyperlink`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Hiperłącza po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")

 Pierwszego planu (tekst)

 `Environment.PanelHyperlinkHover`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Hiperłącze naciśnięty](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")

 Pierwszego planu (tekst)

 `Environment.PanelHyperlinkPressed`

 **Wyłączone**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Hiperłącze wyłączone](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")

 Pierwszego planu (tekst)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Pasek informacyjny
 Infobars są używane do Podaj więcej informacji na temat danego kontekstu i zawsze pojawiają się w górnej części okna dokumentu lub okna narzędzi.

 ![Pasek informacyjny poprawek](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")

 Użyj...
Podczas tworzenia niestandardowego infobars.

 Nie używaj...
dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego.

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pasek informacyjny](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")

 **Pasek informacyjny**

 Tło

 `Environment.InfoBackground`

 Pierwszego planu (tekst)

 `Environment.InfoText`

 Obramowanie

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Pasek przewijania
 Paski przewijania mają różne przez środowisko Visual Studio i nie będą musiały mieć motywów. Jednak można zdecydować, czy chcesz korzystać kolorów używanych na paski przewijania, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

 ![Pasek przewijania poprawek](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")

 Użyj...
Podczas tworzenia interfejsu użytkownika, który chcesz dopasować paski przewijania w programie Visual Studio.

 Nie używaj... dla wszystkich elementów, nie chcesz zawsze odpowiadać paska przewijania interfejsu użytkownika.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pasek przewijania](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")

 **Pasek przewijania**

 Pasek przewijania

 `Environment.ScrollBarBackground`

 Pierwszego planu (przycisku przewijania)

 `Environment.ScrollBarThumbBackground`

 ![Paska strzałki przewijania](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")

 **Strzałki przewijania**

 Tło

 `Environment.ScrollBarArrowBackground`

 Ustaw kolor paska przewijania.

 Pierwszego planu (symbol)

 `Environment.ScrollBarArrowGlyph`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pasek przewijania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")

 **Pasek przewijania**

 Pasek przewijania

 `Environment.ScrollBarBackground`

 Pierwszego planu (przycisku przewijania)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Przewiń w pasku strzałkę po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")

 **Strzałki przewijania**

 Tło

 `Environment.ScrollBarArrowMouseOverBackground`

 Ustaw kolor paska przewijania.

 Pierwszego planu (symbol)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Naciśnięto paska przewijania](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")

 **Pasek przewijania**

 Pasek przewijania

 `Environment.ScrollBarBackground`

 Pierwszego planu (przycisku przewijania)

 `Environment.ScrollBarThumbPressedBackground`

 ![Paska kliknięciu strzałki przewijania](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")

 **Strzałki przewijania**

 Tło

 `Environment.ScrollBarArrowPressedBackground`

 Ustaw ten sam kolor jak pasek przewijania.

 Pierwszego planu (symbol)

 `Environment.ScrollBarArrowGlyphPressed`

###  <a name="BKMK_TreeView"></a> Widok drzewa
 Kilkoma oknami narzędzi, w tym Eksploratora rozwiązań, Eksploratora serwera i widoku klasy implementuje hierarchiczne schematu organizacyjnego którego kolory są kontrolowane przez nazw kolorów w kategorii TreeView. Wszystkie elementy w widoku drzewa mają kolor tła i tekstu. Elementy, które zostały zagnieżdżone elementy podrzędne mają także symbole, które wskazują, czy element jest rozwijane czy zwijane.

 ![Widok drzewa poprawek](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")

 Użyj...
wszędzie, musisz zaimplementować hierarchiczny widok organizacji.

 Nie używaj...
 -   dla wszystkich elementów, który nie jest podobny do widoku drzewa.

- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Widok drzewa](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")

  Tło

  `TreeView.Background`

  Pierwszego planu (tekst)

  `TreeView.Background`

  Pierwszego planu (symbol)

  `TreeView.Glyph`

  Obramowanie

  Brak

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Widoku drzewa w przesunięciu](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")

  Tło

  `TreeView.Background`

  Pierwszego planu (tekst)

  `TreeView.Background`

  Pierwszego planu (symbol)

  `TreeView.GlyphMouseOver`

  Obramowanie

  Brak

  **Przeciągnij kursor nad**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Dragover widok drzewa](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")

  Tło

  `TreeView.DragOverItem`

  Pierwszego planu (tekst)

  `TreeView.DragOverItem`

  Pierwszego planu (symbol)

  `TreeView.DragOverItemGlyph`

  Obramowanie

  Brak

  **Wybrane**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Fokus widoku drzewa](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")

  **Fokus**

  Tło

  `TreeView.SelectedItemActive`

  Pierwszego planu (tekst)

  `TreeView.SelectedItemActive`

  Pierwszego planu (symbol)

  `TreeView.SelectedItemActiveGlyph`

  Obramowanie

  `TreeView.FocusVisualBorder`

  ![Po przeniesieniu fokusu w widoku drzewa](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")

  **Po przeniesieniu fokusu**

  Tło

  `TreeView.SelectedItemInactive`

  Pierwszego planu (tekst)

  `TreeView.SelectedItemInactive`

  Pierwszego planu (symbol)

  `TreeView.SelectedItemInactiveGlyph`

  Obramowanie

  Brak

  **Umieść kursor nad wybrane**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Koncentruje się na przesunięciu widoku drzewa](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")

  **Fokus**

  Tło

  `TreeView.SelectedItemActive`

  Pierwszego planu (tekst)

  `TreeView.SelectedItemActive`

  Pierwszego planu (symbol)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Obramowanie

  Brak`TreeView.FocusVisualBorder`

  ![Widoku drzewa po przeniesieniu fokusu w przesunięciu](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")

  **Po przeniesieniu fokusu**

  Tło

  `TreeView.SelectedItemInactive`

  Pierwszego planu (tekst)

  `TreeView.SelectedItemInactive`

  Pierwszego planu (symbol)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Obramowanie

  Brak

### <a name="button-controls"></a>formanty przycisków
 ![Kontrolka przycisku poprawek](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")

 Użyj...
w przypadku przycisków w źródle dokumentu, którą chcesz zintegrować z kompozycji programu Visual Studio (światło, ciemny, niebieski lub kompozycję Duży kontrast systemu).

 Nie używaj...
dla przycisków, które będą wyświetlane na tle niestandardowego, który nie jest częścią motywu programu Visual Studio.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Przycisk](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")

 Przycisk

 `CommonControls.Button`

 Obramowanie przycisku

 `CommonControls.ButtonBorder`

 **Wyłączone**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")

 Przycisk

 `CommonControls.ButtonDisabled`

 Obramowanie przycisku

 `CommonControls.ButtonBorderDisabled`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Przycisk po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")

 Przycisk

 `CommonControls.ButtonHover`

 Obramowanie przycisku

 `CommonControls.ButtonBorderHover`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Wciśnięcie przycisku](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")

 Przycisk

 `CommonControls.ButtonPressed`

 Obramowanie przycisku

 `CommonControls.ButtonBorderPressed`

 **Fokus**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Fokus przycisku](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")

 Przycisk

 `CommonControls.ButtonFocused`

 Obramowanie przycisku

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Formanty pól wyboru
 ![Pole wyboru poprawek](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")

 Użyj...
Formanty pól wyboru znajdujących się w dokumencie dobrze.

 Nie używaj...
dla dowolnego interfejsu użytkownika, który nie jest kontrolkę pola wyboru.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")

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

 Nazwa tokenu: Category.color

 ![Pole wyboru wyłączone](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")

 Tło

 `CommonControls.CheckBoxBackgroundDisabled`

 Obramowanie

 `CommonControls.CheckBoxBorderDisabled`

 Tekst

 `CommonControls.CheckBoxTextDisabled`

 Symbol

 `CommonControls.CheckBoxGlyphDisabled`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pole wyboru po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")

 Tło

 `CommonControls.CheckBoxBackgroundHover`

 Obramowanie

 `CommonControls.CheckBoxBorderHover`

 Tekst

 `CommonControls.CheckBoxTextHover`

 Symbol

 `CommonControls.CheckBoxGlyphHover`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pole wyboru naciśnięty](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")

 Tło

 `CommonControls.CheckBoxBackgroundPressed`

 Obramowanie

 `CommonControls.CheckBoxBorderPressed`

 Tekst

 `CommonControls.CheckBoxTextPressed`

 Symbol

 `CommonControls.CheckBoxGlyphPressed`

 **Fokus**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Pole wyboru, które skupia się](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")

 Tło

 `CommonControls.CheckBoxBackgroundFocused`

 Obramowanie

 `CommonControls.CheckBoxBorderFocused`

 Tekst

 `CommonControls.CheckBoxTextFocused`

 Symbol

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Upuść formantów pola kombi/pola
 ![Upuść&#45;dół&#47;poprawek pola kombi](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")

 Użyj...
listy rozwijane i pole kombi pola, które są również częścią dokumentu.

 Nie używaj...
 -   dla dowolnego interfejsu użytkownika, który nie jest listy rozwijanej lub pola kombi.

- Aby uzyskać [listy rozwijanej](../../misc/shared-colors.md#BKMK_CommandDropDown) lub [pola kombi](../../misc/shared-colors.md#BKMK_CommandComboBox) na pasku poleceń.

  **Default**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;pola kombi](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")

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

  Tło glifów

  `CommonControls.ComboBoxGlyphBackground`

  **Wyłączone**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;pola kombi wyłączone](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")

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

  Tło glifów

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Po wskazaniu wskaźnikiem**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")

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

  Tło glifów

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Naciśnięto**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;pola kombi naciśnięty](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")

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

  Tło glifów

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Fokus**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;pola kombi, które skupia się](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")

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

  Tło glifów

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Wybór danych wejściowych tekstu**

  Składnik

  Element

  Nazwa tokenu: Category.color

  ![Upuść&#45;dół&#47;wprowadź tekst pola kombi](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")

  Wyróżnij

  `CommonControls.ComboBoxTextInputSelection`

  **Naciśnięto — widok elementu listy**

  ![Upuść&#45;dół&#47;widoku listy pole kombi](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")

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

  Tło w tle

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Formanty danych tabelarycznych (siatki)
 Formanty danych tabelarycznych, znany także jako formantach siatki są wspólnych formantów dla programu Visual Studio, który może służyć do prezentowania dużych ilości danych w wielu kolumnach. Formanty standardowe dane tabelaryczne znajdują się w wielu miejscach w programie Visual Studio: Lista błędów okna narzędzia, raporty funkcji IntelliTrace i widok sterty w pamięci, między innymi. Zawsze używaj kontrolek standardowych danych tabelarycznych, pod warunkiem. W sporadycznych przypadkach możesz utracić dostęp do formantów standardowych danych tabelarycznych. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika jest zgodne z innymi formantami danych tabelarycznych w programie Visual Studio.

 ![Dane tabelaryczne &#40;formant siatki&#41; poprawek](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")

 Użyj...
Aby uzyskać tabelaryczny lub kontrolki siatki.

 Nie używaj...
dla wszelkich elementów interfejsu użytkownika, który nie jest formantem tabelarycznych lub siatkę.

#### <a name="column-headers"></a>Nagłówki kolumn
 Nagłówki kolumn składają się z tło, obramowanie, tekst tytułu i opcjonalnie symbol zwykle używany podczas siatki są posortowane według tej kolumny.

 Stan

 Element

 Nazwa tokenu: Category.color

 Domyślny

 Tło

 `Header.Default`

 Pierwszego planu (tekst)

 `Environment.CommandBarTextActive`

 Pierwszego planu (symbol)

 `Header.Glyph`

 Obramowanie

 `Header.SeparatorLine`

 Po wskazaniu wskaźnikiem

 Tło

 `Header.MouseOver`

 Pierwszego planu (tekst)

 `Environment.CommandBarTextHover`

 Pierwszego planu (symbol)

 `Header.MouseOverGlyph`

 Obramowanie

 `Header.SeparatorLine`

 Naciśnięto

 Tło

 `CommonControls.CheckBoxBackgroundPressed`

 Pierwszego planu (tekst)

 `CommonControls.CheckBoxBorderPressed`

 Pierwszego planu (symbol)

 `CommonControls.CheckBoxTextPressed`

 Obramowanie

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Elementy widoku listy
 Elementy widoku listy składają się z tła i jego zawartość. Zawartość może być tekst i/lub ikonę.

 Stan

 Element

 Nazwa tokenu: Category.color

 Domyślny

 Tło

 Przezroczyste

 Pierwszego planu (tekst)

 `Environment.CommandBarTextActive`

 Obramowanie

 Brak

 Zaznaczone (aktywny)

 Tło

 `TreeView.SelectedItemActive`

 Pierwszego planu (tekst)

 `TreeView.SelectedItemActiveText`

 Obramowanie

 Brak

 Zaznaczone (nieaktywny)

 Tło

 `TreeView.SelectedItemInactive`

 Pierwszego planu (tekst)

 `TreeView.SelectedItemInactiveText`

 Obramowanie

 Brak

## <a name="manifest-designer"></a>Manifest Designer
 Manifest Designer został zaprojektowany jako sposób, aby ułatwić edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Gdy nie ma udostępnionego framework dostępne do użycia, może być odpowiednia dla Ciebie dopasować układ i kolory kart orientacji/nawigacji i ogólną strukturę. Aby uzyskać więcej informacji na temat szczegółów układ zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

 ![Projektant manifestu poprawek](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")

 Użyj...
 -   dla projektantów, które są podobne do projektanta manifestu.

- zamiast przy użyciu karty wspólne kontroluje również w górnej części edytora w obrębie dokumentu.

  Nie używaj...
  -   Jeśli masz więcej niż sześć kart.

- dla wszelkich elementów interfejsu użytkownika, który nie ma struktury, takich jak projektant manifestów.

  Stan

  Składnik

  Element

  Nazwa tokenu: Category.color

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

  Tekst pomocy w oknie dialogowym

  `ManifestDesigner.WatermarkText`

  Ta nazwa tokenu jest niezgodna z jego funkcji.

  Inne niż wybrane

  Tab

  Tło

  `ManifestDesigner.Tab.Inactive`

  Po wskazaniu wskaźnikiem

  Tab

  Tło

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Znakowanie
 Program Visual Studio obsługuje, tagowanie, co pozwala użytkownikowi zadeklarować można wyszukiwać słowa kluczowe na potrzeby śledzenia. Na przykład menedżerów projektów i programistów umożliwia Team Foundation Server (TFS) tagów elementów roboczych. W poniższych tabelach podać nazw kolorów zarówno samego znacznika, jak i "zamknąć ikonę" symbol, umieść kursor i wybranych stanów.

 ![Znakowanie poprawek](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")

 Użyj...
dla interfejsu użytkownika, który obsługuje znakowanie.

 Nie używaj...
dla wszystkich innych typów interfejsu użytkownika.

### <a name="tag"></a>Tag
 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")

 **Default**

 Tło

 `Tag.Background`

 Pierwszego planu (tekst)

 `Tag.Background`

 ![Tag po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")

 **Po wskazaniu wskaźnikiem**

 Tło

 `Tag.HoverBackground`

 Pierwszego planu (tekst)

 `Tag.HoverBackgroundText`

 ![Tag naciśnięty](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")

 **Naciśnięto**

 Tło

 `Tag.PressedBackground`

 Pierwszego planu (tekst)

 `Tag.PressedBackgroundText`

 ![Zaznaczony tag](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")

 **Wybrane**

 Tło

 `Tag.SelectedBackground`

 Pierwszego planu (tekst)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Symbol (ikonę zamknięcia)
 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Tag &#40;symbol&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")

 **Domyślne (ustawienie domyślne tagu)**

 Tło

 Brak

 Pierwszego planu (symbol)

 `Tag.TagHoverGlyph`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Tag &#40;symbol&#41; po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")

 **Po wskazaniu wskaźnikiem (ustawienie domyślne tagu)**

 Tło

 `Tag.TagHoverGlyphHoverBackground`

 Pierwszego planu (symbol)

 `Tag.TagHoverGlyphHover`

 Obramowanie

 `Tag.TagHoverGlyphHoverBorder`

 **Naciśnięto**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Tag &#40;symbol&#41; naciśnięty](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")

 **Naciśnięto (ustawienie domyślne tagu)**

 Tło

 `Tag.TagHoverGlyphPressedBackground`

 Pierwszego planu (symbol)

 `Tag.TagHoverGlyphPressed`

 Obramowanie

 `Tag.TagHoverGlyphPressedBorder`

 **Domyślne wybrany symbol znacznika**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Zaznaczony tag](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")

 **Domyślne (wybrane tag)**

 Tło

 Brak

 Pierwszego planu (symbol)

 `Tag.TagSelectedGlyph`

 **Wybrany symbol znacznika po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Tag wybrane po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")

 **Po wskazaniu wskaźnikiem (wybrany tag)**

 Tło

 `Tag.TagSelectedGlyphHoverBackground`

 Pierwszego planu (symbol)

 `Tag.TagSelectedGlyphHover`

 Obramowanie

 `Tag.TagSelectedGlyphHoverBorder`

 **Wybrano/symbol tagu wciśnięty**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Zaznaczony tag naciśnięty](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")

 **Po naciśnięciu (wybrany tag)**

 Tło

 `Tag.TagSelectedGlyphPressedBackground`

 Foreground(Glyph)

 `Tag.TagSelectedGlyphPressed`

 Obramowanie

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Powłoka

### <a name="background"></a>Tło
 Tło środowiska składa się z dwóch warstw. Dolna warstwa jest jednolitego koloru, który obejmuje całe środowisko IDE. Górną warstwę mieści się w obszarze półki polecenia i między kanałami automatycznego ukrywania okna narzędzia na lewej lub prawej krawędzi środowiska IDE. Począwszy od programu Visual Studio 2013 warstwy tła górny i dolny są ustawione na ten sam kolor w motywy jasny i ciemny motyw.

 ![Tło powłoki poprawek](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")

 Użyj...
dla miejsc, które chcesz dopasować tło środowiska Visual Studio.

 Nie używaj...
 -   jako wypełnienia dla miejsc, które nie są tła powierzchni.

- jako tła, na którym chcesz umieścić elementy pierwszego planu.

  Składnik

  Element

  Nazwa tokenu: Category.color

  Dolna warstwa

  Tło

  `Environment.EnvironmentBackground`

  Składnik

  Element

  Nazwa tokenu: Category.color

  Górną warstwę

  Tło

  *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Polecenie Półka
 Dwa zestawy token nazwy są używane do tła półki polecenia: on ustawiony, na którym znajduje się na pasku menu, a drugi dla gdzie znajdują się paski poleceń. Grupa pasek indywidualne polecenie ma swoje własne wartości kolorów tła, które zostały omówione bardziej szczegółowo w sekcji "polecenie bar". Menu paska i polecenia paska tekstu omówiono w sekcji pasek menu i poleceń, odpowiednio.

 ![Polecenie półki poprawek](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")

 Użyj...
 -   dla obszarów, w którym umieszcza się menu i paski narzędzi.

- w tle poprawne /? kombinacji Nazwa tokenu pierwszego planu.

  Nie używaj...
  dla obszarów, które nie są podobne do półki polecenia.

  Składnik

  Element

  Nazwa tokenu: Category.color

  Pasek menu

  Tło

  *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Pasek poleceń

  Tło

  *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Przybornik
 Przybornik jest jednym z typowych okien narzędzi, które jest najczęściej używany w programie Visual Studio. Jest zasadniczo kontrolki drzewa za pomocą specjalnych motywu i stylów zastosowana.

 ![Przybornik poprawek](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")

 Użyj...
Podczas projektowania okna narzędzi, które chcesz, aby zawsze były zgodne z przybornika powłoki.

 Nie używaj...
dla każdego elementu, który nie jest podobne do przybornika interfejsu użytkownika lub jeśli wiesz, czy interfejs użytkownika będą mieć problemy, jeśli Przybornik powłoki kolory zmiany.

 **Default**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")

 **Węzeł nadrzędny**

 ![Węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")

 **Węzeł podrzędny**

 Tło

 `Environment.ToolboxContent`

 Nagłówki

 `Environment.ToolWindowBackground`

 Poszczególne elementy lub całe okno, jeśli brak dostępnych kontrolek

 Obramowanie

 Brak

 Pierwszego planu (symbol)

 `Environment.ToolboxContent`

 Pierwszego planu (tekst)

 `Environment.ToolboxContent`

 **Po wskazaniu wskaźnikiem**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Węzeł podrzędny przybornika po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")

 **Przybornik umieść wskaźnik myszy na węzeł podrzędny**

 Tło

 `Environment.ToolboxContentMouseOver`

 Tylko pojedynczych elementów

 Obramowanie

 Brak

 Pierwszego planu (tekst)

 `Environment.ToolboxContentMouseOver`

 Tylko pojedynczych elementów

 **Wybrane**

 Składnik

 Element

 Nazwa tokenu: Category.color

 ![Węzeł nadrzędny przybornika skupia się](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")

 **Węzeł nadrzędny fokusem**

 ![Węzeł podrzędny przybornika skupia się](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")

 **Węzeł podrzędny fokusem**

 Tło

 `TreeView.SelectedItemActive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 Obramowanie

 `TreeView.FocusVisualBorder`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 Pierwszego planu (symbol)

 `TreeView.SelectedItemActive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 Pierwszego planu (tekst)

 `TreeView.SelectedItemActive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 ![Po przeniesieniu fokusu węzła nadrzędnego przybornika](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")

 **Węzeł nadrzędny po przeniesieniu fokusu**

 ![Węzeł podrzędny przybornika po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")

 **Węzeł podrzędny bez fokusu**

 Tło

 `TreeView.SelectedItemInactive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 Obramowanie

 Brak

 Pierwszego planu (symbol)

 `TreeView.SelectedItemInactive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii

 Pierwszego planu (tekst)

 `TreeView.SelectedItemInactive`

 Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii
