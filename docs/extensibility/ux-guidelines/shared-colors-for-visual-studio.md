---
title: Kolory udostępnione dla programu Visual Studio | Microsoft Docs
description: Dowiedz się, jak używać typowych elementów i motywów powłoki programu Visual Studio, aby zaprojektować własny niestandardowy interfejs użytkownika, który jest zgodny ze środowiskiem programu Visual Studio.
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 856f071cbab3156daa6afd0a5282a69636f2fe8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927226"
---
# <a name="shared-colors-for-visual-studio"></a>Kolory udostępnione dla programu Visual Studio
Gdy projektujesz interfejs użytkownika, który używa typowych elementów powłoki programu Visual Studio, lub chcesz, aby element interfejsu był spójny z podobnymi funkcjami, Użyj istniejących nazw tokenów w plikach definicji pakietów, aby wybrać i przypisać kolory. Dzięki temu interfejs użytkownika pozostaje spójny z ogólnym środowiskiem programu Visual Studio i jest aktualizowany automatycznie po dodaniu lub zaktualizowaniu motywów.

W tym artykule opisano typowe elementy interfejsu użytkownika i używane przez nie nazwy tokenów, które można przywołać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje na temat uzyskiwania dostępu do tych tokenów kolorów, zobacz [usługę VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Upewnij się, że nazwy tokenów są poprawnie używane:

- **Używaj nazw tokenów opartych na funkcjach, a nie na samym kolorze.** Wspólne kolory udostępnione są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko dla tych samych lub podobnych funkcji. Na przykład nie należy ponownie używać koloru naciśniętego pola kombi dla obracającej animacji postępu, tak samo jak kolor. Funkcje pola kombi i animacji są różne i jeśli kolor skojarzony z polem kombi zmieni się, może to oznaczać, że nie jest już odpowiednim kolorem elementu animacji. Spójne użycie koloru pozwala na ukierunkowanie użytkowników i zapobieganie niepomyleniu.

- **Używaj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które mają być używane z tekstem, będą mieć skojarzony kolor tekstu. Nie używaj kolorów tekstu innych niż określone dla danego tła. Jeśli nie ma skojarzonego koloru tekstu, nie używaj tego koloru tła dla każdej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą spowodować nieczytelny interfejs.

- **Użyj kolorów kontroli odpowiednich dla ich lokalizacji.** W niektórych stanach niektóre kontrolki programu Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego wybierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów, które są odpowiednie dla lokalizacji, w której umieszczasz formant.

> [!IMPORTANT]
> Nie można używać tokenów w kategoriach "Start Page" lub "jabłecznik".

## <a name="common-shared-controls"></a>Wspólne formanty udostępnione

Gdy korzystasz ze standardowego paska poleceń programu Visual Studio, będziesz mieć dostęp do kontrolek powłoki z stylem. Nie należy zmienić szablonu tych wspólnych kontrolek. Jeśli jednak trzeba utworzyć niestandardowy pasek poleceń, może być konieczne także skompilowanie niestandardowych kontrolek. W takim przypadku upewnij się, że używasz prawidłowych nazw tokenów dla każdej z następujących kontrolek, aby interfejs użytkownika był spójny z pozostałą częścią programu Visual Studio.

### <a name="button-controls"></a>formanty przycisków

![Button — formant Redline](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 — 155_ButtonControlRedline")

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku przycisków w dokumencie, które chcesz zintegrować z motywami programu Visual Studio (jasnym, ciemniejszym, niebieskim lub duży kontrastm systemu). | ... w przypadku przycisków, które będą wyświetlane na tle niestandardowym, które nie jest częścią motywu programu Visual Studio. |

**Przycisk: stan standardowy**

![Przycisk standardowy](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. Standard")<br />Przycisk standardowy

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.Button` |
| Obramowanie przycisku | `CommonControls.ButtonBorder` |

**Przycisk: stan domyślny**

![Przycisk domyślny](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. default")<br />Przycisk domyślny

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDefault` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDefault` |

**Przycisk: stan wyłączony**

![Przycisk wyłączony](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. disabled")<br />Przycisk wyłączony

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDisabled` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDisabled` |

**Button: stan aktywowania**

![Przycisk po aktywowaniu](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. Aktywuj")<br />Przycisk po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonHover` |
| Obramowanie przycisku | `CommonControls.ButtonBorderHover` |

**Button: stan naciśniętego**

![Przycisk naciśnięty](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. naciśnięto")<br />Przycisk naciśnięty

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonPressed` |
| Obramowanie przycisku | `CommonControls.ButtonBorderPressed` |

**Przycisk: priorytetowy stan**

![Przycisk priorytetowy](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button.")<br />Przycisk priorytetowy

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonFocused` |
| Obramowanie przycisku | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrolki pola wyboru
![Pole wyboru (Redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 — 161_CheckboxRedline")<br />Pole wyboru (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla kontrolek pola wyboru zawartych w tym dokumencie. | ... dla wszystkich interfejsów użytkownika, które nie są kontrolką pola wyboru. |

**Pole wyboru: stan domyślny**

![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 — 162_Checkbox")<br />Domyślne pole wyboru

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackground` |
| Obramowanie | `CommonControls.CheckBoxBorder` |
| Tekst | `CommonControls.CheckBoxText` |
| Symbol | `CommonControls.CheckBoxGlyph` |

**Pole wyboru: stan wyłączony**

![Wyłączone pole wyboru](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 — 163_CheckboxDisabled")<br />Wyłączone pole wyboru

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.CheckBoxBorderDisabled` |
| Tekst | `CommonControls.CheckBoxTextDisabled` |
| Symbol | `CommonControls.CheckBoxGlyphDisabled` |

**Pole wyboru: stan aktywowania**

 ![Pole wyboru przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 — 164_CheckboxHover")<br />Pole wyboru przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundHover` |
| Obramowanie | `CommonControls.CheckBoxBorderHover` |
| Tekst | `CommonControls.CheckBoxTextHover` |
| Symbol | `CommonControls.CheckBoxGlyphHover` |

**Pole wyboru: stan naciśniętego**

![Naciśnięte pole wyboru](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 — 165_CheckboxPressed")<br />Naciśnięte pole wyboru

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Obramowanie | `CommonControls.CheckBoxBorderPressed` |
| Tekst | `CommonControls.CheckBoxTextPressed` |
| Symbol | `CommonControls.CheckBoxGlyphPressed` |

**Pole wyboru: priorytetowy stan**

![Pole wyboru skoncentrowane](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 — 166_CheckboxFocused")<br />Pole wyboru skoncentrowane

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundFocused` |
| Obramowanie | `CommonControls.CheckBoxBorderFocused` |
| Tekst | `CommonControls.CheckBoxTextFocused` |
| Symbol | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listy rozwijane i pola kombi
![Lista rozwijana/pole kombi (Redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 — 167_DropDownComboBoxRedline")<br />Lista rozwijana/pole kombi (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w polu listy rozwijane i pola kombi w obszarze dokumentu. | ... dla każdego interfejsu użytkownika, który nie jest polem listy rozwijanej ani pola kombi. |
| | ... [Lista rozwijana](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) lub [pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listy rozwijane i pola kombi: stan domyślny**

![Domyślne pole listy rozwijanej/kombi](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 — 168_DropDownComboBox")<br />Domyślne pole listy rozwijanej/kombi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackground` |
| Obramowanie | `CommonControls.ComboBoxBorder` |
| Tekst | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Symbol | `CommonControls.ComboBoxGlyph` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackground` |

**Listy rozwijane i pola kombi: stan wyłączony**

![Wyłączone pole listy rozwijanej/kombi](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 — 169_DropDownComboBoxDisabled")<br />Wyłączone pole listy rozwijanej/kombi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.ComboBoxBorderDisabled` |
| Tekst | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Symbol | `CommonControls.ComboBoxGlyphDisabled` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listy rozwijane i pola kombi: stan aktywowania**

![Lista rozwijana/pole kombi przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 — 170_DropDownComboBoxHover")<br />Lista rozwijana/pole kombi przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundHover` |
| Obramowanie | `CommonControls.ComboBoxBorderHover` |
| Tekst | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Symbol | `CommonControls.ComboBoxGlyphHover` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listy rozwijane i pola kombi: stan naciśniętych**

![Naciśnięte pole listy rozwijanej/pola kombi](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 — 171_DropDownComboBoxPressed")<br />Naciśnięte pole listy rozwijanej/pola kombi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundPressed` |
| Obramowanie | `CommonControls.ComboBoxBorderPressed` |
| Tekst | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Symbol | `CommonControls.ComboBoxGlyphPressed` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Lista rozwijana i pola kombi widok elementu listy: stan naciśnięte**

 ![Widok elementu listy rozwijanej/pola kombi](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 — 174_DropDownComboBoxListView")<br />Widok elementu listy rozwijanej/pola kombi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Tekst elementu | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Cień tła | `CommonControls.ComboBoxListBackgroundShadow` |

**Listy rozwijane i pola kombi: priorytetowy stan**

![Lista rozwijana/pole kombi z fokusem](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 — 172_DropDownComboBoxFocused")<br />Lista rozwijana/pole kombi z fokusem

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxBorderFocused` |
| Tekst | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Symbol | `CommonControls.ComboBoxGlyphFocused` |
| Tło symbolu | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listy rozwijane i pola kombi: wybór wprowadzania tekstu**

![Pole listy rozwijanej i wprowadzanie tekstu w polu kombi](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 — 173_DropDownComboBoxTextInput")<br />Pole listy rozwijanej i wprowadzanie tekstu w polu kombi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Wyróżnij | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelarycznych (siatka)
Kontrolki danych tabelarycznych, znane także jako kontrolki siatki, są typowymi kontrolkami dla programu Visual Studio, których można użyć do prezentowania dużych ilości danych w wielu kolumnach. Standardowe kontrolki danych tabelarycznych można znaleźć w wielu miejscach w programie Visual Studio: okno narzędzia Lista błędów, raporty IntelliTrace i widok sterty pamięci, między innymi. Należy zawsze używać standardowych formantów danych tabelarycznych. W niektórych rzadkich przypadkach może nie mieć dostępu do standardowych formantów danych tabelarycznych. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelarycznych w programie Visual Studio.

![Kontrolka danych tabelarycznych/siatki (Redline)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 — 197_TabularDataGridControlRedline")<br />Kontrolka danych tabelarycznych/siatki (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla kontrolek tabelarycznych lub siatki. | ... dla każdego interfejsu użytkownika, który nie jest kontrolką tabelaryczną lub siatką. |

#### <a name="column-headers"></a>Nagłówki kolumn
Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego symbolu zwykle używane, gdy siatka jest posortowana według tej kolumny.

**Nagłówek kolumny: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Header.Default` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (symbol) | `Header.Glyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan aktywowania**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Header.MouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (symbol) | `Header.MouseOverGlyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan naciśniętego**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Pierwszy plan (tekst) | `CommonControls.CheckBoxBorderPressed` |
| Pierwszy plan (symbol) | `CommonControls.CheckBoxTextPressed` |
| Obramowanie | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Wyświetl listę elementów
 Elementy widoku listy składają się z tła i zawartości. Zawartość może być tekstem, ikoną lub obu.

**Elementy widoku listy: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Przezroczyste |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Elementy widoku listy: stan aktywny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActiveText` |
| Obramowanie | Brak |

**Elementy widoku listy: stan nieaktywny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactiveText` |
| Obramowanie | Brak |

### <a name="ui-text"></a>Tekst interfejsu użytkownika

#### <a name="instructional-text"></a>Tekst instruktażowy
Tekst instruktażowy zawiera wyraźne główne wyjaśnienie, co należy zrobić w oknie dialogowym lub stronie dokumentu.

![Domyślny tekst instrukcji](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Domyślny tekst instrukcji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Pomocniczy tekst instrukcji
Na stronach dokumentu z dużą ilością tekstu i kontrolek, niektóre teksty instruktażowe wykorzystują inną wartość koloru. Pozwala to na przekazywanie informacji najważniejszych i zmniejsza ogólną gęstość elementów interfejsu użytkownika. (Zobacz również poniżej sekcję dotyczącą tekstu wskazówki).

![Pomocniczy tekst instrukcji](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Pomocniczy tekst instrukcji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Tekst wskazówki
Tekst wskazówki pojawia się w pustej kontrolce, poniżej kontrolki lub na pustej powierzchni dokumentu, aby pokazać użytkownikowi, co należy zrobić dalej. Możesz użyć tekstu wskazówki z tłem okna lub formantu.

**Domyślny tekst wskazówki**

![Domyślny tekst wskazówki](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Domyślny tekst wskazówki

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

**Wymagany tekst wskazówki**

![Wymagany tekst wskazówki](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Wymagany tekst wskazówki

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlRequiredHintText` |
| Tło | `Environment.ControlRequiredBackground` |

**Tekst kontrolny pola wyszukiwania**

> Zobacz [pola wyszukiwania](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) dla innych tokenów kolorów związanych z kontrolką wyszukiwania.

![Tekst kontrolny pola wyszukiwania](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Tekst kontrolny pola wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Hiperłącze jest jedną kontrolką, która nie ma pary pierwszego planu i tła. We wszystkich przypadkach Użyj koloru hiperlinku pierwszego planu, który będzie wyświetlany prawidłowo na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu koloru dla kontrolki Hyperlink, zobaczysz domyślny kolor systemowy dla "naciśniętego", który będzie miał barwę błyskową Red. Jest to sygnał, że formant nie używa poprawnego tokenu koloru środowiska.

![Hyperlink (Redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 — 133_HyperlinkRedline")<br />Hyperlink (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdy musisz utworzyć niestandardowe hiperłącze. | ... dla wszystkich elementów, które nie są hiperłączem. |

**Hyperlink: stan domyślny**

![Hiperłącze domyślne](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 — 134_Hyperlink")<br />Hiperłącze domyślne

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlink` |

**Hyperlink: stan aktywowania**

![Hiperłącze przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 — 135_HyperlinkHover")<br />Hiperłącze przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkHover` |

**Hyperlink: stan naciśniętych**

![Naciśnięto hiperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 — 136_HyperlinkPressed")<br />Naciśnięto hiperlink

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkPressed` |

**Hiperlink: stan wyłączony**

![Wyłączone hiperłącze](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 — 137_HyperlinkDisabled")<br />Wyłączone hiperłącze

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Infobars są używane do udostępniania więcej informacji na temat danego kontekstu i są zawsze wyświetlane w górnej części okna dokumentu lub okna narzędzi.

![Pasek informacyjny (Redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 — 138_InfobarRedline")<br />Pasek informacyjny (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowej infobars. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego. |

**Pasek informacyjny: stan domyślny**

![Domyślny pasek informacyjny](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 — 139_Infobar")<br />Domyślny pasek informacyjny

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.InfoBarBackground` |
| Pierwszy plan (tekst) | `InfoBar.InfoBar` |
| Obramowanie | `InfoBar.InfoBarBorder` |

**Przycisk zamykania paska informacji ( &times; ): stan domyślny**

![Domyślny przycisk zamykania paska informacji ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Domyślny przycisk zamykania paska informacji ( &times; )

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.CloseButton` |
| Obramowanie | `InfoBar.CloseButtonBorder` |
| Symbol | `InfoBar.CloseButtonGlyph` |

**Przycisk Zamknij pasek informacji ( &times; ): stan aktywowania**

![Przycisk zamykania paska informacji ( &times; ) po aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Przycisk zamykania paska informacji ( &times; ) po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.CloseButtonHover` |
| Obramowanie | `InfoBar.CloseButtonHoverBorder` |
| Symbol | `InfoBar.CloseButtonHoverGlyph` |

**Przycisk zamykania paska informacji ( &times; ): stan naciśniętego**

![Przycisk zamykania paska na pasku informacji ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Przycisk zamykania paska na pasku informacji ( &times; )

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.CloseButtonDown` |
| Obramowanie | `InfoBar.CloseButtonDownBorder` |
| Symbol | `InfoBar.CloseButtonDownGlyph` |

**Przycisk hiperłącza paska informacji: stan domyślny**

![Przycisk hiperłącza domyślnego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Przycisk hiperłącza domyślnego paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Przycisk hiperłącza paska informacji: stan aktywowania**

![Przycisk hiperłącza paska informacji po aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Przycisk hiperłącza paska informacji po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Przycisk hiperłącza paska informacji: stan naciśnięte**

![Przycisk hiperłącza naciśniętego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Przycisk hiperłącza naciśniętego paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreśleniem) |

**Hiperłącze wbudowane na pasku informacyjnym (w zdaniu): domyślny stan**

![Przycisk hiperłącza domyślnego wbudowanego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Przycisk hiperłącza domyślnego wbudowanego paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Hiperłącze wbudowane paska informacji (w zdaniu): stan aktywowania**

![Przycisk hiperłącza wbudowanego na pasku informacji na aktywowanie](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Przycisk hiperłącza wbudowanego na pasku informacji na aktywowanie

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Hiperłącze wbudowane paska informacji (w zdaniu): stan naciśniętego**

![Przycisk hiperłącza naciśniętego na pasku informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Przycisk hiperłącza naciśniętego na pasku informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreśleniem) |

**Przycisk paska informacji: domyślny stan**

![Domyślny przycisk paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Domyślny przycisk paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.Button` |
| Pierwszy plan (tekst) | `InfoBar.Button` |
| Obramowanie | `InfoBar.ButtonBorder` |

**Przycisk paska informacji: stan aktywowania**

![Przycisk paska informacji po aktywowaniu](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Przycisk paska informacji po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseOver` |
| Pierwszy plan (tekst) | `InfoBar.ButtonMouseOver` |
| Obramowanie | `InfoBar.ButtonMouseOverBorder` |

**Przycisk paska informacji: stan naciśniętego**

![Przycisk naciśniętego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Przycisk naciśniętego paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseDown` |
| Pierwszy plan (tekst) | `InfoBar.ButtonMouseDown` |
| Obramowanie | `InfoBar.ButtonMouseDownBorder` |

**Przycisk paska informacji: stan wyłączenia**

![Przycisk wyłączony pasek informacyjny](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Przycisk wyłączony pasek informacyjny

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.ButtonDisabled` |
| Pierwszy plan (tekst) | `InfoBar.ButtonDisabled` |
| Obramowanie | `InfoBar.ButtonDisabledBorder` |

**Przycisk paska informacji: priorytetowy stan**

![Przycisk fokusowego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Przycisk fokusowego paska informacji

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `InfoBar.ButtonFocus` |
| Pierwszy plan (tekst) | `InfoBar.ButtonFocus` |
| Obramowanie | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania są wzorowane przez środowisko programu Visual Studio i nie muszą być dla nich konieczne. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w paskach przewijania, tak aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.

![Pasek przewijania (Redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 — 140_ScrollbarRedline")<br />Pasek przewijania (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... Gdy tworzysz interfejs użytkownika, który chcesz dopasować do pasków przewijania programu Visual Studio. | ... dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika paska przewijania. |

**Pasek przewijania: stan domyślny**

![Domyślny pasek przewijania](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 — 141_Scrollbar")<br />Domyślny pasek przewijania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbBackground` |

**Pasek przewijania: stan aktywowania**

![Pasek przewijania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 — 143_ScrollbarHover")<br />Pasek przewijania przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbMouseOverBackground` |

*Pasek przewijania: stan naciśniętych**

![Naciśnięto pasek przewijania](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 — 145_ScrollbarPressed")<br />Naciśnięto pasek przewijania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbPressedBackground` |

**Strzałka paska przewijania: stan domyślny**

![Domyślna strzałka paska przewijania](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 — 142_ScrollbarArrow")<br />Domyślna strzałka paska przewijania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowBackground`<br />(Ustaw na ten sam kolor jako pasek przewijania). |
| Pierwszy plan (symbol) | `Environment.ScrollBarArrowGlyph` |

**Strzałka paska przewijania: stan aktywowania**

![Strzałka paska przewijania przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 — 144_ScrollbarArrowHover")<br />Strzałka paska przewijania przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowMouseOverBackground`<br />(Ustaw na ten sam kolor jako pasek przewijania). |
| Pierwszy plan (symbol) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Strzałka paska przewijania: stan naciśniętych**

![Strzałka naciśniętego paska przewijania](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 — 146_ScrollbarArrowPressed")<br />Strzałka naciśniętego paska przewijania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowPressedBackground`<br />(Ustaw na ten sam kolor jako pasek przewijania). |
| Pierwszy plan (symbol) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Pola wyszukiwania
Jeśli to możliwe, użyj typowej kontrolki wyszukiwania dostarczonej przez środowisko programu Visual Studio. Kolory pola wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors. pkgdef** , który zawiera nazwy tokenów pola wejściowego, akcji przycisku, listy rozwijanej i menu rozwijanego.

Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wykluczają się wzajemnie:

- "Skoncentrowane" lub "bez fokusu" odnosi się do tego, czy kursor znajduje się w polu tekstowym.

- "Aktywne" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadza zapytanie wyszukiwania w polu tekstowym.

- "Aktywowany" oznacza, że użytkownik przeznaczył mysz nad polem wyszukiwania za pomocą myszy (ten stan zastępuje wszystkie inne Stany).

- Wartość "wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.

![Pole wyszukiwania (Redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 — 110_SearchBoxRedline")<br />Pole wyszukiwania (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania niestandardowego pola wyszukiwania. | ... dla wszystkich elementów, które nie są polem wyszukiwania. |
| | ... dla wszystkich elementów, które nie powinny być zawsze zgodne z interfejsem użytkownika pola wyszukiwania. |

**Pole wejściowe wyszukiwania ukierunkowanego**

![Pole wejściowe wyszukiwania ukierunkowanego](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 — 111_SearchInputFieldFocused")<br />Pole wejściowe wyszukiwania ukierunkowanego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.FocusedBackground` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Nieskoncentrowane, aktywne pole wejściowe wyszukiwania**

![Wyszukiwanie pola wejściowego jako nieskoncentrowane](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 — 114_SearchInputFieldUnfocused")<br />Nieskoncentrowane, aktywne pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.SearchActiveBackground` |
| Pierwszy plan (tekst) | `SearchControl.SearchActiveBackground` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Nieskoncentrowane pole wejściowe wyszukiwania nieaktywnego**

![Nieskoncentrowane pole wejściowe wyszukiwania nieaktywnego](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nieskoncentrowane pole wejściowe wyszukiwania nieaktywnego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.Unfocused` |
| Pierwszy plan (tekst) | `SearchControl.Unfocused` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Wyróżnione pole wejściowe wyszukiwania (tylko tekst)**

![Wyróżnione pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 — 120_SearchInputFieldHighlight")<br />Wyróżnione pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.Selection` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | Brak |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Wyłączone pole wejściowe wyszukiwania**

![Wyłączone pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 — 121_SearchInputFieldDisabled")<br />Wyłączone pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.Disabled` |
| Pierwszy plan (tekst) | `SearchControl.Disabled` |
| Obramowanie | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Przycisk akcji wyszukiwania priorytetowego**

![Przycisk akcji wyszukiwania — fokus](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 — 112_SearchActionButtonFocused")<br />Przycisk akcji wyszukiwania priorytetowego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (symbol wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszy plan (symbol STOP) | `SearchControl.StopGlyph` |
| Pierwszy plan (czysty symbol) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk akcji wyszukiwania nieskoncentrowanego**

![Przycisk akcji wyszukiwania nieskoncentrowanego](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 — 115_SearchActionButtonUnfocused")<br />Przycisk akcji wyszukiwania nieskoncentrowanego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszy plan (symbol STOP) | `SearchControl.StopGlyph` |
| Pierwszy plan (czysty symbol) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk akcji wyszukiwania naciśniętego**

![Przycisk akcji wyszukiwania naciśniętego](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Przycisk akcji wyszukiwania naciśniętego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.ActionButtonMouseDown` |
| Pierwszy plan (symbol) | `SearchControl.ActionButtonMouseDownGlyph` |
| Obramowanie | `SearchControl.ActionButtonMouseDownBorder` |

**Przycisk akcji wyszukiwania wyłączone**

![Przycisk akcji wyszukiwania jest wyłączony](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 — 122_SearchActionButtonDisabled")<br />Przycisk akcji wyszukiwania wyłączone

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (symbol) | `SearchControl.ActionButtonDisabledGlyph` |
| Obramowanie | Brak |

**Przycisk listy rozwijanej wyszukiwania ukierunkowanego**

![Przycisk listy rozwijanej wyszukiwania ukierunkowanego](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 — 113_SearchDropdownButtonFocused")<br />Przycisk listy rozwijanej wyszukiwania ukierunkowanego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.FocusedDropDownButton` |
| Pierwszy plan (symbol) | `SearchControl.FocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.FocusedDropDownButtonBorder` |

**Przycisk listy rozwijanej wyszukiwanie nieskoncentrowane**

![Przycisk listy rozwijanej wyszukiwanie nieskoncentrowane](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 — 116_SearchDropdownButtonUnfocused")<br />Przycisk listy rozwijanej wyszukiwanie nieskoncentrowane

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.UnfocusedDropDownButton` |
| Pierwszy plan (symbol) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.UnfocusedDropDownButtonBorder` |

**Przycisk listy rozwijanej naciśniętego wyszukiwania**

![Przycisk listy rozwijanej naciśniętego wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Przycisk listy rozwijanej naciśniętego wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.MouseDownDropDownButton` |
| Pierwszy plan (symbol) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Obramowanie | `SearchControl.MouseDownDropDownButtonBorder` |

**Przycisk listy rozwijanej wyłączone wyszukiwanie**

![Przycisk listy rozwijanej wyłączone wyszukiwanie](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 — 123_SearchDropdownButtonDisabled")<br />Przycisk listy rozwijanej wyłączone wyszukiwanie

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (symbol) | `SearchControl.DisabledDownButtonGlyph` |
| Obramowanie | Brak |

#### <a name="search-drop-down-lists"></a>Lista rozwijana wyszukiwania
Menu rozwijane pola wyszukiwania może być nieco bardziej złożone niż inne menu rozwijane w programie Visual Studio. Sekcje "sugerowane wyszukiwania" i "Opcje wyszukiwania" mogą występować samodzielnie lub razem w menu, a każdy z nich jest kolorowy osobno. Linia oddziela również te dwie sekcje, gdy pojawiają się razem, a obramowanie otacza całe menu rozwijane.

![Lista rozwijana wyszukiwania (Redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 — 124_SearchDropdownRedline")<br />Lista rozwijana wyszukiwania (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia listy rozwijanej wyszukiwanie niestandardowe. | ... dla list rozwijanych, które są wyświetlane w innych kontekstach. |
| ... poprawne nazwy tokenów dla poprawnych składników listy. | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Wyszukaj elementy listy rozwijanej**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Obramowanie | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Sugerowane wyszukiwania: stan domyślny**

![Sugerowane domyślne wyszukiwania](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 — 125_SearchSuggested")<br />Sugerowane domyślne wyszukiwania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `SearchControl.PopupItemText` |

**Sugerowane wyszukiwania: stan aktywowania**

![Sugerowane wyszukiwania na aktywowaniu](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 — 128_SearchSuggestedHover")<br />Sugerowane wyszukiwania na aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `SearchControl.PopupMouseOverItemText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan domyślny**

![Pole wyboru wyszukiwania](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 — 126_SearchCheckbox")<br />Domyślne opcje wyszukiwania (pole wyboru)

![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 — 127_SearchOptions")<br />Domyślne opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxText` |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonText` |
| Tło nagłówka | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst nagłówka) | `SearchControl.PopupSectionHeaderText` |

**Opcje wyszukiwania: stan aktywowania**

![Opcje wyszukiwania (pole wyboru) przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 — 129_SearchCheckboxHover")<br />Opcje wyszukiwania (pole wyboru) przy aktywowaniu

![Opcje wyszukiwania (link) przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 — 130_SearchOptionsHover")<br />Opcje wyszukiwania (link) przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonMouseDownText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan naciśniętych**

![Opcje wyszukiwania naciśniętego (pole wyboru)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 — 131_SearchSuggestedPressed")<br />Opcje wyszukiwania naciśniętego (pole wyboru)

![Opcje wyszukiwania naciśniętego (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 — 132_SearchOptionsPressed")<br />Opcje wyszukiwania naciśniętego (link)

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło pola wyboru | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Tło łącza | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Widoki drzewa
Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwera i Widok klasy, Implementuj hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w `TreeView` kategorii. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy z zagnieżdżonymi elementami podrzędnymi również mają glify wskazujące, czy element jest rozwinięty, czy zwinięty.

![Widok drzewa (Redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 — 147_TreeViewRedline")<br />Widok drzewa (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... wszędzie tam, gdzie trzeba zaimplementować hierarchiczny widok organizacyjny. | ... dla wszystkich elementów, które nie są podobne do widoku drzewa. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Element widoku drzewa: stan domyślny**

![Domyślny element widoku drzewa](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 — 148_TreeView")<br />Domyślny element widoku drzewa

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (symbol) | `TreeView.Glyph` |
| Obramowanie | Brak |

**Element widoku drzewa: stan aktywowania**

![Element widoku drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 — 149_TreeViewHover")<br />Element widoku drzewa przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (symbol) | `TreeView.GlyphMouseOver` |
| Obramowanie | Brak |

**Element widoku drzewa: przeciągnij nad stanem**

![Element widoku drzewa na przeciągnięciu](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 — 150_TreeViewDragOver")<br />Element widoku drzewa na przeciągnięciu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.DragOverItem` |
| Pierwszy plan (tekst) | `TreeView.DragOverItem` |
| Pierwszy plan (symbol) | `TreeView.DragOverItemGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: wybrany, priorytetowy stan**

![Wybrany i skoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 — 151_TreeViewFocused")<br />Wybrany i skoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (symbol) | `TreeView.SelectedItemActiveGlyph` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: wybrany stan nieskoncentrowany**

![Wybrany i nieskoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 — 152_TreeViewUnfocused")<br />Wybrany i nieskoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (symbol) | `TreeView.SelectedItemInactiveGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: aktywowany, wybrany i priorytetowy stan**

![Wybrany i skoncentrowany element widoku drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 — 153_TreeViewFocusedHover")<br />Wybrany i skoncentrowany element widoku drzewa przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan aktywowany, wybrany i nieskoncentrowany**

![Zaznaczony i nieskoncentrowany element widoku drzewa przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 — 154_TreeViewUnfocusedHover")<br />Zaznaczony i nieskoncentrowany element widoku drzewa przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | Brak |

## <a name="shell-appearance"></a>Wygląd powłoki

### <a name="background"></a>Tło
Tło środowiska składa się z dwóch warstw. Warstwa dolna to pełny kolor, który obejmuje całe środowisko IDE. Górna warstwa dopasowuje się do półki poleceń i między oknem narzędzia a ukrywanie kanałów po lewej i prawej stronie IDE. Górne i dolne warstwy tła są ustawione na ten sam kolor w jasnych i ciemnych motywach.

![Tło powłoki programu Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 — 187_ShellBackgroundRedline")<br />Tło powłoki programu Visual Studio (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... miejsce, w którym chcesz dopasować tło środowiska programu Visual Studio. | ... jako wypełnienie miejsc, które nie są powierzchniami tła. |
| | ... jako tło do umieszczania elementów pierwszego planu. |

**Kolor dolnej powłoki warstwowej**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.EnvironmentBackground` |

**Wygląd górnej powłoki warstw**

> Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Półka polecenia
Dwa zestawy nazw tokenów są używane na potrzeby tła półki poleceń: jeden zestaw dla miejsca, w którym znajduje się pasek menu, i jeden dla miejsca, w którym znajdują się paski poleceń. Pojedyncza grupa pasków poleceń ma własne wartości koloru tła, które zostały omówione bardziej szczegółowo w sekcji "pasek poleceń". Tekst paska menu i paska poleceń jest omówiony odpowiednio w sekcji menu i paska poleceń.

![Półka poleceń programu Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 — 188_CommandShelfRedline")<br />Półka poleceń programu Visual Studio (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku obszarów, w których są umieszczane menu lub paski narzędzi. | ... w przypadku obszarów, które nie są podobne do półki poleceń. |
|... z poprawną kombinacją nazw tokenów tła/pierwszego planu. | |

**Pasek menu półki polecenia**

> Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Pasek poleceń półki polecenia**

> Ustawienie gradientu ma ustawioną wartość tego samego koloru w Visual Studio 2013 jasnym i ciemnym motywie.

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest Designer
Projektant manifestu został zaprojektowany jako sposób ułatwiający edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Chociaż nie jest dostępna żadna udostępniona architektura do użycia, może być odpowiednie dopasowanie układu projektu i kolorów na kartach Orientacja/Nawigacja i ogólna struktura. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Projektant manifestu (Redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 — 175_ManifestDesignerRedline")<br />Projektant manifestu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla projektantów, które są podobne do projektanta manifestu. | ... Jeśli masz więcej niż sześć kart. |
| ... zamiast używania wspólnych kontrolek kart w górnej części edytora w obszarze dokumentu. | ... dla każdego interfejsu użytkownika, który nie jest uporządkowany jak projektant manifestu. |

**Wybrana karta projektanta manifestu: domyślny stan**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `ManifestDesigner.TabActive` |
| Obramowanie | Brak |

**Okienko opisu wybranego projektanta manifestu: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `ManifestDesigner.DescriptionPane` |

**Strona zawartości wybranego projektanta manifestu: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `ManifestDesigner.Background` |
| Tekst pomocnika okna dialogowego | `ManifestDesigner.WatermarkText`<br />(Ta nazwa tokenu nie jest zgodna z jej funkcją). |

**Karta projektanta manifestu: niezaznaczony stan**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Inactive` |

**Karta projektanta manifestu: stan aktywowania**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Struktury poleceń

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menu
Menu mogą wystąpić w kilku miejscach w programie Visual Studio: główny pasek menu, osadzony w dokumencie lub narzędziu, lub po kliknięciu prawym przyciskiem myszy w różnych lokalizacjach w środowisku IDE. Implementacje menu skojarzonych z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiedniego elementu. Należy zawsze używać standardowej implementacji menu dostarczanej przez środowisko programu Visual Studio. Jednak w niektórych rzadkich przypadkach może nie mieć dostępu do standardowych menu programu Visual Studio. W takich sytuacjach Użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w programie Visual Studio.

![Menu programu Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 — 000_MenuRedline")<br />Menu programu Visual Studio (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdy musisz utworzyć niestandardowe menu.| ... sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu w określony sposób. |
| ... gdy masz nowy składnik interfejsu użytkownika, który chcesz dopasować do menu programu Visual Studio.| |

#### <a name="menu-titles"></a>Tytuły menu
Tytuły menu składają się z tła, obramowania i tekstu tytułu, a także symbolu opcjonalnego, zazwyczaj gdy menu znajduje się na pasku poleceń.

![Tytuł menu (Redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 — 001_MenuTitleRedline")<br />Tytuł menu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... za każdym razem, gdy tworzysz tytuł menu niestandardowego. | ... dla wszystkich elementów, które nie powinny być zawsze zgodne z tytułem menu. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Tytuł menu: stan domyślny**

![Tytuł menu domyślnego](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 — 002_MenuTitleDefault")<br />Tytuł menu domyślnego

![Tytuł menu domyślnego z glifem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 — 003_MenuTitleWithGlyphDefault")<br />Tytuł menu domyślnego z glifem

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (symbol) | `Environment.CommandBarMenuGlyph` |
| Obramowanie | Brak |

**Tytuł menu: stan aktywowania**

![Tytuł menu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 — 004_MenuTitleHover")<br />Tytuł menu przy aktywowaniu

![Tytuł menu z symbolem po aktywowaniu](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 — 005_MenuTitleWithGlyphHover")<br />Tytuł menu z symbolem po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (symbol) | `Environment.CommandBarMenuMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |

**Tytuł menu: stan naciśniętego**

![Tytuł menu naciśniętego](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 — 006_MenuTitlePressed")<br />Tytuł menu naciśniętego

![Tytuł menu naciśniętego z symbolem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 — 007_MenuTitleWithGlyphPressed")<br />Tytuł menu naciśniętego z symbolem

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (symbol) | `Environment.CommandBarMenuMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder`<br />(Tylko w lewo, u góry i po prawej stronie). |

**Tytuł menu: stan wyłączenia**

![Tytuł menu wyłączone z glifem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 — 008_MenuTitleWithGlyphDisabled")<br />Tytuł menu wyłączone z glifem

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszy plan (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

#### <a name="menu-items"></a>Elementy menu
Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub symbolu podmenu. Zmiana koloru tła i tekstu przy aktywowaniu. Ten token koloru to para tła/pierwszego planu.

![Elementy menu Redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 — 009_MenuItemRedline")

| Użyj... | Nie używaj... |
|---|---|
| ... dla każdej listy rozwijanej, która jest uruchamiana z paska menu lub paska poleceń. | ... dla każdej listy rozwijanej w innym kontekście. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Elementy menu: stan domyślny**

![Domyślne elementy menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 — 010_MenuDefault")<br />Domyślne elementy menu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (symbol podmenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder` |
| Tło ikony kanału | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Elementy menu: Stany zaznaczone i wybrane**

![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 — 011_MenuChecked")<br />Zaznaczony element menu

![Wybrano menu](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 — 012_MenuSelected")<br />Wybrany element menu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Znacznik wyboru | `Environment.CommandBarCheckBox` |
| Znacznik wyboru tła | `Environment.CommandBarSelectedIcon` |
| Tło ikony | `Environment.CommandBarSelected` |
| Obramowanie ikony | `Environment.CommandBarSelectedBorder` |

**Elementy menu: stan aktywowania**

![Aktywowanie menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 — 013_MenuHover")<br />Element menu przy aktywowaniu

![Zaznaczono aktywowany menu](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 — 014_MenuHoverChecked")<br />Zaznaczony element menu przy aktywowaniu

![Wybrano aktywowany menu](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 — 015_MenuHoverSelected")<br />Wybrany element menu przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuItemMouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarMenuItemMouseOverText` |
| Pierwszy plan (symbol podmenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxMouseOver` |
| Znacznik wyboru tła | `Environment.CommandBarHoverOverSelectedIcon` |
| Tło ikony | `Environment.CommandBarHoverOverSelected` |
| Obramowanie ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementy menu: stan wyłączony**

![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 — 016_MenuDisabled")<br />Wyłączony element menu

![Wyłączono zaznaczenie opcji menu](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 — 017_MenuDisabledChecked")<br />Wyłączony element menu ze znacznikiem wyboru

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszy plan (symbol podmenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxDisabled` |
| Znacznik wyboru tła | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Paski poleceń
Pasek poleceń może pojawić się w wielu miejscach w środowisku IDE programu Visual Studio, w szczególności z półkami poleceń i osadzonych w oknach narzędzi lub dokumentów.

Ogólnie rzecz biorąc zawsze używaj standardowej implementacji paska poleceń dostarczonej przez środowisko programu Visual Studio. Zastosowanie mechanizmu standardowego gwarantuje, że wszystkie szczegóły wizualizacji będą wyświetlane poprawnie i że te elementy interaktywne będą stale działać z innymi kontrolkami paska poleceń programu Visual Studio. Jeśli jednak jest to konieczne, aby skompilować własny pasek poleceń, upewnij się, że styl jest poprawnie używany przy użyciu następujących nazw tokenów.

![Pasek poleceń Redline](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 — 018_CommandBarRedline")<br />Pasek poleceń (Redline)

![Przycisk przepełnienia Redline](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 — 019_OverflowButtonRedline")<br />Przycisk przepełnienia (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenów. |

#### <a name="command-bar-groups"></a>Grupy paska poleceń
Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przyciski podzielone, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów są regulowane przez oddzielne nazwy tokenów i są omawiane osobno w innym miejscu w tym przewodniku. Linia separatora służy do dzielenia grupy paska poleceń na powiązane podgrupy.

![Redline grupy paska poleceń](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 — 020_CommandBarGroupRedline")<br />Grupa paska poleceń (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w miejscach, gdzie jest potrzebny osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenów. |

**Grupa paska poleceń: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Obramowanie | `Environment.CommandBarToolBarBorder` |
| Przeciągnij uchwyt | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony poleceń
![Ikona polecenia Redline](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 — 021_CommandIconRedline1")<br />Ikona polecenia (Redline)

![Ikona polecenia z tekstem Redline](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 — 022_CommandIconRedline2")<br />Ikona polecenia z tekstem (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla każdego przycisku, który zostanie umieszczony na pasku poleceń. | ... dla kontrolek mających własne nazwy tokenów. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Ikona polecenia: stan domyślny**

![Domyślna ikona polecenia](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 — 023_CommandIconDefault")<br />Ikona polecenia domyślnego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z poziomu tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Nie dotyczy |

**Ikona polecenia: stan domyślny, wybrane**

![Domyślna, wybrana ikona polecenia](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 — 024_CommandIconDefaultSelected")<br />Domyślna, wybrana ikona polecenia

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextSelected` |
| Obramowanie | `Environment.CommandBarSelectedBorder` |

**Ikona polecenia: stan aktywowania lub fokusu**

![Ikona polecenia na aktywowanie lub fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 — 025_CommandIconHover")<br />Ikona polecenia na aktywowanie lub fokus

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: Stany aktywowania lub fokusu, wybrane**

![Wybrana ikona polecenia na aktywowanie lub fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 — 026_CommandIconHoverSelected")<br />Wybrana ikona polecenia na aktywowanie lub fokus

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarHoverOverSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHoverOverSelected` |
| Obramowanie | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona polecenia: stan naciśniętego**

![Ikona polecenia naciśniętego](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 — 027_CommandIconPressed")<br />Ikona polecenia naciśniętego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stan wyłączony**

![Ikona polecenia wyłączonego](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 — 028_CommandIconDisabled")<br />Ikona polecenia wyłączonego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z poziomu tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Pola kombi paska poleceń

> [!IMPORTANT]
> Pola kombi są podobne do list rozwijanych, ale zawierają edytowalny region tekstu. Jeśli lista rozwijana nie zawiera regionu tekstu edytowalnego, użyj tokenów koloru dla [listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Pole kombi Redline pasku poleceń](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 — 029_ComboBoxRedline")<br />Pole kombi paska poleceń (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas kompilowania niestandardowych pól kombi. | ... dla wszystkich elementów, które nie zawsze pasują do interfejsu użytkownika paska poleceń. |
| ... podczas tworzenia kontrolki paska poleceń, która jest podobna do pola kombi. | ... gdy masz dostęp do pola kombi z stylem. |

**Pole kombi pola wejściowego paska poleceń: domyślny stan**

![Pole kombi pola wejściowego paska poleceń](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 — 030_ComboBoxInputField")<br />Pole kombi pola wejściowego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxText` |
| Obramowanie | `Environment.ComboBoxBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej pasek poleceń: stan domyślny**

![Pole kombi upuść&#45;przycisk w dół](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 — 031_ComboBoxDropdownButton")<br />Przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z poziomu tła paska poleceń) |
| Pierwszy plan (symbol) | `Environment.ComboBoxGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Lista rozwijana paska poleceń](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 — 032_ComboBoxDropdownList")<br />Lista rozwijana paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxPopupBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.ComboBoxPopupBorder` |

**Pole kombi pola wejściowego paska poleceń: stan aktywowania**

![Pole kombi pola wejściowego paska poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 — 033_ComboBoxInputFieldHover")<br />Pole kombi pola wejściowego paska poleceń przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseOverText` |
| Obramowanie | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Przycisk listy rozwijanej pasek poleceń: stan aktywowania**

![Przycisk rozwijany pasek poleceń pole kombi po umieszczeniu wskaźnika myszy](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 — 034_ComboBoxDropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseOverBackground` |
| Pierwszy plan (symbol) | `Environment.ComboBoxMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan aktywowania**

 ![Lista rozwijana pola kombi paska poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 — 035_ComboBoxDropdownListHover")<br />Lista rozwijana paska poleceń przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło (element menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole kombi pola wejściowego paska poleceń: priorytetowy stan**

![Pole wejściowe pola kombi z fokusowym paskiem poleceń](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 — 036_ComboBoxInputFieldFocused")<br />Pole wejściowe pola kombi z fokusowym paskiem poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxFocusedText` |
| Obramowanie | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Przycisk listy rozwijanej pasek poleceń: priorytetowy stan**

![Przycisk listy rozwijanej priorytetowego paska poleceń](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 — 037_ComboBoxDropdownButtonFocused")<br />Przycisk listy rozwijanej priorytetowego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedButtonBackground` |
| Pierwszy plan (symbol) | `Environment.ComboBoxFocusedGlyph` |

 **Pole kombi pola wejściowego paska poleceń: stan naciśniętego**

![Pole kombi naciśniętego paska poleceń](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 — 038_ComboBoxInputFieldPressed")<br />Pole kombi naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseDownText` |
| Obramowanie | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Przycisk listy rozwijanej pasek poleceń: stan naciśnięte**

![Przycisk rozwijany pola kombi naciśniętego paska poleceń](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 — 039_ComboBoxDropdownButtonPressed")<br />Przycisk listy rozwijanej naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseDownBackground` |
| Pierwszy plan (symbol) | `Environment.ComboBoxMouseDownGlyph` |

**Pole kombi pola wejściowego paska poleceń: stan wyłączony**

![Pole wejściowe pola kombi wyłączonego paska poleceń](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 — 041_ComboBoxInputFieldDisabled")<br />Pole wejściowe pola kombi wyłączonego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ComboBoxDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxDisabledText` |
| Obramowanie | `Environment.ComboBoxDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej pasek poleceń: stan wyłączony**

![Przycisk listy rozwijanej pole kombi wyłączonego paska poleceń](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 — 040_ComboBoxDropdownButtonDisabled")<br />Przycisk listy rozwijanej wyłączony pasek poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (symbol) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Lista rozwijana paska poleceń

> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale brak edytowalnych regionów tekstu. Jeśli lista rozwijana zawiera region tekstu edytowalnego, użyj tokenów koloru dla [pól kombi paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Lista rozwijana paska poleceń (Redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 — 042_DropdownRedline")<br />Lista rozwijana paska poleceń (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowych kontrolek listy rozwijanej. | ... dla wszystkich elementów, które nie są podobne do listy rozwijanej. |
| | ... dla pól kombi lub przycisków podziału. |

**Pole wyboru listy rozwijanej paska poleceń: stan domyślny**

![Pole wyboru domyślnego paska poleceń menu rozwijanego](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 — 043_DropdownSelectionField")<br />Pole wyboru domyślnego paska poleceń menu rozwijanego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownBackground` |
| Pierwszy plan (tekst) | `DropDownText` |
| Obramowanie | `DropDownBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej pasek poleceń: stan domyślny**

![Przycisk listy rozwijanej domyślny pasek poleceń](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 — 044_DropdownButton")<br />Przycisk listy rozwijanej domyślny pasek poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (symbol) | `Environment.DropDownGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Lista rozwijana domyślnego paska poleceń](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 — 045_DropdownList")<br />Lista rozwijana domyślnego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownPopupBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.DropDownPopupBorder` |
| W tle | `Environment.DropShadowBackground` |

**Pole wyboru listy rozwijanej paska poleceń: stan aktywowania**

![Pole wyboru menu rozwijanego paska poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 — 046_DropdownSelectionFieldHover")<br />Pole wyboru menu rozwijanego paska poleceń przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.DropDownMouseOverText` |
| Obramowanie | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Przycisk listy rozwijanej pasek poleceń: stan aktywowania**

![Przycisk listy rozwijanej paska poleceń po aktywowaniu](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 — 047_DropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseOverBackground` |
| Pierwszy plan (symbol) | `Environment.DropDownMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan aktywowania**

![Lista rozwijana paska poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 — 048_DropdownListHover")<br />Lista rozwijana paska poleceń przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło (element menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wyboru listy rozwijanej paska poleceń: stan naciśniętego**

![Naciśnięto pole wyboru&#45;w dół](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 — 049_DropdownSelectionFieldPressed")<br />Pole wyboru naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownMouseDownText` |
| Obramowanie | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Przycisk listy rozwijanej pasek poleceń: stan naciśnięte**

![Przycisk listy rozwijanej naciśniętego paska poleceń](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 — 050_DropdownButtonPressed")<br />Przycisk listy rozwijanej naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseDownBackground` |
| Pierwszy plan (symbol) | `Environment.DropDownMouseDownGlyph` |

**Pole wyboru listy rozwijanej paska poleceń: stan wyłączony**

![Pole wyboru wyłączonego paska poleceń](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 — 051_DropdownSelectionFieldDisabled")<br />Pole wyboru wyłączonego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DropDownDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownDisabledText` |
| Obramowanie | `Environment.DropDownDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej pasek poleceń: stan wyłączony**

![Przycisk listy rozwijanej wyłączony pasek poleceń](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 — 052_DropdownButtonDisabled")<br />Przycisk listy rozwijanej wyłączony pasek poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Przyciski podziału paska poleceń
Przyciski podziału współdzielą wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne nazwy tokenów przycisku akcji i listy rozwijanej są powtarzane w tym miejscu dla wygody. Lista rozwijana przycisku podziału to implementacje [menu paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Przycisk podziału Redline](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 — 053_SplitButtonRedline")<br />Przycisk podziału paska poleceń (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowego przycisku podziału. | ... dla innych rodzajów przycisków. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Przycisk podziału paska poleceń: domyślny stan**

![Przycisk podziału domyślnego paska poleceń](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 — 054_SplitButton")<br />Przycisk podziału domyślnego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (symbol) | `Environment.CommandBarSplitButtonGlyph` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: stan aktywowania**

![Przycisk podziału paska poleceń po aktywowaniu](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 — 055_SplitButtonHover")<br />Przycisk podziału paska poleceń po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (symbol) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Przycisk podziału paska poleceń: stan naciśniętego**

![Przycisk podziału naciśniętego paska poleceń](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 — 056_SplitButtonPressed")<br />Przycisk podziału naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Pierwszy plan (symbol) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: wyłączony stan**

![Przycisk podziału wyłączonego paska poleceń](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 — 057_SplitButtonDisabled")<br />Przycisk podziału wyłączonego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemTextInactive` |
| Pierwszy plan (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Przyciski "więcej opcji" i "overflow" paska poleceń
Przycisk "więcej opcji" jest używany, gdy grupy paska poleceń można dostosowywać przez dodawanie lub usuwanie powiązanych przycisków paska poleceń. Przycisk "przepełnienie" pojawia się, gdy pasek poleceń został obcięty z powodu braku miejsca w poziomie, a w obszarze kliknij Pokaż menu zawierające przyciski paska poleceń, których nie można wyświetlić. Kolory tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.

![Przycisk "więcej opcji" paska poleceń (Redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 — 058_MoreOptionsRedline")<br />Przycisk "więcej opcji" paska poleceń (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla niestandardowych przycisków "więcej opcji" lub "overflow". | ... przyciski, które nie mają podobnej funkcjonalności, do przycisku "więcej opcji" lub "overflow". |

**Przyciski "więcej opcji" i "overflow" paska poleceń: stan domyślny**

![Przycisk "więcej opcji" z domyślnym paskiem poleceń](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 — 059_MoreOptions")<br />Przycisk "więcej opcji" z domyślnym paskiem poleceń

![Przycisk "overflow" domyślnego paska poleceń](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 — 060_Overflow")<br />Przycisk "overflow" domyślnego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsBackground` |
| Pierwszy plan (symbol) | `Environment.CommandBarOptionsGlyph` |

**Pasek poleceń — przyciski "więcej opcji" i "overflow": stan aktywowania**

![Przycisk "więcej opcji" paska poleceń po aktywowaniu](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 — 061_MoreOptionsHover")<br />Przycisk "więcej opcji" paska poleceń po aktywowaniu

![Przycisk "overflow" paska poleceń przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 — 062_OverflowOptions")<br />Przycisk "overflow" paska poleceń przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Pasek poleceń "więcej opcji" i "overflow" przycisków: stan naciśnięty**

![Przycisk "więcej opcji" naciśniętego paska poleceń](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 — 063_MoreOptionsPressed")<br />Przycisk "więcej opcji" naciśniętego paska poleceń

![Naciśnięto przepełnienie](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 — 064_OverflowPressed")<br />Przycisk "overflow" naciśniętego paska poleceń

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentów
Nie ma potrzeby replikowania okien dokumentów, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach dokumentów, aby interfejs użytkownika zawsze był widoczny spójny z tą częścią środowiska programu Visual Studio.

W przypadku używania tokenów kolorów okna dokumentu należy zachować ostrożność, aby użyć ich tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, możesz uzyskać nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frames"></a>Ramki okna dokumentu
Okna dokumentów mogą być zadokowane w środowisku IDE lub przestawne jako oddzielne okno. Gdy okno dokumentu jest przepływa poza IDE, nadal znajduje się w dokumencie i ma kolory tła, obramowania, tekstu i karty, które są takie same, jak w przypadku części IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne kolory tła, obramowania i tekstu. Gdy okna narzędzi są zadokowane w tym dokumencie, dziedziczą one zachowanie i kolor ich kart z nazw tokenów okna dokumentu.

![Okno zadokowanego dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 — 065_DockedDocumentWindowRedline")<br />Okno zadokowanego dokumentu (Redline)

![Przestawne okno dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 — 066_FloatingDocumentWindowRedline")<br />Przestawne okno dokumentu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... wszędzie tam, gdzie tworzysz interfejs użytkownika, który chcesz dopasować do okna dokumentu. | ...  dla każdego interfejsu użytkownika, którego nie chcesz automatycznie zmieniać, jeśli powłoka ma aktualizację motywu. |

**Zadokowane lub przestawne okno dokumentu: stan domyślny**

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Zależy od typu dokumentu |
| Pierwszy plan (tekst) | Zależy od typu dokumentu |
| Obramowanie | `Environment.ToolWindowBorder` |

**Skoncentrowane, ruchome ramki okna dokumentu: stan domyślny**

![Domyślne skoncentrowane, przestawne ramki okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 — 067_FrameFocused")<br />Domyślne skoncentrowane, przestawne ramki okna dokumentu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (symbol) | `Environment.RaftedWindowButtonActiveGlyph` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonActiveBorder`<br />(Ustaw jako przezroczyste) |

**Nieskoncentrowane, ruchome ramki okna dokumentu: stan domyślny**

![Domyślnie nieskoncentrowane ramki okna dokumentu](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 — 068_FrameUnfocused")<br />Domyślnie nieskoncentrowane ramki okna dokumentu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (symbol) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Ustaw jako przezroczyste) |

**Skoncentrowane, ruchome ramki okna dokumentu: stan aktywowania**

![Skoncentrowana, ruchoma ramka okna dokumentu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 — 069_FrameFocusedHover")<br />Skoncentrowana, ruchoma ramka okna dokumentu przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonHoverActive` |
| Pierwszy plan (symbol) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Nieskoncentrowane, ruchome ramki okna dokumentu: stan aktywowania**

![Nieskoncentrowane, ruchome ramki okna dokumentu przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 — 070_FrameUnfocusedHover")<br />Nieskoncentrowane, ruchome ramki okna dokumentu przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło (symbol) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Pierwszy plan (symbol) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Skoncentrowana, ruchoma ramka okna dokumentu: stan naciśniętego**

![Skoncentrowane, ruchome ramki okna dokumentu przy naciśnięciu](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 — 071_FrameFocusedPressed")<br />Skoncentrowane, ruchome ramki okna dokumentu przy naciśnięciu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonDown` |
| Pierwszy plan (symbol) | `Environment.RaftedWindowButtonDownGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Karty dokumentów
Karty dokumentów znajdują się w kanale karty, aby wskazać, które dokumenty są obecnie otwarte, wraz z których jeden jest bieżącym zaznaczonym lub aktywnym dokumentem. Okna narzędzi można także zadokować w kanale karty dokumentu, jeśli użytkownik umieści je w tym miejscu. W takiej sytuacji używają tych samych kolorów karty co okna dokumentu. Jeśli tworzysz interfejs użytkownika, który chcesz zawsze dopasować kolory okna dokumentu (w tym aktualizacje motywu lub zainstalować nowe motywy), odwołując się do tych tokenów kolorów.

![Karty dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 — 072_DocumentTabRedline")<br />Karty dokumentu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdziekolwiek tworzysz interfejs użytkownika, który chcesz dopasować do kart dokumentów i automatycznie pobrać aktualizacje motywu lub nowe kolory motywu. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, gdy powłoka ma aktualizację motywu. |

#### <a name="open-document-tabs"></a>Otwórz karty dokumentów
Każdy otwarty dokument zawiera kartę w kanale karty dokumentu, który wyświetla jego nazwę. Dokumenty mogą być wybierane lub otwierane w tle, a ich karty odzwierciedlają te stany:

- Wybrana karta przedstawia dokument, który jest aktualnie wyświetlany w dokumencie. Wybrana karta zawiera obramowanie dokumentu, które rozciąga się między górną krawędzią dokumentu.

- Karty w tle to karty dokumentów, które nie są obecnie wybrane. Po kliknięciu stają się one wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.

![Otwórz kartę dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 — 073_OpenDocumentTabRedline")<br />Otwórz kartę dokumentu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowych kart dokumentów. | ... dla kart tymczasowych (Podgląd). |
| | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zaznaczona, karta skoncentrowanego dokumentu**

![Zaznaczona, karta skoncentrowanego dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 — 074_SelectedTabFocused")<br />Zaznaczona, karta skoncentrowanego dokumentu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabSelectedGradientTop`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.FileTabSelectedText` |
| Obramowanie | `Environment.FileTabSelectedBorder`<br />(Ustaw na ten sam kolor jako tło). |
| Obramowanie dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Zaznaczona, karta dokument nieskoncentrowany**

![Zaznaczona, karta dokument nieskoncentrowany](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 — 075_SelectedTabUnfocused")<br />Zaznaczona, karta dokument nieskoncentrowany

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabInactiveGradientTop`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.FileTabInactiveText` |
| Obramowanie | `Environment.FileTabInactiveBorder`<br />(Ustaw na ten sam kolor jako tło). |
| Obramowanie dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta dokumentu tła: stan domyślny**

![Domyślna karta dokumentu tła](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 — 076_BackgroundTab")<br />Domyślna karta dokumentu tła

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabBackground` |
| Pierwszy plan (tekst) | `Environment.FileTabText` |
| Obramowanie | `Environment.FileTabBorder`<br />(Ustaw na ten sam kolor jako tło). |

**Karta dokumentu tła: stan aktywowania**

![Zakładka dokumentu tła przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 — 077_BackgroundTabHover")<br />Zakładka dokumentu tła przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabHotGradientTop`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.FileTabHotText` |
| Obramowanie | `Environment.FileTabHotBorder`<br />(Ustaw na ten sam kolor jako tło). |

#### <a name="preview-tab"></a>Karta Podgląd
Nazywana również kartą "tymczasowy". Karta Podgląd zostanie wyświetlona po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksplorator rozwiązań. Działa jako wersja zapoznawcza dokumentu, a także daje użytkownikowi możliwość otwarcia dokumentu po lewej stronie kanału karty dokumentu. Tylko jedna otwarta karta podglądu może być otwarta w danym momencie. Karty podglądu mają Stany tła i wybrane, takie jak otwarte karty i mogą być skoncentrowane lub nieskoncentrowane w stanie aktywnym.

![Karta podglądu (Redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 — 078_PreviewTabRedline")<br />Karta podglądu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w dowolnym miejscu tworzysz tymczasową wersję zapoznawczą i chcesz, aby część elementu była zgodna z bieżącym kolorem karty podglądu. | ... dla dowolnego rodzaju dokumentu lub karty, która nie jest tymczasowa (wersja zapoznawcza). |
| | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zakładka z fokusem, wybrana wersja zapoznawcza**

![Zakładka z fokusem, wybrana wersja zapoznawcza](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 — 079_PreviewTabFocused")<br />Zakładka z fokusem, wybrana wersja zapoznawcza

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedActive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Ustaw na ten sam kolor jako tło). |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Nieskoncentrowana, wybrana karta podglądu**

![Nieskoncentrowana, wybrana karta podglądu](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 — 080_PreviewTabUnfocused")<br />Nieskoncentrowana, wybrana karta podglądu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Podgląd w tle: stan domyślny**

![Domyślna karta podglądu tła](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 — 081_PreviewBackgroundTab")<br />Domyślna karta podglądu tła

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalInactiveBorder`<br />(Ustaw na ten sam kolor jako tło). |

**Karta Podgląd w tle: stan aktywowania**

![Karta podglądu w tle na aktywowaniu](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 — 082_PreviewBackgroundTabHover")<br />Karta podglądu w tle na aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalHover` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalHoverForeground` |
| Obramowanie | `Environment.FileTabProvisionalHoverBorder`<br />(Ustaw na ten sam kolor jako tło). |

#### <a name="document-overflow-button"></a>Przycisk przepełnienia dokumentu
Przycisk przepełnienia dokumentu jest obecny, jeśli istnieje co najmniej jeden otwarty dokument, bez względu na to, czy w bieżącej konfiguracji znajduje się odstęp w pionie, aby dopasować wszystkie karty dokumentu. Menu rozwijane przepełnienie dokumentu, które jest kontrolowane przez kolory [menu paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) , wyświetla listę wszystkich otwartych dokumentów, zarówno widocznych, jak i ukrytych, i zmienia się w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale karty.

![Przycisk przepełnienia dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 — 083_OverflowRedline")<br />Przycisk przepełnienia dokumentu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowego przycisku przepełnienia dokumentu. | ... dla interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia. |
| | ... dla przycisków przepełnienia paska poleceń. |

**Przycisk przepełnienia dokumentu: stan domyślny**

![Przycisk przepełnienia dokumentu domyślnego](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 — 084_Overflow")<br />Przycisk przepełnienia dokumentu domyślnego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonBackground` |
| Pierwszy plan (symbol) | `Environment.DocWellOverflowButtonGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk przepełnienia dokumentu: stan aktywowania**

![Przycisk przepełnienia dokumentu po aktywowaniu](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 — 085_OverflowHover")<br />Przycisk przepełnienia dokumentu po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Pierwszy plan (symbol) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Przycisk przepełnienia dokumentu: stan naciśniętego**

![Przycisk przepełnienia dokumentu przy naciśnięciu klawisza](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 — 086_OverflowPressed")<br />Przycisk przepełnienia dokumentu przy naciśnięciu klawisza

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Pierwszy plan (symbol) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Znakowanie
Program Visual Studio obsługuje tagowanie, dzięki czemu użytkownik może zadeklarować słowa kluczowe do przeszukiwania do celów śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać Team Foundation Server (TFS) do tagowania elementów roboczych. Poniższe tabele zawierają nazwy kolorów zarówno dla samego tagu, jak i symboli "Close Icon", które pojawiają się w Stanach aktywowania i wybrane.

![Tagowanie w programie Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 — 176_TaggingRedline")<br />Tagowanie w programie Visual Studio (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla interfejsu użytkownika obsługującego tagowanie. | ... dla każdego innego typu interfejsu użytkownika. |

#### <a name="tags"></a>Tagi

**Tag: domyślny stan**

![Tag domyślny](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 — 177_Tag")<br />Tag domyślny

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.Background` |
| Pierwszy plan (tekst) | `Tag.Background` |

**Tag: stan aktywowania**

![Oznacz przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 — 178_TagHover")<br />Oznacz przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.HoverBackground` |
| Pierwszy plan (tekst) | `Tag.HoverBackgroundText` |

**Tag: stan naciśniętego**

![Naciśnięto tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 — 179_TagPressed")<br />Naciśnięto tag

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.PressedBackground` |
| Pierwszy plan (tekst) | `Tag.PressedBackgroundText` |

**Tag: wybrany stan**

![Wybrany tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 — 180_TagSelected")<br />Wybrany tag

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.SelectedBackground` |
| Pierwszy plan (tekst) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>&times;Symbol tagu Close ()

**&times;Symbol tagu Close (): stan domyślny**

![Domyślny &times; symbol tagu Close ()](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 — 181_TagGlyph")<br />Domyślny &times; symbol tagu Close ()

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol) | `Tag.TagHoverGlyph` |

**&times;Symbol tagu Close (): stan aktywowania**

![&times;Symbol tagu Close () przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 — 182_TagGlyphHover")<br />&times;Symbol tagu Close () przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphHoverBackground` |
| Pierwszy plan (symbol) | `Tag.TagHoverGlyphHover` |
| Obramowanie | `Tag.TagHoverGlyphHoverBorder` |

**&times;Symbol tagu Close (): stan naciśniętego**

![Symbol tagu zamykającego ( &times; )](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 — 183_TagGlyphPressed")<br />Symbol tagu zamykającego ( &times; )

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphPressedBackground` |
| Pierwszy plan (symbol) | `Tag.TagHoverGlyphPressed` |
| Obramowanie | `Tag.TagHoverGlyphPressedBorder` |

**Wybrany tag z symbolem zamykającym ( &times; ): stan domyślny**

![Domyślny zaznaczony tag z symbolem zamykającym ( &times; )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 — 184_TagSelected")<br />Domyślny zaznaczony tag z symbolem zamykającym ( &times; )

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol) | `Tag.TagSelectedGlyph` |

**Zaznaczony tag z symbolem zamykającym ( &times; ): stan aktywowany**

![Zaznaczony tag z symbolem zamykającym ( &times; ) przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 — 185_TagSelectedHover")<br />Zaznaczony tag z symbolem zamykającym ( &times; ) przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphHoverBackground` |
| Pierwszy plan (symbol) | `Tag.TagSelectedGlyphHover` |
| Obramowanie | `Tag.TagSelectedGlyphHoverBorder` |

**Zaznaczony tag z symbolem zamykającym ( &times; ): stan naciśniętego**

![Wybrany, naciśnięty tag z symbolem zamykającym ( &times; )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 — 186_TagSelectedPressed")<br />Wybrany, naciśnięty tag z symbolem zamykającym ( &times; )

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphPressedBackground` |
| Pierwszy plan (symbol) | `Tag.TagSelectedGlyphPressed` |
| Obramowanie | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna narzędzi
Nie trzeba replikować okien narzędzi, ponieważ są one dostarczane przez środowisko Visual Studio. Jednak możesz zdecydować, że chcesz wykorzystać kolory używane w oknach narzędzi, tak aby interfejs użytkownika zawsze pojawiał się w spójny sposób z tą częścią środowiska programu Visual Studio.

![Okno narzędzi (Redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 — 087_ToolWindowRedline")<br />Okno narzędzi (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... z dowolnego miejsca tworzysz interfejs użytkownika, który ma być zgodny z oknami narzędzi. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

### <a name="tool-window-frame"></a>Ramka okna narzędzi
Okna narzędzi w programie Visual Studio są używane dla wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzi jest otwarte, można je przypisać do dowolnej z czterech boków obszaru dokumentu. Okna narzędzi można również przepływać poza IDE, co umożliwia ich zmianę położenia w dowolnym miejscu na ekranie użytkownika. Przestawne okna zawsze znajdują się na wierzchu IDE. Na koniec okna narzędzi mogą być zadokowane jako okna dokumentu i wyświetlane jako karta w obszarze dokumentu. Okna narzędzi, które zostały zadokowane jako okna dokumentów, są kolorowe w części przy użyciu nazw tokenów okna dokumentu.

![Ramka okna narzędzi (Redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 — 088_ToolWindowFrameRedline")<br />Ramka okna narzędzi (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ...  z dowolnego miejsca tworzysz interfejs użytkownika, który ma być zgodny z oknami narzędzi. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zadokowane okno narzędzi**

![Zadokowane okno narzędzi](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 — 089_ToolWindowDocked")<br />Zadokowane okno narzędzi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.ToolWindowBorder` |

**Przestawne, ukierunkowane okno narzędzi**

![Przestawne, ukierunkowane okno narzędzi](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 — 090_ToolWindowFocused")<br />Przestawne, ukierunkowane okno narzędzi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |

**Przestawne, nieskoncentrowane okno narzędzi**

![Przestawne, nieskoncentrowane okno narzędzi](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 — 091_ToolWindowUnfocused")<br />Przestawne, nieskoncentrowane okno narzędzi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Okna podobne do przybornika
Przybornik jest jednym z najczęściej używanych popularnych okien narzędzi w programie Visual Studio. Zasadniczo jest to formant drzewa z zastosowaniem specjalnego motywu i stylu.

![Okno podobne do przybornika (Redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 — 189_ToolboxRedline")<br />Okno podobne do przybornika (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania okna narzędzi, które chcesz zawsze zachować spójność z przybornikiem powłoki. | ... dla wszystkich elementów, które nie są podobne do interfejsu użytkownika przybornika, lub jeśli nie masz pewności, czy interfejs użytkownika będzie miał problemy, jeśli zmienią się kolory przybornika powłoki. |

**Węzły przybornika: stan domyślny**

![Domyślny węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 — 190_ToolboxParentNode")<br />Domyślny węzeł nadrzędny przybornika

![Domyślny węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 — 191_ToolboxChildNode")<br />Domyślny węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolboxContent`<br />Pozycje |
| Tło | `Environment.ToolWindowBackground`<br />(Poszczególne elementy lub całe okno, jeśli nie ma dostępnych kontrolek) |
| Obramowanie | Brak |
| Pierwszy plan (symbol) | `Environment.ToolboxContent` |
| Pierwszy plan (tekst) | `Environment.ToolboxContent` |

**Węzły podrzędne przybornika: stan aktywowania**

![Węzeł podrzędny przybornika przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 — 192_ToolboxChildNodeHover")<br />Węzeł podrzędny przybornika przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolboxContentMouseOver`<br />(Tylko poszczególne elementy) |
| Obramowanie | Brak |
| Pierwszy plan (tekst) | `Environment.ToolboxContentMouseOver`<br />(Tylko poszczególne elementy) |

**Wybrane węzły przybornika: priorytetowy stan**

![Fokus, wybrany węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 — 193_ToolboxParentNodeFocused")<br />Fokus, wybrany węzeł nadrzędny przybornika

![Fokus, wybrany węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 — 194_ToolboxChildNodeFocused")<br />Fokus, wybrany węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Obramowanie | `TreeView.FocusVisualBorder`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (symbol) | `TreeView.SelectedItemActive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Wybrane węzły przybornika: stan nieskoncentrowany**

![Zaznaczony, nieskoncentrowany węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 — 195_ToolboxParentNodeUnfocused")<br />Zaznaczony, nieskoncentrowany węzeł nadrzędny przybornika

![Wybrany, nieskoncentrowany węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 — 196_ToolboxChildNodeUnfocused")<br />Wybrany, nieskoncentrowany węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Obramowanie | Brak |
| Pierwszy plan (symbol) | `TreeView.SelectedItemInactive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive`<br />Z kategorii [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi
Obramowanie paska tytułu nie jest obramowaniem prawda, jest to gruby wiersz w górnej części paska tytułu. Nie ma nazwy tokenu dla stanu nieskoncentrowanego.

![Pasek tytułu okna narzędzi (Redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 — 092_ToolWindowTitleBarRedline")<br />Pasek tytułu okna narzędzi (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... z dowolnego miejsca tworzysz interfejs użytkownika, który ma być zgodny z oknami narzędzi. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Priorytetowy pasek tytułu**

![Priorytetowy pasek tytułu](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 — 093_TitleBarFocused")<br />Priorytetowy pasek tytułu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.TitleBarActiveGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.TitleBarActiveText` |
| Obramowanie | `Environment.TitleBarActiveBorder`<br />(Ustaw na ten sam kolor jako tło). |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandleActive` |

**Nieskoncentrowany pasek tytułu**

![Pasek tytułu bez fokusu](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 — 094_TitleBarUnfocused")<br />Nieskoncentrowany pasek tytułu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.TitleBarInactiveGradientBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.TitleBarInactiveText` |
| Obramowanie | Nie dotyczy |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Przyciski paska tytułu okna narzędzi
![Przycisk paska tytułu (Redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 — 095_TitleBarButtonRedline")<br />Przycisk paska tytułu (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku przycisków, które są wyświetlane w interfejsie użytkownika, które używają tokenów kolorów z pasków tytułu okna narzędzi. | ... w przypadku przycisków, które są wyświetlane w innych lokalizacjach. |
| | ... w każdej kombinacji tła/pierwszego planu poza określoną. |

**Przyciski paska tytułu z fokusem: stan domyślny**

![Domyślne przyciski paska tytułu z fokusem](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 — 096_TitleBarButtonFocused")<br />Domyślne przyciski paska tytułu z fokusem

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonActiveGlyph` |
| Obramowanie | Nie dotyczy |

**Przyciski paska tytułu nieskoncentrowane: stan domyślny**

![Domyślne, nieskoncentrowane przyciski paska tytułu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 — 097_TitleBarButtonUnfocused")<br />Domyślne, nieskoncentrowane przyciski paska tytułu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonInactiveGlyph` |
| Obramowanie | Nie dotyczy |

**Przyciski paska tytułu z fokusem: stan aktywowania**

![Przyciski paska tytułu z fokusem po aktywowaniu](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 — 098_TitleBarButtonFocusedHover")<br />Przyciski paska tytułu z fokusem po aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverActive` |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverActiveBorder` |

**Przyciski paska tytułu nieskoncentrowane: stan aktywowania**

![Przyciski paska tytułu nieskoncentrowane na aktywowaniu](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 — 099_TitleBarButtonUnfocusedHover")<br />Przyciski paska tytułu nieskoncentrowane na aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverInactive` |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Przyciski paska tytułu z fokusem: stan naciśnięte**

![Przyciski paska tytułu z fokusem podczas naciskania](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 — 100_TitleBarButtonFocusedPressed")<br />Przyciski paska tytułu z fokusem podczas naciskania

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

**Przyciski paska tytułu nieskoncentrowane: stan naciśniętych**

![Przyciski paska tytułu nieskoncentrowane na naciśnięciu](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 — 101_TitleBarButtonUnfocusedPressed")<br />Przyciski paska tytułu nieskoncentrowane na naciśnięciu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (symbol) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna narzędzi
![Karta okna narzędzi (Redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 — 102_ToolWindowTabRedline")<br />Karta okna narzędzi (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... z dowolnego miejsca tworzysz interfejs użytkownika, który ma być zgodny z oknami narzędzi. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zaznaczona, ukierunkowana Karta okna narzędzi**

![Zaznaczona, ukierunkowana Karta okna narzędzi](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 — 103_ToolWindowTabFocused")<br />Zaznaczona, ukierunkowana Karta okna narzędzi

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedActiveText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw na ten sam kolor jako tło). |

**Zaznaczona, Karta okna narzędzia nieskoncentrowanego**

![Zaznaczona, Karta okna narzędzia nieskoncentrowanego](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 — 104_ToolWindowTabUnfocused")<br />Zaznaczona, Karta okna narzędzia nieskoncentrowanego

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw na ten sam kolor jako tło). |

**Karta okna narzędzia tła: stan domyślny**

![Domyślna Karta okna narzędzia tła](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 — 105_ToolWindowBackgroundTab")<br />Domyślna Karta okna narzędzia tła

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Ustawienie gradientu jest ustawione na wartość tego samego koloru w Visual Studio 2013). |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabText` |
| Obramowanie | `Environment.ToolWindowTabBorder` |

**Karta okna narzędzia tła: stan aktywowania**

![Karta okna narzędzia tła na aktywowaniu](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 — 106_ToolWindowBackgroundTabHover")<br />Karta okna narzędzia tła na aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Ustawienie gradientu jest ustawione na wartość tego samego koloru w Visual Studio 2013). |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabMouseOverText` |
| Obramowanie | `Environment.ToolWindowTabMouseOverBorder`<br />(Ustaw na ten sam kolor jako tło). |

### <a name="auto-hide-tabs"></a>Autoukrywanie kart

![Autoukrywanie kart (Redline)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 — 107_AutoHideRedline") Autoukrywanie kart (Redline)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdziekolwiek tworzysz interfejs użytkownika, który chcesz dopasować do kart okna z autoukrywaniem. | ... dla każdego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Autoukrywanie kart: stan domyślny**

![Domyślna karta Autoukrywanie](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 — 108_AutoHideTab")<br />Domyślna karta Autoukrywanie

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.AutoHideTabBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.AutoHideTabText` |
| Obramowanie | `Environment.AutoHideTabBorder` |

**Autoukrywanie kart: stan aktywowany**

![Autoukrywanie karty przy aktywowaniu](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 — 109_AutoHideTabHover")<br />Autoukrywanie karty przy aktywowaniu

| Element | Nazwa tokenu: Category. Color |
| --- | --- |
| Tło | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Zatrzymanie gradientu dla tego tokenu nie jest używane w interfejsie użytkownika). |
| Pierwszy plan (tekst) | `Environment.AutoHideTabMouseOverText` |
| Obramowanie | `Environment.AutoHideTabMouseOverBorder` |
