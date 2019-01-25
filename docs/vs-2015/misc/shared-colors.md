---
title: Udostępnione kolory | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: v-brickg
ms.openlocfilehash: e6dad35d2fe70866eee8ffbace81c44c502f67d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764659"
---
# <a name="shared-colors"></a>Udostępnione kolory
Tutaj wstaw wprowadzenie.  
  
## <a name="shared-colors"></a>Udostępnione kolory  
 Podczas projektowania interfejsu użytkownika, który używa wspólnych elementów powłoki programu Visual Studio lub chcesz, aby Twoje element interfejsu, aby były zgodne z podobne funkcje, umożliwia już istniejącymi nazwami tokenu w plikach definicji pakietu wybierz i przypisania kolorów. Gwarantuje to, że Twój interfejs użytkownika pozostaje zgodny z całego środowiska programu Visual Studio i że jest aktualizowana automatycznie po motywy są dodawane lub aktualizowane.  
  
 W tym artykule opisano typowe elementy interfejsu użytkownika i token nazwy które używają, które można odwoływać się podczas kompilowania z podobnym interfejsem użytkownika. Dla określonych informacji dotyczących tych kolorów tokeny dostępu, zobacz [usługa VSColor](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Upewnij się, że prawidłowo używać nazw tokenu:  
  
-   **Użyj tokenu nazw na podstawie funkcji, nie na samego koloru.** Typowe udostępnione kolory są skojarzone z elementami określonego interfejsu i są przeznaczone wyłącznie do użytku takie same lub podobne funkcje. Na przykład nie używaj ponownie plików kolor po naciśnięciu kombi dla Animacja postępu rotowania tylko dlatego, jak kolor. Funkcje pola kombi i animacji są różne, a Jeśli kolor skojarzony z zmiany pola kombi, mogą już być odpowiedni kolor w odniesieniu do danego elementu animacji. Spójnego używania koloru pomaga w poznaniu użytkowników i uniknąć pomyłek.  
  
-   **Użyj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które są przeznaczone do użycia z tekstem będzie miał kolor tekstu. Nie używaj kolorów tekstu innego niż został określony dla w tle. Jeśli nie jest kolorem skojarzony tekst, nie należy używać tego kolor tła dla dowolnego powierzchni, w którym oczekujesz, że do wyświetlania tekstu. Inne kombinacje kolorów tekstu i tła może spowodować w interfejsie nie można go odczytać.  
  
-   **Użyj kolorów kontrolki, które są odpowiednie dla ich lokalizacji.** W określonych stanach niektóre formanty programu Visual Studio nie mają osobne obramowania i kolory tła. Zamiast tego przejmą ich te kolory z powierzchni spodem. Upewnij się, zawsze używaj tokenów nazwy, które są odpowiednie dla lokalizacji, w którym umieszcza się kontrolka.  
  
> [!IMPORTANT]
>  Nie używaj tokenów w kategorii "Stronę startową" lub "Jabłecznik"!  
  
### <a name="command-structures"></a>Polecenie struktury  
  
####  <a name="BKMK_CommandMenus"></a> Menu  
 Menu może wystąpić w kilku miejscach w programie Visual Studio 2013: główny pasek menu, osadzony w dokumencie lub narzędzia systemu windows lub kliknij prawym przyciskiem myszy w różnych miejscach w całej IDE. Implementacje menu skojarzone z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiednich elementów. Zawsze należy używać implementacji standardowe menu oferowanych przez środowisko Visual Studio. Jednak w sporadycznych przypadkach możesz utracić dostęp do standardowego menu programu Visual Studio. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika są spójne z innych menu w programie Visual Studio.  
  
 ![Menu poprawek](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")  
  
 Użyj...  
 -   Kiedy należy utworzyć niestandardowe menu.  
  
- Jeśli masz nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.  
  
  Nie używaj...  
  kolor tła samodzielnie. Zawsze użyj kombinacji tła/pierwszego planu, jak określono.  
  
##### <a name="menu-title"></a>Tytuł menu  
 Tytuły menu składają się z tła, obramowania i tekst tytułu, a także opcjonalnie symbol, zwykle w przypadku, gdy menu znajduje się na pasku poleceń.  
  
 ![Tytuł menu poprawek](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")  
  
 Użyj...  
 zawsze, gdy tworzysz tytuł menu niestandardowe.  
  
 Nie używaj...  
 -   dla wszystkich elementów, które nie chcesz zawsze odpowiada tytuł menu.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Tło|Brak|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z domyślną symbol](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifów**|Pierwszego planu (symbol)|`Environment.CommandBarMenuGlyph`|  
|![Tytuł menu z domyślną symbol](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifów**|Obramowanie|Brak|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu, po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Tytuł menu, po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")<br /><br /> **Tytuł menu**|Pierwszego planu (tekst)|`Environment.CommandBarTextHover`|  
|![Tytuł menu z symbol po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifów**|Pierwszego planu (symbol)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Tytuł menu z symbol po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifów**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu naciśnięty](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Tytuł menu naciśnięty](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z naciśnięto symbol](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifów**|Pierwszego planu (symbol)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Tytuł menu z naciśnięto symbol](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifów**|Obramowanie|`Environment.CommandBarMenuBorder`<br /><br /> Tylko po lewej stronie, górnej i prawej stronie.|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu przy użyciu symbolu wyłączone](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifów**|Tło|Brak|  
|![Tytuł menu przy użyciu symbolu wyłączone](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifów**|Pierwszego planu (tekst)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu przy użyciu symbolu wyłączone](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifów**|Pierwszego planu (symbol)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu przy użyciu symbolu wyłączone](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifów**|Obramowanie|Brak|  
  
##### <a name="menu"></a>Menu  
 Element menu poszczególnych składa się z tekst menu i opcjonalnej ikony, pole wyboru lub symbol podmenu. Jego tekstu i tła kolorów zmiana po najechaniu wskaźnikiem. Token ten kolor to para tła/pierwszego planu.  
  
 ![Elementy menu poprawek](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")  
  
 Użyj...  
 Aby uzyskać wszystkie listy rozwijanej, który jest uruchamiany z paska menu i paska poleceń.  
  
 Nie używaj...  
 -   Aby uzyskać wszystkie listy rozwijanej, która występuje w kontekście innego.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Pierwszego planu (podmenu symbol)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Obramowanie|`Environment.CommandBarMenuBorder`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Tło kanału ikony|`Environment.CommandBarMenuIconBackground`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|Separator|`Environment.CommandBarMenuSeparator`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menu**|W tle|`Environment.DropShadowBackground`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")<br /><br /> **Zaznaczone**|Znacznik wyboru|`Environment.CommandBarCheckBox`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")<br /><br /> **Zaznaczone**|Znacznik wyboru tła|`Environment.CommandBarSelectedIcon`|  
|![Wybrane menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")<br /><br /> **Wybrane**|Tło ikony|`Environment.CommandBarSelected`|  
|![Wybrane menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")<br /><br /> **Wybrane**|Ikona obramowania|`Environment.CommandBarSelectedBorder`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Po wskazaniu wskaźnikiem menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Element menu**|Tło|`Environment.CommandBarMenuItemMouseOver`|  
|![Po wskazaniu wskaźnikiem menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Element menu**|Pierwszego planu (tekst)|`Environment.CommandBarMenuItemMouseOver`|  
|![Po wskazaniu wskaźnikiem menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Element menu**|Pierwszego planu (podmenu symbol)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Po wskazaniu wskaźnikiem menu zaznaczone](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")<br /><br /> **Zaznaczone**|Znacznik wyboru|`Environment.CommandBarCheckBoxMouseOver`|  
|![Po wskazaniu wskaźnikiem menu zaznaczone](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")<br /><br /> **Zaznaczone**|Znacznik wyboru tła|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Po wskazaniu wskaźnikiem menu wybrane](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")<br /><br /> **Wybrane**|Tło ikony|`Environment.CommandBarHoverOverSelected`|  
|![Po wskazaniu wskaźnikiem menu wybrane](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")<br /><br /> **Wybrane**|Ikona obramowania|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")<br /><br /> Element menu|Pierwszego planu (tekst)|`Environment.CommandBarTextInactive`|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")<br /><br /> Element menu|Pierwszego planu (podmenu symbol)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Zaznaczone wyłączone menu](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")<br /><br /> Zaznaczone|Znacznik wyboru|`Environment.CommandBarCheckBoxDisabled`|  
|![Zaznaczone wyłączone menu](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")<br /><br /> Zaznaczone|Znacznik wyboru tła|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Pasek poleceń  
 Na pasku poleceń może znajdować się w wielu miejscach w programie Visual Studio IDE, głównie półki polecenia i narzędzia embedded na platformie lub okna dokumentu.  
  
 Ogólnie rzecz biorąc należy zawsze używać implementacja paska poleceń standardowych, które są dostarczane przez środowisko Visual Studio. Przy użyciu standardowego mechanizmu zapewnia, są poprawnie wyświetlane wszystkie szczegóły visual i że elementów interaktywnych będą zachowywać się spójne z innymi formantami paska poleceń programu Visual Studio. Jednak jeśli jest to niezbędne do tworzenia własnego paska poleceń, upewnij się, że poprawnie za pomocą następujących nazw tokenu stylu.  
  
 ![Pasek poleceń poprawek](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")  
  
 ![Przycisk przepełnienie poprawek](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")  
  
 Użyj...  
 w miejscach osadzone polecenia pasek ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio.  
  
 Nie używaj...  
 -   dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  
  
-   Aby uzyskać inne niż te, dla których token nazwy zostały określone składniki paska poleceń.  
  
##### <a name="command-bar-group"></a>Grupy pasek poleceń  
 Grupy pasek poleceń zawiera zestaw powiązanych formantów paska poleceń i może zawierać dowolną liczbę przyciski, Podziel przyciski, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów jest regulowane przez oddzielne nazwy tokenu i są omówione oddzielnie w innym miejscu, w tym przewodniku. Linii separatora jest używane do dzielenia grupy pasek poleceń do powiązanych podgrupy.  
  
 ![Grupa paska poleceń poprawek](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")  
  
 Użyj...  
 w miejscach osadzone polecenia pasek ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio.  
  
 Nie używaj...  
 -   dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  
  
- Aby uzyskać inne niż te, dla których token nazwy zostały określone składniki paska poleceń.  
  
  **Domyślne** (nie innych Państw)  
  
|Element|Nazwa tokenu: Category.Color|  
|-------------|--------------------------------|  
|Tło|`Environment.CommandBarGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|Obramowanie|`Environment.CommandBarToolBarBorder`|  
|Przeciągnij uchwyt|`Environment.CommandBarDragHandle`|  
|Separator|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ikony poleceń  
 ![Ikona polecenia poprawek](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")  
  
 ![Ikona polecenia poprawek](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")  
  
 Użyj...  
 dla przycisków, które zostaną umieszczone na pasku poleceń.  
  
 Nie używaj...  
 -   dla formantów, które mają własne nazwy tokenu.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Polecenie domyślną ikonę](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Tło|N/d (dziedziczy tło paska poleceń)|  
|![Polecenie domyślną ikonę](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|![Polecenie domyślną ikonę](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Obramowanie|Brak|  
|![Polecenie ikonę domyślnie wybrana](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Wybrane**|Tło|`Environment.CommandBarSelected`|  
|![Polecenie ikonę domyślnie wybrana](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Wybrane**|Pierwszego planu (tekst)|`Environment.CommandBarTextSelected`|  
|![Polecenie ikonę domyślnie wybrana](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Wybrane**|Obramowanie|`Environment.CommandBarSelectedBorder`|  
  
 **Aktywowanie i fokus klawiatury**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Polecenie ikony po wskazaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Standardowa po najechaniu wskaźnikiem**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Polecenie ikony po wskazaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Standardowa po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.CommandBarTextHover`|  
|![Polecenie ikony po wskazaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Standardowa po najechaniu wskaźnikiem**|Obramowanie|`Environment.CommandBarBorder`|  
|![Polecenie ikony po wskazaniu wskaźnikiem, wybrane](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu wskaźnikiem**|Tło|`Environment.CommandBarHoverOverSelected`|  
|![Polecenie ikony po wskazaniu wskaźnikiem, wybrane](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.CommandBarTextHoverOverSelected`|  
|![Polecenie ikony po wskazaniu wskaźnikiem, wybrane](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Wybrane po najechaniu wskaźnikiem**|Obramowanie|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ikona polecenia naciśnięty](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Ikona po naciśnięciu polecenia**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Ikona polecenia naciśnięty](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Ikona po naciśnięciu polecenia**|Pierwszego planu (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Ikona polecenia naciśnięty](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Ikona po naciśnięciu polecenia**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ikona polecenia wyłączone](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączenia**|Tło|N/d (dziedziczy tło paska poleceń)|  
|![Ikona polecenia wyłączone](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączenia**|Pierwszego planu (tekst)|`Environment.CommandBarTextInactive`|  
|![Ikona polecenia wyłączone](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączenia**|Obramowanie|Brak|  
  
#####  <a name="BKMK_CommandComboBox"></a> Pole kombi  
  
> [!IMPORTANT]
>  Pola kombi są podobne do list rozwijanych, ale zawierają region tekst do edycji. Jeśli z listy rozwijanej nie obejmuje regionu tekst do edycji, należy użyć tokenów kolor, znajdującym się [listy rozwijanej](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Pole kombi poprawek](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")  
  
 Użyj...  
 -   Podczas tworzenia pola kombi niestandardowych.  
  
- Podczas tworzenia formantu paska poleceń, która jest podobna do pola kombi.  
  
  Nie używaj...  
  -   dla wszystkich elementów, nie należy zawsze dopasować polecenia paska.  
  
- Jeśli masz dostęp do pola kombi ze stylem.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Pola wejściowego**|Tło|`Environment.ComboBoxBackground`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`Environment.ComboBoxText`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Pola wejściowego**|Obramowanie|`Environment.ComboBoxBorder`|  
|![Pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Pola wejściowego**|Separator|Nie separatora|  
|![Listy pola kombi&#45;naciśnięty przycisk](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|N/d (dziedziczy)|  
|![Listy pola kombi&#45;naciśnięty przycisk](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.ComboBoxGlyph`|  
|![Pole kombi&#47;porzucić&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Listy rozwijanej**|Tło|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pole kombi&#47;porzucić&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Listy rozwijanej**|Pierwszego planu (tekst)|`Environment.ComboBoxItemText`|  
|![Pole kombi&#47;porzucić&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Listy rozwijanej**|Obramowanie|`Environment.ComboBoxPopupBorder`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole kombi pola wejściowego po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Pola wejściowego**|Tło|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pole kombi pola wejściowego po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`Environment.ComboBoxMouseOverText`|  
|![Pole kombi pola wejściowego po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Pola wejściowego**|Obramowanie|`Environment.ComboBoxMouseOverBorder`|  
|![Pole kombi pola wejściowego po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Pola wejściowego**|Separator|`Environment.ComboBoxMouseOverSeparator`|  
|![Pole kombi&#47;porzucić&#45;przycisku po umieszczeniu na](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Pole kombi&#47;porzucić&#45;przycisku po umieszczeniu na](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.ComboBoxMouseOverGlyph`|  
|![Pole kombi&#47;porzucić&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Listy rozwijanej**|W tle (element Menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Pole kombi&#47;porzucić&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Listy rozwijanej**|Pierwszego planu (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Pole kombi&#47;porzucić&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Listy rozwijanej**|Obramowanie (element Menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi skupia się](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Pola wejściowego**|Tło|`Environment.ComboBoxFocusedBackground`|  
|![Pole wejściowe pola kombi skupia się](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`Environment.ComboBoxFocusedText`|  
|![Pole wejściowe pola kombi skupia się](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Pola wejściowego**|Obramowanie|`Environment.ComboBoxFocusedBorder`|  
|![Pole wejściowe pola kombi skupia się](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Pola wejściowego**|Separator|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Pole kombi&#47;porzucić&#45;naciśnięty przycisk skupia się](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxFocusedButtonBackground`|  
|![Pole kombi&#47;porzucić&#45;naciśnięty przycisk skupia się](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Pola wejściowego**|Tło|`Environment.ComboBoxMouseDownBackground`|  
|![Pole wejściowe pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`Environment.ComboBoxMouseDownText`|  
|![Pole wejściowe pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Pola wejściowego**|Obramowanie|`Environment.ComboBoxMouseDownBorder`|  
|![Pole wejściowe pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Pola wejściowego**|Separator|`Environment.ComboBoxMouseDownSeparator`|  
|![Pole kombi&#47;porzucić&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Pole kombi&#47;porzucić&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Pola wejściowego**|Tło|`Environment.ComboBoxDisabledBackground`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`Environment.ComboBoxDisabledText`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Pola wejściowego**|Obramowanie|`Environment.ComboBoxDisabledBorder`|  
|![Pole wejściowe pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Pola wejściowego**|Separator|Nie separatora|  
|![Pole kombi&#47;porzucić&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Pole kombi&#47;porzucić&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.ComboBoxDisabledGlyph`|  
  
#####  <a name="BKMK_CommandDropDown"></a> Lista rozwijana  
  
> [!IMPORTANT]
>  Listy rozwijane są podobne do pola kombi, ale brak regionów tekst do edycji. Jeśli z listy rozwijanej zawiera tekst do edycji regionu, należy użyć tokenów kolor, znajdującym się [pola kombi](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Upuść&#45;poprawek w dół](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")  
  
 Użyj...  
 Podczas tworzenia kontrolki niestandardowej listy rozwijanej.  
  
 Nie używaj...  
 -   dla wszystkich elementów, który nie jest podobna do listy rozwijanej.  
  
- dla pola kombi lub przyciski dzielone.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół do pola wyboru](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownBackground`|  
|![Upuść&#45;w dół do pola wyboru](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Pierwszego planu (tekst)|`DropDownText`|  
|![Upuść&#45;w dół do pola wyboru](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Obramowanie|`DropDownBorder`|  
|![Upuść&#45;w dół do pola wyboru](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Separator|Nie separatora|  
|![Upuść&#45;naciśnięty przycisk](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Upuść&#45;naciśnięty przycisk](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.DropDownGlyph`|  
|![Upuść&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Listy rozwijanej**|Tło|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Upuść&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Listy rozwijanej**|Pierwszego planu (tekst)|`Environment.ComboBoxItemText`|  
|![Upuść&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Listy rozwijanej**|Obramowanie|`Environment.DropDownPopupBorder`|  
|![Upuść&#45;listy rozwijanej](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Listy rozwijanej**|W tle|`Environment.DropShadowBackground`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół do pola wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Upuść&#45;w dół do pola wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Pierwszego planu (tekst)|`Environment.DropDownMouseOverText`|  
|![Upuść&#45;w dół do pola wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseOverBorder`|  
|![Upuść&#45;w dół do pola wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseOverSeparator`|  
|![Upuść&#45;przycisku po umieszczeniu na](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseOverBackground`|  
|![Upuść&#45;przycisku po umieszczeniu na](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.DropDownMouseOverGlyph`|  
|![Upuść&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Listy rozwijanej**|W tle (element Menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Upuść&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Listy rozwijanej**|Pierwszego planu (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Upuść&#45;listy po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Listy rozwijanej**|Obramowanie (element Menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół do pola wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseDownBackground`|  
|![Upuść&#45;w dół do pola wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Pierwszego planu (tekst)|`Environment.DropDownMouseDownText`|  
|![Upuść&#45;w dół do pola wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseDownBorder`|  
|![Upuść&#45;w dół do pola wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseDownSeparator`|  
|![Upuść&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseDownBackground`|  
|![Upuść&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`Environment.DropDownMouseDownGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół do pola wyboru wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Tło|`Environment.DropDownDisabledBackground`|  
|![Upuść&#45;w dół do pola wyboru wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Pierwszego planu (tekst)|`Environment.DropDownDisabledText`|  
|![Upuść&#45;w dół do pola wyboru wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Obramowanie|`Environment.DropDownDisabledBorder`|  
|![Upuść&#45;w dół do pola wyboru wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Separator|Nie separatora|  
|![Upuść&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")|Tło|Brak|  
|![Upuść&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")|Pierwszego planu (symbol)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Przycisk podziału  
 Przyciski dzielone udostępniać wiele tokenów nazwy inne kontrolki paska poleceń, takich jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne działania i przycisk listy rozwijanej token nazwy są powtarzane tutaj dla wygody. Listy rozwijane w przycisku podziału stanowią implementacje paska poleceń [menu](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Przycisk podziału poprawek](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")  
  
 Użyj...  
 Kiedy tworzysz przycisku podziału niestandardowych.  
  
 Nie używaj...  
 -   dla innych rodzajów przycisków.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Przycisk podziału (ustawienie domyślne)**|Tło|Brak|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Przycisk podziału (ustawienie domyślne)**|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Przycisk podziału (ustawienie domyślne)**|Pierwszego planu (symbol)|`Environment.CommandBarSplitButtonGlyph`|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Przycisk podziału (ustawienie domyślne)**|Obramowanie|Brak|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Przycisk podziału (ustawienie domyślne)**|Separator|Brak|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Przycisk podziału (po najechaniu wskaźnikiem)**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Przycisk podziału po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Przycisk podziału (po najechaniu wskaźnikiem)**|Pierwszego planu (tekst)|`Environment.CommandBarTextHover`|  
|![Przycisk podziału po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Przycisk podziału (po najechaniu wskaźnikiem)**|Pierwszego planu (symbol)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Przycisk podziału po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Przycisk podziału (po najechaniu wskaźnikiem)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Przycisk podziału po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Przycisk podziału (po najechaniu wskaźnikiem)**|Separator|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięcie przycisku podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (po naciśnięciu)**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wciśnięcie przycisku podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (po naciśnięciu)**|Pierwszego planu (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Wciśnięcie przycisku podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (po naciśnięciu)**|Pierwszego planu (symbol)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Wciśnięcie przycisku podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (po naciśnięciu)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Wciśnięcie przycisku podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (po naciśnięciu)**|Separator|Brak|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału wyłączone](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Tło|Brak|  
|![Przycisk podziału wyłączone](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Pierwszego planu (tekst)|`Environment.ComboBoxItemTextInactive`|  
|![Przycisk podziału wyłączone](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Pierwszego planu (symbol)|`Environment.CommandBarTextInactive`|  
|![Przycisk podziału wyłączone](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Obramowanie|Brak|  
|![Przycisk podziału wyłączone](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Separator|Brak|  
  
##### <a name="more-options-and-overflow-buttons"></a>Przyciski "Overflow ma wartość" i więcej opcji  
 Przycisk "Więcej opcji" jest używany, gdy grupy pasek poleceń jest możliwe do dostosowania, albo dodając lub usuwając przyciski paska poleceń powiązanych. Przycisk "Overflow" jest wyświetlany, gdy pasek poleceń zostały obcięte ze względu na Brak miejsca w poziomie, a po kliknięciu pokazuje menu zawierające przyciski paska poleceń nie może być wyświetlany. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw tokenów nazwy.  
  
 ![Więcej opcji poprawek](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")  
  
 Użyj...  
 niestandardowe "więcej opcji" lub "Overflow" przycisków.  
  
 Nie używaj...  
 dla przycisków, które nie mają podobne funkcje do bardziej opcji lub przycisku "Overflow".  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")<br /><br /> **Więcej opcji**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsGlyph`|  
|![Przycisk przepełnienie](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")<br /><br /> **przepełnienia**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Przycisk przepełnienie](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")<br /><br /> **przepełnienia**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsGlyph`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Więcej opcji po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Overflow po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")<br /><br /> **przepełnienia**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Overflow po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")<br /><br /> **przepełnienia**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji naciśnięty](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Więcej opcji naciśnięty](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Przepełnienie naciśnięty](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")<br /><br /> **przepełnienia**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Przepełnienie naciśnięty](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")<br /><br /> **przepełnienia**|Pierwszego planu (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Okna dokumentów  
 Nie ma potrzeby replikowanie okna dokumentu, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolory używane w oknach dokumentów, tak, aby Twój interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.  
  
 Korzystając z tokenów kolor okna dokumentu, należy uważać, aby używać ich tylko dla podobnych elementów oraz zawsze par. Jeśli nie zrobisz, będziesz mieć nieoczekiwane wyniki w interfejsie użytkownika.  
  
#### <a name="document-window-frame"></a>Ramka okna dokumentu  
 Okna dokumentów może być zadokowane w IDE lub zmiennoprzecinkową jako oddzielne okno. Gdy okno dokumentu jest liczb zmiennoprzecinkowych poza IDE, ona nadal znajduje się w źródle dokumentu i ma tła, obramowania, tekstu i kolorów karty, które są takie same jak, gdy jest on częścią środowiska IDE. Jednak dokumentu znajduje się wewnątrz ramki, który ma swój własny tło obramowania i kolorów tekstu. Gdy okna narzędziowe są zadokowane w źródle dokumentu, dziedziczą zachowanie i koloru dla swoich kart z nazwy tokenu okien dokumentu.  
  
 ![Okno zadokowane dokumentu poprawek](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")  
  
 **Okno zadokowane dokumentu**  
  
 ![Przestawne okna dokumentu poprawek](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")  
  
 **Przestawne okna dokumentu.**  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okno dokumentu.  
  
 Nie używaj...  
 dla dowolnego interfejsu użytkownika, których nie chcesz automatycznie umożliwia zmianę powłoki ma aktualizacji motywu.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|Dokument: zadokowany lub liczb zmiennoprzecinkowych|Tło|Zależy od typu dokumentu|  
|Dokument: zadokowany lub liczb zmiennoprzecinkowych|Pierwszego planu (tekst)|Zależy od typu dokumentu|  
|Dokument: zadokowany lub liczb zmiennoprzecinkowych|Obramowanie|`Environment.ToolWindowBorder`|  
|![Ramka skupia się](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Ramka: Opływanie, fokus**|Tło|`Environment.ToolWindowFloatingFrame`|  
|![Ramka skupia się](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Ramka: Opływanie, fokus**|Pierwszego planu (tekst)|`Environment.ToolWindowFloatingFrame`|  
|![Ramka skupia się](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Ramka: Opływanie, fokus**|Pierwszego planu (symbol)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Ramka skupia się](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Ramka: Opływanie, fokus**|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
|![Ramka skupia się](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Ramka: Opływanie, fokus**|Obramowanie (symbol)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Ustaw przezroczyste|  
|![Po przeniesieniu fokusu ramki](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Tło|`Environment.ToolWindowFloatingFrameInactive`|  
|![Po przeniesieniu fokusu ramki](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Pierwszego planu (tekst)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Po przeniesieniu fokusu ramki](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Pierwszego planu (symbol)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Po przeniesieniu fokusu ramki](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Obramowanie|`Environment.MainWindowInactiveBorder`|  
|![Po przeniesieniu fokusu ramki](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Obramowanie (symbol)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Ustaw przezroczyste|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ramka koncentruje się na przesunięciu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Ramka: Opływanie, fokus**|Tło (symbol)|`Environment.RaftedWindowButtonHoverActive`|  
|![Ramka koncentruje się na przesunięciu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Ramka: Opływanie, fokus**|Pierwszego planu (symbol)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Ramka koncentruje się na przesunięciu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Ramka: Opływanie, fokus**|Obramowanie (symbol)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Po przeniesieniu fokusu po najechaniu wskaźnikiem ramki](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Tło (symbol)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Po przeniesieniu fokusu po najechaniu wskaźnikiem ramki](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Pierwszego planu (symbol)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Po przeniesieniu fokusu po najechaniu wskaźnikiem ramki](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Ramka: liczb zmiennoprzecinkowych, po przeniesieniu fokusu**|Obramowanie (symbol)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Ramka skupia się po naciśnięciu](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Ramka: Opływanie, fokus**|Tło (symbol)|`Environment.RaftedWindowButtonDown`|  
|![Ramka skupia się po naciśnięciu](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Ramka: Opływanie, fokus**|Pierwszego planu (symbol)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Ramka skupia się po naciśnięciu](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Ramka: Opływanie, fokus**|Obramowanie (symbol)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Karty dokumentów  
 Karty dokumentów znajdują się w kanale kartę, aby wskazać, które dokumenty są obecnie otwarte, oraz które z nich jest bieżąca wybrane lub aktywnego dokumentu. Okna narzędzi również może być zadokowane w kanale kartę dokumentu, jeśli użytkownik przełączy je ma. W takiej sytuacji używają takich samych kolorów karty jako okna dokumentu. Czy tworzenie interfejsu użytkownika chcesz zawsze odpowiada kolory okna dokumentu (w tym aktualizacje motywu lub jeśli są zainstalowane nowe motywy), a następnie odwoływać się do tych tokenów kolorów.  
  
 ![Karty dokumentów poprawek](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować karty dokumentów i automatycznie pobierał kompozycję aktualizacje lub nowe kolory motywu.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, gdy powłoka ma motyw aktualizacji.  
  
##### <a name="open-document-tabs"></a>Otwórz dokument karty  
 Każdy otwarty dokument ma kartę w kanale kartę dokumentu, który wyświetla jego nazwę. Dokumenty można albo wybrać lub otworzyć w tle, a ich karty odzwierciedlać te stany:  
  
- Wybrane karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie dobrze. Kartę wybraną ma obramowanie dokumentu, które dobrze rozszerza między górną krawędzią dokumentu.  
  
- Karty w tle są żadnych kart dokumentu, które nie są aktualnie wybrana karta. Po kliknięciu stają się wybranej karty i uzyskania wszystkich obramowania, tekstu i tła kolorów z tymi nazwami tokenu.  
  
  ![Karta otwartym dokumencie poprawek](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")  
  
  Użyj...  
  Podczas tworzenia karty niestandardowego dokumentu.  
  
  Nie używaj...  
  -   dla karty tymczasowe (wersja zapoznawcza).  
  
- dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
##### <a name="selected-tab"></a>Wybranej karty  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Kartę wybraną skupia się](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Karcie wybrany dokument skupia się**|Tło|`Environment.FileTabSelectedGradientTop`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Kartę wybraną skupia się](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Karcie wybrany dokument skupia się**|Pierwszego planu (tekst)|`Environment.FileTabSelectedText`|  
|![Kartę wybraną skupia się](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Karcie wybrany dokument skupia się**|Obramowanie|`Environment.FileTabSelectedBorder`<br /><br /> Ustaw kolor tła.|  
|![Kartę wybraną skupia się](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Karcie wybrany dokument skupia się**|Obramowanie dokumentu|`Environment.FileTabDocumentBorderBackground`|  
  
 **Po przeniesieniu fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Po przeniesieniu fokusu kartę wybraną](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument, po przeniesieniu fokusu**|Tło|`Environment.FileTabInactiveGradientTop`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Po przeniesieniu fokusu kartę wybraną](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument, po przeniesieniu fokusu**|Pierwszego planu (tekst)|`Environment.FileTabInactiveText`|  
|![Po przeniesieniu fokusu kartę wybraną](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument, po przeniesieniu fokusu**|Obramowanie|`Environment.FileTabInactiveBorder`<br /><br /> Ustaw kolor tła.|  
|![Po przeniesieniu fokusu kartę wybraną](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument, po przeniesieniu fokusu**|Obramowanie dokumentu|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Karta tła  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta tła](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Tło|`Environment.FileTabBackground`|  
|![Karta tła](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Pierwszego planu (tekst)|`Environment.FileTabText`|  
|![Karta tła](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Obramowanie|`Environment.FileTabBorder`<br /><br /> Ustaw kolor tła.|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta tło po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Karta tło po najechaniu wskaźnikiem**|Tło|`Environment.FileTabHotGradientTop`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Karta tło po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Karta tło po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.FileTabHotText`|  
|![Karta tło po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Karta tło po najechaniu wskaźnikiem**|Obramowanie|`Environment.FileTabHotBorder`<br /><br /> Ustaw kolor tła.|  
  
##### <a name="preview-tab"></a>Karta (wersja zapoznawcza)  
 Karta (wersja zapoznawcza) pojawia się po prawej stronie kanału kartę dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksploratora rozwiązań. On działa w wersji zapoznawczej dokumentu, a także zapewnia możliwość nie zamykaj dokumentu po lewej stronie kanału karty dokumentu. Otwórz kartę tylko jeden (wersja zapoznawcza) może być otwarty naraz. Podgląd karty mają zarówno w tle i wybranych stanów, takie jak karty i może być ukierunkowane lub po przeniesieniu fokusu w ich stanie aktywnym.  
  
 ![Karta Podgląd poprawek](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")  
  
 Użyj...  
 dowolne miejsce tworzenia tymczasowych (wersja zapoznawcza) i ma pewien element, aby dopasować bieżący kolor karcie podglądu.  
  
 Nie używaj...  
 -   dla każdego rodzaju dokumentu lub kartę, która nie jest tymczasowe (wersja zapoznawcza).  
  
- dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
  **Karta wybranego (wersja zapoznawcza): Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta (wersja zapoznawcza) koncentruje się](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Karta specjalistyczny (wersja zapoznawcza)**|Tło|`Environment.FileTabProvisionalSelectedActive`|  
|![Karta (wersja zapoznawcza) koncentruje się](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Karta specjalistyczny (wersja zapoznawcza)**|Pierwszego planu (tekst)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Karta (wersja zapoznawcza) koncentruje się](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Karta specjalistyczny (wersja zapoznawcza)**|Obramowanie|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Ustaw kolor tła.|  
|![Karta (wersja zapoznawcza) koncentruje się](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Karta specjalistyczny (wersja zapoznawcza)**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Karta wybranego (wersja zapoznawcza): Po przeniesieniu fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta (wersja zapoznawcza) po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Karta po przeniesieniu fokusu (wersja zapoznawcza)**|Tło|`Environment.FileTabProvisionalSelectedInactive`|  
|![Karta (wersja zapoznawcza) po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Karta po przeniesieniu fokusu (wersja zapoznawcza)**|Pierwszego planu (tekst)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Karta (wersja zapoznawcza) po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Karta po przeniesieniu fokusu (wersja zapoznawcza)**|Obramowanie|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Karta (wersja zapoznawcza) po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Karta po przeniesieniu fokusu (wersja zapoznawcza)**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Karta (wersja zapoznawcza) tła: Domyślne**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła w wersji zapoznawczej](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tła**|Tło|`Environment.FileTabProvisionalInactive`|  
|![Karta tła w wersji zapoznawczej](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tła**|Pierwszego planu (tekst)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Karta tła w wersji zapoznawczej](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tła**|Obramowanie|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Ustaw kolor tła.|  
  
 **Karta (wersja zapoznawcza) tła: Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła (wersja zapoznawcza) po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tło po najechaniu wskaźnikiem**|Tło|`Environment.FileTabProvisionalHover`|  
|![Karta tła (wersja zapoznawcza) po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tło po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.FileTabProvisionalHoverForeground`|  
|![Karta tła (wersja zapoznawcza) po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **W wersji zapoznawczej zarządzania tab tab tło po najechaniu wskaźnikiem**|Obramowanie|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Ustaw kolor tła.|  
  
##### <a name="document-overflow-button"></a>Przycisk przepełnienie dokument  
 Przycisk przepełnienie dokument jest obecny, jeśli istnieje jeden lub więcej dokumentów otworzyć, niezależnie od tego, czy brak miejsca w pionie w bieżącej konfiguracji, aby dopasować wszystkich kartach dokumentów. Menu rozwijanego przepełnienie dokumentu, które są kontrolowane przez **CommandBarMenu** kolory (zobacz [menu](../misc/shared-colors.md#BKMK_CommandMenus)), zostanie wyświetlona lista wszystkich otwartych dokumentach widoczna i ukryta, i zmienia się glif przepełnienia w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale kartę.  
  
 ![Przepełnienie poprawek](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")  
  
 Użyj...  
 Podczas tworzenia niestandardowego dokumentu przycisku przepełnienia.  
  
 Nie używaj...  
 -   dla interfejsu użytkownika, który nie jest podobne do przycisku przepełnienia.  
  
- dla przycisków przepełnienie paska poleceń.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Przycisk przepełnienie dokument**|Tło|`Environment.DocWellOverflowButtonBackground`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Przycisk przepełnienie dokument**|Pierwszego planu (symbol)|`Environment.DocWellOverflowButtonGlyph`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Przycisk przepełnienie dokument**|Obramowanie|Brak|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Overflow po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Przycisk przepełnienie dokument po najechaniu wskaźnikiem**|Tło|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Overflow po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Przycisk przepełnienie dokument po najechaniu wskaźnikiem**|Pierwszego planu (symbol)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Overflow po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Przycisk przepełnienie dokument po najechaniu wskaźnikiem**|Obramowanie|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przepełnienie naciśnięty](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Naciśnięty przycisk przepełnienie dokument**|Tło|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Przepełnienie naciśnięty](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Naciśnięty przycisk przepełnienie dokument**|Pierwszego planu (symbol)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Przepełnienie naciśnięty](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Naciśnięty przycisk przepełnienie dokument**|Obramowanie|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Okna narzędzi  
 Nie ma potrzeby replikowanie okien narzędziowych, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolorów używanych w oknach narzędzi, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.  
  
 ![Okno narzędzia poprawek](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
#### <a name="tool-window-frame"></a>Ramki okna narzędzi  
 Okna narzędzi w programie Visual Studio są używane w przypadku wielu różnych zadań, a może znajdować się w jednej z kilku różnych stanów. Jeśli okno narzędzi jest otwarty, można przypisać do dowolnego z czterech bokach obszar dokumentu. Okna narzędzi można również liczb zmiennoprzecinkowych poza IDE, co pozwala na można zmieniać pozycji w dowolnym miejscu w ramach ekranu użytkownika. Zmiennoprzecinkowe systemu windows zawsze znajdują się na górze IDE. Na koniec okna narzędzi może być zadokowane jako okien dokumentu i są wyświetlane na karcie w dokumencie dobrze. Okna narzędzi, które zostały zadokowane jako okien dokumentu mają kolor w części za pomocą nazwy tokenu okien dokumentu.  
  
 ![Ramka okna narzędzia poprawek](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
 **Zadokowane**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Okno zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")|Tło|`Environment.ToolWindowBackground`|  
|![Okno zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")|Obramowanie|`Environment.ToolWindowBorder`|  
  
 **Zmiennoprzecinkowa: fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Okna narzędzi, które skupia się](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")|Tło|`Environment.ToolWindowBackground`|  
|![Okna narzędzi, które skupia się](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Zmiennoprzecinkowa: po przeniesieniu fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Po przeniesieniu fokusu okna narzędzi](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")|Tło|`Environment.ToolWindowBackground`|  
|![Po przeniesieniu fokusu okna narzędzi](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")|Obramowanie|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi  
 Obramowania paska tytułu nie jest PRAWDA obramowanie, ale Gruba linia wzdłuż górnej krawędzi paska tytułu. Nie ma w Nazwa tokenu dla jego stanu po przeniesieniu fokusu.  
  
 ![Pasek tytułu okna narzędzia poprawek](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pasek tytułu skupia się](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Pasek tytułu fokusem**|Tło|`Environment.TitleBarActiveGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pasek tytułu skupia się](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Pasek tytułu fokusem**|Pierwszego planu (tekst)|`Environment.TitleBarActiveText`|  
|![Pasek tytułu skupia się](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Pasek tytułu fokusem**|Obramowanie|`Environment.TitleBarActiveBorder`<br /><br /> Ustaw kolor tła.|  
|![Pasek tytułu skupia się](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Pasek tytułu fokusem**|Przeciągnij uchwyt|`Environment.TitleBarDragHandleActive`|  
  
 **Po przeniesieniu fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Po przeniesieniu fokusu paska tytułu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Pasek tytułu po przeniesieniu fokusu**|Tło|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Po przeniesieniu fokusu paska tytułu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Pasek tytułu po przeniesieniu fokusu**|Pierwszego planu (tekst)|`Environment.TitleBarInactiveText`|  
|![Po przeniesieniu fokusu paska tytułu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Pasek tytułu po przeniesieniu fokusu**|Obramowanie|Brak|  
|![Po przeniesieniu fokusu paska tytułu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Pasek tytułu po przeniesieniu fokusu**|Przeciągnij uchwyt|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Przyciski paska tytułu  
 ![Przycisk paska tytułu poprawek](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")  
  
 Użyj...  
 przycisków, które są wyświetlane w interfejs użytkownika, który używa tokenów kolor z paski tytułu okna narzędzia.  
  
 Nie używaj...  
 -   w przypadku przycisków, które pojawiają się w innych lokalizacjach.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł paska przycisk skupia się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Fokus**|Tło|Brak|  
|![Tytuł paska przycisk skupia się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Fokus**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Tytuł paska przycisk skupia się](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Fokus**|Obramowanie|Brak|  
|![Tytuł paska przycisku po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Tło|Brak|  
|![Tytuł paska przycisku po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Tytuł paska przycisku po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Obramowanie|Brak|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu, który skupia się na przesunięciu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Fokus**|Tło|`Environment.ToolWindowButtonHoverActive`|  
|![Przycisk paska tytułu, który skupia się na przesunięciu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Fokus**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Przycisk paska tytułu, który skupia się na przesunięciu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Fokus**|Obramowanie|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Tytuł paska przycisku po przeniesieniu fokusu po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Tło|`Environment.ToolWindowButtonHoverInactive`|  
|![Tytuł paska przycisku po przeniesieniu fokusu po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Tytuł paska przycisku po przeniesieniu fokusu po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Obramowanie|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł paska przycisk fokus i naciśnięciu](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Fokus**|Tło|`Environment.ToolWindowButtonDown`|  
|![Tytuł paska przycisk fokus i naciśnięciu](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Fokus**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Tytuł paska przycisk fokus i naciśnięciu](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Fokus**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
|![Przycisk paska tytułu, po przeniesieniu fokusu i po naciśnięciu](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Po przeniesieniu fokusu**|Tło|`Environment.ToolWindowButtonDown`|  
|![Przycisk paska tytułu, po przeniesieniu fokusu i po naciśnięciu](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (symbol)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Przycisk paska tytułu, po przeniesieniu fokusu i po naciśnięciu](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Po przeniesieniu fokusu**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Karty okna narzędzi  
 ![Karta okna narzędzia poprawek](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
 **Wybranej karty**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta okna narzędzia skupia się](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Karta okna narzędzia wybrane, ukierunkowane**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna narzędzia skupia się](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Karta okna narzędzia wybrane, ukierunkowane**|Pierwszego planu (tekst)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Karta okna narzędzia skupia się](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Karta okna narzędzia wybrane, ukierunkowane**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw kolor tła.|  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta w oknie narzędzia po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Karta okna narzędzia zaznaczona, po przeniesieniu fokusu**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Karta w oknie narzędzia po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Karta okna narzędzia zaznaczona, po przeniesieniu fokusu**|Pierwszego planu (tekst)|`Environment.ToolWindowTabSelectedText`|  
|![Karta w oknie narzędzia po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Karta okna narzędzia zaznaczona, po przeniesieniu fokusu**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw kolor tła.|  
  
 **Karta tła**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia do tła**|Tło|`Environment.ToolWindowTabGradientBegin`<br /><br /> Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.|  
|![Karta tła okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia do tła**|Pierwszego planu (tekst)|`Environment.ToolWindowTabText`|  
|![Karta tła okna narzędzia](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia do tła**|Obramowanie|`Environment.ToolWindowTabBorder`|  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła okna narzędzia po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tło po najechaniu wskaźnikiem**|Tło|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Ustaw na tę samą wartość koloru w programie Visual Studio 2013 zatrzymania gradientu.|  
|![Karta tła okna narzędzia po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tło po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.ToolWindowTabMouseOverText`|  
|![Karta tła okna narzędzia po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tło po najechaniu wskaźnikiem**|Obramowanie|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Ustaw kolor tła.|  
  
#### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart  
 ![Automatyczne&#45;ukrywanie poprawek](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")  
  
 Użyj...  
 dowolne miejsce służy do utworzenia interfejsu użytkownika, który chcesz dopasować karty okna ukryte automatycznie narzędzi.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, nie chcesz zmienić automatycznie, jeśli powłoka ma aktualizacji motywu.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Automatyczne&#45;Ukrywanie karty](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Domyślną kartę autoukrywanie**|Tło|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Automatyczne&#45;Ukrywanie karty](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Domyślną kartę autoukrywanie**|Pierwszego planu (tekst)|`Environment.AutoHideTabText`|  
|![Automatyczne&#45;Ukrywanie karty](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Domyślną kartę autoukrywanie**|Obramowanie|`Environment.AutoHideTabBorder`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Automatyczne&#45;Ukrywanie karty po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Autoukrywanie kartę po najechaniu wskaźnikiem**|Tło|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Automatyczne&#45;Ukrywanie karty po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Autoukrywanie kartę po najechaniu wskaźnikiem**|Pierwszego planu (tekst)|`Environment.AutoHideTabMouseOverText`|  
|![Automatyczne&#45;Ukrywanie karty po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Autoukrywanie kartę po najechaniu wskaźnikiem**|Obramowanie|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Typowe kontrolki udostępnionego  
 Używając standardowego paska poleceń programu Visual Studio w Twojej funkcji, będziesz mieć dostęp do formantów powłoki ze stylem, a powinien nie re szablonu tych wspólnych formantów. Jednak jeśli potrzebujesz do tworzenia paska poleceń niestandardowych, może być konieczne do tworzenia kontrolek niestandardowych również. W takim przypadku upewnij się, że Użyj poprawne nazwy tokenu dla każdego z następujących formantów interfejsu użytkownika jest zgodne z pozostałą częścią programu Visual Studio.  
  
#### <a name="search-box"></a>Pole wyszukiwania  
 Możliwe, używaj wspólnej kontroli wyszukiwania oferowanych przez środowisko Visual Studio. Kolory pole wyszukiwania znajdują się w kategorii "SearchControl" **ShellColors.pkgdef** pliku, który zawiera token nazwy pola wejściowego, przycisk akcji, przycisk listy rozwijanej i menu rozwijanego.  
  
 Pole wyszukiwania może być jednym z kilku Państw, z których niektóre są wzajemnie wykluczających się:  
  
- "Skupia się" lub "po przeniesieniu fokusu" odnosi się do czy kursor znajduje się w polu tekstowym.  
  
- "Active" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadził zapytania wyszukiwania w polu tekstowym.  
  
- "Aktywowaniu" oznacza, że użytkownik ma moused w polu wyszukiwania za pomocą myszy (ten stan zastępuje inne stany).  
  
- "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączone dla bieżącego kontekstu.  
  
  ![Pole wyszukiwania poprawek](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")  
  
  Użyj...  
  Podczas projektowania pole wyszukiwania niestandardowego.  
  
  Nie używaj...  
  -   dla wszystkich elementów, który nie jest pole wyszukiwania.  
  
- dla każdego elementu, który nie ma zawsze do dopasowania wyszukiwania polu interfejsu użytkownika.  
  
  **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe wyszukiwania skupia się](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Pola wejściowego**|Tło|`SearchControl.FocusedBackground`|  
|![Pole wejściowe wyszukiwania skupia się](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`SearchControl.FocusedBackground`|  
|![Pole wejściowe wyszukiwania skupia się](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Pola wejściowego**|Obramowanie|`SearchControl.FocusedBorder`|  
|![Pole wejściowe wyszukiwania skupia się](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Pola wejściowego**|Separator|`SearchControl.FocusedDropDownSeparator`|  
|![Fokus przycisku akcji Wyszukaj](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Akcja przycisku**|Tło|Brak|  
|![Fokus przycisku akcji Wyszukaj](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (symbol wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Fokus przycisku akcji Wyszukaj](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (Zatrzymaj symbol)|`SearchControl.StopGlyph`|  
|![Fokus przycisku akcji Wyszukaj](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (Wyczyść symbol)|`SearchControl.ClearGlyph`|  
|![Fokus przycisku akcji Wyszukaj](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Akcja przycisku**|Obramowanie|Brak|  
|![Listy wyszukiwania&#45;naciśnięty przycisk skupia się](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.FocusedDropDownButton`|  
|![Listy wyszukiwania&#45;naciśnięty przycisk skupia się](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Listy wyszukiwania&#45;naciśnięty przycisk skupia się](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Po przeniesieniu fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pola wejściowego**|Tło|`SearchControl.SearchActiveBackground`|  
|![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pola wejściowego**|Pierwszego planu (tekst)|`SearchControl.SearchActiveBackground`|  
|![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pola wejściowego**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pola wejściowego**|Separator|`SearchControl.DropDownSeparator`|  
|![Pole wejściowe wyszukiwania po przeniesieniu fokusu i nieaktywnych](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pola wejściowego**|Tło|`SearchControl.Unfocused`|  
|![Pole wejściowe wyszukiwania po przeniesieniu fokusu i nieaktywnych](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pola wejściowego**|Pierwszego planu (tekst)|`SearchControl.Unfocused`|  
|![Pole wejściowe wyszukiwania po przeniesieniu fokusu i nieaktywnych](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pola wejściowego**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Pole wejściowe wyszukiwania po przeniesieniu fokusu i nieaktywnych](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pola wejściowego**|Separator|`SearchControl.DropDownSeparator`|  
|![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Akcja przycisku**|Tło|Brak|  
|![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (symbol wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (Zatrzymaj symbol)|`SearchControl.StopGlyph`|  
|![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Akcja przycisku**|Pierwszego planu (Wyczyść symbol)|`SearchControl.ClearGlyph`|  
|![Przycisk wyszukiwania akcji po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Akcja przycisku**|Obramowanie|Brak|  
|![Listy wyszukiwania&#45;naciśnięty przycisk po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.UnfocusedDropDownButton`|  
|![Listy wyszukiwania&#45;naciśnięty przycisk po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Listy wyszukiwania&#45;naciśnięty przycisk po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Akcja przycisku**|Tło|`SearchControl.ActionButtonMouseDown`|  
|![Naciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Akcja przycisku**|Pierwszego planu (symbol)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Naciśnięty przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Akcja przycisku**|Obramowanie|`SearchControl.ActionButtonMouseDownBorder`|  
|![Listy wyszukiwania&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.MouseDownDropDownButton`|  
|![Listy wyszukiwania&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Listy wyszukiwania&#45;dół wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Wyróżnione (tylko tekst)**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe tekst wyróżniony**|Tło|`SearchControl.Selection`|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe tekst wyróżniony**|Pierwszego planu (tekst)|`SearchControl.FocusedBackground`|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe tekst wyróżniony**|Obramowanie|Brak|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe tekst wyróżniony**|Separator|`SearchControl.FocusedDropDownSeparator`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Pola wejściowego**|Tło|`SearchControl.Disabled`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Pola wejściowego**|Pierwszego planu (tekst)|`SearchControl.Disabled`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Pola wejściowego**|Obramowanie|`SearchControl.DisabledBorder`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Pola wejściowego**|Separator|`SearchControl.DropDownSeparator`|  
|![Wyszukiwanie akcji przycisk wyłączone](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Akcja przycisku**|Tło|Brak|  
|![Wyszukiwanie akcji przycisk wyłączone](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Akcja przycisku**|Pierwszego planu (symbol)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Wyszukiwanie akcji przycisk wyłączone](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Akcja przycisku**|Obramowanie|Brak|  
|![Listy wyszukiwania&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Listy wyszukiwania&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszego planu (symbol)|`SearchControl.DisabledDownButtonGlyph`|  
|![Listy wyszukiwania&#45;naciśnięty przycisk wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|Brak|  
  
##### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania  
 Menu rozwijane pole wyszukiwania ma być nieco bardziej skomplikowane niż inne menu rozwijanych w programie Visual Studio. "Sugerowane wyszukiwania" i sekcje "Opcje wyszukiwania" może występować samodzielnie, lub ze sobą w menu, a każdy z nich jest kolorowe oddzielnie. Wiersz również oddziela te dwie sekcje, gdy pojawiają się ze sobą i obramowanie wokół menu rozwijane całego.  
  
 ![Listy wyszukiwania&#45;poprawek w dół](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")  
  
 Użyj...  
 -   Podczas tworzenia listy rozwijanej wyszukiwania niestandardowego.  
  
- Prawidłowe nazwy tokenu dla składników poprawnej listy.  
  
  Nie używaj...  
  -   Aby uzyskać listy rozwijane, które pojawiają się w innych kontekstach.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Domyślne (nie innych Państw)**  
  
|Element|Nazwa tokenu: Category.Color|  
|-------------|--------------------------------|  
|Obramowanie|`SearchControl.PopupBorder`|  
|Separator|`SearchControl.PopupSectionHeaderSeparator`|  
|W tle|`Environment.DropShadowBackground`|  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukaj sugerowane](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Pierwszego planu (tekst)|`SearchControl.PopupItemText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole)**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole)**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole)**|Pierwszego planu (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszego planu (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukaj sugerowane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Pierwszego planu (tekst)|`SearchControl.PopupMouseOverItemText`|  
|![Wyszukaj sugerowane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Pole wyboru wyszukiwania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole)**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje po najechaniu wskaźnikiem wyszukiwania](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole)**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opcje po najechaniu wskaźnikiem wyszukiwania](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Pole wyboru wyszukiwania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole)**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Opcje po najechaniu wskaźnikiem wyszukiwania](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Pole wyboru wyszukiwania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole)**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Opcje po najechaniu wskaźnikiem wyszukiwania](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukaj sugerowane naciśnięty](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje naciśnięty wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane naciśnięty](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje naciśnięty wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane naciśnięty](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole)**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opcje naciśnięty wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszego planu (pole tekstowe)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Wyszukaj sugerowane naciśnięty](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole)**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Opcje naciśnięty wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Nie są używane w nowoczesny interfejs użytkownika z motywami, istnieją ograniczniki gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane naciśnięty](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole)**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
|![Opcje naciśnięty wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszego planu (tekst łącza)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 Hiperlink jest jeden formant, który nie ma parę tła/na pierwszym planie. We wszystkich przypadkach należy użyć hiperłącze kolor pierwszego planu, który pojawi się prawidłowo na ciemny i symulowanych map bitowych białe tło. Jeśli nie używa tokenu kolor kontrolki hiperlinku, pojawią się domyślny kolor systemu dla "naciśnięty", "który będzie flash czerwony. To sygnał, formant nie używa tokenu kolor odpowiednie środowisko.  
  
 ![Hiperłącze poprawek](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")  
  
 Użyj...  
 Kiedy należy utworzyć niestandardowy hiperlink.  
  
 Nie używaj...  
 dla wszystkich elementów, które nie są hiperłączem.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Domyślne hiperłącze](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")|Pierwszego planu (tekst)|`Environment.PanelHyperlink`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącza po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")|Pierwszego planu (tekst)|`Environment.PanelHyperlinkHover`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze naciśnięty](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")|Pierwszego planu (tekst)|`Environment.PanelHyperlinkPressed`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze wyłączone](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")|Pierwszego planu (tekst)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Pasek informacyjny  
 Infobars są używane do Podaj więcej informacji na temat danego kontekstu i zawsze pojawiają się w górnej części okna dokumentu lub okna narzędzi.  
  
 ![Pasek informacyjny poprawek](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")  
  
 Użyj...  
 Podczas tworzenia niestandardowego infobars.  
  
 Nie używaj...  
 dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego.  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Pasek informacyjny**|Tło|`Environment.InfoBackground`|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Pasek informacyjny**|Pierwszego planu (tekst)|`Environment.InfoText`|  
|![Pasek informacyjny](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Pasek informacyjny**|Obramowanie|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Pasek przewijania  
 Paski przewijania mają różne przez środowisko Visual Studio i nie będą musiały mieć motywów. Jednak można zdecydować, czy chcesz korzystać kolorów używanych na paski przewijania, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.  
  
 ![Pasek przewijania poprawek](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")  
  
 Użyj...  
 Podczas tworzenia interfejsu użytkownika, który chcesz dopasować paski przewijania w programie Visual Studio.  
  
 Nie używaj...  
 dla wszystkich elementów, nie chcesz zawsze odpowiadać paska przewijania interfejsu użytkownika.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")<br /><br /> **Pasek przewijania**|Pasek przewijania|`Environment.ScrollBarBackground`|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")<br /><br /> **Pasek przewijania**|Pierwszego planu (przycisku przewijania)|`Environment.ScrollBarThumbBackground`|  
|![Paska strzałki przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")<br /><br /> **Strzałki przewijania**|Tło|`Environment.ScrollBarArrowBackground`<br /><br /> Ustaw kolor paska przewijania.|  
|![Paska strzałki przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")<br /><br /> **Strzałki przewijania**|Pierwszego planu (symbol)|`Environment.ScrollBarArrowGlyph`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")<br /><br /> **Pasek przewijania**|Pasek przewijania|`Environment.ScrollBarBackground`|  
|![Pasek przewijania po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")<br /><br /> **Pasek przewijania**|Pierwszego planu (przycisku przewijania)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Przewiń w pasku strzałkę po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br /><br /> **Strzałki przewijania**|Tło|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Ustaw kolor paska przewijania.|  
|![Przewiń w pasku strzałkę po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br /><br /> **Strzałki przewijania**|Pierwszego planu (symbol)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto paska przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")<br /><br /> **Pasek przewijania**|Pasek przewijania|`Environment.ScrollBarBackground`|  
|![Naciśnięto paska przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")<br /><br /> **Pasek przewijania**|Pierwszego planu (przycisku przewijania)|`Environment.ScrollBarThumbPressedBackground`|  
|![Paska kliknięciu strzałki przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br /><br /> **Strzałki przewijania**|Tło|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Ustaw ten sam kolor jak pasek przewijania.|  
|![Paska kliknięciu strzałki przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br /><br /> **Strzałki przewijania**|Pierwszego planu (symbol)|`Environment.ScrollBarArrowGlyphPressed`|  
  
####  <a name="BKMK_TreeView"></a> Widok drzewa  
 Kilkoma oknami narzędzi, w tym Eksploratora rozwiązań, Eksploratora serwera i widoku klasy implementuje hierarchiczne schematu organizacyjnego którego kolory są kontrolowane przez nazw kolorów w kategorii TreeView. Wszystkie elementy w widoku drzewa mają kolor tła i tekstu. Elementy, które zostały zagnieżdżone elementy podrzędne mają także symbole, które wskazują, czy element jest rozwijane czy zwijane.  
  
 ![Widok drzewa poprawek](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")  
  
 Użyj...  
 wszędzie, musisz zaimplementować hierarchiczny widok organizacji.  
  
 Nie używaj...  
 -   dla wszystkich elementów, który nie jest podobny do widoku drzewa.  
  
- w dowolnej kombinacji tła/pierwszego planu, inny niż określony.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Tło|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Pierwszego planu (tekst)|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Pierwszego planu (symbol)|`TreeView.Glyph`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Obramowanie|Brak|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Widoku drzewa w przesunięciu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Tło|`TreeView.Background`|  
|![Widoku drzewa w przesunięciu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Pierwszego planu (tekst)|`TreeView.Background`|  
|![Widoku drzewa w przesunięciu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Pierwszego planu (symbol)|`TreeView.GlyphMouseOver`|  
|![Widoku drzewa w przesunięciu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Obramowanie|Brak|  
  
 **Przeciągnij kursor nad**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Dragover widok drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Tło|`TreeView.DragOverItem`|  
|![Dragover widok drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Pierwszego planu (tekst)|`TreeView.DragOverItem`|  
|![Dragover widok drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Pierwszego planu (symbol)|`TreeView.DragOverItemGlyph`|  
|![Dragover widok drzewa](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Obramowanie|Brak|  
  
 **Wybrane**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Fokus widoku drzewa](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Fokus widoku drzewa](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Fokus**|Pierwszego planu (tekst)|`TreeView.SelectedItemActive`|  
|![Fokus widoku drzewa](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Fokus**|Pierwszego planu (symbol)|`TreeView.SelectedItemActiveGlyph`|  
|![Fokus widoku drzewa](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Fokus**|Obramowanie|`TreeView.FocusVisualBorder`|  
|![Po przeniesieniu fokusu w widoku drzewa](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Tło|`TreeView.SelectedItemInactive`|  
|![Po przeniesieniu fokusu w widoku drzewa](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (tekst)|`TreeView.SelectedItemInactive`|  
|![Po przeniesieniu fokusu w widoku drzewa](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (symbol)|`TreeView.SelectedItemInactiveGlyph`|  
|![Po przeniesieniu fokusu w widoku drzewa](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Po przeniesieniu fokusu**|Obramowanie|Brak|  
  
 **Umieść kursor nad wybrane**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Koncentruje się na przesunięciu widoku drzewa](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Koncentruje się na przesunięciu widoku drzewa](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Fokus**|Pierwszego planu (tekst)|`TreeView.SelectedItemActive`|  
|![Koncentruje się na przesunięciu widoku drzewa](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Fokus**|Pierwszego planu (symbol)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Koncentruje się na przesunięciu widoku drzewa](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Fokus**|Obramowanie|Brak`TreeView.FocusVisualBorder`|  
|![Widoku drzewa po przeniesieniu fokusu w przesunięciu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Tło|`TreeView.SelectedItemInactive`|  
|![Widoku drzewa po przeniesieniu fokusu w przesunięciu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (tekst)|`TreeView.SelectedItemInactive`|  
|![Widoku drzewa po przeniesieniu fokusu w przesunięciu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Pierwszego planu (symbol)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Widoku drzewa po przeniesieniu fokusu w przesunięciu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Po przeniesieniu fokusu**|Obramowanie|Brak|  
  
#### <a name="button-controls"></a>formanty przycisków  
 ![Kontrolka przycisku poprawek](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")  
  
 Użyj...  
 w przypadku przycisków w źródle dokumentu, którą chcesz zintegrować z kompozycji programu Visual Studio (światło, ciemny, niebieski lub kompozycję Duży kontrast systemu).  
  
 Nie używaj...  
 dla przycisków, które będą wyświetlane na tle niestandardowego, który nie jest częścią motywu programu Visual Studio.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")|Przycisk|`CommonControls.Button`|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")|Obramowanie przycisku|`CommonControls.ButtonBorder`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk wyłączone](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")|Przycisk|`CommonControls.ButtonDisabled`|  
|![Przycisk wyłączone](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")|Obramowanie przycisku|`CommonControls.ButtonBorderDisabled`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")|Przycisk|`CommonControls.ButtonHover`|  
|![Przycisk po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")|Obramowanie przycisku|`CommonControls.ButtonBorderHover`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")|Przycisk|`CommonControls.ButtonPressed`|  
|![Wciśnięcie przycisku](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")|Obramowanie przycisku|`CommonControls.ButtonBorderPressed`|  
  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Fokus przycisku](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")|Przycisk|`CommonControls.ButtonFocused`|  
|![Fokus przycisku](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")|Obramowanie przycisku|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Formanty pól wyboru  
 ![Pole wyboru poprawek](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")  
  
 Użyj...  
 Formanty pól wyboru znajdujących się w dokumencie dobrze.  
  
 Nie używaj...  
 dla dowolnego interfejsu użytkownika, który nie jest kontrolkę pola wyboru.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Tło|`CommonControls.CheckBoxBackground`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Obramowanie|`CommonControls.CheckBoxBorder`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Tekst|`CommonControls.CheckBoxText`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Symbol|`CommonControls.CheckBoxGlyph`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Tło|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Obramowanie|`CommonControls.CheckBoxBorderDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Tekst|`CommonControls.CheckBoxTextDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Symbol|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Tło|`CommonControls.CheckBoxBackgroundHover`|  
|![Pole wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Obramowanie|`CommonControls.CheckBoxBorderHover`|  
|![Pole wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Tekst|`CommonControls.CheckBoxTextHover`|  
|![Pole wyboru po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Symbol|`CommonControls.CheckBoxGlyphHover`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|![Pole wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Obramowanie|`CommonControls.CheckBoxBorderPressed`|  
|![Pole wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Tekst|`CommonControls.CheckBoxTextPressed`|  
|![Pole wyboru naciśnięty](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Symbol|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru, które skupia się](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Tło|`CommonControls.CheckBoxBackgroundFocused`|  
|![Pole wyboru, które skupia się](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Obramowanie|`CommonControls.CheckBoxBorderFocused`|  
|![Pole wyboru, które skupia się](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Tekst|`CommonControls.CheckBoxTextFocused`|  
|![Pole wyboru, które skupia się](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Symbol|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Upuść formantów pola kombi/pola  
 ![Upuść&#45;dół&#47;poprawek pola kombi](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")  
  
 Użyj...  
 listy rozwijane i pole kombi pola, które są również częścią dokumentu.  
  
 Nie używaj...  
 -   dla dowolnego interfejsu użytkownika, który nie jest listy rozwijanej lub pola kombi.  
  
- Aby uzyskać [listy rozwijanej](../misc/shared-colors.md#BKMK_CommandDropDown) lub [pola kombi](../misc/shared-colors.md#BKMK_CommandComboBox) na pasku poleceń.  
  
  **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Tło|`CommonControls.ComboBoxBackground`|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Obramowanie|`CommonControls.ComboBoxBorder`|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Tekst|`CommonControls.ComboBoxText`|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Separator|`CommonControls.ComboBoxSeparator`|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Symbol|`CommonControls.ComboBoxGlyph`|  
|![Upuść&#45;dół&#47;pola kombi](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Tło glifów|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Wyłączone**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Tło|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Obramowanie|`CommonControls.ComboBoxBorderDisabled`|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Tekst|`CommonControls.ComboBoxTextDisabled`|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Separator|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Symbol|`CommonControls.ComboBoxGlyphDisabled`|  
|![Upuść&#45;dół&#47;pola kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Tło|`CommonControls.ComboBoxBackgroundHover`|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Obramowanie|`CommonControls.ComboBoxBorderHover`|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Tekst|`CommonControls.ComboBoxTextHover`|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Separator|`CommonControls.ComboBoxSeparatorHover`|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Symbol|`CommonControls.ComboBoxGlyphHover`|  
|![Upuść&#45;dół&#47;pola kombi po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Tło|`CommonControls.ComboBoxBackgroundPressed`|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Obramowanie|`CommonControls.ComboBoxBorderPressed`|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Tekst|`CommonControls.ComboBoxTextPressed`|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Separator|`CommonControls.ComboBoxSeparatorPressed`|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Symbol|`CommonControls.ComboBoxGlyphPressed`|  
|![Upuść&#45;dół&#47;pola kombi naciśnięty](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Fokus**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Tło|`CommonControls.ComboBoxBackgroundFocused`|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Obramowanie|`CommonControls.ComboBoxBorderFocused`|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Tekst|`CommonControls.ComboBoxTextFocused`|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Separator|`CommonControls.ComboBoxSeparatorFocused`|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Symbol|`CommonControls.ComboBoxGlyphFocused`|  
|![Upuść&#45;dół&#47;pola kombi, które skupia się](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Tło glifów|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Wybór danych wejściowych tekstu**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;wprowadź tekst pola kombi](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")|Wyróżnij|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Naciśnięto — widok elementu listy**  
  
|Składnik|Element|Nazwa tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackground`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackgroundHover`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorder`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderHover`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderPressed`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderFocused`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemText`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextHover`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextPressed`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextFocused`|  
|![Upuść&#45;dół&#47;widoku listy pole kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Tło w tle|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Formanty danych tabelarycznych (siatki)  
 Formanty danych tabelarycznych, znany także jako formantach siatki są wspólnych formantów dla programu Visual Studio, który może służyć do prezentowania dużych ilości danych w wielu kolumnach. Formanty standardowe dane tabelaryczne znajdują się w wielu miejscach w programie Visual Studio: Lista błędów okna narzędzia, raporty funkcji IntelliTrace i widok sterty w pamięci, między innymi. Zawsze używaj kontrolek standardowych danych tabelarycznych, pod warunkiem. W sporadycznych przypadkach możesz utracić dostęp do formantów standardowych danych tabelarycznych. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika jest zgodne z innymi formantami danych tabelarycznych w programie Visual Studio.  
  
 ![Dane tabelaryczne &#40;formant siatki&#41; poprawek](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")  
  
 Użyj...  
 Aby uzyskać tabelaryczny lub kontrolki siatki.  
  
 Nie używaj...  
 dla wszelkich elementów interfejsu użytkownika, który nie jest formantem tabelarycznych lub siatkę.  
  
##### <a name="column-headers"></a>Nagłówki kolumn  
 Nagłówki kolumn składają się z tło, obramowanie, tekst tytułu i opcjonalnie symbol zwykle używany podczas siatki są posortowane według tej kolumny.  
  
|Stan|Element|Nazwa tokenu: Category.Color|  
|-----------|-------------|--------------------------------|  
|Domyślny|Tło|`Header.Default`|  
|Domyślny|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|Domyślny|Pierwszego planu (symbol)|`Header.Glyph`|  
|Domyślny|Obramowanie|`Header.SeparatorLine`|  
|Po wskazaniu wskaźnikiem|Tło|`Header.MouseOver`|  
|Po wskazaniu wskaźnikiem|Pierwszego planu (tekst)|`Environment.CommandBarTextHover`|  
|Po wskazaniu wskaźnikiem|Pierwszego planu (symbol)|`Header.MouseOverGlyph`|  
|Po wskazaniu wskaźnikiem|Obramowanie|`Header.SeparatorLine`|  
|Naciśnięto|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|Naciśnięto|Pierwszego planu (tekst)|`CommonControls.CheckBoxBorderPressed`|  
|Naciśnięto|Pierwszego planu (symbol)|`CommonControls.CheckBoxTextPressed`|  
|Naciśnięto|Obramowanie|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Elementy widoku listy  
 Elementy widoku listy składają się z tła i jego zawartość. Zawartość może być tekst i/lub ikonę.  
  
|Stan|Element|Nazwa tokenu: Category.Color|  
|-----------|-------------|--------------------------------|  
|Domyślny|Tło|Przezroczyste|  
|Domyślny|Pierwszego planu (tekst)|`Environment.CommandBarTextActive`|  
|Domyślny|Obramowanie|Brak|  
|Zaznaczone (aktywny)|Tło|`TreeView.SelectedItemActive`|  
|Zaznaczone (aktywny)|Pierwszego planu (tekst)|`TreeView.SelectedItemActiveText`|  
|Zaznaczone (aktywny)|Obramowanie|Brak|  
|Zaznaczone (nieaktywny)|Tło|`TreeView.SelectedItemInactive`|  
|Zaznaczone (nieaktywny)|Pierwszego planu (tekst)|`TreeView.SelectedItemInactiveText`|  
|Zaznaczone (nieaktywny)|Obramowanie|Brak|  
  
### <a name="manifest-designer"></a>Manifest Designer  
 Manifest Designer został zaprojektowany jako sposób, aby ułatwić edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Gdy nie ma udostępnionego framework dostępne do użycia, może być odpowiednia dla Ciebie dopasować układ i kolory kart orientacji/nawigacji i ogólną strukturę. Aby uzyskać więcej informacji na temat szczegółów układ zobacz [układu dla programu Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Projektant manifestu poprawek](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")  
  
 Użyj...  
 -   dla projektantów, które są podobne do projektanta manifestu.  
  
- zamiast przy użyciu karty wspólne kontroluje również w górnej części edytora w obrębie dokumentu.  
  
  Nie używaj...  
  -   Jeśli masz więcej niż sześć kart.  
  
- dla wszelkich elementów interfejsu użytkownika, który nie ma struktury, takich jak projektant manifestów.  
  
|Stan|Składnik|Element|Nazwa tokenu: Category.Color|  
|-----------|---------------|-------------|--------------------------------|  
|Domyślne (wybrane)|Tab|Tło|`ManifestDesigner.TabActive`|  
|Domyślne (wybrane)|Tab|Obramowanie|Brak|  
|Domyślne (wybrane)|Okienko opisu|Tło|`ManifestDesigner.DescriptionPane`|  
|Domyślne (wybrane)|Strona zawartości|Tło|`ManifestDesigner.Background`|  
|Domyślne (wybrane)|Strona zawartości|Tekst pomocy w oknie dialogowym|`ManifestDesigner.WatermarkText`<br /><br /> Ta nazwa tokenu jest niezgodna z jego funkcji.|  
|Inne niż wybrane|Tab|Tło|`ManifestDesigner.Tab.Inactive`|  
|Po wskazaniu wskaźnikiem|Tab|Tło|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Znakowanie  
 Program Visual Studio obsługuje, tagowanie, co pozwala użytkownikowi zadeklarować można wyszukiwać słowa kluczowe na potrzeby śledzenia. Na przykład menedżerów projektów i programistów umożliwia Team Foundation Server (TFS) tagów elementów roboczych. W poniższych tabelach podać nazw kolorów zarówno samego znacznika, jak i "zamknąć ikonę" symbol, umieść kursor i wybranych stanów.  
  
 ![Znakowanie poprawek](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")  
  
 Użyj...  
 dla interfejsu użytkownika, który obsługuje znakowanie.  
  
 Nie używaj...  
 dla wszystkich innych typów interfejsu użytkownika.  
  
#### <a name="tag"></a>Tag  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")<br /><br /> **Default**|Tło|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")<br /><br /> **Default**|Pierwszego planu (tekst)|`Tag.Background`|  
|![Tag po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")<br /><br /> **Po wskazaniu wskaźnikiem**|Tło|`Tag.HoverBackground`|  
|![Tag po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")<br /><br /> **Po wskazaniu wskaźnikiem**|Pierwszego planu (tekst)|`Tag.HoverBackgroundText`|  
|![Tag naciśnięty](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")<br /><br /> **Naciśnięto**|Tło|`Tag.PressedBackground`|  
|![Tag naciśnięty](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")<br /><br /> **Naciśnięto**|Pierwszego planu (tekst)|`Tag.PressedBackgroundText`|  
|![Zaznaczony tag](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")<br /><br /> **Wybrane**|Tło|`Tag.SelectedBackground`|  
|![Zaznaczony tag](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")<br /><br /> **Wybrane**|Pierwszego planu (tekst)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Symbol (ikonę zamknięcia)  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;symbol&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")<br /><br /> **Domyślne (ustawienie domyślne tagu)**|Tło|Brak|  
|![Tag &#40;symbol&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")<br /><br /> **Domyślne (ustawienie domyślne tagu)**|Pierwszego planu (symbol)|`Tag.TagHoverGlyph`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;symbol&#41; po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Po wskazaniu wskaźnikiem (ustawienie domyślne tagu)**|Tło|`Tag.TagHoverGlyphHoverBackground`|  
|![Tag &#40;symbol&#41; po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Po wskazaniu wskaźnikiem (ustawienie domyślne tagu)**|Pierwszego planu (symbol)|`Tag.TagHoverGlyphHover`|  
|![Tag &#40;symbol&#41; po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Po wskazaniu wskaźnikiem (ustawienie domyślne tagu)**|Obramowanie|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Naciśnięto**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;symbol&#41; naciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Naciśnięto (ustawienie domyślne tagu)**|Tło|`Tag.TagHoverGlyphPressedBackground`|  
|![Tag &#40;symbol&#41; naciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Naciśnięto (ustawienie domyślne tagu)**|Pierwszego planu (symbol)|`Tag.TagHoverGlyphPressed`|  
|![Tag &#40;symbol&#41; naciśnięty](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Naciśnięto (ustawienie domyślne tagu)**|Obramowanie|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Domyślne wybrany symbol znacznika**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Zaznaczony tag](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")<br /><br /> **Domyślne (wybrane tag)**|Tło|Brak|  
|![Zaznaczony tag](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")<br /><br /> **Domyślne (wybrane tag)**|Pierwszego planu (symbol)|`Tag.TagSelectedGlyph`|  
  
 **Wybrany symbol znacznika po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Tag wybrane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Po wskazaniu wskaźnikiem (wybrany tag)**|Tło|`Tag.TagSelectedGlyphHoverBackground`|  
|![Tag wybrane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Po wskazaniu wskaźnikiem (wybrany tag)**|Pierwszego planu (symbol)|`Tag.TagSelectedGlyphHover`|  
|![Tag wybrane po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Po wskazaniu wskaźnikiem (wybrany tag)**|Obramowanie|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Wybrano/symbol tagu wciśnięty**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Zaznaczony tag naciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **Po naciśnięciu (wybrany tag)**|Tło|`Tag.TagSelectedGlyphPressedBackground`|  
|![Zaznaczony tag naciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **Po naciśnięciu (wybrany tag)**|Foreground(Glyph)|`Tag.TagSelectedGlyphPressed`|  
|![Zaznaczony tag naciśnięty](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **Po naciśnięciu (wybrany tag)**|Obramowanie|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Powłoka  
  
#### <a name="background"></a>Tło  
 Tło środowiska składa się z dwóch warstw. Dolna warstwa jest jednolitego koloru, który obejmuje całe środowisko IDE. Górną warstwę mieści się w obszarze półki polecenia i między kanałami automatycznego ukrywania okna narzędzia na lewej lub prawej krawędzi środowiska IDE. Począwszy od programu Visual Studio 2013 warstwy tła górny i dolny są ustawione na ten sam kolor w motywy jasny i ciemny motyw.  
  
 ![Tło powłoki poprawek](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")  
  
 Użyj...  
 dla miejsc, które chcesz dopasować tło środowiska Visual Studio.  
  
 Nie używaj...  
 -   jako wypełnienia dla miejsc, które nie są tła powierzchni.  
  
-   jako tła, na którym chcesz umieścić elementy pierwszego planu.  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|Dolna warstwa|Tło|`Environment.EnvironmentBackground`|  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|Górną warstwę|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Górną warstwę|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Górną warstwę|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Górną warstwę|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Polecenie Półka  
 Dwa zestawy token nazwy są używane do tła półki polecenia: on ustawiony, na którym znajduje się na pasku menu, a drugi dla gdzie znajdują się paski poleceń. Grupa pasek indywidualne polecenie ma swoje własne wartości kolorów tła, które zostały omówione bardziej szczegółowo w sekcji "polecenie bar". Menu paska i polecenia paska tekstu omówiono w sekcji pasek menu i poleceń, odpowiednio.  
  
 ![Polecenie półki poprawek](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")  
  
 Użyj...  
 -   dla obszarów, w którym umieszcza się menu i paski narzędzi.  
  
- w tle poprawne / pierwszego planu token kombinacja nazwy.  
  
  Nie używaj...  
  dla obszarów, które nie są podobne do półki polecenia.  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|Pasek menu|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Pasek menu|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Pasek menu|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Pasek poleceń|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Pasek poleceń|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Pasek poleceń|Tło<br /><br /> *Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Przybornik  
 Przybornik jest jednym z typowych okien narzędzi, które jest najczęściej używany w programie Visual Studio. Jest zasadniczo kontrolki drzewa za pomocą specjalnych motywu i stylów zastosowana.  
  
 ![Przybornik poprawek](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")  
  
 Użyj...  
 Podczas projektowania okna narzędzi, które chcesz, aby zawsze były zgodne z przybornika powłoki.  
  
 Nie używaj...  
 dla każdego elementu, który nie jest podobne do przybornika interfejsu użytkownika lub jeśli wiesz, czy interfejs użytkownika będą mieć problemy, jeśli Przybornik powłoki kolory zmiany.  
  
 **Default**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli brak dostępnych kontrolek|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli brak dostępnych kontrolek|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszego planu (symbol)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszego planu (symbol)|`Environment.ToolboxContent`|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszego planu (tekst)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszego planu (tekst)|`Environment.ToolboxContent`|  
  
 **Po wskazaniu wskaźnikiem**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł podrzędny przybornika po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Przybornik umieść wskaźnik myszy na węzeł podrzędny**|Tło|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedynczych elementów|  
|![Węzeł podrzędny przybornika po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Przybornik umieść wskaźnik myszy na węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika po najechaniu wskaźnikiem](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Przybornik umieść wskaźnik myszy na węzeł podrzędny**|Pierwszego planu (tekst)|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedynczych elementów|  
  
 **Wybrane**  
  
|Składnik|Element|Nazwa tokenu: Category.Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł nadrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Węzeł nadrzędny fokusem**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Węzeł podrzędny fokusem**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł nadrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Węzeł nadrzędny fokusem**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Węzeł podrzędny fokusem**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł nadrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Węzeł nadrzędny fokusem**|Pierwszego planu (symbol)|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Węzeł podrzędny fokusem**|Pierwszego planu (symbol)|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł nadrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Węzeł nadrzędny fokusem**|Pierwszego planu (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika skupia się](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Węzeł podrzędny fokusem**|Pierwszego planu (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Po przeniesieniu fokusu węzła nadrzędnego przybornika](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny po przeniesieniu fokusu**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny bez fokusu**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Po przeniesieniu fokusu węzła nadrzędnego przybornika](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny po przeniesieniu fokusu**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny bez fokusu**|Obramowanie|Brak|  
|![Po przeniesieniu fokusu węzła nadrzędnego przybornika](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny po przeniesieniu fokusu**|Pierwszego planu (symbol)|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny bez fokusu**|Pierwszego planu (symbol)|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Po przeniesieniu fokusu węzła nadrzędnego przybornika](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny po przeniesieniu fokusu**|Pierwszego planu (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
|![Węzeł podrzędny przybornika po przeniesieniu fokusu](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny bez fokusu**|Pierwszego planu (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView) kategorii|  
  
## <a name="color-value-reference"></a>Odwołanie wartości koloru  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Składnik|Część|Element|Stan|Światła|Ciemny|Niebieski|Duży kontrast|  
|Linie podziału|||Domyślny|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Ekspander glifów||Pierwszy plan|Domyślny|||||  
|Ekspander glifów||Pierwszy plan|Po wskazaniu wskaźnikiem|||||  
|Ekspander glifów||Tło|Domyślny|||||  
|Ekspander glifów||Tło|Po wskazaniu wskaźnikiem|||||  
|Ekspander glifów||Obramowanie|Domyślny|||||  
|Ekspander glifów||Obramowanie|Po wskazaniu wskaźnikiem|||||