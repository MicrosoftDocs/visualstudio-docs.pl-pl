---
title: Udostępnione kolory programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699932"
---
# <a name="shared-colors-for-visual-studio"></a>Udostępnione kolory programu Visual Studio
Podczas projektowania interfejsu użytkownika, który używa wspólnych elementów powłoki programu Visual Studio lub chcesz, aby element interfejsu był zgodny z podobnymi funkcjami, użyj istniejących nazw tokenów w plikach definicji pakietu, aby wybrać i przypisać kolory. Gwarantuje to, że interfejs użytkownika pozostaje zgodny z ogólnym środowisku programu Visual Studio i że aktualizuje się automatycznie po dodaniu lub zaktualizowaniu motywów.

W tym artykule opisano typowe elementy interfejsu użytkownika i nazwy tokenów, których używają, do których można się odwoływać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje dotyczące uzyskiwania dostępu do tych tokenów kolorów, zobacz [Usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Upewnij się, że nazwy tokenów są używane poprawnie:

- **Użyj nazw tokenów opartych na funkcji, a nie na samym kolorze.** Typowe kolory udostępnione są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko do użycia dla tych samych lub podobnych funkcji. Na przykład nie należy ponownie używać koloru wciśniętym polu kombi dla animacji postępu wirowania tylko dlatego, że podoba Ci się kolor. Funkcje pola kombi i animacji są różne, a jeśli kolor skojarzony z polem kombi ulegnie zmianie, może nie być już odpowiedni kolor dla elementu animacji. Konsekwentne korzystanie z kolorów pomaga zorientować użytkowników i zapobiec pomyłce.

- **Użyj kolorów tła i tekstu w odpowiedniej kombinacji.** Kolory tła, które mają być używane z tekstem, będą miały skojarzony kolor tekstu. Nie używaj kolorów tekstowych innych niż określone dla tego tła. Jeśli nie ma skojarzonego koloru tekstu, nie używaj tego koloru tła dla żadnej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą spowodować nieczytelny interfejs.

- **Użyj kolorów formantów, które są odpowiednie dla ich lokalizacji.** W niektórych stanach niektóre formanty programu Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego zbierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów, które są odpowiednie dla lokalizacji, w której umieszczasz formant.

> [!IMPORTANT]
> Nie używaj tokenów znalezionych w kategoriach "Strona początkowa" lub "Cydr".

## <a name="common-shared-controls"></a>Typowe kontrolki współużytkowane

Korzystając ze standardowego paska poleceń programu Visual Studio w funkcji, będziesz mieć dostęp do stylizowanych formantów powłoki. Nie należy ponownie szablon tych typowych formantów. Jednak jeśli trzeba utworzyć pasek poleceń niestandardowe, może być konieczne tworzenie formantów niestandardowych, jak również. W takim przypadku należy pamiętać, aby użyć poprawne nazwy tokenów dla każdego z następujących formantów, tak aby interfejs użytkownika jest zgodny z resztą programu Visual Studio.

### <a name="button-controls"></a>formanty przycisków

![Czerwona linia sterowania przyciskami](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla przycisków w dokumencie dobrze, że chcesz zintegrować z motywami programu Visual Studio (Jasny, Ciemny, Niebieski lub system wysoki kontrast motywu). | ... dla przycisków, które będą wyświetlane na niestandardowym tle, który nie jest częścią motywu programu Visual Studio. |

**Przycisk: stan standardowy**

![Przycisk Standardowy](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Przycisk Standardowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.Button` |
| Obramowanie przycisków | `CommonControls.ButtonBorder` |

**Przycisk: stan domyślny**

![Przycisk Domyślny](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Przycisk Domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonDefault` |
| Obramowanie przycisków | `CommonControls.ButtonBorderDefault` |

**Przycisk: stan wyłączenia**

![Przycisk Wyłączono](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Wyłączone")<br />Przycisk Wyłączono

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonDisabled` |
| Obramowanie przycisków | `CommonControls.ButtonBorderDisabled` |

**Przycisk: stan aktywowania**

![Przycisk po najechaniu kursorem](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Przycisk po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonHover` |
| Obramowanie przycisków | `CommonControls.ButtonBorderHover` |

**Przycisk: stan naciśnięcia**

![Przycisk Wciśnięty](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Wciśnięty")<br />Przycisk Wciśnięty

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonPressed` |
| Obramowanie przycisków | `CommonControls.ButtonBorderPressed` |

**Przycisk: stan skupienia**

![Przycisk Skupiona](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Przycisk Skupiona

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonFocused` |
| Obramowanie przycisków | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrolki pola wyboru
![Pole wyboru (czerwona linia)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Pole wyboru (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla formantów pola wyboru zawartych w dokumencie dobrze. | ... dla dowolnego interfejsu użytkownika, który nie jest formantem pola wyboru. |

**Pole wyboru: stan domyślny**

![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Domyślne pole wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackground` |
| Obramowanie | `CommonControls.CheckBoxBorder` |
| Tekst | `CommonControls.CheckBoxText` |
| Glifów | `CommonControls.CheckBoxGlyph` |

**Pole wyboru: stan wyłączona**

![Wyłączone pole wyboru](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Wyłączone pole wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.CheckBoxBorderDisabled` |
| Tekst | `CommonControls.CheckBoxTextDisabled` |
| Glifów | `CommonControls.CheckBoxGlyphDisabled` |

**Pole wyboru: stan aktywowania wskaźnika**

 ![Pole wyboru po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Pole wyboru po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundHover` |
| Obramowanie | `CommonControls.CheckBoxBorderHover` |
| Tekst | `CommonControls.CheckBoxTextHover` |
| Glifów | `CommonControls.CheckBoxGlyphHover` |

**Pole wyboru: stan naciśnięcia**

![Wciśnięty pole wyboru](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Wciśnięty pole wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Obramowanie | `CommonControls.CheckBoxBorderPressed` |
| Tekst | `CommonControls.CheckBoxTextPressed` |
| Glifów | `CommonControls.CheckBoxGlyphPressed` |

**Pole wyboru: stan skupiona**

![Pole wyboru Skupione](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Pole wyboru Skupione

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundFocused` |
| Obramowanie | `CommonControls.CheckBoxBorderFocused` |
| Tekst | `CommonControls.CheckBoxTextFocused` |
| Glifów | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listy rozwijane i skrzynki kombi
![Pole listy rozwijanej/kombi (czerwona linia)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Pole listy rozwijanej/kombi (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla rozwijanych i pól kombi w dokumencie dobrze. | ... dla dowolnego interfejsu użytkownika, który nie jest polem rozwijanym ani kombi. |
| | ... dla listy [rozwijanej paska](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) poleceń lub [pól kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listy rozwijane i pola kombi: stan domyślny**

![Domyślne pole listy rozwijanej/kombi](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Domyślne pole listy rozwijanej/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackground` |
| Obramowanie | `CommonControls.ComboBoxBorder` |
| Tekst | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Glifów | `CommonControls.ComboBoxGlyph` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackground` |

**Listy rozwijane i pola kombi: stan wyłączony**

![Wyłączone pole listy rozwijanej/kombi](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Wyłączone pole listy rozwijanej/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.ComboBoxBorderDisabled` |
| Tekst | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifów | `CommonControls.ComboBoxGlyphDisabled` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listy rozwijane i pola kombi: stan aktywowania**

![Pole listy rozwijanej/kombi po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Pole listy rozwijanej/kombi po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundHover` |
| Obramowanie | `CommonControls.ComboBoxBorderHover` |
| Tekst | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Glifów | `CommonControls.ComboBoxGlyphHover` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listy rozwijane i skrzynki kombi: stan wciśnięty**

![Wciśnięte pole rozwijane/kombi](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Wciśnięte pole rozwijane/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundPressed` |
| Obramowanie | `CommonControls.ComboBoxBorderPressed` |
| Tekst | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Glifów | `CommonControls.ComboBoxGlyphPressed` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Lista rozwijana i pola kombi wyświetlają pozycję: stan naciśnięcia**

 ![Widok elementu listy rozwijanej/kombi](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Widok elementu listy rozwijanej/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Tekst elementu | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Cień tła | `CommonControls.ComboBoxListBackgroundShadow` |

**Listy rozwijane i pola kombi: stan skoncentrowany**

![Pole rozwijane/kombi z ostrością](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Pole rozwijane/kombi z ostrością

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxBorderFocused` |
| Tekst | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Glifów | `CommonControls.ComboBoxGlyphFocused` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listy rozwijane i pola kombi: wybór wprowadzania tekstu**

![Zaznaczenie tekstu pola rozwijane/pole kombi](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Zaznaczenie tekstu pola rozwijane/pole kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Wyróżnij | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelaryczne (siatki)
Kontrolki danych tabelaryczne, znane również jako formanty siatki, są typowymi formantami programu Visual Studio, które mogą być używane do prezentowania dużych ilości danych w wielu kolumnach. Standardowe kontrole danych tabelaryczne można znaleźć w wielu miejscach w programie Visual Studio: okno narzędzia lista błędów, raporty IntelliTrace i widok sterty pamięci, między innymi. Zawsze używaj standardowych kontroli danych tabelaryczne. W niektórych rzadkich przypadkach może nie mieć dostępu do standardowych kontroli danych tabelaryczne. W takich sytuacjach należy użyć następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelaryczne w programie Visual Studio.

![Tabelaryczne dane/kontrola siatki (czerwona linia)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabelaryczne dane/kontrola siatki (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla kontrolek tabelaryczne lub siatki. | ... dla dowolnego interfejsu użytkownika, który nie jest formantem tabelarycznym ani siatki. |

#### <a name="column-headers"></a>Nagłówki kolumn
Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego glifów zwykle używanych, gdy siatka jest sortowana według tej kolumny.

**Nagłówek kolumny: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.Default` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (Glif) | `Header.Glyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan aktywowania wskaźnika**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.MouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (Glif) | `Header.MouseOverGlyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan naciśnięcia**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Pierwszy plan (tekst) | `CommonControls.CheckBoxBorderPressed` |
| Pierwszy plan (Glif) | `CommonControls.CheckBoxTextPressed` |
| Obramowanie | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementy widoku listy
 Elementy widoku listy składają się z tła i zawartości. Zawartość może być tekstem, ikoną lub obiema.

**Elementy widoku listy: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Przezroczyste |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Elementy widoku listy: stan aktywny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActiveText` |
| Obramowanie | Brak |

**Elementy widoku listy: stan nieaktywny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactiveText` |
| Obramowanie | Brak |

### <a name="ui-text"></a>Tekst interfejsu użytkownika

#### <a name="instructional-text"></a>Tekst instruktażowy
Tekst instruktażowy daje widoczne główne wyjaśnienie, co należy zrobić w oknie dialogowym lub na stronie dokumentu.

![Domyślny tekst instruktażowy](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Domyślny tekst instruktażowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Pomocniczy tekst instruktażowy
Na stronach dokumentu z dużą ilością tekstu i formantów niektóre teksty instruktażowe używają innej wartości koloru. Pomaga to przekazać, które informacje są najważniejsze i zmniejszyć ogólną gęstość elementów interfejsu użytkownika. (Zobacz też poniższą sekcję dotyczącą tekstu podpowiedzi).

![Pomocniczy tekst instruktażowy](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Pomocniczy tekst instruktażowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Tekst podpowiedzi
Tekst wskazówki pojawia się w pustym formancie, poniżej formantu lub na pustej powierzchni dokumentu, aby pokazać użytkownikowi, co należy zrobić dalej. Można użyć tekstu podpowiedzi z tłem Okna lub Sterowanie.

**Domyślny tekst wskazówki**

![Domyślny tekst wskazówki](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Domyślny tekst wskazówki

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

**Wymagany tekst wskazówki**

![Wymagany tekst wskazówki](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Wymagany tekst wskazówki

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlRequiredHintText` |
| Tło | `Environment.ControlRequiredBackground` |

**Tekst formantu pola wyszukiwania**

> Zobacz [Pola wyszukiwania](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) dla innych tokenów kolorów związanych z search kontroli.

![Tekst formantu pola wyszukiwania](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Tekst formantu pola wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Hiperłącze jest jednym formancie, który nie ma pary pierwszego planu/tła. We wszystkich przypadkach należy użyć koloru hiperłącza pierwszego planu, który będzie wyświetlany poprawnie na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu kolorów dla formantu hiperłącza, zobaczysz domyślny kolor systemu dla "wciśnięty", który będzie migać na czerwono. To sygnał, że formant nie używa tokenu kolor poprawne środowisko.

![Hiperłącze (czerwona linia)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hiperłącze (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... gdy trzeba utworzyć niestandardowe hiperłącze. | ... dla wszystkiego, co nie jest hiperłączem. |

**Hiperłącze: stan domyślny**

![Domyślne hiperłącze](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Domyślne hiperłącze

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlink` |

**Hiperłącze: stan aktywowania**

![Hiperłącze po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hiperłącze po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkHover` |

**Hiperłącze: stan naciśnięcia**

![Wciśnięty hiperłącze](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Wciśnięty hiperłącze

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkPressed` |

**Hiperłącze: stan wyłączona**

![Wyłączone hiperłącze](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Wyłączone hiperłącze

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Paski informacyjne
Paski informacyjne są używane w celu zapewnienia więcej informacji o danym kontekście i zawsze pojawiają się w górnej części okna dokumentu lub okna narzędzia.

![Pasek informacyjny (czerwona linia)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Pasek informacyjny (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych pasków informacyjnych. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego. |

**Pasek informacyjny: stan domyślny**

![Domyślny pasek informacyjny](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Domyślny pasek informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.InfoBarBackground` |
| Pierwszy plan (tekst) | `InfoBar.InfoBar` |
| Obramowanie | `InfoBar.InfoBarBorder` |

**Przycisk Zamknij&times;pasek informacyjny : stan domyślny**

![Domyślny przycisk&times;Zamknij pasek informacyjny ( )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Domyślny przycisk&times;Zamknij pasek informacyjny ( )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButton` |
| Obramowanie | `InfoBar.CloseButtonBorder` |
| Glifów | `InfoBar.CloseButtonGlyph` |

**Przycisk Zamknij&times;pasek informacyjny: stan aktywowania**

![Przycisk Zamknij&times;pasek informacyjny ( ) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Przycisk Zamknij&times;pasek informacyjny ( ) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonHover` |
| Obramowanie | `InfoBar.CloseButtonHoverBorder` |
| Glifów | `InfoBar.CloseButtonHoverGlyph` |

**Przycisk Zamknij&times;pasek informacyjny : stan naciśnięcia**

![Wciśnięty przycisk&times;zamknij pasek informacyjny ( )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Wciśnięty przycisk&times;zamknij pasek informacyjny ( )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonDown` |
| Obramowanie | `InfoBar.CloseButtonDownBorder` |
| Glifów | `InfoBar.CloseButtonDownGlyph` |

**Przycisk hiperłącza paska informacyjnego: stan domyślny**

![Domyślny przycisk hiperłącza paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny przycisk hiperłącza paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Przycisk hiperłącza paska informacyjnego: stan aktywowania**

![Przycisk hiperłącza paska informacyjnego po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Przycisk hiperłącza paska informacyjnego po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Przycisk hiperłącza paska informacyjnego: stan naciśnięcia**

![Wciśnięty przycisk hiperłącza paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Wciśnięty przycisk hiperłącza paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreśleniem) |

**Hiperłącze wbudowane paska informacyjnego (w zdaniu): stan domyślny**

![Domyślny wbudowany przycisk hiperłącza do paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny wbudowany przycisk hiperłącza do paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Hiperłącze wbudowane paska informacyjnego (w zdaniu): stan myszy**

![Przycisk hiperłącza wbudowanego paska informacyjnego po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Przycisk hiperłącza wbudowanego paska informacyjnego po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Hiperłącze wbudowane paska informacyjnego (w zdaniu): stan naciśnięcia**

![Naciśnięty przycisk hiperłącza wbudowanego paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Naciśnięty przycisk hiperłącza wbudowanego paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreśleniem) |

**Przycisk paska informacyjnego: stan domyślny**

![Domyślny przycisk paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Domyślny przycisk paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.Button` |
| Pierwszy plan (tekst) | `InfoBar.Button` |
| Obramowanie | `InfoBar.ButtonBorder` |

**Przycisk paska informacyjnego: stan aktywowania**

![Przycisk paska informacyjnego po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Przycisk paska informacyjnego po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseOver` |
| Pierwszy plan (tekst) | `InfoBar.ButtonMouseOver` |
| Obramowanie | `InfoBar.ButtonMouseOverBorder` |

**Przycisk paska informacyjnego: stan naciśnięcia**

![Naciśnięty przycisk paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Naciśnięty przycisk paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseDown` |
| Pierwszy plan (tekst) | `InfoBar.ButtonMouseDown` |
| Obramowanie | `InfoBar.ButtonMouseDownBorder` |

**Przycisk paska informacyjnego: stan wyłączenia**

![Wyłączony przycisk paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Wyłączony przycisk paska informacyjnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonDisabled` |
| Pierwszy plan (tekst) | `InfoBar.ButtonDisabled` |
| Obramowanie | `InfoBar.ButtonDisabledBorder` |

**Przycisk paska informacyjnego: stan skupienia**

![Przycisk na pasku informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Przycisk na pasku informacyjnym

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonFocus` |
| Pierwszy plan (tekst) | `InfoBar.ButtonFocus` |
| Obramowanie | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania są stylizowane przez środowisko programu Visual Studio i nie muszą być tematyce. Jednak można zdecydować, że chcesz wykorzystać kolory używane w paski przewijania, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.

![Pasek przewijania (czerwona linia)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Pasek przewijania (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia interfejsu użytkownika, który chcesz dopasować paski przewijania programu Visual Studio. | ... dla wszystkiego, czego nie chcesz zawsze dopasować interfejsu użytkownika paska przewijania. |

**Pasek przewijania: stan domyślny**

![Domyślny pasek przewijania](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Domyślny pasek przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbBackground` |

**Pasek przewijania: stan aktywowania**

![Pasek przewijania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Pasek przewijania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbMouseOverBackground` |

*Pasek przewijania: stan naciśnięcia**

![Wciśnięty pasek przewijania](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Wciśnięty pasek przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (kciuk) | `Environment.ScrollBarThumbPressedBackground` |

**Strzałka paska przewijania: stan domyślny**

![Domyślna strzałka paska przewijania](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Domyślna strzałka paska przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (Glif) | `Environment.ScrollBarArrowGlyph` |

**Strzałka paska przewijania: stan aktywowania**

![Strzałka paska przewijania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Strzałka paska przewijania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowMouseOverBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (Glif) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Strzałka paska przewijania: stan naciśnięcia**

![Strzałka naciśnięty pasek przewijania](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Strzałka naciśnięty pasek przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowPressedBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (Glif) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Pola wyszukiwania
Jeśli to możliwe, należy użyć wspólnego formantu wyszukiwania dostarczonego przez środowisko programu Visual Studio. Kolory pól wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors.pkgdef,** który zawiera nazwy tokenów dla pola wejściowego, przycisku akcji, przycisku rozwijanego i menu rozwijanego.

Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wzajemnie się wykluczają:

- "Koncentruje się" lub "nieskoncentrowane" odnosi się do tego, czy kursor znajduje się w polu tekstowym.

- "Aktywny" lub "nieaktywny" odnosi się do tego, czy użytkownik ma wprowadzić zapytanie wyszukiwania w polu tekstowym.

- "Hover" oznacza, że użytkownik ma myszy nad polem wyszukiwania za pomocą myszy (ten stan zastępuje wszystkie inne stany).

- "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.

![Pole wyszukiwania (czerwona linia)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Pole wyszukiwania (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas projektowania niestandardowego pola wyszukiwania. | ... dla wszystkiego, co nie jest polem wyszukiwania. |
| | ... dla wszystkiego, co nie chcesz zawsze pasować do interfejsu użytkownika pola wyszukiwania. |

**Pole wprowadzania wyszukiwania skoncentrowane**

![Pole wprowadzania wyszukiwania skoncentrowane](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Pole wprowadzania wyszukiwania skoncentrowane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedBackground` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Nieskoncentrowane, aktywne pole wprowadzania wyszukiwania**

![Wyszukiwanie pola wejściowego nieskoncentrowane](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Nieskoncentrowane, aktywne pole wprowadzania wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.SearchActiveBackground` |
| Pierwszy plan (tekst) | `SearchControl.SearchActiveBackground` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Nieskoncentrowane, nieaktywne pole wprowadzania wyszukiwania**

![Nieskoncentrowane, nieaktywne pole wprowadzania wyszukiwania](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nieskoncentrowane, nieaktywne pole wprowadzania wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Unfocused` |
| Pierwszy plan (tekst) | `SearchControl.Unfocused` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Wyróżnione pole wprowadzania wyszukiwania (tylko tekst)**

![Wyróżnione pole wprowadzania wyszukiwania](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Wyróżnione pole wprowadzania wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Selection` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | Brak |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Wyłączone pole wprowadzania wyszukiwania**

![Wyłączone pole wprowadzania wyszukiwania](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Wyłączone pole wprowadzania wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Disabled` |
| Pierwszy plan (tekst) | `SearchControl.Disabled` |
| Obramowanie | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Przycisk akcji wyszukiwania skupiona**

![Przycisk akcji wyszukiwania koncentruje](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Przycisk akcji wyszukiwania skupiona

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (glif wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszy plan (stop glif) | `SearchControl.StopGlyph` |
| Pierwszy plan (przezroczysty glif) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk akcji wyszukiwanie nieskoncentrowanego**

![Przycisk akcji wyszukiwanie nieskoncentrowanego](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Przycisk akcji wyszukiwanie nieskoncentrowanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszy plan (stop glif) | `SearchControl.StopGlyph` |
| Pierwszy plan (przezroczysty glif) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Naciśnięty przycisk akcji wyszukiwania**

![Naciśnięty przycisk akcji wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Naciśnięty przycisk akcji wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.ActionButtonMouseDown` |
| Pierwszy plan (Glif) | `SearchControl.ActionButtonMouseDownGlyph` |
| Obramowanie | `SearchControl.ActionButtonMouseDownBorder` |

**Przycisk Akcji wyszukiwania wyłączone**

![Przycisk akcji wyszukiwania wyłączony](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Przycisk Akcji wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (Glif) | `SearchControl.ActionButtonDisabledGlyph` |
| Obramowanie | Brak |

**Przycisk listy rozwijanej wyszukiwanie skoncentrowane**

![Przycisk listy rozwijanej wyszukiwanie skoncentrowane](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Przycisk listy rozwijanej wyszukiwanie skoncentrowane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedDropDownButton` |
| Pierwszy plan (Glif) | `SearchControl.FocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.FocusedDropDownButtonBorder` |

**Przycisk listy rozwijanej wyszukiwanie bez skupić**

![Przycisk listy rozwijanej wyszukiwanie bez skupić](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Przycisk listy rozwijanej wyszukiwanie bez skupić

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.UnfocusedDropDownButton` |
| Pierwszy plan (Glif) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.UnfocusedDropDownButtonBorder` |

**Naciśnięty przycisk listy rozwijanej wyszukiwania**

![Naciśnięty przycisk listy rozwijanej wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Naciśnięty przycisk listy rozwijanej wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.MouseDownDropDownButton` |
| Pierwszy plan (Glif) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Obramowanie | `SearchControl.MouseDownDropDownButtonBorder` |

**Wyłączony przycisk listy rozwijanej wyszukiwania**

![Wyłączony przycisk listy rozwijanej wyszukiwania](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (Glif) | `SearchControl.DisabledDownButtonGlyph` |
| Obramowanie | Brak |

#### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania
Menu rozwijane pola wyszukiwania ma potencjał, aby być nieco bardziej złożone niż inne menu rozwijane w programie Visual Studio. Sekcje "sugerowane wyszukiwania" i "opcje wyszukiwania" mogą pojawić się samodzielnie lub razem w menu, a każda z nich jest kolorowana oddzielnie. Linia oddziela również te dwie sekcje, gdy pojawiają się razem, a obramowanie otacza całe menu rozwijane.

![Lista rozwijana wyszukiwania (czerwona linia)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista rozwijana wyszukiwania (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowej listy rozwijanej wyszukiwania. | ... listy rozwijanej, które pojawiają się w innych kontekstach. |
| ... poprawne nazwy tokenów dla składników listy poprawne. | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Szukaj elementów listy rozwijanej**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Obramowanie | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Sugerowane wyszukiwania: stan domyślny**

![Domyślne sugerowane wyszukiwania](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Domyślne sugerowane wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `SearchControl.PopupItemText` |

**Sugerowane wyszukiwania: stan aktywowania**

![Sugerowane wyszukiwania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Sugerowane wyszukiwania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `SearchControl.PopupMouseOverItemText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan domyślny**

![Pole wyboru Wyszukaj](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Domyślne opcje wyszukiwania (pole wyboru)

![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Domyślne opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxText` |
| Pierwszy plan (tekst łącza) | `SearchControl.PopupButtonText` |
| Tło nagłówka | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst nagłówka) | `SearchControl.PopupSectionHeaderText` |

**Opcje wyszukiwania: stan aktywowania**

![Opcje wyszukiwania (pole wyboru) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opcje wyszukiwania (pole wyboru) po najechaniu kursorem

![Opcje wyszukiwania (link) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opcje wyszukiwania (link) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Pierwszy plan (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan naciśnięcia**

![Wciśnięty opcje wyszukiwania (pole wyboru)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Wciśnięty opcje wyszukiwania (pole wyboru)

![Wytłoczone opcje wyszukiwania (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Wytłoczone opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło pola wyboru | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Tło łącza | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Widoki drzewa
Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwerów i Widok klasy, `TreeView` implementuje hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w kategorii. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy, które mają zagnieżdżone elementy podrzędne mają również glify, które wskazują, czy element jest rozwinięty lub zwinięty.

![Widok drzewa (czerwona linia)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Widok drzewa (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w dowolnym miejscu, w dowolnym miejscu, aby zaimplementować hierarchiczny widok organizacyjny. | ... dla wszystkiego, co nie jest podobne do widoku drzewa. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Element widoku drzewa: stan domyślny**

![Domyślny element widoku drzewa](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Domyślny element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (Glif) | `TreeView.Glyph` |
| Obramowanie | Brak |

**Element widoku drzewa: stan myszy**

![Element widoku drzewa po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Element widoku drzewa po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (Glif) | `TreeView.GlyphMouseOver` |
| Obramowanie | Brak |

**Element widoku drzewa: przeciągnij nad stan**

![Element widoku drzewa po przeciągnięciu](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Element widoku drzewa po przeciągnięciu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.DragOverItem` |
| Pierwszy plan (tekst) | `TreeView.DragOverItem` |
| Pierwszy plan (Glif) | `TreeView.DragOverItemGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: wybrany, stan skupienia**

![Zaznaczony i ukoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Zaznaczony i ukoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (Glif) | `TreeView.SelectedItemActiveGlyph` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: zaznaczony, nieskoncentrowany stan**

![Zaznaczony i nieskoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Zaznaczony i nieskoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (Glif) | `TreeView.SelectedItemInactiveGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: stan myszy, zaznaczony i skupiony**

![Zaznaczony i unieszczony element widoku drzewa po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Zaznaczony i unieszczony element widoku drzewa po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (Glif) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan myszy, zaznaczony i nieskoncentrowany**

![Zaznaczony i nieskoncentrowany element widoku drzewa po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Zaznaczony i nieskoncentrowany element widoku drzewa po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (Glif) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | Brak |

## <a name="shell-appearance"></a>Wygląd powłoki

### <a name="background"></a>Tło
Tło środowiska składa się z dwóch warstw. Dolna warstwa jest jednolity kolor, który obejmuje cały IDE. Górna warstwa mieści się pod półką poleceń i między oknem narzędzia automatycznie ukrywaj kanały po lewej i prawej krawędzi IDE. Górne i dolne warstwy tła są ustawione na ten sam kolor w motywach Jasne i Ciemne.

![Tło powłoki programu Visual Studio (czerwona linia)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Tło powłoki programu Visual Studio (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla miejsc, w których chcesz dopasować tło środowiska programu Visual Studio. | ... jako wypełnienie dla miejsc, które nie są powierzchniami tła. |
| | ... jako tło, aby umieścić elementy pierwszego planu. |

**Wygląd skorupy warstwy dolnej**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.EnvironmentBackground` |

**Wygląd skorupy warstwy górnej**

> Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Półka poleceń
Dwa zestawy nazw tokenów są używane dla tła półki poleceń: jeden zestaw, dla którego znajduje się pasek menu i jeden dla miejsca, w którym znajdują się paski poleceń. Indywidualna grupa paska poleceń ma własne wartości kolorów tła, które są omówione bardziej szczegółowo w sekcji "pasek poleceń". Pasek menu i tekst paska poleceń są omawiane odpowiednio w sekcjach menu i paska poleceń.

![Półka poleceń programu Visual Studio (czerwona linia)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Półka poleceń programu Visual Studio (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla obszarów, w których umieszczasz menu lub paski narzędzi. | ... dla obszarów, które nie są podobne do półki poleceń. |
|... z prawidłową kombinacją nazw tokenów tła/pierwszego planu. | |

**Pasek menu półki poleceń**

> Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Pasek poleceń półki poleceń**

> Gradient zatrzymuje ustawioną na tę samą wartość koloru w motywach jasnych i ciemnych programu Visual Studio 2013.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest Designer
Projektant manifestu został zaprojektowany jako sposób na ułatwienie edytowania pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Chociaż nie ma żadnej udostępnionej struktury dostępnej do użycia, może być odpowiedni dla ciebie, aby dopasować układ projektu i kolory kart orientacji/nawigacji i ogólnej struktury. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [Układ programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Projektant manifestów (czerwona linia)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Projektant manifestów (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla projektantów, które są podobne do Projektanta manifestu. | ... jeśli masz więcej niż sześć kart. |
| ... zamiast używania wspólnych kontrolek kart w górnej części edytora w dokumencie. | ... dla dowolnego interfejsu użytkownika, który nie jest skonstruowany jak Projektant manifestu. |

**Wybrana karta Projektant manifestu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.TabActive` |
| Obramowanie | Brak |

**Wybrane okienko opisu Projektant manifestu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.DescriptionPane` |

**Wybrany projektant manifestu strona zawartości: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Background` |
| Tekst pomocnika okna dialogowego | `ManifestDesigner.WatermarkText`<br />(Ta nazwa tokenu nie pasuje do jego funkcji).) |

**Karta Projektant manifestu: stan niezaznaczony**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Inactive` |

**Karta Projektant manifestu: stan aktywowania**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Struktury poleceń

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menu
Menu może występować w kilku miejscach w programie Visual Studio: pasek menu głównego, osadzone w oknach dokumentu lub narzędzia lub po kliknięciu prawym przyciskiem myszy w różnych lokalizacjach w całej IDE. Implementacje menu skojarzone z innymi elementami interfejsu użytkownika są omówione w sekcji dla odpowiedniego elementu. Należy zawsze używać implementacji menu standardowego dostarczonych przez środowisko programu Visual Studio. Jednak w niektórych rzadkich przypadkach może nie mieć dostępu do standardowych menu programu Visual Studio. W takich sytuacjach należy użyć następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w programie Visual Studio.

![Menu programu Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu programu Visual Studio (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... gdy trzeba utworzyć menu niestandardowe.| ... sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu, jak określono. |
| ... gdy masz nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.| |

#### <a name="menu-titles"></a>Tytuły menu
Tytuły menu składają się z tła, obramowania i tekstu tytułowego, a także opcjonalnego glifu, zwykle gdy menu znajduje się na pasku poleceń.

![Tytuł menu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Tytuł menu (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... przy każdym tworzeniu niestandardowego tytułu menu. | ... na wszystko, czego nie chcesz zawsze pasować do tytułu menu. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Tytuł menu: stan domyślny**

![Domyślny tytuł menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Domyślny tytuł menu

![Domyślny tytuł menu z glifem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Domyślny tytuł menu z glifem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (glif) | `Environment.CommandBarMenuGlyph` |
| Obramowanie | Brak |

**Tytuł menu: stan aktywowania**

![Tytuł menu po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Tytuł menu po najechaniu kursorem myszy

![Tytuł menu z glifem po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Tytuł menu z glifem po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (glif) | `Environment.CommandBarMenuMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |

**Tytuł menu: stan naciśnięcia**

![Wciśnięty tytuł menu](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Wciśnięty tytuł menu

![Wciśnięty tytuł menu z glifem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Wciśnięty tytuł menu z glifem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (Glif) | `Environment.CommandBarMenuMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder`<br />(Tylko po lewej, górnej i prawej stronie). |

**Tytuł menu: stan wyłączona**

![Wyłączony tytuł menu z glifem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Wyłączony tytuł menu z glifem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszy plan (Glif) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

#### <a name="menu-items"></a>Elementy menu
Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub glifu podmenu. Jego tło i kolor tekstu zmieniają się po najechaniu kursorem. Ten token kolorów jest parą tła/pierwszego planu.

![Elementy menu redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Używać... | Nie używaj ... |
|---|---|
| ... dla każdej listy rozwijanej uruchomionej z paska menu lub paska poleceń. | ... dla każdej listy rozwijanej w innym kontekście. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Elementy menu: stan domyślny**

![Domyślne elementy menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Domyślne elementy menu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (glif podmenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder` |
| Tło kanału ikony | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Elementy menu: sprawdzone i wybrane stany**

![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Zaznaczony element menu

![Wybrane menu](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Zaznaczony element menu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Sprawdź znacznik | `Environment.CommandBarCheckBox` |
| Sprawdzanie tła znacznika | `Environment.CommandBarSelectedIcon` |
| Tło ikony | `Environment.CommandBarSelected` |
| Obramowanie ikony | `Environment.CommandBarSelectedBorder` |

**Elementy menu: stan aktywowania pozycji**

![Najechać menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Pozycja menu po najechaniu kursorem

![Menu poleć wskaźnik myszy](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Zaznaczony element menu po najechaniu kursorem

![Wybrano opcję Najechajnie](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Zaznaczony element menu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuItemMouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarMenuItemMouseOverText` |
| Pierwszy plan (glif podmenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Sprawdź znacznik | `Environment.CommandBarCheckBoxMouseOver` |
| Sprawdzanie tła znacznika | `Environment.CommandBarHoverOverSelectedIcon` |
| Tło ikony | `Environment.CommandBarHoverOverSelected` |
| Obramowanie ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementy menu: stan wyłączona**

![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Wyłączony element menu

![Menu wyłączone zaznaczone](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Wyłączony element menu ze znacznikiem wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszy plan (glif podmenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Sprawdź znacznik | `Environment.CommandBarCheckBoxDisabled` |
| Sprawdzanie tła znacznika | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Paski poleceń
Pasek poleceń może pojawić się w wielu miejscach w środowisku IDE programu Visual Studio, w szczególności na półce poleceń i osadzony w oknach narzędzi lub dokumentów.

Ogólnie rzecz biorąc należy zawsze używać implementacji standardowego paska poleceń dostarczonych przez środowisko programu Visual Studio. Za pomocą standardowego mechanizmu zapewnia, że wszystkie szczegóły wizualne będą wyświetlane poprawnie i że elementy interaktywne będą zachowywać się zgodnie z innymi formantami paska poleceń programu Visual Studio. Jeśli jednak konieczne jest zbudowanie własnego paska poleceń, upewnij się, że styl poprawnie używasz następujących nazw tokenów.

![Czerwona linia paska poleceń](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Pasek poleceń (czerwona linia)

![Czerwony przycisk przepełnienia](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Przycisk przepełnienie (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenów. |

#### <a name="command-bar-groups"></a>Grupy paska poleceń
Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przycisków podziału, menu rozwijanych, pól kombi lub menu. Kolory dla tych formantów są regulowane przez oddzielne nazwy tokenów i są omawiane indywidualnie w innym miejscu w tym przewodniku. Linia separatora służy do dzielenia grupy pasków poleceń na powiązane podgrupy.

![Czerwona linia grupy paska polecenia](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupa paska poleceń (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej implementacji paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenów. |

**Grupa paska poleceń: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Obramowanie | `Environment.CommandBarToolBarBorder` |
| Przeciągnij uchwyt | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony poleceń
![Czerwona linia ikony polecenia](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Ikona polecenia (czerwona linia)

![Ikona polecenia z czerwoną kartką tekstu](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Ikona polecenia z tekstem (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla wszystkich przycisków, które zostaną umieszczone na pasku poleceń. | ... formanty, które mają własne nazwy tokenów. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Ikona polecenia: stan domyślny**

![Domyślna ikona polecenia](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Domyślna ikona polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Nie dotyczy |

**Ikona polecenia: stan domyślny, zaznaczona**

![Domyślna, zaznaczona ikona polecenia](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Domyślna, zaznaczona ikona polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextSelected` |
| Obramowanie | `Environment.CommandBarSelectedBorder` |

**Ikona polecenia: stan myszy lub fokusu**

![Ikona polecenia po najechaniu kursorem lub fokusie](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Ikona polecenia po najechaniu kursorem lub fokusie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stan myszy lub fokusu, zaznaczona**

![Ikona zaznaczonego polecenia po najechaniu kursorem myszy lub fokusie](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ikona zaznaczonego polecenia po najechaniu kursorem myszy lub fokusie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarHoverOverSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHoverOverSelected` |
| Obramowanie | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona polecenia: stan naciśnięcia**

![Ikona wciśnięty polecenia](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Ikona wciśnięty polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stan wyłączona**

![Ikona polecenia Wyłączone](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Ikona polecenia Wyłączone

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Pola kombi paska poleceń

> [!IMPORTANT]
> Pola kombi są podobne do rozwijanych, ale zawierają edytowalny region tekstu. Jeśli listy rozwijanej nie obejmują edytowalny region tekstu, użyj tokenów kolorów dla [listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Czerwona linia pola paska polecenia](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Pole kombi paska poleceń (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych skrzynek kombi. | ... dla wszystkiego, czego nie chcesz zawsze pasować do interfejsu użytkownika paska poleceń. |
| ... podczas tworzenia formantu paska poleceń, który jest podobny do pola kombi. | ... gdy masz dostęp do stylizowanego pola kombi. |

**Pole wejściowe paska polecenia: stan domyślny**

![Pole wejściowe pola paska polecenia](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Pole wejściowe pola paska polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxText` |
| Obramowanie | `Environment.ComboBoxBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan domyślny**

![Przycisk upuszczania pola kombi&#45;w dół](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy (dziedziczy z tła paska poleceń) |
| Pierwszy plan (Glif) | `Environment.ComboBoxGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Lista rozwijana paska poleceń](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista rozwijana paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxPopupBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.ComboBoxPopupBorder` |

**Pole wejściowe paska polecenia: stan aktywowania**

![Pole wejściowe paska polecenia po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Pole wejściowe paska polecenia po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseOverText` |
| Obramowanie | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Przycisk listy rozwijanej paska poleceń: stan aktywowania**

![Przycisk listy rozwijanej paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseOverBackground` |
| Pierwszy plan (Glif) | `Environment.ComboBoxMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan aktywowania wskaźnika**

 ![Lista rozwijana paska poleceń po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista rozwijana paska poleceń po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (pozycja menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (pozycja menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wejściowe pola paska polecenia: stan skupiona**

![Pole wejściowe pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Pole wejściowe pola kombi paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxFocusedText` |
| Obramowanie | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan skupienia**

![Przycisk listy rozwijanej paska poleceń z punktem skupienia](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Przycisk listy rozwijanej paska poleceń z punktem skupienia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedButtonBackground` |
| Pierwszy plan (Glif) | `Environment.ComboBoxFocusedGlyph` |

 **Pole wejściowe pola paska polecenia: stan naciśnięcia**

![Wciśnięty pole wejściowe pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Wciśnięty pole wejściowe pola kombi paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseDownText` |
| Obramowanie | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan naciśnięcia**

![Wciśnięty przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Wciśnięty przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseDownBackground` |
| Pierwszy plan (Glif) | `Environment.ComboBoxMouseDownGlyph` |

**Pole wejściowe pola paska polecenia: stan wyłączona**

![Wyłączone pole wejściowe pola paska poleceń](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Wyłączone pole wejściowe pola paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxDisabledText` |
| Obramowanie | `Environment.ComboBoxDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan wyłączenia**

![Wyłączony przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (Glif) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Listy rozwijane paska poleceń

> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale brakuje edytowalnych regionów tekstowych. Jeśli twoja rozwijana liczba zawiera edytowalny region tekstowy, użyj tokenów kolorów dla [pól kombi paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Z listy rozwijanej paska poleceń (czerwona linia)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Z listy rozwijanej paska poleceń (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych formantów listy rozwijanej. | ... dla wszystkiego, co nie jest podobne do listy rozwijanej. |
| | ... dla skrzynek kombi lub przycisków dzielonych. |

**Pole wyboru listy rozwijanej paska poleceń: stan domyślny**

![Domyślne pole wyboru listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Domyślne pole wyboru listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownBackground` |
| Pierwszy plan (tekst) | `DropDownText` |
| Obramowanie | `DropDownBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan domyślny**

![Domyślny przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Domyślny przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (Glif) | `Environment.DropDownGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Domyślna lista rozwijana paska poleceń](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Domyślna lista rozwijana paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownPopupBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.DropDownPopupBorder` |
| W tle | `Environment.DropShadowBackground` |

**Pole wyboru listy rozwijanej paska poleceń: stan aktywowania**

![Pole wyboru listy rozwijanej paska poleceń po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Pole wyboru listy rozwijanej paska poleceń po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.DropDownMouseOverText` |
| Obramowanie | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan aktywowania**

![Przycisk listy rozwijanej paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseOverBackground` |
| Pierwszy plan (Glif) | `Environment.DropDownMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan aktywowania wskaźnika**

![Lista rozwijana paska poleceń po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista rozwijana paska poleceń po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (pozycja menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (pozycja menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wyboru listy rozwijanej paska poleceń: stan naciśnięcia**

![Wciśnięte pole wyboru&#45;w dół](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Wciśnięty pasek polecenia pole wyboru rozwijanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownMouseDownText` |
| Obramowanie | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan naciśnięcia**

![Wciśnięty przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Wciśnięty przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseDownBackground` |
| Pierwszy plan (Glif) | `Environment.DropDownMouseDownGlyph` |

**Pole wyboru listy rozwijanej paska poleceń: stan wyłączenia**

![Wyłączone pole wyboru listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Wyłączone pole wyboru listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownDisabledText` |
| Obramowanie | `Environment.DropDownDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan wyłączenia**

![Wyłączony przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (Glif) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Przyciski podziału paska poleceń
Przyciski podziału współużytkują wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne działania i nazwy tokenów przycisku rozwijane są powtarzane tutaj dla wygody. Listy rozwijane przycisków podziału są implementacjami [menu paska poleceń.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)

![Czerwony przycisk Podziału](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Przycisk podziału paska poleceń (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowego przycisku podziału. | ... dla innych rodzajów przycisków. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Przycisk podziału paska poleceń: stan domyślny**

![Domyślny przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Domyślny przycisk podziału paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (Glif) | `Environment.CommandBarSplitButtonGlyph` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: stan aktywowania**

![Przycisk podziału paska poleceń po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Przycisk podziału paska poleceń po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (Glif) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Przycisk podziału paska poleceń: stan naciśnięcia**

![Naciśnięty przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Naciśnięty przycisk podziału paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Pierwszy plan (Glif) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: stan wyłączenia**

![Wyłączony przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Wyłączony przycisk podziału paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemTextInactive` |
| Pierwszy plan (Glif) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Przyciski "Więcej opcji" i "Przepełnienie" na pasku poleceń
Przycisk "Więcej opcji" jest używany, gdy grupa paska poleceń można dostosować, dodając lub usuwając powiązane przyciski paska poleceń. Przycisk "Przepełnienie" pojawia się, gdy pasek poleceń jest obcinany z powodu braku miejsca w poziomie, a po kliknięciu pokazuje menu zawierające przyciski paska poleceń, które nie mogą być wyświetlane. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.

![Przycisk "Więcej opcji" na pasku poleceń (redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Przycisk "Więcej opcji" na pasku poleceń (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla niestandardowych przycisków "Więcej opcji" lub "Przepełnienie". | ... dla przycisków, które nie mają podobnych funkcji do przycisku "Więcej opcji" lub "Przepełnienie". |

**Przyciski "Więcej opcji" i "Przepełnienie": stan domyślny**

![Domyślny pasek poleceń przycisk "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Domyślny pasek poleceń przycisk "Więcej opcji"

![Domyślny pasek poleceń "Przepełnienie" przycisk](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Domyślny pasek poleceń "Przepełnienie" przycisk

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsBackground` |
| Pierwszy plan (Glif) | `Environment.CommandBarOptionsGlyph` |

**Przyciski "Więcej opcji" i "Przepełnienie": stan aktywowania**

![Przycisk "Więcej opcji" na pasku polecenia po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Przycisk "Więcej opcji" na pasku polecenia po najechaniu kursorem

![Przycisk "Przepełnienie" na pasku polecenia po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Przycisk "Przepełnienie" na pasku polecenia po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (Glif) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Przyciski "Więcej opcji" i "Przepełnienie" baru: stan naciśnięcia**

![Wciśnięty pasek poleceń przycisk "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Wciśnięty pasek poleceń przycisk "Więcej opcji"

![Przepełnienie wciśnięte](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Wciśnięty pasek poleceń "Przepełnienie" przycisk

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (Glif) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentów
Nie ma potrzeby replikowania okien dokumentów, ponieważ są one dostarczane przez środowisko programu Visual Studio. Jednak można zdecydować, że chcesz wykorzystać kolory używane w oknach dokumentów, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.

Podczas korzystania z tokenów kolorów okna dokumentu należy uważać, aby używać ich tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, możesz uzyskać nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frames"></a>Ramki okien dokumentu
Okna dokumentu mogą być zadokowane w IDE lub pływające jako oddzielne okno. Gdy okno dokumentu jest przestawne poza IDE, nadal znajduje się w dokumencie dobrze i ma tła, obramowania, tekstu i kolorów kart, które są takie same, jak wtedy, gdy jest częścią IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne kolory tła, obramowania i tekstu. Gdy okna narzędzi są dobrze zadokowane w dokumencie, dziedziczą zachowanie i kolor ich kart z nazw tokenów okna dokumentu.

![Zadokowane okno dokumentu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Zadokowane okno dokumentu (czerwona linia)

![Pływające okno dokumentu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Pływające okno dokumentu (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w dowolnym miejscu, w tym interfejsie użytkownika, który ma być zgodny z oknem dokumentu. | ...  dla dowolnego interfejsu użytkownika, który nie ma być automatycznie zmieniany, jeśli powłoka ma aktualizację motywu. |

**Zadokowane lub pływające okno dokumentu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Zależy od typu dokumentu |
| Pierwszy plan (tekst) | Zależy od typu dokumentu |
| Obramowanie | `Environment.ToolWindowBorder` |

**Skoncentrowana, przestawna ramka okna dokumentu: stan domyślny**

![Domyślna, przestawna ramka okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Domyślna, przestawna ramka okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (Glif) | `Environment.RaftedWindowButtonActiveGlyph` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |
| Obramowanie (Glif) | `Environment.RaftedWindowButtonActiveBorder`<br />(Ustawiona na przezroczysta) |

**Nieskoncentrowana, przestawna ramka okna dokumentu: stan domyślny**

![Domyślna nieskoncentrowana, przestawna ramka okna dokumentu](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Domyślna nieskoncentrowana, przestawna ramka okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (Glif) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |
| Obramowanie (Glif) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Ustawiona na przezroczysta) |

**Skoncentrowana, przestawna ramka okna dokumentu: stan aktywowania**

![Skoncentrowana, przestawna ramka okna dokumentu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Skoncentrowana, przestawna ramka okna dokumentu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (Glif) | `Environment.RaftedWindowButtonHoverActive` |
| Pierwszy plan (Glif) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Obramowanie (Glif) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Nieskoncentrowana, przestawna ramka okna dokumentu: stan aktywowania**

![Nieskoncentrowana, pływająca ramka okna dokumentu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Nieskoncentrowana, pływająca ramka okna dokumentu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (Glif) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Pierwszy plan (Glif) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Obramowanie (Glif) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Skoncentrowana, pływająca ramka okna dokumentu: stan naciśnięcia**

![Skoncentrowana, pływająca ramka okna dokumentu na prasie](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Skoncentrowana, pływająca ramka okna dokumentu na prasie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (Glif) | `Environment.RaftedWindowButtonDown` |
| Pierwszy plan (Glif) | `Environment.RaftedWindowButtonDownGlyph` |
| Obramowanie (Glif) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Karty dokumentów
Karty dokumentów znajdują się w kanale kart, aby wskazać, które dokumenty są aktualnie otwarte, wraz z tym, który z nich jest bieżącym wybranym lub aktywnym dokumentem. Okna narzędzi można również zadokować w kanale karty dokumentu, jeśli użytkownik je tam umieszcza. W tej sytuacji używają tych samych kolorów kart, co okna dokumentu. Jeśli tworzysz interfejs użytkownika, który ma być zawsze zgodny z kolorami okna dokumentu (w tym aktualizacjami motywu lub jeśli są zainstalowane nowe motywy), odwoł się do tych tokenów kolorów.

![Karty dokumentów (czerwona linia)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Karty dokumentów (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... W dowolnym miejscu tworzysz interfejs użytkownika, który chcesz dopasować karty dokumentów i automatycznie odbierać aktualizacje motywu lub nowe kolory motywu. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, gdy powłoka ma aktualizację motywu. |

#### <a name="open-document-tabs"></a>Otwieranie kart dokumentów
Każdy otwarty dokument ma kartę w kanale kart dokumentu, na których wyświetlana jest jego nazwa. Dokumenty można wybierać lub otwierać w tle, a ich karty odzwierciedlają następujące stany:

- Wybrana karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie. Wybrana karta ma obramowanie dokumentu, które dobrze rozciąga się na górną krawędź dokumentu.

- Karty tła to wszystkie karty dokumentów, które nie są aktualnie zaznaczoną kartą. Po kliknięciu stają się one wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.

![Otwórz kartę dokumentu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Otwórz kartę dokumentu (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych kart dokumentów. | ... dla tymczasowych (podgląd) kart. |
| | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Wybrana karta dokumentu z fokusem**

![Wybrana karta dokumentu z fokusem](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Wybrana karta dokumentu z fokusem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabSelectedGradientTop`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.FileTabSelectedText` |
| Obramowanie | `Environment.FileTabSelectedBorder`<br />(Ustawiona na ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Wybrana karta dokumentu nieskoncentrowanego**

![Wybrana karta dokumentu nieskoncentrowanego](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Wybrana karta dokumentu nieskoncentrowanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabInactiveGradientTop`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.FileTabInactiveText` |
| Obramowanie | `Environment.FileTabInactiveBorder`<br />(Ustawiona na ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta Dokument w tle: stan domyślny**

![Karta Domyślny dokument w tle](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Karta Domyślny dokument w tle

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabBackground` |
| Pierwszy plan (tekst) | `Environment.FileTabText` |
| Obramowanie | `Environment.FileTabBorder`<br />(Ustawiona na ten sam kolor co tło). |

**Karta Dokument w tle: stan myszy**

![Karta Dokumentu tła po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Karta Dokumentu tła po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabHotGradientTop`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.FileTabHotText` |
| Obramowanie | `Environment.FileTabHotBorder`<br />(Ustawiona na ten sam kolor co tło). |

#### <a name="preview-tab"></a>Karta Podgląd
Nazywana również zakładką "tymczasowa". Karta podglądu pojawi się po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksploratora rozwiązań. Działa jako podgląd dokumentu, a także daje użytkownikowi możliwość utrzymania dokumentu otwartego po lewej stronie kanału karty dokumentu. W ciągu jednego czasu można otworzyć tylko jedną kartę podglądu. Karty podglądu mają zarówno tło, jak i wybrane stany, takie jak otwarte karty, i mogą być skoncentrowane lub nieskoncentrowane w ich aktywnym stanie.

![Karta Podgląd (czerwona linia)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Karta Podgląd (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... gdziekolwiek tworzysz tymczasowy podgląd i chcesz, aby jakiś element pasował do bieżącego koloru karty podglądu. | ... dla każdego rodzaju dokumentu lub karty, która nie jest tymczasowa (podgląd). |
| | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Skupiona, wybrana karta podglądu**

![Skupiona, wybrana karta podglądu](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Skupiona, wybrana karta podglądu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedActive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Ustawiona na ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Nieskoncentrowana, wybrana karta podglądu**

![Nieskoncentrowana, wybrana karta podglądu](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Nieskoncentrowana, wybrana karta podglądu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Podgląd tła: stan domyślny**

![Domyślna karta podglądu tła](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Domyślna karta podglądu tła

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalInactiveBorder`<br />(Ustawiona na ten sam kolor co tło). |

**Karta podglądu tła: stan myszy**

![Karta podglądu tła po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Karta podglądu tła po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalHover` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalHoverForeground` |
| Obramowanie | `Environment.FileTabProvisionalHoverBorder`<br />(Ustawiona na ten sam kolor co tło). |

#### <a name="document-overflow-button"></a>Przycisk Przepełnienie dokumentu
Przycisk przepełnienia dokumentu jest obecny, jeśli jest otwarty jeden lub więcej dokumentów, niezależnie od tego, czy w bieżącej konfiguracji jest miejsce w pionie, aby zmieścić wszystkie karty dokumentu. Menu rozwijane przepełnienia dokumentu, które jest kontrolowane przez kolory [menu paska poleceń,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) wyświetla listę wszystkich otwartych dokumentów, zarówno widocznych, jak i ukrytych, a glif przepełnienia zmienia się w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale kart.

![Przycisk przepełnienia dokumentu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Przycisk przepełnienia dokumentu (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowego przycisku przepełnienia dokumentu. | ... dla interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia. |
| | ... dla przycisków przepełnienia paska poleceń. |

**Przycisk przepełnienie dokumentu: stan domyślny**

![Domyślny przycisk przepełnienia dokumentu](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Domyślny przycisk przepełnienia dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonBackground` |
| Pierwszy plan (Glif) | `Environment.DocWellOverflowButtonGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk przepełnienie dokumentu: stan najechaniu kursorem**

![Przycisk Przepełnienie dokumentu po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Przycisk Przepełnienie dokumentu po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Pierwszy plan (Glif) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Przycisk przepełnienia dokumentu: stan naciśnięcia**

![Przycisk przepełnienie dokumentu po naciśnięciu przycisku](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Przycisk przepełnienie dokumentu po naciśnięciu przycisku

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Pierwszy plan (Glif) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Znakowanie
Visual Studio obsługuje tagowanie, co pozwala użytkownikowi zadeklarować słowa kluczowe z wyszukuj do celów śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać team foundation server (TFS) do oznaczania elementów roboczych. Poniższe tabele podają nazwy kolorów zarówno dla samego tagu, jak i glifu "zamknij ikonę", który pojawia się w stanach myszy i wybranych.

![Tagowanie w programie Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Tagowanie w programie Visual Studio (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla interfejsu użytkownika, który obsługuje tagowanie. | ... dla innego typu interfejsu użytkownika. |

#### <a name="tags"></a>Tagi

**Tag: stan domyślny**

![Tag domyślny](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Tag domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.Background` |
| Pierwszy plan (tekst) | `Tag.Background` |

**Tag: stan aktywowania**

![Tag po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tag po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.HoverBackground` |
| Pierwszy plan (tekst) | `Tag.HoverBackgroundText` |

**Tag: stan wciśnięty**

![Wciśnięty znacznik](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Wciśnięty znacznik

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.PressedBackground` |
| Pierwszy plan (tekst) | `Tag.PressedBackgroundText` |

**Tag: wybrany stan**

![Wybrany znacznik](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Wybrany znacznik

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.SelectedBackground` |
| Pierwszy plan (tekst) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zamknij&times;( ) znacznik glif

**Zamknij&times;( ) znacznik glif: stan domyślny**

![Domyślny&times;znacznik Zamknij ( ) glif znacznika](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Domyślny&times;znacznik Zamknij ( ) glif znacznika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (Glif) | `Tag.TagHoverGlyph` |

**Zamknij&times;( ) znacznik glif: stan aktywowania**

![Zamknij&times;( ) znacznik glif na najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Zamknij&times;( ) znacznik glif na najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphHoverBackground` |
| Pierwszy plan (Glif) | `Tag.TagHoverGlyphHover` |
| Obramowanie | `Tag.TagHoverGlyphHoverBorder` |

**Zamknij&times;( ) znacznik glif: stan wciśnięty**

![Wciśnięty&times;znacznik Zamknij ( ) glif znacznika](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Wciśnięty&times;znacznik Zamknij ( ) glif znacznika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphPressedBackground` |
| Pierwszy plan (Glif) | `Tag.TagHoverGlyphPressed` |
| Obramowanie | `Tag.TagHoverGlyphPressedBorder` |

**Wybrany znacznik z&times;glifem Zamknij ( ): stan domyślny**

![Domyślny zaznaczony&times;znacznik z glifem Zamknij ( )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Domyślny zaznaczony&times;znacznik z glifem Zamknij ( )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (Glif) | `Tag.TagSelectedGlyph` |

**Wybrany znacznik z&times;glifem Zamknij ( ): stan najechacza**

![Wybrany znacznik z&times;glifem Zamknij ( ) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Wybrany znacznik z&times;glifem Zamknij ( ) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphHoverBackground` |
| Pierwszy plan (Glif) | `Tag.TagSelectedGlyphHover` |
| Obramowanie | `Tag.TagSelectedGlyphHoverBorder` |

**Wybrany znacznik z&times;glifem Zamknij ( ): stan naciśnięcia**

![Wybrany, wciśnięty znacznik&times;z glifem Zamknij ( )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Wybrany, wciśnięty znacznik&times;z glifem Zamknij ( )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphPressedBackground` |
| Pierwszy plan(Glif) | `Tag.TagSelectedGlyphPressed` |
| Obramowanie | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna narzędzi
Nie ma potrzeby replikowania okien narzędzi, ponieważ są one dostarczane przez środowisko programu Visual Studio. Jednak można zdecydować, że chcesz wykorzystać kolory używane w oknach narzędzi, tak aby interfejs użytkownika zawsze pojawia się zgodne z tej części środowiska programu Visual Studio.

![Okno narzędzia (czerwona linia)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Okno narzędzia (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

### <a name="tool-window-frame"></a>Ramka okna narzędzia
Okna narzędzi w programie Visual Studio są używane dla wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzia jest otwarte, można je przypisać do dowolnej z czterech stron obszaru dokumentu. Okna narzędzi można również unosić się poza IDE, co pozwala na ich zmianę położenia w dowolnym miejscu na ekranie użytkownika. Okna przestawne zawsze znajdują się na szczycie IDE. Na koniec okna narzędzi mogą być zadokowane jako okna dokumentów i dobrze wyświetlane jako karta w dokumencie. Okna narzędzi, które zostały zadokowane jako okna dokumentów, są częściowo barwione przy użyciu nazw tokenów okna dokumentu.

![Ramka okna narzędzia (czerwona linia)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Ramka okna narzędzia (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ...  w dowolnym miejscu tworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zadokowane okno narzędzia**

![Zadokowane okno narzędzia](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Zadokowane okno narzędzia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.ToolWindowBorder` |

**Pływające, skoncentrowane okno narzędzia**

![Pływające, skoncentrowane okno narzędzia](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Pływające, skoncentrowane okno narzędzia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |

**Pływające, nieskoncentrowane okno narzędzia**

![Pływające, nieskoncentrowane okno narzędzia](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Pływające, nieskoncentrowane okno narzędzia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Okna podobne do przybornika
Przybornik jest jednym z najczęściej używanych typowych okien narzędzi w programie Visual Studio. Jest to zasadniczo kontrola drzewa ze specjalnym motywem i zastosowanej stylizacji.

![Okno podobne do przybornika (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Okno podobne do przybornika (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas projektowania okna narzędzia, które ma być zawsze zgodne z przybornikami powłoki. | ... dla wszystkiego, co nie jest podobne do interfejsu użytkownika przybornika lub jeśli nie masz pewności, czy interfejs użytkownika będzie miał problemy, jeśli zmienią się kolory przybornika powłoki. |

**Węzły przybornika: stan domyślny**

![Domyślny węzeł nadrzędny przybornika przybornika](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Domyślny węzeł nadrzędny przybornika przybornika

![Domyślny węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Domyślny węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContent`<br />(Nagłówki) |
| Tło | `Environment.ToolWindowBackground`<br />(Pojedyncze elementy lub całe okno, jeśli nie ma dostępnych formantów) |
| Obramowanie | Brak |
| Pierwszy plan (Glif) | `Environment.ToolboxContent` |
| Pierwszy plan (tekst) | `Environment.ToolboxContent` |

**Przybornik podrzędnych węzłów: stan aktywowania**

![Węzeł podrzędny przyborniku przy najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Węzeł podrzędny przyborniku przy najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContentMouseOver`<br />(Tylko pojedyncze przedmioty) |
| Obramowanie | Brak |
| Pierwszy plan (tekst) | `Environment.ToolboxContentMouseOver`<br />(Tylko pojedyncze przedmioty) |

**Wybrane węzły przybornika: stan skupiona**

![Skoncentrowany, zaznaczony węzeł nadrzędny przybornika przybornika](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Skoncentrowany, zaznaczony węzeł nadrzędny przybornika przybornika

![Skoncentrowany, zaznaczony węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Skoncentrowany, zaznaczony węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Obramowanie | `TreeView.FocusVisualBorder`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (Glif) | `TreeView.SelectedItemActive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Wybrane węzły przybornika: stan nieskoncentrowany**

![Zaznaczony, nieskoncentrowany węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Zaznaczony, nieskoncentrowany węzeł nadrzędny przybornika

![Zaznaczony, nieskoncentrowany węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Zaznaczony, nieskoncentrowany węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Obramowanie | Brak |
| Pierwszy plan (Glif) | `TreeView.SelectedItemInactive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive`<br />Z kategorii [widok drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzia
Obramowanie paska tytułu nie jest prawdziwym obramowaniem, ale grubą linią w górnej części paska tytułu. Nie ma nazwy tokenu dla jego stan nieskoncentrowany.

![Pasek tytułu okna narzędzia (czerwona linia)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Pasek tytułu okna narzędzia (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Ostry pasek tytułu**

![Ostry pasek tytułu](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Ostry pasek tytułu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarActiveGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.TitleBarActiveText` |
| Obramowanie | `Environment.TitleBarActiveBorder`<br />(Ustawiona na ten sam kolor co tło). |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandleActive` |

**Nieskoncentrowany pasek tytułu**

![Pasek tytułu nieskoncentrowany](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Nieskoncentrowany pasek tytułu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarInactiveGradientBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.TitleBarInactiveText` |
| Obramowanie | Nie dotyczy |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Przyciski paska tytułu okna narzędzia
![Przycisk paska tytułu (czerwona linia)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Przycisk paska tytułu (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla przycisków, które pojawiają się w interfejsie użytkownika, który używa tokenów kolorów z pasków tytułów okna narzędzia. | ... dla przycisków wyświetlanych w innych lokalizacjach. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Przyciski paska tytułu z punktem skupienia: stan domyślny**

![Domyślne przyciski paska tytułu z fokusem](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Domyślne przyciski paska tytułu z fokusem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonActiveGlyph` |
| Obramowanie | Nie dotyczy |

**Nieskoncentrowane przyciski paska tytułu: stan domyślny**

![Domyślne, nieskoncentrowane przyciski paska tytułu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Domyślne, nieskoncentrowane przyciski paska tytułu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonInactiveGlyph` |
| Obramowanie | Nie dotyczy |

**Przyciski paska tytułu: stan aktywowania**

![Przyciski paska tytułu na podstawie ostrego przycisku myszy](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Przyciski paska tytułu na podstawie ostrego przycisku myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverActive` |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverActiveBorder` |

**Nieskoncentrowane przyciski paska tytułu: stan aktywowania**

![Nieskoncentrowane przyciski paska tytułu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Nieskoncentrowane przyciski paska tytułu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverInactive` |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Przyciski paska tytułu: stan naciśnięcia**

![Przyciski paska tytułu na celu nacisk](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Przyciski paska tytułu na celu nacisk

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

**Nieskoncentrowane przyciski paska tytułu: stan naciśnięcia**

![Nieskoncentrowane przyciski paska tytułu po naciśnięciu przycisku](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Nieskoncentrowane przyciski paska tytułu po naciśnięciu przycisku

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (Glif) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna narzędzia
![Karta okno narzędzia (czerwona linia)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Karta okno narzędzia (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Karta Okno zaznaczone, skupione narzędzie**

![Karta Okno zaznaczone, skupione narzędzie](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Karta Okno zaznaczone, skupione narzędzie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedActiveText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustawiona na ten sam kolor co tło). |

**Karta okno narzędzia zaznaczone, nieskoncentrowane**

![Karta okno narzędzia zaznaczone, nieskoncentrowane](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Karta okno narzędzia zaznaczone, nieskoncentrowane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustawiona na ten sam kolor co tło). |

**Karta okno narzędzia tło: stan domyślny**

![Karta Okno narzędzia domyślne tło](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Karta Okno narzędzia domyślne tło

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient zatrzymuje się na taką samą wartość koloru w programie Visual Studio 2013.) |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabText` |
| Obramowanie | `Environment.ToolWindowTabBorder` |

**Karta okno narzędzia tło: stan myszy**

![Karta okno narzędzia tło po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Karta okno narzędzia tło po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient zatrzymuje się na taką samą wartość koloru w programie Visual Studio 2013.) |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabMouseOverText` |
| Obramowanie | `Environment.ToolWindowTabMouseOverBorder`<br />(Ustawiona na ten sam kolor co tło). |

### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart

![Automatyczne ukrywanie kart (czerwona linia)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Automatyczne ukrywanie kart (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który ma być zgodny z automatycznie ukrytymi kartami okna narzędzia. | ... dla dowolnego interfejsu użytkownika, który nie ma być zmieniany automatycznie, jeśli powłoka ma aktualizację motywu. |

**Automatyczne ukrywanie kart: stan domyślny**

![Domyślna karta automatycznego ukrywania](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Domyślna karta automatycznego ukrywania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.AutoHideTabText` |
| Obramowanie | `Environment.AutoHideTabBorder` |

**Automatyczne ukrywanie kart: stan aktywowania**

![Automatyczne ukrywanie karty po najechaniu kursorem myszy](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automatyczne ukrywanie karty po najechaniu kursorem myszy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Pochylenie zatrzymuje dla tego tokenu nie używane w tematyce interfejsu użytkownika.) |
| Pierwszy plan (tekst) | `Environment.AutoHideTabMouseOverText` |
| Obramowanie | `Environment.AutoHideTabMouseOverBorder` |
