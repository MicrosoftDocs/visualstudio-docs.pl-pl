---
title: Kolory udostępnione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 76c04680b63eb362e02fdf26d817660d671b3b52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548359"
---
# <a name="shared-colors"></a>Kolory udostępnione
Tutaj wstaw wprowadzenie.  
  
## <a name="shared-colors"></a>Kolory udostępnione  
 Podczas projektowania interfejsu użytkownika, który używa typowych elementów programu Visual Studio Shell lub chcesz, aby element interfejsu był spójny z podobnymi funkcjami, Użyj istniejących nazw tokenów w plikach definicji pakietów, aby wybrać i przypisać kolory. Dzięki temu interfejs użytkownika pozostaje spójny z ogólnym środowiskiem programu Visual Studio i jest aktualizowany automatycznie po dodaniu lub zaktualizowaniu motywów.  
  
 W tym artykule opisano typowe elementy interfejsu użytkownika i używane przez nie nazwy tokenów, które można przywołać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje na temat uzyskiwania dostępu do tych tokenów kolorów, zobacz [usługę VSColor](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Upewnij się, że nazwy tokenów są poprawnie używane:  
  
- **Używaj nazw tokenów opartych na funkcjach, a nie na samym kolorze.** Wspólne kolory udostępnione są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko dla tych samych lub podobnych funkcji. Na przykład nie należy ponownie używać koloru naciśniętego pola kombi dla obracającej animacji postępu, tak samo jak kolor. Funkcje pola kombi i animacji są różne i jeśli kolor skojarzony z polem kombi zmieni się, może to nie być już odpowiedni kolor elementu animacji. Spójne użycie koloru pozwala na ukierunkowanie użytkowników i zapobieganie niepomyleniu.  
  
- **Używaj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które mają być używane z tekstem, będą mieć skojarzony kolor tekstu. Nie używaj kolorów tekstu innych niż określone dla danego tła. Jeśli nie ma skojarzonego koloru tekstu, nie używaj tego koloru tła dla każdej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą spowodować nieczytelny interfejs.  
  
- **Użyj kolorów kontroli odpowiednich dla ich lokalizacji.** W niektórych stanach niektóre kontrolki programu Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego wybierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów, które są odpowiednie dla lokalizacji, w której umieszczasz formant.  
  
> [!IMPORTANT]
> Nie można używać tokenów znajdujących się w kategorii "Start Page" lub "jabłecznik".  
  
### <a name="command-structures"></a>Struktury poleceń  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menu  
 Menu mogą wystąpić w kilku miejscach w Visual Studio 2013: główny pasek menu, osadzony w dokumencie lub w oknach narzędzi lub kliknij prawym przyciskiem myszy w różnych lokalizacjach w środowisku IDE. Implementacje menu skojarzonych z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiedniego elementu. Należy zawsze używać standardowej implementacji menu dostarczanej przez środowisko programu Visual Studio. Jednak w niektórych rzadkich przypadkach może nie mieć dostępu do standardowych menu programu Visual Studio. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w programie Visual Studio.  
  
 ![Menu Redline](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 — 000_MenuRedline")  
  
Użyj...  
- zawsze, gdy trzeba utworzyć niestandardowe menu.  
  
- gdy masz nowy składnik interfejsu użytkownika, który chcesz dopasować do menu programu Visual Studio.  
  
Nie używaj...  
sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu w określony sposób.  
  
##### <a name="menu-title"></a>Tytuł menu  
 Tytuły menu składają się z tła, obramowania i tekstu tytułu, a także symbolu opcjonalnego, zazwyczaj gdy menu znajduje się na pasku poleceń.  
  
 ![Tytuł menu Redline](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 — 001_MenuTitleRedline")  
  
Użyj...  
za każdym razem, gdy tworzysz tytuł menu niestandardowego.  
  
Nie używaj...  
- dla wszystkich elementów, które nie powinny być zawsze zgodne z tytułem menu.  
  
- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 — 002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Tło|Brak|  
|![Domyślny tytuł menu](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 — 002_MenuTitleDefault")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z wartością domyślną glifu](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (symbol)|`Environment.CommandBarMenuGlyph`|  
|![Tytuł menu z wartością domyślną glifu](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")<br /><br /> **Tytuł menu z glifem**|Obramowanie|Brak|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu przy aktywowaniu](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 — 004_MenuTitleHover")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Tytuł menu przy aktywowaniu](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 — 004_MenuTitleHover")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Tytuł menu z symbolem po aktywowaniu](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (symbol)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Tytuł menu z symbolem po aktywowaniu](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")<br /><br /> **Tytuł menu z glifem**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto tytuł menu](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 — 006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto tytuł menu](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 — 006_MenuTitlePressed")<br /><br /> **Tytuł menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Tytuł menu z naciśniętym symbolem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (symbol)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Tytuł menu z naciśniętym symbolem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")<br /><br /> **Tytuł menu z glifem**|Obramowanie|`Environment.CommandBarMenuBorder`<br /><br /> Tylko lewe, górne i prawe.|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Tło|Brak|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Pierwszy plan (symbol)|`Environment.CommandBarTextInactive`|  
|![Tytuł menu z wyłączonym glifem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br /><br /> **Tytuł menu z glifem**|Obramowanie|Brak|  
  
##### <a name="menu"></a>Menu  
 Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub symbolu podmenu. Zmiana koloru tła i tekstu przy aktywowaniu. Ten token koloru to para tła/pierwszego planu.  
  
 ![Elementy menu Redline](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 — 009_MenuItemRedline")  
  
 Użyj...  
 dla każdej listy rozwijanej, która jest uruchamiana z paska menu lub paska poleceń.  
  
Nie używaj...  
- dla każdej listy rozwijanej, która występuje w innym kontekście.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Tło|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Pierwszy plan (symbol podmenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Obramowanie|`Environment.CommandBarMenuBorder`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Tło ikony kanału|`Environment.CommandBarMenuIconBackground`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|Separator|`Environment.CommandBarMenuSeparator`|  
|![Domyślne menu](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 — 010_MenuDefault")<br /><br /> **Menu**|W tle|`Environment.DropShadowBackground`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 — 011_MenuChecked")<br /><br /> **Dane**|Znacznik wyboru|`Environment.CommandBarCheckBox`|  
|![Menu zaznaczone](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 — 011_MenuChecked")<br /><br /> **Dane**|Znacznik wyboru tła|`Environment.CommandBarSelectedIcon`|  
|![Wybrano menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 — 012_MenuSelected")<br /><br /> **Wybrano**|Tło ikony|`Environment.CommandBarSelected`|  
|![Wybrano menu](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 — 012_MenuSelected")<br /><br /> **Wybrano**|Obramowanie ikony|`Environment.CommandBarSelectedBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Aktywowanie menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 — 013_MenuHover")<br /><br /> **Element menu**|Tło|`Environment.CommandBarMenuItemMouseOver`|  
|![Aktywowanie menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 — 013_MenuHover")<br /><br /> **Element menu**|Pierwszy plan (tekst)|`Environment.CommandBarMenuItemMouseOver`|  
|![Aktywowanie menu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 — 013_MenuHover")<br /><br /> **Element menu**|Pierwszy plan (symbol podmenu)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Zaznaczono aktywowany menu](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 — 014_MenuHoverChecked")<br /><br /> **Dane**|Znacznik wyboru|`Environment.CommandBarCheckBoxMouseOver`|  
|![Zaznaczono aktywowany menu](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 — 014_MenuHoverChecked")<br /><br /> **Dane**|Znacznik wyboru tła|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Wybrano aktywowany menu](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 — 015_MenuHoverSelected")<br /><br /> **Wybrano**|Tło ikony|`Environment.CommandBarHoverOverSelected`|  
|![Wybrano aktywowany menu](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 — 015_MenuHoverSelected")<br /><br /> **Wybrano**|Obramowanie ikony|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 — 016_MenuDisabled")<br /><br /> Element menu|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Menu wyłączone](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 — 016_MenuDisabled")<br /><br /> Element menu|Pierwszy plan (symbol podmenu)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Wyłączono zaznaczenie opcji menu](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 — 017_MenuDisabledChecked")<br /><br /> Zaznaczono|Znacznik wyboru|`Environment.CommandBarCheckBoxDisabled`|  
|![Wyłączono zaznaczenie opcji menu](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 — 017_MenuDisabledChecked")<br /><br /> Zaznaczono|Znacznik wyboru tła|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Pasek poleceń  
 Pasek poleceń może pojawić się w wielu miejscach w środowisku IDE programu Visual Studio, w szczególności z półkami poleceń i osadzonych w oknach narzędzi lub dokumentów.  
  
 Ogólnie rzecz biorąc zawsze używaj standardowej implementacji paska poleceń dostarczonej przez środowisko programu Visual Studio. Zastosowanie mechanizmu standardowego gwarantuje, że wszystkie szczegóły wizualizacji będą wyświetlane poprawnie i że te elementy interaktywne będą stale działać z innymi kontrolkami paska poleceń programu Visual Studio. Jeśli jednak jest to konieczne, aby skompilować własny pasek poleceń, upewnij się, że styl jest poprawnie używany przy użyciu następujących nazw tokenów.  
  
 ![Pasek poleceń Redline](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 — 018_CommandBarRedline")  
  
 ![Przycisk przepełnienia Redline](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 — 019_OverflowButtonRedline")  
  
 Użyj...  
 w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.  
  
Nie używaj...  
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.  
  
##### <a name="command-bar-group"></a>Grupa paska poleceń  
 Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przyciski podzielone, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów są regulowane przez oddzielne nazwy tokenów i są omawiane osobno w innym miejscu w tym przewodniku. Linia separatora służy do dzielenia grupy paska poleceń na powiązane podgrupy.  
  
 ![Redline grupy paska poleceń](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 — 020_CommandBarGroupRedline")  
  
 Użyj...  
 w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio.  
  
Nie używaj...  
- dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń.  

- dla składników paska poleceń innych niż te, dla których określono nazwy tokenów.  
  
  **Domyślne** (nie inne Stany)  
  
|Element|Nazwa tokenu: Category. Color|  
|-------------|--------------------------------|  
|Tło|`Environment.CommandBarGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|Obramowanie|`Environment.CommandBarToolBarBorder`|  
|Przeciągnij uchwyt|`Environment.CommandBarDragHandle`|  
|Separator|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ikony poleceń  
 ![Ikona polecenia Redline](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 — 021_CommandIconRedline1")  
  
 ![Ikona polecenia Redline](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 — 022_CommandIconRedline2")  
  
 Użyj...  
 dla każdego przycisku, który zostanie umieszczony na pasku poleceń.  
  
Nie używaj...  
- dla kontrolek mających własne nazwy tokenów.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 — 023_CommandIconDefault")<br /><br /> **Domyślny**|Tło|Nie dotyczy (dziedziczy z poziomu tła paska poleceń)|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 — 023_CommandIconDefault")<br /><br /> **Domyślny**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Domyślna ikona polecenia](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 — 023_CommandIconDefault")<br /><br /> **Domyślny**|Obramowanie|Nie dotyczy|  
|![Wybrana domyślnie ikona polecenia](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Tło|`Environment.CommandBarSelected`|  
|![Wybrana domyślnie ikona polecenia](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Pierwszy plan (tekst)|`Environment.CommandBarTextSelected`|  
|![Wybrana domyślnie ikona polecenia](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")<br /><br /> **Wybrano**|Obramowanie|`Environment.CommandBarSelectedBorder`|  
  
 **Aktywowanie i klawiatura ukierunkowana**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Ikona polecenia — Umieść kursor](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 — 025_CommandIconHover")<br /><br /> **Standardowy przy aktywowaniu**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Ikona polecenia — Umieść kursor](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 — 025_CommandIconHover")<br /><br /> **Standardowy przy aktywowaniu**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Ikona polecenia — Umieść kursor](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 — 025_CommandIconHover")<br /><br /> **Standardowy przy aktywowaniu**|Obramowanie|`Environment.CommandBarBorder`|  
|![Ikona polecenia — Wybierz kursor](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")<br /><br /> **Wybrane przy aktywowaniu**|Tło|`Environment.CommandBarHoverOverSelected`|  
|![Ikona polecenia — Wybierz kursor](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")<br /><br /> **Wybrane przy aktywowaniu**|Pierwszy plan (tekst)|`Environment.CommandBarTextHoverOverSelected`|  
|![Ikona polecenia — Wybierz kursor](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")<br /><br /> **Wybrane przy aktywowaniu**|Obramowanie|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 — 027_CommandIconPressed")<br /><br /> **Ikona polecenia naciśniętego**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 — 027_CommandIconPressed")<br /><br /> **Ikona polecenia naciśniętego**|Pierwszy plan (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Naciśnięto ikonę polecenia](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 — 027_CommandIconPressed")<br /><br /> **Ikona polecenia naciśniętego**|Obramowanie|`Environment.CommandBarBorder`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 — 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączonego**|Tło|Nie dotyczy (dziedziczy z poziomu tła paska poleceń)|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 — 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączonego**|Pierwszy plan (tekst)|`Environment.CommandBarTextInactive`|  
|![Ikona polecenia wyłączona](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 — 028_CommandIconDisabled")<br /><br /> **Ikona polecenia wyłączonego**|Obramowanie|Nie dotyczy|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Pole kombi  
  
> [!IMPORTANT]
> Pola kombi są podobne do list rozwijanych, ale zawierają edytowalny region tekstu. Jeśli lista rozwijana nie zawiera regionu tekstu edytowalnego, użyj tokenów kolorów znalezionych w obszarze [listy rozwijanej](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Pole kombi Redline](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 — 029_ComboBoxRedline")  
  
Użyj...  
- podczas kompilowania niestandardowych pól kombi.  

- podczas tworzenia kontrolki paska poleceń, która jest podobna do pola kombi.  

Nie używaj...  
- dla wszystkich elementów, które nie zawsze pasują do interfejsu użytkownika paska poleceń.  

- gdy masz dostęp do pola kombi z stylem.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole kombi pola wejściowego](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxBackground`|  
|![Pole kombi pola wejściowego](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxText`|  
|![Pole kombi pola wejściowego](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxBorder`|  
|![Pole kombi pola wejściowego](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br /><br /> **Pole wejściowe**|Separator|Brak separatora|  
|![Pole kombi upuść&#45;przycisk w dół](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|Nie dotyczy (dziedziczy)|  
|![Pole kombi upuść&#45;przycisk w dół](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.ComboBoxGlyph`|  
|![Pole kombi&#47;upuść&#45;lista](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Tło|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pole kombi&#47;upuść&#45;lista](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemText`|  
|![Pole kombi&#47;upuść&#45;lista](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")<br /><br /> **Lista rozwijana**|Obramowanie|`Environment.ComboBoxPopupBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole kombi pola wejściowego przy aktywowaniu](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pole kombi pola wejściowego przy aktywowaniu](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxMouseOverText`|  
|![Pole kombi pola wejściowego przy aktywowaniu](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxMouseOverBorder`|  
|![Pole kombi pola wejściowego przy aktywowaniu](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxMouseOverSeparator`|  
|![Pole kombi&#47;upuść&#45;przycisk w dół na przycisku aktywowany](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Pole kombi&#47;upuść&#45;przycisk w dół na przycisku aktywowany](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.ComboBoxMouseOverGlyph`|  
|![Pole kombi&#47;upuść&#45;listy przy aktywowaniu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Tło (element menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Pole kombi&#47;upuść&#45;listy przy aktywowaniu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Pole kombi&#47;upuść&#45;listy przy aktywowaniu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")<br /><br /> **Lista rozwijana**|Obramowanie (element menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Pole kombi pola wejściowego z fokusem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxFocusedBackground`|  
|![Pole kombi pola wejściowego z fokusem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxFocusedText`|  
|![Pole kombi pola wejściowego z fokusem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxFocusedBorder`|  
|![Pole kombi pola wejściowego z fokusem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Pole kombi&#47;upuść&#45;przycisk w dół](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxFocusedButtonBackground`|  
|![Pole kombi&#47;upuść&#45;przycisk w dół](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxMouseDownBackground`|  
|![Naciśnięto pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxMouseDownText`|  
|![Naciśnięto pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxMouseDownBorder`|  
|![Naciśnięto pole wejściowe pola kombi](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br /><br /> **Pole wejściowe**|Separator|`Environment.ComboBoxMouseDownSeparator`|  
|![Pole kombi&#47;naciśnięcie przycisku upuść&#45;w dół](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Pole kombi&#47;naciśnięcie przycisku upuść&#45;w dół](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe pola kombi jest wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Tło|`Environment.ComboBoxDisabledBackground`|  
|![Pole wejściowe pola kombi jest wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`Environment.ComboBoxDisabledText`|  
|![Pole wejściowe pola kombi jest wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Obramowanie|`Environment.ComboBoxDisabledBorder`|  
|![Pole wejściowe pola kombi jest wyłączone](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br /><br /> **Pole wejściowe**|Separator|Brak separatora|  
|![Pole kombi&#47;upuść&#45;przycisk w dół wyłączone](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Pole kombi&#47;upuść&#45;przycisk w dół wyłączone](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Lista rozwijana  
  
> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale brak edytowalnych regionów tekstu. Jeśli lista rozwijana zawiera region tekstu edytowalnego, użyj tokenów kolorów znajdujących się w [polu kombi](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Porzuć&#45;w dół Redline](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 — 042_DropdownRedline")  
  
 Użyj...  
 podczas tworzenia niestandardowych kontrolek listy rozwijanej.  
  
Nie używaj...  
- dla wszystkich elementów, które nie są podobne do listy rozwijanej.  

- dla pól kombi lub przycisków podziału.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownBackground`|  
|![Upuść pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`DropDownText`|  
|![Upuść pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Obramowanie|`DropDownBorder`|  
|![Upuść pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br /><br /> **Pole wyboru**|Separator|Brak separatora|  
|![Przycisk Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 — 044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Przycisk Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 — 044_DropdownButton")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.DropDownGlyph`|  
|![Upuść&#45;ą listę](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")<br /><br /> **Lista rozwijana**|Tło|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Upuść&#45;ą listę](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemText`|  
|![Upuść&#45;ą listę](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")<br /><br /> **Lista rozwijana**|Obramowanie|`Environment.DropDownPopupBorder`|  
|![Upuść&#45;ą listę](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 — 045_DropdownList")<br /><br /> **Lista rozwijana**|W tle|`Environment.DropShadowBackground`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść pole wyboru&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Upuść pole wyboru&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`Environment.DropDownMouseOverText`|  
|![Upuść pole wyboru&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseOverBorder`|  
|![Upuść pole wyboru&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseOverSeparator`|  
|![Przycisk Porzuć&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseOverBackground`|  
|![Przycisk Porzuć&#45;w dół na aktywowaniu](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.DropDownMouseOverGlyph`|  
|![Upuść&#45;ą listę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 — 048_DropdownListHover")<br /><br /> **Lista rozwijana**|Tło (element menu)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Upuść&#45;ą listę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 — 048_DropdownListHover")<br /><br /> **Lista rozwijana**|Pierwszy plan (tekst)|`Environment.ComboBoxItemMouseOverText`|  
|![Upuść&#45;ą listę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 — 048_DropdownListHover")<br /><br /> **Lista rozwijana**|Obramowanie (element menu)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Tło|`Environment.DropDownMouseDownBackground`|  
|![Naciśnięto pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Pierwszy plan (tekst)|`Environment.DropDownMouseDownText`|  
|![Naciśnięto pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Obramowanie|`Environment.DropDownMouseDownBorder`|  
|![Naciśnięto pole wyboru&#45;w dół](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br /><br /> **Pole wyboru**|Separator|`Environment.DropDownButtonMouseDownSeparator`|  
|![Naciśnięto przycisk Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`Environment.DropDownButtonMouseDownBackground`|  
|![Naciśnięto przycisk Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść pole wyboru&#45;wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")|Tło|`Environment.DropDownDisabledBackground`|  
|![Upuść pole wyboru&#45;wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")|Pierwszy plan (tekst)|`Environment.DropDownDisabledText`|  
|![Upuść pole wyboru&#45;wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")|Obramowanie|`Environment.DropDownDisabledBorder`|  
|![Upuść pole wyboru&#45;wyłączone](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")|Separator|Brak separatora|  
|![Przycisk usuwania&#45;w dół jest wyłączony](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")|Tło|Nie dotyczy|  
|![Przycisk usuwania&#45;w dół jest wyłączony](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")|Pierwszy plan (symbol)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Przycisk podziału  
 Przyciski podziału współdzielą wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne nazwy tokenów przycisku akcji i listy rozwijanej są powtarzane w tym miejscu dla wygody. Lista rozwijana przycisku podziału to implementacje [menu](../misc/shared-colors.md#BKMK_CommandMenus)paska poleceń.  
  
 ![Przycisk podziału Redline](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 — 053_SplitButtonRedline")  
  
 Użyj...  
 podczas tworzenia niestandardowego przycisku podziału.  
  
Nie używaj...  
- dla innych rodzajów przycisków.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")<br /><br /> **Przycisk podziału (wartość domyślna)**|Tło|Brak|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")<br /><br /> **Przycisk podziału (wartość domyślna)**|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")<br /><br /> **Przycisk podziału (wartość domyślna)**|Pierwszy plan (symbol)|`Environment.CommandBarSplitButtonGlyph`|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")<br /><br /> **Przycisk podziału (wartość domyślna)**|Obramowanie|Nie dotyczy|  
|![Przycisk podziału](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 — 054_SplitButton")<br /><br /> **Przycisk podziału (wartość domyślna)**|Separator|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału po aktywowaniu](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")<br /><br /> **Przycisk podziału (przy aktywowaniu)**|Tło|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Przycisk podziału po aktywowaniu](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")<br /><br /> **Przycisk podziału (przy aktywowaniu)**|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|![Przycisk podziału po aktywowaniu](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")<br /><br /> **Przycisk podziału (przy aktywowaniu)**|Pierwszy plan (symbol)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Przycisk podziału po aktywowaniu](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")<br /><br /> **Przycisk podziału (przy aktywowaniu)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Przycisk podziału po aktywowaniu](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 — 055_SplitButtonHover")<br /><br /> **Przycisk podziału (przy aktywowaniu)**|Separator|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto przycisk podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (naciśnięto)**|Tło|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto przycisk podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (naciśnięto)**|Pierwszy plan (tekst)|`Environment.CommandBarTextMouseDown`|  
|![Naciśnięto przycisk podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (naciśnięto)**|Pierwszy plan (symbol)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Naciśnięto przycisk podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (naciśnięto)**|Obramowanie|`Environment.CommandBarBorder`|  
|![Naciśnięto przycisk podziału](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br /><br /> **Przycisk podziału (naciśnięto)**|Separator|Nie dotyczy|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Tło|Nie dotyczy|  
|![Przycisk podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Pierwszy plan (tekst)|`Environment.ComboBoxItemTextInactive`|  
|![Przycisk podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Pierwszy plan (symbol)|`Environment.CommandBarTextInactive`|  
|![Przycisk podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Obramowanie|Nie dotyczy|  
|![Przycisk podziału wyłączony](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br /><br /> **Przycisk podziału (wyłączony)**|Separator|Nie dotyczy|  
  
##### <a name="more-options-and-overflow-buttons"></a>Przyciski "więcej opcji" i "overflow"  
 Przycisk "więcej opcji" jest używany, gdy grupy paska poleceń można dostosowywać przez dodawanie lub usuwanie powiązanych przycisków paska poleceń. Przycisk "przepełnienie" pojawia się, gdy pasek poleceń został obcięty z powodu braku miejsca w poziomie, a w obszarze kliknij Pokaż menu zawierające przyciski paska poleceń, których nie można wyświetlić. Kolory tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.  
  
 ![Więcej opcji Redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 — 058_MoreOptionsRedline")  
  
 Użyj...  
 dla niestandardowych przycisków "więcej opcji" lub "overflow".  
  
 Nie używaj...  
 przyciski, które nie mają podobnej funkcjonalności, do przycisku "więcej opcji" lub "overflow".  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 — 059_MoreOptions")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Więcej opcji](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 — 059_MoreOptions")<br /><br /> **Więcej opcji**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsGlyph`|  
|![Przycisk przepełnienia](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 — 060_Overflow")<br /><br /> **Przepływ**|Tło|`Environment.CommandBarOptionsBackground`|  
|![Przycisk przepełnienia](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 — 060_Overflow")<br /><br /> **Przepływ**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Więcej opcji przy aktywowaniu](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 — 061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Więcej opcji przy aktywowaniu](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 — 061_MoreOptionsHover")<br /><br /> **Więcej opcji**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Przepełnienie przy aktywowaniu](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 — 062_OverflowOptions")<br /><br /> **Przepływ**|Tło|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Przepełnienie przy aktywowaniu](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 — 062_OverflowOptions")<br /><br /> **Przepływ**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto więcej opcji](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 — 063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto więcej opcji](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 — 063_MoreOptionsPressed")<br /><br /> **Więcej opcji**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Naciśnięto przepełnienie](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 — 064_OverflowPressed")<br /><br /> **Przepływ**|Tło|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto przepełnienie](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 — 064_OverflowPressed")<br /><br /> **Przepływ**|Pierwszy plan (symbol)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Okna dokumentów  
 Nie ma potrzeby replikowania okien dokumentów, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach dokumentów, aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.  
  
 W przypadku używania tokenów kolorów okna dokumentu należy zachować ostrożność, aby użyć ich tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, będziesz mieć nieoczekiwane wyniki w interfejsie użytkownika.  
  
#### <a name="document-window-frame"></a>Ramka okna dokumentu  
 Okna dokumentów mogą być zadokowane w środowisku IDE lub przestawne jako oddzielne okno. Gdy okno dokumentu jest przepływające poza IDE, nadal znajduje się w dokumencie i ma kolory tła, obramowania, tekstu i karty, które są takie same, jak gdy jest częścią IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne kolory tła, obramowania i tekstu. Gdy okna narzędzi są zadokowane w tym dokumencie, dziedziczą one zachowanie i kolor ich kart z nazw tokenów okna dokumentu.  
  
 ![Okno zadokowanego dokumentu Redline](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 — 065_DockedDocumentWindowRedline")  
  
 **Okno zadokowanego dokumentu**  
  
 ![Przestawne okno dokumentu Redline](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 — 066_FloatingDocumentWindowRedline")  
  
 **Przestawne okno dokumentu**  
  
 Użyj...  
 wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okna dokumentu.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, którego nie chcesz automatycznie zmieniać, jeśli powłoka ma aktualizację motywu.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|Dokument: zadokowane lub przestawne|Tło|Zależy od typu dokumentu|  
|Dokument: zadokowane lub przestawne|Pierwszy plan (tekst)|Zależy od typu dokumentu|  
|Dokument: zadokowane lub przestawne|Obramowanie|`Environment.ToolWindowBorder`|  
|![Ramka skoncentrowana](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Tło|`Environment.ToolWindowFloatingFrame`|  
|![Ramka skoncentrowana](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Pierwszy plan (tekst)|`Environment.ToolWindowFloatingFrame`|  
|![Ramka skoncentrowana](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Pierwszy plan (symbol)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Ramka skoncentrowana](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
|![Ramka skoncentrowana](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 — 067_FrameFocused")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Obramowanie (symbol)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Ustaw jako przezroczysty|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Tło|`Environment.ToolWindowFloatingFrameInactive`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Pierwszy plan (tekst)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Pierwszy plan (symbol)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Obramowanie|`Environment.MainWindowInactiveBorder`|  
|![Ramka nieskoncentrowana](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 — 068_FrameUnfocused")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Obramowanie (symbol)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Ustaw jako przezroczysty|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Ramka skoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 — 069_FrameFocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Tło (symbol)|`Environment.RaftedWindowButtonHoverActive`|  
|![Ramka skoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 — 069_FrameFocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Pierwszy plan (symbol)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Ramka skoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 — 069_FrameFocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Obramowanie (symbol)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Ramka nieskoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Tło (symbol)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Ramka nieskoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Pierwszy plan (symbol)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Ramka nieskoncentrowana na aktywowaniu](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")<br /><br /> **Ramka: zmiennoprzecinkowe, nieskoncentrowane**|Obramowanie (symbol)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto fokus ramki](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 — 071_FrameFocusedPressed")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Tło (symbol)|`Environment.RaftedWindowButtonDown`|  
|![Naciśnięto fokus ramki](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 — 071_FrameFocusedPressed")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Pierwszy plan (symbol)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Naciśnięto fokus ramki](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 — 071_FrameFocusedPressed")<br /><br /> **Ramka: zmiennoprzecinkowe, ukierunkowane**|Obramowanie (symbol)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Karty dokumentów  
 Karty dokumentów znajdują się w kanale karty, aby wskazać, które dokumenty są obecnie otwarte, wraz z których jeden jest bieżącym zaznaczonym lub aktywnym dokumentem. Okna narzędzi można także zadokować w kanale karty dokumentu, jeśli użytkownik umieści je w tym miejscu. W takiej sytuacji używają tych samych kolorów karty co okna dokumentu. Jeśli tworzysz interfejs użytkownika, który chcesz zawsze dopasować kolory okna dokumentu (w tym aktualizacje motywu lub zainstalować nowe motywy), odwołując się do tych tokenów kolorów.  
  
 ![Karta dokumentu Redline](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 — 072_DocumentTabRedline")  
  
 Użyj...  
 w dowolnym miejscu tworzysz interfejs użytkownika, który chcesz dopasować do kart dokumentów i automatycznie pobrać aktualizacje motywu lub nowe kolory motywu.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, gdy powłoka ma aktualizację motywu.  
  
##### <a name="open-document-tabs"></a>Otwórz karty dokumentów  
 Każdy otwarty dokument zawiera kartę w kanale karty dokumentu, który wyświetla jego nazwę. Dokumenty mogą być wybierane lub otwierane w tle, a ich karty odzwierciedlają te stany:  
  
- Wybrana karta przedstawia dokument, który jest aktualnie wyświetlany w dokumencie. Wybrana karta zawiera obramowanie dokumentu, które rozciąga się między górną krawędzią dokumentu.  
  
- Karty w tle to karty dokumentów, które nie są obecnie wybrane. Po kliknięciu stają się one wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.  
  
  ![Otwórz Redline karty dokumentu](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 — 073_OpenDocumentTabRedline")  
  
  Użyj...  
  podczas tworzenia niestandardowych kart dokumentów.  
  
  Nie używaj...  
  - dla kart tymczasowych (Podgląd).  
  
- dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
##### <a name="selected-tab"></a>Wybrana karta  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wybrana karta skoncentrowana](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br /><br /> **Karta wybrany dokument z fokusem**|Tło|`Environment.FileTabSelectedGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Wybrana karta skoncentrowana](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br /><br /> **Karta wybrany dokument z fokusem**|Pierwszy plan (tekst)|`Environment.FileTabSelectedText`|  
|![Wybrana karta skoncentrowana](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br /><br /> **Karta wybrany dokument z fokusem**|Obramowanie|`Environment.FileTabSelectedBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
|![Wybrana karta skoncentrowana](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br /><br /> **Karta wybrany dokument z fokusem**|Obramowanie dokumentu|`Environment.FileTabDocumentBorderBackground`|  
  
 **Bez fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wybrana karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument z fokusem**|Tło|`Environment.FileTabInactiveGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Wybrana karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument z fokusem**|Pierwszy plan (tekst)|`Environment.FileTabInactiveText`|  
|![Wybrana karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument z fokusem**|Obramowanie|`Environment.FileTabInactiveBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
|![Wybrana karta nieskoncentrowana](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br /><br /> **Karta wybrany dokument z fokusem**|Obramowanie dokumentu|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Karta tło  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Karta tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 — 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Tło|`Environment.FileTabBackground`|  
|![Karta tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 — 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Pierwszy plan (tekst)|`Environment.FileTabText`|  
|![Karta tło](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 — 076_BackgroundTab")<br /><br /> **Domyślna karta tła**|Obramowanie|`Environment.FileTabBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Karta tła na aktywowaniu](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 — 077_BackgroundTabHover")<br /><br /> **Karta tła na aktywowaniu**|Tło|`Environment.FileTabHotGradientTop`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Karta tła na aktywowaniu](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 — 077_BackgroundTabHover")<br /><br /> **Karta tła na aktywowaniu**|Pierwszy plan (tekst)|`Environment.FileTabHotText`|  
|![Karta tła na aktywowaniu](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 — 077_BackgroundTabHover")<br /><br /> **Karta tła na aktywowaniu**|Obramowanie|`Environment.FileTabHotBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
##### <a name="preview-tab"></a>Karta Podgląd  
 Karta Podgląd zostanie wyświetlona po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksplorator rozwiązań. Działa jako wersja zapoznawcza dokumentu, a także daje użytkownikowi możliwość otwarcia dokumentu po lewej stronie kanału karty dokumentu. Tylko jedna otwarta karta podglądu może być otwarta w danym momencie. Karty podglądu mają Stany tła i wybrane, takie jak otwarte karty i mogą być skoncentrowane lub nieskoncentrowane w stanie aktywnym.  
  
 ![Redline karty podglądu](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 — 078_PreviewTabRedline")  
  
 Użyj...  
 w dowolnym miejscu tworzysz tymczasową wersję zapoznawczą i chcesz, aby część elementu była zgodna z bieżącym kolorem karty podglądu.  
  
Nie używaj...  
- dla dowolnego rodzaju dokumentu lub karty, która nie jest tymczasowa (wersja zapoznawcza).  

- dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
  **Wybrana karta podglądu: skoncentrowana**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Zakładka zapoznawcza](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")<br /><br /> **Karta ukierunkowana wersja zapoznawcza**|Tło|`Environment.FileTabProvisionalSelectedActive`|  
|![Zakładka zapoznawcza](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")<br /><br /> **Karta ukierunkowana wersja zapoznawcza**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Zakładka zapoznawcza](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")<br /><br /> **Karta ukierunkowana wersja zapoznawcza**|Obramowanie|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
|![Zakładka zapoznawcza](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 — 079_PreviewTabFocused")<br /><br /> **Karta ukierunkowana wersja zapoznawcza**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Wybrana karta podglądu: nieskoncentrowany**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Nieskoncentrowana karta podglądu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br /><br /> **Nieskoncentrowana karta podglądu**|Tło|`Environment.FileTabProvisionalSelectedInactive`|  
|![Nieskoncentrowana karta podglądu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br /><br /> **Nieskoncentrowana karta podglądu**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Nieskoncentrowana karta podglądu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br /><br /> **Nieskoncentrowana karta podglądu**|Obramowanie|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Nieskoncentrowana karta podglądu](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br /><br /> **Nieskoncentrowana karta podglądu**|Obramowanie dokumentu|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Karta Podgląd w tle: domyślna**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła podglądu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")<br /><br /> **Karta tła karty podglądu**|Tło|`Environment.FileTabProvisionalInactive`|  
|![Karta tła podglądu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")<br /><br /> **Karta tła karty podglądu**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Karta tła podglądu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")<br /><br /> **Karta tła karty podglądu**|Obramowanie|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
 **Karta Podgląd w tle: aktywowanie**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła podglądu przy aktywowaniu](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty podglądu przy aktywowaniu**|Tło|`Environment.FileTabProvisionalHover`|  
|![Karta tła podglądu przy aktywowaniu](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty podglądu przy aktywowaniu**|Pierwszy plan (tekst)|`Environment.FileTabProvisionalHoverForeground`|  
|![Karta tła podglądu przy aktywowaniu](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")<br /><br /> **Karta tła karty podglądu przy aktywowaniu**|Obramowanie|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
##### <a name="document-overflow-button"></a>Przycisk przepełnienia dokumentu  
 Przycisk przepełnienia dokumentu jest obecny, jeśli istnieje co najmniej jeden otwarty dokument, bez względu na to, czy w bieżącej konfiguracji znajduje się odstęp w pionie, aby dopasować wszystkie karty dokumentu. Menu rozwijane przepełnienie dokumentu, które jest kontrolowane przez kolory **CommandBarMenu** (zobacz [menu](../misc/shared-colors.md#BKMK_CommandMenus)), wyświetla listę wszystkich otwartych dokumentów, zarówno widocznych, jak i ukrytych, oraz zmiany glifu przepełnienia w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale karty.  
  
 ![Przepełnienie Redline](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 — 083_OverflowRedline")  
  
Użyj...  
podczas tworzenia niestandardowego przycisku przepełnienia dokumentu.  

Nie używaj...  
- dla interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia.  

- dla przycisków przepełnienia paska poleceń.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przepływ](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 — 084_Overflow")<br /><br /> **Przycisk przepełnienia dokumentu**|Tło|`Environment.DocWellOverflowButtonBackground`|  
|![Przepływ](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 — 084_Overflow")<br /><br /> **Przycisk przepełnienia dokumentu**|Pierwszy plan (symbol)|`Environment.DocWellOverflowButtonGlyph`|  
|![Przepływ](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 — 084_Overflow")<br /><br /> **Przycisk przepełnienia dokumentu**|Obramowanie|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przepełnienie przy aktywowaniu](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 — 085_OverflowHover")<br /><br /> **Przycisk przepełnienia dokumentu po aktywowaniu**|Tło|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Przepełnienie przy aktywowaniu](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 — 085_OverflowHover")<br /><br /> **Przycisk przepełnienia dokumentu po aktywowaniu**|Pierwszy plan (symbol)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Przepełnienie przy aktywowaniu](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 — 085_OverflowHover")<br /><br /> **Przycisk przepełnienia dokumentu po aktywowaniu**|Obramowanie|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto przepełnienie](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 — 086_OverflowPressed")<br /><br /> **Przycisk przepełnienia naciśniętego dokumentu**|Tło|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Naciśnięto przepełnienie](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 — 086_OverflowPressed")<br /><br /> **Przycisk przepełnienia naciśniętego dokumentu**|Pierwszy plan (symbol)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Naciśnięto przepełnienie](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 — 086_OverflowPressed")<br /><br /> **Przycisk przepełnienia naciśniętego dokumentu**|Obramowanie|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Okna narzędzi  
 Nie ma potrzeby replikowania okien narzędzi, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach narzędzi, tak aby interfejs użytkownika zawsze pojawiał się w spójny sposób z tą częścią środowiska programu Visual Studio.  
  
 ![Okno narzędzi Redline](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 — 087_ToolWindowRedline")  
  
 Użyj...  
 wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
#### <a name="tool-window-frame"></a>Ramka okna narzędzi  
 Okna narzędzi w programie Visual Studio są używane dla wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzi jest otwarte, można je przypisać do dowolnej z czterech boków obszaru dokumentu. Okna narzędzi można również przepływać poza IDE, co umożliwia ich zmianę położenia w dowolnym miejscu na ekranie użytkownika. Przestawne okna zawsze znajdują się na wierzchu IDE. Na koniec okna narzędzi mogą być zadokowane jako okna dokumentu i wyświetlane jako karta w obszarze dokumentu. Okna narzędzi, które zostały zadokowane jako okna dokumentów, są kolorowe w części przy użyciu nazw tokenów okna dokumentu.  
  
 ![Ramka okna narzędzia Redline](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 — 088_ToolWindowFrameRedline")  
  
 Użyj...  
 wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Zadokowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Okno narzędzia zostało zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 — 089_ToolWindowDocked")|Tło|`Environment.ToolWindowBackground`|  
|![Okno narzędzia zostało zadokowane](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 — 089_ToolWindowDocked")|Obramowanie|`Environment.ToolWindowBorder`|  
  
 **Przestawne: skoncentrowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Okno narzędzia z fokusem](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 — 090_ToolWindowFocused")|Tło|`Environment.ToolWindowBackground`|  
|![Okno narzędzia z fokusem](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 — 090_ToolWindowFocused")|Obramowanie|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Zmiennoprzecinkowe: nieskoncentrowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Okno narzędzia bez fokusu](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")|Tło|`Environment.ToolWindowBackground`|  
|![Okno narzędzia bez fokusu](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")|Obramowanie|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi  
 Obramowanie paska tytułu nie jest obramowaniem o wartości true, ale jest to linia pogrubiona w górnej części paska tytułu. Nie ma nazwy tokenu dla stanu nieskoncentrowanego.  
  
 ![Pasek tytułu okna narzędzi Redline](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 — 092_ToolWindowTitleBarRedline")  
  
 Użyj...  
 wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pasek tytułu skoncentrowany](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")<br /><br /> **Priorytetowy pasek tytułu**|Tło|`Environment.TitleBarActiveGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pasek tytułu skoncentrowany](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")<br /><br /> **Priorytetowy pasek tytułu**|Pierwszy plan (tekst)|`Environment.TitleBarActiveText`|  
|![Pasek tytułu skoncentrowany](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")<br /><br /> **Priorytetowy pasek tytułu**|Obramowanie|`Environment.TitleBarActiveBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
|![Pasek tytułu skoncentrowany](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 — 093_TitleBarFocused")<br /><br /> **Priorytetowy pasek tytułu**|Przeciągnij uchwyt|`Environment.TitleBarDragHandleActive`|  
  
 **Bez fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pasek tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Tło|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pasek tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Pierwszy plan (tekst)|`Environment.TitleBarInactiveText`|  
|![Pasek tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Obramowanie|Nie dotyczy|  
|![Pasek tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br /><br /> **Nieskoncentrowany pasek tytułu**|Przeciągnij uchwyt|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Przyciski paska tytułu  
 ![Przycisk paska tytułu Redline](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 — 095_TitleBarButtonRedline")  
  
 Użyj...  
 w przypadku przycisków, które są wyświetlane w interfejsie użytkownika, które używają tokenów kolorów z pasków tytułu okna narzędzi.  
  
Nie używaj...  
- w przypadku przycisków, które są wyświetlane w innych lokalizacjach.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu — fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Tło|Nie dotyczy|  
|![Przycisk paska tytułu — fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Przycisk paska tytułu — fokus](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")<br /><br /> **Ustawiono fokus**|Obramowanie|Nie dotyczy|  
|![Przycisk paska tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Tło|Nie dotyczy|  
|![Przycisk paska tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Przycisk paska tytułu bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Obramowanie|Nie dotyczy|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Tło|`Environment.ToolWindowButtonHoverActive`|  
|![Przycisk paska tytułu skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Przycisk paska tytułu skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")<br /><br /> **Ustawiono fokus**|Obramowanie|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Przycisk paska tytułu bez fokusu po aktywowaniu](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Tło|`Environment.ToolWindowButtonHoverInactive`|  
|![Przycisk paska tytułu bez fokusu po aktywowaniu](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Przycisk paska tytułu bez fokusu po aktywowaniu](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Obramowanie|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk paska tytułu skoncentrowany i wciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Tło|`Environment.ToolWindowButtonDown`|  
|![Przycisk paska tytułu skoncentrowany i wciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Przycisk paska tytułu skoncentrowany i wciśnięty](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")<br /><br /> **Ustawiono fokus**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
|![Przycisk paska tytułu bez fokusu i został naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Tło|`Environment.ToolWindowButtonDown`|  
|![Przycisk paska tytułu bez fokusu i został naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Pierwszy plan (symbol)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Przycisk paska tytułu bez fokusu i został naciśnięty](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Obramowanie|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Karty okna narzędzi  
 ![Karta okna narzędzi Redline](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 — 102_ToolWindowTabRedline")  
  
 Użyj...  
 wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okien narzędzi.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Wybrana karta**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta okna narzędzi ukierunkowana](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")<br /><br /> **Zaznaczona, ukierunkowana Karta okna narzędzi**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna narzędzi ukierunkowana](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")<br /><br /> **Zaznaczona, ukierunkowana Karta okna narzędzi**|Pierwszy plan (tekst)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Karta okna narzędzi ukierunkowana](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")<br /><br /> **Zaznaczona, ukierunkowana Karta okna narzędzi**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta okna narzędzi bez fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")<br /><br /> **Zaznaczona, Karta okna narzędzia nieskoncentrowanego**|Tło|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna narzędzi bez fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")<br /><br /> **Zaznaczona, Karta okna narzędzia nieskoncentrowanego**|Pierwszy plan (tekst)|`Environment.ToolWindowTabSelectedText`|  
|![Karta okna narzędzi bez fokusu](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")<br /><br /> **Zaznaczona, Karta okna narzędzia nieskoncentrowanego**|Obramowanie|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
 **Karta tło**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła okna narzędzi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia tła**|Tło|`Environment.ToolWindowTabGradientBegin`<br /><br /> Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.|  
|![Karta tła okna narzędzi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia tła**|Pierwszy plan (tekst)|`Environment.ToolWindowTabText`|  
|![Karta tła okna narzędzi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")<br /><br /> **Karta okna narzędzia tła**|Obramowanie|`Environment.ToolWindowTabBorder`|  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Karta tła okna narzędzi przy aktywowaniu](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tła na aktywowaniu**|Tło|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Ustawienia gradientu są ustawione na wartość tego samego koloru w Visual Studio 2013.|  
|![Karta tła okna narzędzi przy aktywowaniu](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tła na aktywowaniu**|Pierwszy plan (tekst)|`Environment.ToolWindowTabMouseOverText`|  
|![Karta tła okna narzędzi przy aktywowaniu](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna narzędzia tła na aktywowaniu**|Obramowanie|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Ustaw na ten sam kolor, co tło.|  
  
#### <a name="auto-hide-tabs"></a>Autoukrywanie kart  
 ![Auto&#45;Ukryj Redline](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 — 107_AutoHideRedline")  
  
 Użyj...  
 w dowolnym miejscu tworzysz interfejs użytkownika, który chcesz dopasować do kart okna z autoukrywaniem.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Auto&#45;Ukryj kartę](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 — 108_AutoHideTab")<br /><br /> **Domyślna karta Autoukrywanie**|Tło|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Auto&#45;Ukryj kartę](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 — 108_AutoHideTab")<br /><br /> **Domyślna karta Autoukrywanie**|Pierwszy plan (tekst)|`Environment.AutoHideTabText`|  
|![Auto&#45;Ukryj kartę](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 — 108_AutoHideTab")<br /><br /> **Domyślna karta Autoukrywanie**|Obramowanie|`Environment.AutoHideTabBorder`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Auto&#45;Ukryj kartę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 — 109_AutoHideTabHover")<br /><br /> **Autoukrywanie karty przy aktywowaniu**|Tło|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Auto&#45;Ukryj kartę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 — 109_AutoHideTabHover")<br /><br /> **Autoukrywanie karty przy aktywowaniu**|Pierwszy plan (tekst)|`Environment.AutoHideTabMouseOverText`|  
|![Auto&#45;Ukryj kartę przy aktywowaniu](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 — 109_AutoHideTabHover")<br /><br /> **Autoukrywanie karty przy aktywowaniu**|Obramowanie|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Wspólne formanty udostępnione  
 Jeśli używasz standardowego paska poleceń programu Visual Studio w funkcji, będziesz mieć dostęp do kontrolek powłoki z stylami i nie należy ich powtarzać. Jeśli jednak trzeba utworzyć niestandardowy pasek poleceń, może być konieczne także skompilowanie niestandardowych kontrolek. W takim przypadku upewnij się, że używasz prawidłowych nazw tokenów dla każdej z następujących kontrolek, aby interfejs użytkownika był spójny z pozostałą częścią programu Visual Studio.  
  
#### <a name="search-box"></a>Pole wyszukiwania  
 Jeśli to możliwe, użyj typowej kontrolki wyszukiwania dostarczonej przez środowisko programu Visual Studio. Kolory pola wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors. pkgdef** , który zawiera nazwy tokenów pola wejściowego, akcji przycisku, listy rozwijanej i menu rozwijanego.  
  
 Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wykluczają się wzajemnie:  
  
- "Skoncentrowane" lub "bez fokusu" odnosi się do tego, czy kursor znajduje się w polu tekstowym.  
  
- "Aktywne" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadza zapytanie wyszukiwania w polu tekstowym.  
  
- "Aktywowany" oznacza, że użytkownik przeznaczył mysz nad polem wyszukiwania za pomocą myszy (ten stan zastępuje wszystkie inne Stany).  
  
- Wartość "wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.  
  
  ![Redline pola wyszukiwania](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 — 110_SearchBoxRedline")  
  
  Użyj...  
  podczas projektowania niestandardowego pola wyszukiwania.  
  
  Nie używaj...  
  - dla wszystkich elementów, które nie są polem wyszukiwania.  
  
- dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika pola wyszukiwania.  
  
  **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe wyszukiwania skoncentrowane](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Tło|`SearchControl.FocusedBackground`|  
|![Pole wejściowe wyszukiwania skoncentrowane](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.FocusedBackground`|  
|![Pole wejściowe wyszukiwania skoncentrowane](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Obramowanie|`SearchControl.FocusedBorder`|  
|![Pole wejściowe wyszukiwania skoncentrowane](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br /><br /> **Pole wejściowe**|Separator|`SearchControl.FocusedDropDownSeparator`|  
|![Przycisk akcji wyszukiwania — fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br /><br /> **Przycisk akcji**|Tło|Brak|  
|![Przycisk akcji wyszukiwania — fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Przycisk akcji wyszukiwania — fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol STOP)|`SearchControl.StopGlyph`|  
|![Przycisk akcji wyszukiwania — fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (czysty symbol)|`SearchControl.ClearGlyph`|  
|![Przycisk akcji wyszukiwania — fokus](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br /><br /> **Przycisk akcji**|Obramowanie|Nie dotyczy|  
|![Przycisk wyszukiwania Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.FocusedDropDownButton`|  
|![Przycisk wyszukiwania Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Przycisk wyszukiwania Porzuć&#45;w dół](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Bez fokusu**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Tło|`SearchControl.SearchActiveBackground`|  
|![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.SearchActiveBackground`|  
|![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br /><br /> **Aktywne pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Wyszukiwanie pola wejściowego, które nie jest skoncentrowane i nieaktywne](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Tło|`SearchControl.Unfocused`|  
|![Wyszukiwanie pola wejściowego, które nie jest skoncentrowane i nieaktywne](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.Unfocused`|  
|![Wyszukiwanie pola wejściowego, które nie jest skoncentrowane i nieaktywne](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Obramowanie|`SearchControl.UnfocusedBorder`|  
|![Wyszukiwanie pola wejściowego, które nie jest skoncentrowane i nieaktywne](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Nieaktywne pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Przycisk akcji wyszukiwania — nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br /><br /> **Przycisk akcji**|Tło|Nie dotyczy|  
|![Przycisk akcji wyszukiwania — nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol wyszukiwania)|`SearchControl.SearchGlyph`|  
|![Przycisk akcji wyszukiwania — nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol STOP)|`SearchControl.StopGlyph`|  
|![Przycisk akcji wyszukiwania — nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br /><br /> **Przycisk akcji**|Pierwszy plan (czysty symbol)|`SearchControl.ClearGlyph`|  
|![Przycisk akcji wyszukiwania — nieskoncentrowany](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br /><br /> **Przycisk akcji**|Obramowanie|Nie dotyczy|  
|![Przycisk wyszukiwania Porzuć&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.UnfocusedDropDownButton`|  
|![Przycisk wyszukiwania Porzuć&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Przycisk wyszukiwania Porzuć&#45;w dół nieskoncentrowany](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk akcji**|Tło|`SearchControl.ActionButtonMouseDown`|  
|![Naciśnięto przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Naciśnięto przycisk akcji wyszukiwania](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Przycisk akcji**|Obramowanie|`SearchControl.ActionButtonMouseDownBorder`|  
|![Naciśnięto przycisk wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Tło|`SearchControl.MouseDownDropDownButton`|  
|![Naciśnięto przycisk wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Naciśnięto przycisk wyszukiwania&#45;w dół](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Wyróżniony (tylko tekst)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe z wyróżnionym tekstem**|Tło|`SearchControl.Selection`|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe z wyróżnionym tekstem**|Pierwszy plan (tekst)|`SearchControl.FocusedBackground`|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe z wyróżnionym tekstem**|Obramowanie|Brak|  
|![Wyróżnij pole wejściowe wyszukiwania](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br /><br /> **Pole wejściowe z wyróżnionym tekstem**|Separator|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Tło|`SearchControl.Disabled`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Pierwszy plan (tekst)|`SearchControl.Disabled`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Obramowanie|`SearchControl.DisabledBorder`|  
|![Pole wejściowe wyszukiwania wyłączone](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br /><br /> **Pole wejściowe**|Separator|`SearchControl.DropDownSeparator`|  
|![Przycisk akcji wyszukiwania jest wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")<br /><br /> **Przycisk akcji**|Tło|Brak|  
|![Przycisk akcji wyszukiwania jest wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")<br /><br /> **Przycisk akcji**|Pierwszy plan (symbol)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Przycisk akcji wyszukiwania jest wyłączony](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")<br /><br /> **Przycisk akcji**|Obramowanie|Brak|  
|![Przycisk wyszukiwania Porzuć&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Tło|Brak|  
|![Przycisk wyszukiwania Porzuć&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Pierwszy plan (symbol)|`SearchControl.DisabledDownButtonGlyph`|  
|![Przycisk wyszukiwania Porzuć&#45;w dół wyłączone](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")<br /><br /> **Przycisk listy rozwijanej**|Obramowanie|Brak|  
  
##### <a name="search-drop-down-lists"></a>Lista rozwijana wyszukiwania  
 Menu rozwijane pola wyszukiwania może być nieco bardziej skomplikowane niż inne menu rozwijane w programie Visual Studio. Sekcje "sugerowane wyszukiwania" i "Opcje wyszukiwania" mogą występować samodzielnie lub razem w menu, a każdy z nich jest kolorowy osobno. Linia oddziela również te dwie sekcje, gdy pojawiają się razem, a obramowanie otacza całe menu rozwijane.  
  
 ![Wyszukaj Porzuć&#45;w dół Redline](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 — 124_SearchDropdownRedline")  
  
Użyj...  
- podczas tworzenia listy rozwijanej wyszukiwania niestandardowego.  

- poprawne nazwy tokenów dla poprawnych składników listy.  

Nie używaj...  
- dla list rozwijanych, które są wyświetlane w innych kontekstach.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślne (nie inne Stany)**  
  
|Element|Nazwa tokenu: Category. Color|  
|-------------|--------------------------------|  
|Obramowanie|`SearchControl.PopupBorder`|  
|Separator|`SearchControl.PopupSectionHeaderSeparator`|  
|W tle|`Environment.DropShadowBackground`|  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukaj sugerowane](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 — 125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Wyszukaj sugerowane](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 — 125_SearchSuggested")<br /><br /> **Sugerowane wyszukiwania**|Pierwszy plan (tekst)|`SearchControl.PopupItemText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonText`|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Tło nagłówka|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 — 126_SearchCheckbox")<br /><br /> **Opcje wyszukiwania (pole wyboru)**|Pierwszy plan (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
|![Opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 — 127_SearchOptions")<br /><br /> **Opcje wyszukiwania (link)**|Pierwszy plan (tekst nagłówka)|`SearchControl.PopupSectionHeaderText`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wyszukiwanie sugerowane przy aktywowaniu](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Wyszukiwanie sugerowane przy aktywowaniu](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Pierwszy plan (tekst)|`SearchControl.PopupMouseOverItemText`|  
|![Wyszukiwanie sugerowane przy aktywowaniu](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")<br /><br /> **Sugerowane wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Pole wyboru wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Opcje wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Tło|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Pole wyboru wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Opcje wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Pole wyboru wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonMouseDownText`|  
|![Opcje wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonMouseDownText`|  
|![Pole wyboru wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
|![Opcje wyszukiwania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 — 130_SearchOptionsHover")<br /><br /> **Opcje wyszukiwania**|Obramowanie|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Zaciskaj sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Zaciskaj sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło pola wyboru|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Zaciskaj sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Naciśnięto opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst pola wyboru)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Zaciskaj sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Naciśnięto opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Tło łącza|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Chociaż nie jest używany w nowoczesnych interfejsie użytkownika, istnieją punkty przerwania gradientu i wartości dla tego tła.|  
|![Zaciskaj sugerowane wyszukiwanie](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br /><br /> **Sugerowane wyszukiwania (pole wyboru)**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonMouseDownText`|  
|![Naciśnięto opcje wyszukiwania](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br /><br /> **Opcje wyszukiwania**|Pierwszy plan (tekst linku)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hyperlink  
 Hiperłącze jest jednym formantem, który nie ma pary pierwszego planu/tła. We wszystkich przypadkach Użyj koloru hiperlinku pierwszego planu, który będzie wyświetlany prawidłowo na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu koloru dla kontrolki hiperłącze, zobaczysz domyślny kolor systemowy dla "naciśniętego", który będzie miał lampę błyskową czerwony. Jest to sygnał, że formant nie używa poprawnego tokenu koloru środowiska.  
  
 ![Redline hiperlinków](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 — 133_HyperlinkRedline")  
  
 Użyj...  
 gdy musisz utworzyć niestandardowe hiperłącze.  
  
 Nie używaj...  
 dla wszystkich elementów, które nie są hiperłączem.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Domyślne hiperłącze](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 — 134_Hyperlink")|Pierwszy plan (tekst)|`Environment.PanelHyperlink`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze przy aktywowaniu](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 — 135_HyperlinkHover")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto hiperłącze](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 — 136_HyperlinkPressed")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Hiperłącze wyłączone](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 — 137_HyperlinkDisabled")|Pierwszy plan (tekst)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Powiadomienie  
 Infobars są używane do udostępniania więcej informacji na temat danego kontekstu i są zawsze wyświetlane w górnej części okna dokumentu lub okna narzędzi.  
  
 ![Pasek informacyjny Redline](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 — 138_InfobarRedline")  
  
 Użyj...  
 podczas tworzenia niestandardowej infobars.  
  
 Nie używaj...  
 dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego.  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Powiadomienie](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 — 139_Infobar")<br /><br /> **Powiadomienie**|Tło|`Environment.InfoBackground`|  
|![Powiadomienie](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 — 139_Infobar")<br /><br /> **Powiadomienie**|Pierwszy plan (tekst)|`Environment.InfoText`|  
|![Powiadomienie](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 — 139_Infobar")<br /><br /> **Powiadomienie**|Obramowanie|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Pasek przewijania  
 Paski przewijania są zgodne ze środowiskiem programu Visual Studio i nie będą potrzebne. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w paskach przewijania, tak aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.  
  
 ![Pasek przewijania Redline](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 — 140_ScrollbarRedline")  
  
 Użyj...  
 podczas tworzenia interfejsu użytkownika, który chcesz dopasować do pasków przewijania programu Visual Studio.  
  
 Nie używaj...  
 dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika paska przewijania.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 — 141_Scrollbar")<br /><br /> **Paski**|Paski|`Environment.ScrollBarBackground`|  
|![Pasek przewijania](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 — 141_Scrollbar")<br /><br /> **Paski**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbBackground`|  
|![Strzałka paska przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 — 142_ScrollbarArrow")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowBackground`<br /><br /> Ustaw na taki sam kolor jak pasek przewijania.|  
|![Strzałka paska przewijania](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 — 142_ScrollbarArrow")<br /><br /> **Strzałka przewijania**|Pierwszy plan (symbol)|`Environment.ScrollBarArrowGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pasek przewijania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 — 143_ScrollbarHover")<br /><br /> **Paski**|Paski|`Environment.ScrollBarBackground`|  
|![Pasek przewijania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 — 143_ScrollbarHover")<br /><br /> **Paski**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Strzałka paska przewijania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Ustaw na taki sam kolor jak pasek przewijania.|  
|![Strzałka paska przewijania przy aktywowaniu](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")<br /><br /> **Strzałka przewijania**|Pierwszy plan (symbol)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto pasek przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 — 145_ScrollbarPressed")<br /><br /> **Paski**|Paski|`Environment.ScrollBarBackground`|  
|![Naciśnięto pasek przewijania](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 — 145_ScrollbarPressed")<br /><br /> **Paski**|Pierwszy plan (kciuk)|`Environment.ScrollBarThumbPressedBackground`|  
|![Naciśnięto strzałkę paska przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")<br /><br /> **Strzałka przewijania**|Tło|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Ustaw ten sam kolor jako pasek przewijania.|  
|![Naciśnięto strzałkę paska przewijania](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")<br /><br /> **Strzałka przewijania**|Pierwszy plan (symbol)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Widok drzewa  
 Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwera i Widok klasy, Implementuj hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w kategorii TreeView. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy z zagnieżdżonymi elementami podrzędnymi również mają glify wskazujące, czy element jest rozwinięty, czy zwinięty.  
  
 ![Widok drzewa Redline](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 — 147_TreeViewRedline")  
  
 Użyj...  
 wszędzie tam, gdzie trzeba zaimplementować hierarchiczny widok organizacyjny.  
  
Nie używaj...  
- dla wszystkich elementów, które nie są podobne do widoku drzewa.  

- w każdej kombinacji tła/pierwszego planu poza określoną.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")|Tło|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")|Pierwszy plan (tekst)|`TreeView.Background`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")|Pierwszy plan (symbol)|`TreeView.Glyph`|  
|![Widok drzewa](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 — 148_TreeView")|Obramowanie|Brak|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa przy aktywowaniu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")|Tło|`TreeView.Background`|  
|![Widok drzewa przy aktywowaniu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")|Pierwszy plan (tekst)|`TreeView.Background`|  
|![Widok drzewa przy aktywowaniu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")|Pierwszy plan (symbol)|`TreeView.GlyphMouseOver`|  
|![Widok drzewa przy aktywowaniu](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 — 149_TreeViewHover")|Obramowanie|Brak|  
  
 **Przeciągnij nad**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")|Tło|`TreeView.DragOverItem`|  
|![Widok drzewa DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")|Pierwszy plan (tekst)|`TreeView.DragOverItem`|  
|![Widok drzewa DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")|Pierwszy plan (symbol)|`TreeView.DragOverItemGlyph`|  
|![Widok drzewa DragOver](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 — 150_TreeViewDragOver")|Obramowanie|Brak|  
  
 **Wybrano**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa z fokusem](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Widok drzewa z fokusem](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`|  
|![Widok drzewa z fokusem](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Pierwszy plan (symbol)|`TreeView.SelectedItemActiveGlyph`|  
|![Widok drzewa z fokusem](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 — 151_TreeViewFocused")<br /><br /> **Ustawiono fokus**|Obramowanie|`TreeView.FocusVisualBorder`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Tło|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Pierwszy plan (symbol)|`TreeView.SelectedItemInactiveGlyph`|  
|![Widok drzewa nieskoncentrowany](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Obramowanie|Brak|  
  
 **Umieść kursor nad wybranym**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Widok drzewa skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Tło|`TreeView.SelectedItemActive`|  
|![Widok drzewa skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`|  
|![Widok drzewa skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Pierwszy plan (symbol)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Widok drzewa skoncentrowany na aktywowaniu](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br /><br /> **Ustawiono fokus**|Obramowanie|Dawaj`TreeView.FocusVisualBorder`|  
|![Widok drzewa nieskoncentrowany po aktywowaniu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Tło|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany po aktywowaniu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`|  
|![Widok drzewa nieskoncentrowany po aktywowaniu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Pierwszy plan (symbol)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Widok drzewa nieskoncentrowany po aktywowaniu](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Obramowanie|Brak|  
  
#### <a name="button-controls"></a>formanty przycisków  
 ![Button — formant Redline](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 — 155_ButtonControlRedline")  
  
 Użyj...  
 w przypadku przycisków w dokumencie, które chcesz zintegrować z motywami programu Visual Studio (jasnym, ciemniejszym, niebieskim lub duży kontrastm systemu).  
  
 Nie używaj...  
 w przypadku przycisków, które będą wyświetlane na tle niestandardowym, które nie jest częścią motywu programu Visual Studio.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303 — 156_Button")|Przycisk|`CommonControls.Button`|  
|![Przycisk](../extensibility/ux-guidelines/media/0303-156-button.png "0303 — 156_Button")|Obramowanie przycisku|`CommonControls.ButtonBorder`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk wyłączony](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 — 157_ButtonDisabled")|Przycisk|`CommonControls.ButtonDisabled`|  
|![Przycisk wyłączony](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 — 157_ButtonDisabled")|Obramowanie przycisku|`CommonControls.ButtonBorderDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk po aktywowaniu](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 — 158_ButtonHover")|Przycisk|`CommonControls.ButtonHover`|  
|![Przycisk po aktywowaniu](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 — 158_ButtonHover")|Obramowanie przycisku|`CommonControls.ButtonBorderHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto przycisk](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 — 159_ButtonPressed")|Przycisk|`CommonControls.ButtonPressed`|  
|![Naciśnięto przycisk](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 — 159_ButtonPressed")|Obramowanie przycisku|`CommonControls.ButtonBorderPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Przycisk skoncentrowany](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 — 160_ButtonFocused")|Przycisk|`CommonControls.ButtonFocused`|  
|![Przycisk skoncentrowany](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 — 160_ButtonFocused")|Obramowanie przycisku|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Kontrolki pola wyboru  
 ![Pole wyboru Redline](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 — 161_CheckboxRedline")  
  
 Użyj...  
 dla kontrolek pola wyboru zawartych w tym dokumencie.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie jest kontrolką pola wyboru.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")|Tło|`CommonControls.CheckBoxBackground`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")|Obramowanie|`CommonControls.CheckBoxBorder`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")|Tekst|`CommonControls.CheckBoxText`|  
|![Pole wyboru](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 — 162_Checkbox")|Symbol|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")|Tło|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")|Obramowanie|`CommonControls.CheckBoxBorderDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")|Tekst|`CommonControls.CheckBoxTextDisabled`|  
|![Pole wyboru wyłączone](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 — 163_CheckboxDisabled")|Symbol|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru przy aktywowaniu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")|Tło|`CommonControls.CheckBoxBackgroundHover`|  
|![Pole wyboru przy aktywowaniu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")|Obramowanie|`CommonControls.CheckBoxBorderHover`|  
|![Pole wyboru przy aktywowaniu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")|Tekst|`CommonControls.CheckBoxTextHover`|  
|![Pole wyboru przy aktywowaniu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 — 164_CheckboxHover")|Symbol|`CommonControls.CheckBoxGlyphHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru zostało naciśnięte](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|![Pole wyboru zostało naciśnięte](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")|Obramowanie|`CommonControls.CheckBoxBorderPressed`|  
|![Pole wyboru zostało naciśnięte](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")|Tekst|`CommonControls.CheckBoxTextPressed`|  
|![Pole wyboru zostało naciśnięte](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 — 165_CheckboxPressed")|Symbol|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole wyboru ukierunkowane](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")|Tło|`CommonControls.CheckBoxBackgroundFocused`|  
|![Pole wyboru ukierunkowane](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")|Obramowanie|`CommonControls.CheckBoxBorderFocused`|  
|![Pole wyboru ukierunkowane](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")|Tekst|`CommonControls.CheckBoxTextFocused`|  
|![Pole wyboru ukierunkowane](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 — 166_CheckboxFocused")|Symbol|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Kontrolki pola kombi/pola rozwijalnego  
 ![Upuść&#45;w dół&#47;pole kombi Redline](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 — 167_DropDownComboBoxRedline")  
  
Użyj...  
dla listy rozwijanej i pól kombi, które są częścią dokumentu.  

Nie używaj...  
- dla każdego interfejsu użytkownika, który nie jest polem listy rozwijanej ani pola kombi.  

- dla [listy rozwijanej](../misc/shared-colors.md#BKMK_CommandDropDown) lub [pola kombi](../misc/shared-colors.md#BKMK_CommandComboBox) na pasku poleceń.  
  
  **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Tło|`CommonControls.ComboBoxBackground`|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Obramowanie|`CommonControls.ComboBoxBorder`|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Tekst|`CommonControls.ComboBoxText`|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Separator|`CommonControls.ComboBoxSeparator`|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Symbol|`CommonControls.ComboBoxGlyph`|  
|![Pole kombi Porzuć&#45;w dół&#47;](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 — 168_DropDownComboBox")|Tło symbolu|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled (Wyłączone)**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Tło|`CommonControls.ComboBoxBackgroundDisabled`|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Obramowanie|`CommonControls.ComboBoxBorderDisabled`|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Tekst|`CommonControls.ComboBoxTextDisabled`|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Separator|`CommonControls.ComboBoxSeparatorDisabled`|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Symbol|`CommonControls.ComboBoxGlyphDisabled`|  
|![&#45;upuść&#47;pole kombi wyłączone](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")|Tło symbolu|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Tło|`CommonControls.ComboBoxBackgroundHover`|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Obramowanie|`CommonControls.ComboBoxBorderHover`|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Tekst|`CommonControls.ComboBoxTextHover`|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Separator|`CommonControls.ComboBoxSeparatorHover`|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Symbol|`CommonControls.ComboBoxGlyphHover`|  
|![Upuść&#45;w dół pola kombi&#47;po aktywowaniu](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")|Tło symbolu|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Tło|`CommonControls.ComboBoxBackgroundPressed`|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Obramowanie|`CommonControls.ComboBoxBorderPressed`|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Tekst|`CommonControls.ComboBoxTextPressed`|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Separator|`CommonControls.ComboBoxSeparatorPressed`|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Symbol|`CommonControls.ComboBoxGlyphPressed`|  
|![Naciśnięto pole kombi&#47;&#45;w dół](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")|Tło symbolu|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Ustawiono fokus**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Tło|`CommonControls.ComboBoxBackgroundFocused`|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Obramowanie|`CommonControls.ComboBoxBorderFocused`|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Tekst|`CommonControls.ComboBoxTextFocused`|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Separator|`CommonControls.ComboBoxSeparatorFocused`|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Symbol|`CommonControls.ComboBoxGlyphFocused`|  
|![Upuść&#45;w dół&#47;pole kombi](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")|Tło symbolu|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Wprowadzanie tekstu**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Upuść&#45;w dół&#47;wprowadzanie tekstu w polu kombi](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 — 173_DropDownComboBoxTextInput")|Wyróżnij|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Naciśnięto — widok elementu listy**  
  
|Składnik|Element|Nazwa tokenu: Color. Category|  
|---------------|-------------|--------------------------------|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackground`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListBackgroundHover`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tło|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorder`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderHover`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderPressed`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Obramowanie|`CommonControls.ComboBoxListBorderFocused`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemText`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextHover`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextPressed`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Tekst elementu|`CommonControls.ComboBoxListItemTextFocused`|  
|![Porzuć&#45;w dół&#47;widok listy pola kombi](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")|Cień tła|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelarycznych (siatka)  
 Kontrolki danych tabelarycznych, znane także jako kontrolki siatki, są typowymi kontrolkami dla programu Visual Studio, których można użyć do prezentowania dużych ilości danych w wielu kolumnach. Standardowe kontrolki danych tabelarycznych można znaleźć w wielu miejscach w programie Visual Studio: okno narzędzia Lista błędów, raporty IntelliTrace i widok sterty pamięci, między innymi. Należy zawsze używać standardowych formantów danych tabelarycznych. W niektórych rzadkich przypadkach może nie mieć dostępu do standardowych formantów danych tabelarycznych. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelarycznych w programie Visual Studio.  
  
 ![Dane tabelaryczne &#40;formancie siatki&#41; Redline](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 — 197_TabularDataGridControlRedline")  
  
 Użyj...  
 dla kontrolek tabelarycznych lub siatki.  
  
 Nie używaj...  
 dla każdego interfejsu użytkownika, który nie jest kontrolką tabelaryczną lub siatką.  
  
##### <a name="column-headers"></a>Nagłówki kolumn  
 Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego symbolu zwykle używane, gdy siatka jest posortowana według tej kolumny.  
  
|Stan|Element|Nazwa tokenu: Category. Color|  
|-----------|-------------|--------------------------------|  
|Domyślny|Tło|`Header.Default`|  
|Domyślny|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|Domyślny|Pierwszy plan (symbol)|`Header.Glyph`|  
|Domyślny|Obramowanie|`Header.SeparatorLine`|  
|Aktywowane|Tło|`Header.MouseOver`|  
|Aktywowane|Pierwszy plan (tekst)|`Environment.CommandBarTextHover`|  
|Aktywowane|Pierwszy plan (symbol)|`Header.MouseOverGlyph`|  
|Aktywowane|Obramowanie|`Header.SeparatorLine`|  
|Naciśnięte|Tło|`CommonControls.CheckBoxBackgroundPressed`|  
|Naciśnięte|Pierwszy plan (tekst)|`CommonControls.CheckBoxBorderPressed`|  
|Naciśnięte|Pierwszy plan (symbol)|`CommonControls.CheckBoxTextPressed`|  
|Naciśnięte|Obramowanie|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Wyświetl listę elementów  
 Elementy widoku listy składają się z tła i zawartości. Zawartość może być tekstem, ikoną lub obu.  
  
|Stan|Element|Nazwa tokenu: Category. Color|  
|-----------|-------------|--------------------------------|  
|Domyślny|Tło|Przezroczyste|  
|Domyślny|Pierwszy plan (tekst)|`Environment.CommandBarTextActive`|  
|Domyślny|Obramowanie|Brak|  
|Wybrane (aktywne)|Tło|`TreeView.SelectedItemActive`|  
|Wybrane (aktywne)|Pierwszy plan (tekst)|`TreeView.SelectedItemActiveText`|  
|Wybrane (aktywne)|Obramowanie|Brak|  
|Wybrane (nieaktywne)|Tło|`TreeView.SelectedItemInactive`|  
|Wybrane (nieaktywne)|Pierwszy plan (tekst)|`TreeView.SelectedItemInactiveText`|  
|Wybrane (nieaktywne)|Obramowanie|Brak|  
  
### <a name="manifest-designer"></a>Manifest Designer  
 Projektant manifestu został zaprojektowany jako sposób ułatwiający edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Chociaż nie jest dostępna żadna udostępniona architektura do użycia, może być odpowiednie dopasowanie układu projektu i kolorów na kartach Orientacja/Nawigacja i ogólna struktura. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [układ programu Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Redline projektanta manifestu](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 — 175_ManifestDesignerRedline")  
  
Użyj...  
- dla projektantów, które są podobne do projektanta manifestu.  

- zamiast używania wspólnych kontrolek kart w górnej części edytora w obszarze dokumentu.  

Nie używaj...  
- Jeśli masz więcej niż sześć kart.  

- dla każdego interfejsu użytkownika, który nie jest uporządkowany jak projektant manifestu.  
  
|Stan|Składnik|Element|Nazwa tokenu: Category. Color|  
|-----------|---------------|-------------|--------------------------------|  
|Domyślne (wybrane)|Tab|Tło|`ManifestDesigner.TabActive`|  
|Domyślne (wybrane)|Tab|Obramowanie|Brak|  
|Domyślne (wybrane)|Okienko opisu|Tło|`ManifestDesigner.DescriptionPane`|  
|Domyślne (wybrane)|Strona zawartości|Tło|`ManifestDesigner.Background`|  
|Domyślne (wybrane)|Strona zawartości|Tekst pomocnika okna dialogowego|`ManifestDesigner.WatermarkText`<br /><br /> Ta nazwa tokenu nie jest zgodna z jej funkcją.|  
|Nie wybrano|Tab|Tło|`ManifestDesigner.Tab.Inactive`|  
|Aktywowane|Tab|Tło|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Znakowanie  
 Program Visual Studio obsługuje tagowanie, dzięki czemu użytkownik może zadeklarować słowa kluczowe do przeszukiwania do celów śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać Team Foundation Server (TFS) do tagowania elementów roboczych. Poniższe tabele zawierają nazwy kolorów zarówno dla samego tagu, jak i symboli "Close Icon", które pojawiają się w Stanach aktywowania i wybrane.  
  
 ![Redline tagowania](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 — 176_TaggingRedline")  
  
 Użyj...  
 dla interfejsu użytkownika obsługującego tagowanie.  
  
 Nie używaj...  
 dla każdego innego typu interfejsu użytkownika.  
  
#### <a name="tag"></a>Tag  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 — 177_Tag")<br /><br /> **Domyślny**|Tło|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 — 177_Tag")<br /><br /> **Domyślny**|Pierwszy plan (tekst)|`Tag.Background`|  
|![Oznacz przy aktywowaniu](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 — 178_TagHover")<br /><br /> **Aktywowane**|Tło|`Tag.HoverBackground`|  
|![Oznacz przy aktywowaniu](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 — 178_TagHover")<br /><br /> **Aktywowane**|Pierwszy plan (tekst)|`Tag.HoverBackgroundText`|  
|![Naciśnięto tag](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 — 179_TagPressed")<br /><br /> **Naciśnięte**|Tło|`Tag.PressedBackground`|  
|![Naciśnięto tag](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 — 179_TagPressed")<br /><br /> **Naciśnięte**|Pierwszy plan (tekst)|`Tag.PressedBackgroundText`|  
|![Wybrany tag](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 — 180_TagSelected")<br /><br /> **Wybrano**|Tło|`Tag.SelectedBackground`|  
|![Wybrany tag](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 — 180_TagSelected")<br /><br /> **Wybrano**|Pierwszy plan (tekst)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Symbol (ikona zamknięcia)  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Oznacz symbol &#40;symbolu&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 — 181_TagGlyph")<br /><br /> **Default (tag domyślny)**|Tło|Nie dotyczy|  
|![Oznacz symbol &#40;symbolu&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 — 181_TagGlyph")<br /><br /> **Default (tag domyślny)**|Pierwszy plan (symbol)|`Tag.TagHoverGlyph`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Oznacz symbol &#40;symbolu&#41; przy aktywowaniu](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 — 182_TagGlyphHover")<br /><br /> **Aktywuj (domyślny tag)**|Tło|`Tag.TagHoverGlyphHoverBackground`|  
|![Oznacz symbol &#40;symbolu&#41; przy aktywowaniu](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 — 182_TagGlyphHover")<br /><br /> **Aktywuj (domyślny tag)**|Pierwszy plan (symbol)|`Tag.TagHoverGlyphHover`|  
|![Oznacz symbol &#40;symbolu&#41; przy aktywowaniu](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 — 182_TagGlyphHover")<br /><br /> **Aktywuj (domyślny tag)**|Obramowanie|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Naciśnięte**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Naciśnięto &#40;znacznika&#41; symbolu](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 — 183_TagGlyphPressed")<br /><br /> **Naciśnięto (domyślny tag)**|Tło|`Tag.TagHoverGlyphPressedBackground`|  
|![Naciśnięto &#40;znacznika&#41; symbolu](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 — 183_TagGlyphPressed")<br /><br /> **Naciśnięto (domyślny tag)**|Pierwszy plan (symbol)|`Tag.TagHoverGlyphPressed`|  
|![Naciśnięto &#40;znacznika&#41; symbolu](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 — 183_TagGlyphPressed")<br /><br /> **Naciśnięto (domyślny tag)**|Obramowanie|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Zaznaczony tag/domyślny symbol**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wybrany tag](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 — 184_TagSelected")<br /><br /> **Default (wybrany tag)**|Tło|Nie dotyczy|  
|![Wybrany tag](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 — 184_TagSelected")<br /><br /> **Default (wybrany tag)**|Pierwszy plan (symbol)|`Tag.TagSelectedGlyph`|  
  
 **Zaznaczony znacznik/aktywowany symbol**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Znacznik wybrany przy aktywowaniu](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 — 185_TagSelectedHover")<br /><br /> **Aktywuj (zaznaczony tag)**|Tło|`Tag.TagSelectedGlyphHoverBackground`|  
|![Znacznik wybrany przy aktywowaniu](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 — 185_TagSelectedHover")<br /><br /> **Aktywuj (zaznaczony tag)**|Pierwszy plan (symbol)|`Tag.TagSelectedGlyphHover`|  
|![Znacznik wybrany przy aktywowaniu](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 — 185_TagSelectedHover")<br /><br /> **Aktywuj (zaznaczony tag)**|Obramowanie|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Naciśnięto zaznaczony znacznik/Symbol**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Wybrano tag](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 — 186_TagSelectedPressed")<br /><br /> **Naciśnięto (tag wybrany)**|Tło|`Tag.TagSelectedGlyphPressedBackground`|  
|![Wybrano tag](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 — 186_TagSelectedPressed")<br /><br /> **Naciśnięto (tag wybrany)**|Pierwszy plan (symbol)|`Tag.TagSelectedGlyphPressed`|  
|![Wybrano tag](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 — 186_TagSelectedPressed")<br /><br /> **Naciśnięto (tag wybrany)**|Obramowanie|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Powłoka  
  
#### <a name="background"></a>Tło  
 Tło środowiska składa się z dwóch warstw. Warstwa dolna to pełny kolor, który obejmuje całe środowisko IDE. Górna warstwa dopasowuje się do półki poleceń i między oknem narzędzia a ukrywanie kanałów po lewej i prawej stronie IDE. Począwszy od Visual Studio 2013, górny i dolny warstw tła są ustawione na ten sam kolor w jasnych i ciemnych motywach.  
  
 ![Redline w tle powłoki](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 — 187_ShellBackgroundRedline")  
  
 Użyj...  
 dla miejsc, które chcesz dopasować do tła środowiska programu Visual Studio.  
  
Nie używaj...  
- jako wypełnienie miejsc, które nie są powierzchniami tła.  

- jako tło, w którym chcesz umieścić elementy pierwszego planu.  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|Warstwa dolna|Tło|`Environment.EnvironmentBackground`|  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|Warstwa najwyższej warstwy|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Warstwa najwyższej warstwy|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Warstwa najwyższej warstwy|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Warstwa najwyższej warstwy|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Półka polecenia  
 Dwa zestawy nazw tokenów są używane na potrzeby tła półki poleceń: jeden zestaw dla miejsca, w którym znajduje się pasek menu, i jeden dla miejsca, w którym znajdują się paski poleceń. Pojedyncza grupa pasków poleceń ma własne wartości koloru tła, które zostały omówione bardziej szczegółowo w sekcji "pasek poleceń". Tekst paska menu i paska poleceń jest omówiony odpowiednio w sekcji menu i paska poleceń.  
  
 ![Redline półki polecenia](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 — 188_CommandShelfRedline")  
  
Użyj...  
- w przypadku obszarów, w których są umieszczane menu lub paski narzędzi.  

- z poprawną kombinacją nazw tokenów tła/pierwszego planu.  
  
  Nie używaj...  
  w przypadku obszarów, które nie są podobne do półki poleceń.  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|Pasek menu|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Pasek menu|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Pasek menu|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Pasek poleceń|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Pasek poleceń|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Pasek poleceń|Tło<br /><br /> *Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Przybornik  
 Przybornik jest jednym z popularnych okien narzędzi, które są najczęściej używane w programie Visual Studio. Jest to zasadniczo formant drzewa z zastosowaniem specjalnego motywu i stylu.  
  
 ![Redline przybornika](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 — 189_ToolboxRedline")  
  
 Użyj...  
 podczas projektowania okna narzędzi, które chcesz zawsze zachować spójność z przybornikiem powłoki.  
  
 Nie używaj...  
 dla wszystkich elementów, które nie są podobne do interfejsu użytkownika przybornika, lub jeśli nie masz pewności, czy interfejs użytkownika będzie miał problemy, jeśli zmienią się kolory przybornika powłoki.  
  
 **Domyślny**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli nie ma dostępnych kontrolek|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Tło|`Environment.ToolboxContent`<br /><br /> Nagłówki<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Poszczególne elementy lub całe okno, jeśli nie ma dostępnych kontrolek|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Obramowanie|Brak|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszy plan (symbol)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszy plan (symbol)|`Environment.ToolboxContent`|  
|![Węzeł nadrzędny przybornika](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br /><br /> **Węzeł nadrzędny**|Pierwszy plan (tekst)|`Environment.ToolboxContent`|  
|![Węzeł podrzędny przybornika](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br /><br /> **Węzeł podrzędny**|Pierwszy plan (tekst)|`Environment.ToolboxContent`|  
  
 **Aktywowane**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł podrzędny przybornika przy aktywowaniu](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")<br /><br /> **Umieść kursor w węźle podrzędnym**|Tło|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedyncze elementy|  
|![Węzeł podrzędny przybornika przy aktywowaniu](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")<br /><br /> **Umieść kursor w węźle podrzędnym**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika przy aktywowaniu](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")<br /><br /> **Umieść kursor w węźle podrzędnym**|Pierwszy plan (tekst)|`Environment.ToolboxContentMouseOver`<br /><br /> Tylko pojedyncze elementy|  
  
 **Wybrano**  
  
|Składnik|Element|Nazwa tokenu: Category. Color|  
|---------------|-------------|--------------------------------|  
|![Węzeł nadrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br /><br /> **Fokus węzła nadrzędnego**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika — fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br /><br /> **Priorytetowy węzeł podrzędny**|Tło|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br /><br /> **Fokus węzła nadrzędnego**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika — fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br /><br /> **Priorytetowy węzeł podrzędny**|Obramowanie|`TreeView.FocusVisualBorder`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br /><br /> **Fokus węzła nadrzędnego**|Pierwszy plan (symbol)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika — fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br /><br /> **Priorytetowy węzeł podrzędny**|Pierwszy plan (symbol)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br /><br /> **Fokus węzła nadrzędnego**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika — fokus](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br /><br /> **Priorytetowy węzeł podrzędny**|Pierwszy plan (tekst)|`TreeView.SelectedItemActive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika bez fokusu](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny nieskoncentrowany**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny nieskoncentrowany**|Tło|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika bez fokusu](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny nieskoncentrowany**|Obramowanie|Brak|  
|![Węzeł podrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny nieskoncentrowany**|Obramowanie|Brak|  
|![Węzeł nadrzędny przybornika bez fokusu](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny nieskoncentrowany**|Pierwszy plan (symbol)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny nieskoncentrowany**|Pierwszy plan (symbol)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł nadrzędny przybornika bez fokusu](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br /><br /> **Węzeł nadrzędny nieskoncentrowany**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
|![Węzeł podrzędny przybornika z fokusem](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br /><br /> **Węzeł podrzędny nieskoncentrowany**|Pierwszy plan (tekst)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorii [widoku drzewa](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Odwołanie do wartości koloru  
  
|Składnik|Część|Element|Stan|Jasny|Ciemny|Niebieski|duży kontrast|
|---------|----|-------|-----|-----|----|----|----|  
|Linie podziału|||Domyślny|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Symbol ekspandera||Pierwszy plan|Domyślny|||||  
|Symbol ekspandera||Pierwszy plan|Aktywowane|||||  
|Symbol ekspandera||Tło|Domyślny|||||  
|Symbol ekspandera||Tło|Aktywowane|||||  
|Symbol ekspandera||Obramowanie|Domyślny|||||  
|Symbol ekspandera||Obramowanie|Aktywowane|||||