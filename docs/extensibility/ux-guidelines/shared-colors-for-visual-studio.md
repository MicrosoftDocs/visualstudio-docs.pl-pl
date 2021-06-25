---
title: Udostępnione kolory dla Visual Studio | Microsoft Docs
description: Dowiedz się, jak używać typowych Visual Studio i motywów powłoki do projektowania własnego niestandardowego interfejsu użytkownika, który jest zgodny z Visual Studio środowiska.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262f90fb8d03a9404cdbba8b942e90f6fe6fd3aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903973"
---
# <a name="shared-colors-for-visual-studio"></a>Kolory udostępnione dla Visual Studio
Podczas projektowania interfejsu użytkownika, który używa typowych elementów powłoki Visual Studio, lub chcesz, aby element interfejsu był spójny z podobnymi funkcjami, użyj istniejących nazw tokenów w plikach definicji pakietu, aby wybrać i przypisać kolory. Dzięki temu interfejs użytkownika pozostaje spójny z ogólnym Visual Studio i że jest aktualizowany automatycznie po dodaniu lub zaktualizowania motywów.

W tym artykule opisano typowe elementy interfejsu użytkownika i nazwy tokenów, których używają, do których można się odwoływać podczas tworzenia podobnego interfejsu użytkownika. Aby uzyskać szczegółowe informacje na temat sposobu uzyskiwania dostępu do tych tokenów kolorów, zobacz [usługa VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Upewnij się, że nazwy tokenów są prawidłowo stosowane:

- **Używaj nazw tokenów na podstawie funkcji, a nie samego koloru.** Wspólne kolory współdzielone są skojarzone z określonymi elementami interfejsu i są przeznaczone tylko do tych samych lub podobnych funkcji. Na przykład nie używaj ponownie koloru naciśniętego pola kombi dla animacji postępu wirowania tylko dlatego, że podoba Ci się kolor. Funkcje pola kombi i animacji są różne, a jeśli zmieni się kolor skojarzony z polem kombi, może to nie być już odpowiedni kolor dla elementu animacji. Spójne stosowanie kolorów pomaga zorientować użytkowników i zapobiegać pomyłek.

- **Użyj kolorów tła i tekstu we właściwej kombinacji.** Kolory tła, które mają być używane z tekstem, będą miały skojarzony kolor tekstu. Nie używaj kolorów tekstu innych niż określone dla tego tła. Jeśli nie ma skojarzonego koloru tekstu, nie używaj tego koloru tła dla żadnej powierzchni, na której ma być wyświetlany tekst. Inne kombinacje kolorów tekstu i tła mogą powodować nieczytelny interfejs.

- **Użyj kolorów kontrolek, które są odpowiednie dla ich lokalizacji.** W niektórych stanach niektóre kontrolki Visual Studio nie mają oddzielnych kolorów obramowania i tła. Zamiast tego zbierają te kolory z powierzchni za nimi. Upewnij się, że zawsze używasz nazw tokenów odpowiednich dla lokalizacji, w której umieszczasz kontrolkę.

> [!IMPORTANT]
> Nie używaj tokenów w kategoriach "Strona startowa" lub "Cider".

## <a name="common-shared-controls"></a>Wspólne kontrolki udostępnione

Jeśli używasz standardowego Visual Studio wiersza polecenia w funkcji, będziesz mieć dostęp do kontrolek powłoki ze stylami. Nie należy ponownie szablonu tych typowych kontrolek. Jeśli jednak musisz utworzyć niestandardowy pasek poleceń, może być również konieczne skompilowanie kontrolek niestandardowych. W takim przypadku upewnij się, że używasz prawidłowych nazw tokenów dla każdej z następujących kontrolek, aby interfejs użytkownika był zgodny z resztą Visual Studio.

### <a name="button-controls"></a>formanty przycisków

![Redline kontrolki przycisku](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Używać... | Nie używaj ... |
| --- | --- |
| ... w przypadku przycisków w dokumencie, które chcesz zintegrować z motywami Visual Studio (jasnym, ciemnym, niebieskim lub motywem duży kontrast systemowym). | ... dla przycisków, które będą wyświetlane na niestandardowym tle, które nie jest częścią Visual Studio motywu. |

**Przycisk: stan standardowy**

![Przycisk Standardowa](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Przycisk Standardowa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.Button` |
| Obramowanie przycisku | `CommonControls.ButtonBorder` |

**Przycisk: stan domyślny**

![Przycisk Domyślny](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Przycisk Domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDefault` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDefault` |

**Przycisk: wyłączony stan**

![Wyłączony przycisk](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Wyłączony przycisk

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDisabled` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDisabled` |

**Przycisk: stan wskaźnika myszy**

![Przycisk po najechaniu kursorem](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Przycisk po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonHover` |
| Obramowanie przycisku | `CommonControls.ButtonBorderHover` |

**Przycisk: stan naciśnięty**

![Naciśnięty przycisk](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Naciśnięty przycisk

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonPressed` |
| Obramowanie przycisku | `CommonControls.ButtonBorderPressed` |

**Przycisk: stan skoncentrowany**

![Przycisk z ukierunkowaną koncentrować](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Przycisk z ukierunkowaną koncentrować

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Przycisk | `CommonControls.ButtonFocused` |
| Obramowanie przycisku | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kontrolki pola wyboru
![Pole wyboru (redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Pole wyboru (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w przypadku kontrolek pola wyboru zawartych w obszarze dokumentu. | ... dla dowolnego interfejsu użytkownika, który nie jest kontrolką pola wyboru. |

**Pole wyboru: stan domyślny**

![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Pole wyboru Domyślne

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackground` |
| Obramowanie | `CommonControls.CheckBoxBorder` |
| Tekst | `CommonControls.CheckBoxText` |
| Glifów | `CommonControls.CheckBoxGlyph` |

**Pole wyboru: stan wyłączony**

![Wyłączone pole wyboru](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Wyłączone pole wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.CheckBoxBorderDisabled` |
| Tekst | `CommonControls.CheckBoxTextDisabled` |
| Glifów | `CommonControls.CheckBoxGlyphDisabled` |

**Pole wyboru: stan wskaźnika myszy**

 ![Pole wyboru po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Pole wyboru po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundHover` |
| Obramowanie | `CommonControls.CheckBoxBorderHover` |
| Tekst | `CommonControls.CheckBoxTextHover` |
| Glifów | `CommonControls.CheckBoxGlyphHover` |

**Pole wyboru: stan naciśnięty**

![Naciśnięte pole wyboru](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Naciśnięte pole wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Obramowanie | `CommonControls.CheckBoxBorderPressed` |
| Tekst | `CommonControls.CheckBoxTextPressed` |
| Glifów | `CommonControls.CheckBoxGlyphPressed` |

**Pole wyboru: stan skoncentrowany**

![Pole wyboru Ukierunkowane](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Pole wyboru Ukierunkowane

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundFocused` |
| Obramowanie | `CommonControls.CheckBoxBorderFocused` |
| Tekst | `CommonControls.CheckBoxTextFocused` |
| Glifów | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listy rozwijane i pola kombi
![Lista rozwijana/pole kombi (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Lista rozwijana/pole kombi (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w przypadku listy rozwijanej i pól kombi na liście dokumentów. | ... dla dowolnego interfejsu użytkownika, który nie jest polem listy rozwijanej ani polem kombi. |
| | ... w przypadku listy [rozwijanej paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) [lub pól kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listy rozwijane i pola kombi: stan domyślny**

![Domyślna lista rozwijana/pole kombi](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Domyślna lista rozwijana/pole kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackground` |
| Obramowanie | `CommonControls.ComboBoxBorder` |
| Tekst | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Glifów | `CommonControls.ComboBoxGlyph` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackground` |

**Listy rozwijane i pola kombi: stan wyłączenia**

![Wyłączona lista rozwijana/pole kombi](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Wyłączona lista rozwijana/pole kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.ComboBoxBorderDisabled` |
| Tekst | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifów | `CommonControls.ComboBoxGlyphDisabled` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listy rozwijane i pola kombi: stan wskaźnika myszy**

![Lista rozwijana/pole kombi po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Lista rozwijana/pole kombi po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundHover` |
| Obramowanie | `CommonControls.ComboBoxBorderHover` |
| Tekst | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Glifów | `CommonControls.ComboBoxGlyphHover` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listy rozwijane i pola kombi: stan naciśnięty**

![Naciśnięta lista rozwijana/pole kombi](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Naciśnięta lista rozwijana/pole kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundPressed` |
| Obramowanie | `CommonControls.ComboBoxBorderPressed` |
| Tekst | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Glifów | `CommonControls.ComboBoxGlyphPressed` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Widok elementu listy list:stan naciśnięty**

 ![Widok elementu listy naciśniętego pola rozwijanego/kombi](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Widok elementu listy naciśniętego pola rozwijanego/kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Tekst elementu | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Tle w tle | `CommonControls.ComboBoxListBackgroundShadow` |

**Listy rozwijane i pola kombi: stan skoncentrowany**

![Lista rozwijana/pole kombi z fokusem](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Lista rozwijana/pole kombi z fokusem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxBorderFocused` |
| Tekst | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Glifów | `CommonControls.ComboBoxGlyphFocused` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listy rozwijane i pola kombi: wybór tekstu wejściowego**

![Wybór wprowadzania tekstu w polu listy rozwijanej/polu kombi](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Wybór wprowadzania tekstu w polu listy rozwijanej/polu kombi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Wyróżnij | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Kontrolki danych tabelarycznej (siatki)
Kontrolki danych tabelarycznej, znane również jako kontrolki siatki, są wspólnymi kontrolkami dla Visual Studio, których można użyć do przedstawienia dużych ilości danych w wielu kolumnach. Standardowe kontrolki danych tabelarowych można znaleźć między innymi w wielu miejscach na platformie Visual Studio: oknie narzędzia Lista błędów, raportach IntelliTrace i widoku sterty pamięci. Zawsze używaj standardowych kontrolek danych tabelarowych. W niektórych rzadkich przypadkach możesz nie mieć dostępu do standardowych kontrolek danych tabelarowych. W takich sytuacjach użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi kontrolkami danych tabelar Visual Studio.

![Kontrolka danych tabelarycznej/siatki (czerwona linia)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Kontrolka danych tabelarycznej/siatki (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla kontrolek tabelarycznej lub siatki. | ... dla dowolnego interfejsu użytkownika, który nie jest kontrolką tabelaryjną ani kontrolką siatki. |

#### <a name="column-headers"></a>Nagłówki kolumn
Nagłówki kolumn składają się z tła, obramowania, tekstu tytułu i opcjonalnego glyph zwykle używanego podczas sortowania siatki według tej kolumny.

**Nagłówek kolumny: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.Default` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (glif) | `Header.Glyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan wskaźnika myszy**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Header.MouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (glif) | `Header.MouseOverGlyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: stan naciśnięty**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Pierwszy plan (tekst) | `CommonControls.CheckBoxBorderPressed` |
| Pierwszy plan (glif) | `CommonControls.CheckBoxTextPressed` |
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
Tekst instruktażowy zawiera najważniejsze główne wyjaśnienie tego, co należy zrobić w oknie dialogowym lub na stronie dokumentu.

![Domyślny tekst instruktażowy](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Domyślny tekst instruktażowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Pomocniczy tekst instruktażowy
Na stronach dokumentów z dużą ilością tekstu i kontrolek część tekstu instruktażowego używa innej wartości koloru. Pomaga to przekazać informacje, które są najważniejsze, i zmniejszyć ogólną gęstość elementów interfejsu użytkownika. (Zobacz również sekcję poniżej w tekście wskazówki).

![Pomocniczy tekst instruktażowy](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Pomocniczy tekst instruktażowy

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Tekst wskazówki
Tekst wskazówki jest wyświetlany w pustej kontrolce, poniżej kontrolki lub na pustej powierzchni dokumentu, aby pokazać użytkownikowi, co należy zrobić dalej. Tekstu wskazówek można używać z tłami Okna lub Kontrolka.

**Domyślny tekst wskazówki**

![Domyślny tekst wskazówki](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Domyślny tekst wskazówki

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlEditHintText` |

**Tekst wymaganej wskazówki**

![Tekst wymaganej wskazówki](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Tekst wymaganej wskazówki

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.ControlRequiredHintText` |
| Tło | `Environment.ControlRequiredBackground` |

**Tekst kontrolki pola wyszukiwania**

> Zobacz [Pola wyszukiwania dla](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) innych tokenów kolorów powiązanych z kontrolką Wyszukiwanie.

![Tekst kontrolki pola wyszukiwania](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Tekst kontrolki pola wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Hiperlink to jedna kontrolka, która nie ma pary pierwszy plan/tło. We wszystkich przypadkach użyj koloru hiperlinku pierwszego planu, który będzie wyświetlany poprawnie na ciemnym, szarym i białym tle. Jeśli nie używasz tokenu koloru dla kontrolki hiperlinku, zostanie wyświetlony domyślny kolor systemowy "pressed", który będzie migał na czerwono. Jest to sygnał, że kontrolka nie używa poprawnego tokenu koloru środowiska.

![Hiperlink (redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hiperlink (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w przypadku konieczności utworzenia niestandardowego hiperlinku. | ... dla wszystkiego, co nie jest hiperlinkiem. |

**Hiperlink: stan domyślny**

![Hiperlink domyślny](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hiperlink domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlink` |

**Hiperlink: stan wskaźnika myszy**

![Hiperlink po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hiperlink po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkHover` |

**Hiperlink: stan naciśnięty**

![Naciśnięty hiperlink](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Naciśnięty hiperlink

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkPressed` |

**Hiperlink: stan wyłączony**

![Wyłączony hiperlink](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Wyłączony hiperlink

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Pasek informacyjny
Pasek informacyjny służy do zapewnienia większej liczby informacji o danym kontekście i zawsze pojawia się w górnej części okna dokumentu lub okna narzędzi.

![Pasek informacyjny (redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Pasek informacyjny (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych paskach informacyjnych. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska informacji. |

**Pasek informacji: stan domyślny**

![Domyślny pasek informacyjny](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Domyślny pasek informacyjny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.InfoBarBackground` |
| Pierwszy plan (tekst) | `InfoBar.InfoBar` |
| Obramowanie | `InfoBar.InfoBarBorder` |

**Przycisk Zamknij paska informacyjnego ( &times; ): stan domyślny**

![Domyślny przycisk Zamknij paska informacyjnego ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Domyślny przycisk Zamknij paska informacyjnego ( &times; )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButton` |
| Obramowanie | `InfoBar.CloseButtonBorder` |
| Glifów | `InfoBar.CloseButtonGlyph` |

**Przycisk Zamknij paska informacyjnego ( &times; ): stan wskaźnika myszy**

![Przycisk Zamknij paska informacyjnego ( &times; ) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Przycisk Zamknij paska informacyjnego ( &times; ) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonHover` |
| Obramowanie | `InfoBar.CloseButtonHoverBorder` |
| Glifów | `InfoBar.CloseButtonHoverGlyph` |

**Przycisk Zamknij paska informacyjnego ( &times; ): stan naciśnięty**

![Naciśnięty przycisk Zamknij &times; () na pasku informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Naciśnięty przycisk Zamknij &times; () na pasku informacyjnym

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.CloseButtonDown` |
| Obramowanie | `InfoBar.CloseButtonDownBorder` |
| Glifów | `InfoBar.CloseButtonDownGlyph` |

**Przycisk hiperlinku paska informacji: stan domyślny**

![Domyślny przycisk hiperlinku paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny przycisk hiperlinku paska informacji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Przycisk hiperlinku paska informacji: stan wskaźnika myszy**

![Przycisk hiperlinku paska informacji po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Przycisk hiperlinku paska informacji po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Przycisk hiperlinku paska informacji: stan naciśnięty**

![Naciśnięty przycisk hiperlinku paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Naciśnięty przycisk hiperlinku paska informacji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreśleniem) |

**Hiperlink w tekście paska informacyjnego (w zdaniu): stan domyślny**

![Domyślny przycisk hiperlinku wbudowanego paska informacji](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny przycisk hiperlinku wbudowanego paska informacji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `InfoBar.Hyperlink` |

**Hiperlink w tekście paska informacyjnego (w zdaniu): stan wskaźnika myszy**

![Przycisk hiperlinku wbudowanego na pasku informacyjnym po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Przycisk hiperlinku wbudowanego na pasku informacyjnym po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreśleniem) |

**Hiperlink w tekście paska informacyjnego (w zdaniu): naciśnięty stan**

![Naciśnięty przycisk hiperlinku wbudowanego paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Naciśnięty przycisk hiperlinku wbudowanego paska informacyjnego

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

**Przycisk paska informacyjnego: stan wskaźnika myszy**

![Przycisk paska informacyjnego po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Przycisk paska informacyjnego po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseOver` |
| Pierwszy plan (tekst) | `InfoBar.ButtonMouseOver` |
| Obramowanie | `InfoBar.ButtonMouseOverBorder` |

**Przycisk paska informacyjnego: stan naciśnięty**

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

**Przycisk paska informacyjnego: stan skoncentrowany**

![Przycisk paska informacji z koncentrować się](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Przycisk paska informacji z koncentrować się

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `InfoBar.ButtonFocus` |
| Pierwszy plan (tekst) | `InfoBar.ButtonFocus` |
| Obramowanie | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania są stylowane według Visual Studio i nie muszą mieć one żadnych stylów. Możesz jednak zdecydować, że chcesz korzystać z kolorów używanych w paskach przewijania, aby interfejs użytkownika zawsze był zgodny z tą częścią Visual Studio użytkownika.

![Pasek przewijania (redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Pasek przewijania (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia interfejsu użytkownika, który chcesz dopasować do Visual Studio przewijania. | ... dla wszystkich elementów, które nie mają być zawsze zgodne z interfejsem użytkownika paska przewijania. |

**Pasek przewijania: stan domyślny**

![Domyślny pasek przewijania](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Domyślny pasek przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (miniatura) | `Environment.ScrollBarThumbBackground` |

**Pasek przewijania: stan wskaźnika myszy**

![Pasek przewijania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Pasek przewijania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (miniatura) | `Environment.ScrollBarThumbMouseOverBackground` |

*Pasek przewijania: stan naciśnięcia**

![Pasek przewijania naciśnięty](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Pasek przewijania naciśnięty

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszy plan (miniatura) | `Environment.ScrollBarThumbPressedBackground` |

**Strzałka paska przewijania: stan domyślny**

![Domyślna strzałka paska przewijania](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Domyślna strzałka paska przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (glif) | `Environment.ScrollBarArrowGlyph` |

**Strzałka paska przewijania: stan wskaźnika myszy**

![Strzałka paska przewijania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Strzałka paska przewijania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowMouseOverBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (glif) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Strzałka paska przewijania: stan naciśnięcia**

![Naciśnięta strzałka paska przewijania](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Naciśnięta strzałka paska przewijania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowPressedBackground`<br />(Ustaw ten sam kolor co pasek przewijania). |
| Pierwszy plan (glif) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Pola wyszukiwania
Jeśli to możliwe, użyj wspólnej kontrolki wyszukiwania udostępnianej przez środowisko Visual Studio wyszukiwania. Kolory pól wyszukiwania znajdują się w kategorii "SearchControl" w pliku **ShellColors.pkgdef,** który zawiera nazwy tokenów dla pola wejściowego, przycisku akcji, przycisku listy rozwijanej i menu rozwijanego.

Pole wyszukiwania może być jednym z kilku stanów, z których niektóre wzajemnie się wykluczają:

- Termin "Skoncentrowany" lub "bez koncentracji" odnosi się do tego, czy kursor znajduje się w polu tekstowym.

- "Aktywny" lub "nieaktywny" odnosi się do tego, czy użytkownik ma wprowadzić zapytanie wyszukiwania w polu tekstowym.

- "Zatrzymaj wskaźnik myszy" oznacza, że użytkownik najeżdża kursorem myszy na pole wyszukiwania (ten stan zastępuje wszystkie inne stany).

- "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączona dla bieżącego kontekstu.

![Pole wyszukiwania (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Pole wyszukiwania (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas projektowania pola wyszukiwania niestandardowego. | ... dla wszystkiego, co nie jest polem wyszukiwania. |
| | ... dla wszystkich elementów, które nie mają być zawsze zgodne z interfejsem użytkownika pola wyszukiwania. |

**Pole wejściowe wyszukiwania ukierunkowanego**

![Pole wejściowe wyszukiwania ukierunkowanego](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Pole wejściowe wyszukiwania ukierunkowanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedBackground` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Pole wprowadzania aktywnego wyszukiwania bez koncentracji**

![Pole wejściowe wyszukiwania nie ma koncentracji](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Pole wprowadzania aktywnego wyszukiwania bez koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.SearchActiveBackground` |
| Pierwszy plan (tekst) | `SearchControl.SearchActiveBackground` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Nieaktywne pole wejściowe wyszukiwania bez koncentracji**

![Nieaktywne pole wejściowe wyszukiwania bez koncentracji](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nieaktywne pole wejściowe wyszukiwania bez koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Unfocused` |
| Pierwszy plan (tekst) | `SearchControl.Unfocused` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Wyróżnione pole wejściowe wyszukiwania (tylko tekst)**

![Wyróżnione pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Wyróżnione pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Selection` |
| Pierwszy plan (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | Brak |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Wyłączone pole wejściowe wyszukiwania**

![Wyłączone pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Wyłączone pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.Disabled` |
| Pierwszy plan (tekst) | `SearchControl.Disabled` |
| Obramowanie | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Przycisk akcji wyszukiwania ukierunkowanego**

![Przycisk akcji wyszukiwania z ukierunkowaną akcją](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Przycisk akcji wyszukiwania ukierunkowanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (wyszukiwanie glifów) | `SearchControl.SearchGlyph` |
| Pierwszy plan (zatrzymaj glif) | `SearchControl.StopGlyph` |
| Pierwszy plan (wyczyść glif) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk akcji wyszukiwania bez koncentracji**

![Przycisk akcji wyszukiwania bez koncentracji](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Przycisk akcji wyszukiwania bez koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (wyszukiwanie glifów) | `SearchControl.SearchGlyph` |
| Pierwszy plan (zatrzymaj glif) | `SearchControl.StopGlyph` |
| Pierwszy plan (wyczyść glif) | `SearchControl.ClearGlyph` |
| Obramowanie | Nie dotyczy |

**Naciśnięty przycisk akcji wyszukiwania**

![Naciśnięty przycisk akcji wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Naciśnięty przycisk akcji wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.ActionButtonMouseDown` |
| Pierwszy plan (glif) | `SearchControl.ActionButtonMouseDownGlyph` |
| Obramowanie | `SearchControl.ActionButtonMouseDownBorder` |

**Wyłączony przycisk akcji wyszukiwania**

![Przycisk akcji wyszukiwania jest wyłączony](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Wyłączony przycisk akcji wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (glif) | `SearchControl.ActionButtonDisabledGlyph` |
| Obramowanie | Brak |

**Przycisk listy rozwijanej wyszukiwania ukierunkowanego**

![Przycisk listy rozwijanej wyszukiwania ukierunkowanego](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Przycisk listy rozwijanej wyszukiwania ukierunkowanego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.FocusedDropDownButton` |
| Pierwszy plan (glif) | `SearchControl.FocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.FocusedDropDownButtonBorder` |

**Przycisk listy rozwijanej wyszukiwania bez koncentracji**

![Przycisk listy rozwijanej wyszukiwania bez koncentracji](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Przycisk listy rozwijanej wyszukiwania bez koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.UnfocusedDropDownButton` |
| Pierwszy plan (glif) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.UnfocusedDropDownButtonBorder` |

**Naciśnięty przycisk listy rozwijanej wyszukiwania**

![Naciśnięty przycisk listy rozwijanej wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Naciśnięty przycisk listy rozwijanej wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.MouseDownDropDownButton` |
| Pierwszy plan (glif) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Obramowanie | `SearchControl.MouseDownDropDownButtonBorder` |

**Wyłączony przycisk listy rozwijanej wyszukiwania**

![Wyłączony przycisk listy rozwijanej wyszukiwania](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej wyszukiwania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (glif) | `SearchControl.DisabledDownButtonGlyph` |
| Obramowanie | Brak |

#### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania
Menu rozwijane pola wyszukiwania może być nieco bardziej złożone niż inne menu rozwijane w Visual Studio. Sekcje "sugerowane wyszukiwania" i "opcje wyszukiwania" mogą być wyświetlane samodzielnie lub razem w menu, a każda z nich ma oddzielną kolor. Wiersz oddziela również te dwie sekcje, gdy są one wyświetlane razem, a całe menu rozwijane jest otoczone obramowaniem.

![Lista rozwijana wyszukiwania (redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Lista rozwijana wyszukiwania (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia listy rozwijanej wyszukiwania niestandardowego. | ... w przypadku list rozwijanych, które są wyświetlane w innych kontekstach. |
| ... prawidłowe nazwy tokenów dla poprawnych składników listy. | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Elementy listy rozwijanej wyszukiwania**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Obramowanie | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Sugerowane wyszukiwania: stan domyślny**

![Sugerowane wyszukiwania domyślne](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Sugerowane wyszukiwania domyślne

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `SearchControl.PopupItemText` |

**Sugerowane wyszukiwania: stan wskaźnika myszy**

![Sugerowane wyszukiwania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Sugerowane wyszukiwania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `SearchControl.PopupMouseOverItemText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan domyślny**

![Pole wyboru Wyszukaj](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Domyślne opcje wyszukiwania (pole wyboru)

![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Domyślne opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxText` |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonText` |
| Tło nagłówka | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst nagłówka) | `SearchControl.PopupSectionHeaderText` |

**Opcje wyszukiwania: stan wskaźnika myszy**

![Opcje wyszukiwania (pole wyboru) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Opcje wyszukiwania (pole wyboru) po najechaniu kursorem

![Opcje wyszukiwania (link) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Opcje wyszukiwania (link) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonMouseDownText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: stan naciśnięty**

![Opcje wyszukiwania naciśniętego (pole wyboru)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Opcje wyszukiwania naciśniętego (pole wyboru)

![Opcje wyszukiwania naciśniętego (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Opcje wyszukiwania naciśniętego (link)

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło pola wyboru | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst pola wyboru) | `SearchControl.PopupCheckboxMouseDownText` |
| Tło linku | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst linku) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Widoki drzewa
Kilka okien narzędzi, w tym Eksplorator rozwiązań, Eksplorator serwera i Widok klasy, implementuje hierarchiczny schemat organizacyjny, którego kolory są kontrolowane przez nazwy kolorów w `TreeView` kategorii. Wszystkie elementy w widoku drzewa mają kolory tła i tekstu. Elementy, które mają zagnieżdżone elementy podrzędne, mają również glify wskazujące, czy element jest rozwinięty, czy zwinięty.

![Widok drzewa (redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Widok drzewa (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... wszędzie tam, gdzie trzeba zaimplementować hierarchiczny widok organizacyjny. | ... dla wszystkich danych, które nie są podobne do widoku drzewa. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Element widoku drzewa: stan domyślny**

![Domyślny element widoku drzewa](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Domyślny element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (glif) | `TreeView.Glyph` |
| Obramowanie | Brak |

**Element widoku drzewa: stan wskaźnika myszy**

![Element widoku drzewa po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Element widoku drzewa po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszy plan (tekst) | `TreeView.Background` |
| Pierwszy plan (glif) | `TreeView.GlyphMouseOver` |
| Obramowanie | Brak |

**Element widoku drzewa: przeciąganie stanu**

![Element widoku drzewa podczas przeciągania](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Element widoku drzewa podczas przeciągania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.DragOverItem` |
| Pierwszy plan (tekst) | `TreeView.DragOverItem` |
| Pierwszy plan (glif) | `TreeView.DragOverItemGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: wybrany, skoncentrowany stan**

![Wybrany i skoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Wybrany i skoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (glif) | `TreeView.SelectedItemActiveGlyph` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: wybrany, stan bez koncentracji uwagi**

![Wybrany i nieekskoncentrowany element widoku drzewa](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Wybrany i nieekskoncentrowany element widoku drzewa

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (glif) | `TreeView.SelectedItemInactiveGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: stan najeżdżony, wybrany i skoncentrowany**

![Wybrany i skoncentrowany element widoku drzewa po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Wybrany i skoncentrowany element widoku drzewa po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive` |
| Pierwszy plan (glif) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan z najechaną kursorem, wybraną i bez koncentracji uwagi**

![Wybrany i nieskoncentrowany element widoku drzewa po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Wybrany i nieskoncentrowany element widoku drzewa po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszy plan (glif) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | Brak |

## <a name="shell-appearance"></a>Wygląd powłoki

### <a name="background"></a>Tło
Tło środowiska składa się z dwóch warstw. Dolna warstwa ma pełny kolor, który obejmuje całe idee. Górna warstwa mieści się pod etykietą polecenia i między oknem narzędzi automatycznie ukrywa kanały po lewej i prawej krawędzi środowiska IDE. Górne i dolne warstwy tła są ustawione na ten sam kolor w motywach Jasny i Ciemny.

![Visual Studio powłoki (redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio powłoki (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla miejsc, w których chcesz dopasować tło Visual Studio środowisku. | ... jako wypełnienie dla miejsc, które nie są powierzchniami tła. |
| | ... jako tło, w którym mają być umieszczane elementy pierwszego planu. |

**Wygląd powłoki warstwy dolnej**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.EnvironmentBackground` |

**Wygląd powłoki najwyższej warstwy**

> Gradient zatrzymuje się na tę samą wartość koloru w Visual Studio 2013 jasnych i ciemnych motywach.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Gotowe polecenie
Na półce poleceń są używane dwa zestawy nazw tokenów: jeden dla paska menu, a jeden dla paska poleceń. Poszczególne grupy paska poleceń ma własne wartości koloru tła, które omówiono bardziej szczegółowo w sekcji "pasek poleceń". Tekst paska menu i paska poleceń omówiono odpowiednio w sekcjach menu i paska poleceń.

![Visual Studio polecenia (redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio polecenia (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla obszarów, w których są umieszczane menu lub paski narzędzi. | ... w przypadku obszarów, które nie są podobne do gotowego polecenia. |
|... z poprawną kombinacją nazwy tokenu tła/pierwszego planu. | |

**Pasek menu na półce polecenia**

> Gradient zatrzymuje się na tę samą wartość koloru w Visual Studio 2013 jasnych i ciemnych motywach.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Pasek poleceń na półce polecenia**

> Gradient zatrzymuje się na tę samą wartość koloru w Visual Studio 2013 jasnych i ciemnych motywach.

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest Designer
Projektant manifestu został zaprojektowany jako sposób ułatwiający edytowanie pliku manifestu w Windows 8 i Windows Phone 8. Chociaż nie ma udostępnionej struktury dostępnej do użycia, może być odpowiednie dopasowanie układu projektu i kolorów kart orientacji/nawigacji i ogólnej struktury. Aby uzyskać więcej informacji na temat szczegółów układu, zobacz [Layout for Visual Studio (Układ dla Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)).

![Manifest Designer (redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest Designer (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... Dla projektantów podobnych do Projektanta manifestu. | ... Jeśli masz więcej niż sześć kart. |
| ... w miejsce typowych kontrolek kart w górnej części edytora w obszarze dokumentu. | ... dla dowolnego interfejsu użytkownika, który nie ma struktury podobnej do projektanta manifestu. |

**Wybrana karta Projektanta manifestu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.TabActive` |
| Obramowanie | Brak |

**Wybrane okienko opisu w projektancie manifestu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.DescriptionPane` |

**Strona wybranej zawartości w projektancie manifestu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Background` |
| Tekst pomocnika okna dialogowego | `ManifestDesigner.WatermarkText`<br />(Ta nazwa tokenu nie jest dopasowana do jego funkcji). |

**Karta Projektant manifestu: stan niezaznany**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Inactive` |

**Karta Projektant manifestu: stan wskaźnika myszy**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Struktury poleceń

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menu
Menu mogą występować w kilku miejscach na Visual Studio: na pasku menu głównego, osadzonym w oknach dokumentów lub narzędzi albo po kliknięciu prawym przyciskiem myszy w różnych lokalizacjach w całym idee. Implementacje menu skojarzonych z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiedniego elementu. Zawsze należy używać standardowej implementacji menu dostarczonej przez Visual Studio środowisku. Jednak w niektórych rzadkich przypadkach możesz nie mieć dostępu do standardowych menu Visual Studio menu. W takich sytuacjach użyj następujących nazw tokenów, aby upewnić się, że interfejs użytkownika jest zgodny z innymi menu w Visual Studio.

![Visual Studio menu (redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio menu (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... gdy musisz utworzyć menu niestandardowe.| ... sam kolor tła. Zawsze używaj kombinacji tła/pierwszego planu w określony sposób. |
| ... jeśli masz nowy składnik interfejsu użytkownika, który ma być Visual Studio menu.| |

#### <a name="menu-titles"></a>Tytuły menu
Tytuły menu składają się z tła, obramowania i tekstu tytułu, a także opcjonalnego glifu, zwykle gdy menu znajduje się na pasku poleceń.

![Tytuł menu (redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Tytuł menu (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... za każdym razem, gdy tworzysz tytuł menu niestandardowego. | ... dla wszystkich elementów, które nie mają być zawsze zgodne z tytułem menu. |
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

**Tytuł menu: stan wskaźnika myszy**

![Tytuł menu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Tytuł menu po najechaniu kursorem

![Tytuł menu z glifem po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Tytuł menu z glifem po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (glif) | `Environment.CommandBarMenuMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |

**Tytuł menu: stan naciśnięty**

![Tytuł naciśniętego menu](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Tytuł naciśniętego menu

![Tytuł naciśniętego menu z glifem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Tytuł naciśniętego menu z glifem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Pierwszy plan (glif) | `Environment.CommandBarMenuMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder`<br />(Tylko lewe, górne i prawe strony). |

**Tytuł menu: wyłączony stan**

![Tytuł wyłączonego menu z glifem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Tytuł wyłączonego menu z glifem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszy plan (glif) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

#### <a name="menu-items"></a>Elementy menu
Pojedynczy element menu składa się z tekstu menu i opcjonalnej ikony, pola wyboru lub symbolu podmenu. Kolor tła i tekstu zmienia się po najechaniu kursorem. Ten token koloru jest parą tła/pierwszego planu.

![Elementy menu ( redline)](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Używać... | Nie używaj ... |
|---|---|
| ... dla dowolnej listy rozwijanej, która jest uruchomiona z paska menu lub paska poleceń. | ... dla dowolnej listy rozwijanej w innym kontekście. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Elementy menu: stan domyślny**

![Domyślne elementy menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Domyślne elementy menu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Foreground (podmenu glyph) | `Environment.CommandBarMenuSubmenuGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder` |
| Tło kanału ikony | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Elementy menu: zaznaczone i wybrane stany**

![Zaznaczone menu](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Sprawdzony element menu

![Wybrane menu](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Wybrany element menu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Znacznik wyboru | `Environment.CommandBarCheckBox` |
| Zaznaczanie tła | `Environment.CommandBarSelectedIcon` |
| Tło ikony | `Environment.CommandBarSelected` |
| Obramowanie ikony | `Environment.CommandBarSelectedBorder` |

**Elementy menu: stan wskaźnika myszy**

![Wskaźnik myszy na menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Element menu po najechaniu kursorem

![Zaznaczone aktywowanie menu](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Sprawdzony element menu po najechaniu kursorem

![Wybrany wskaźnik myszy na menu](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Wybrany element menu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMenuItemMouseOver` |
| Pierwszy plan (tekst) | `Environment.CommandBarMenuItemMouseOverText` |
| Foreground (podmenu glyph) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxMouseOver` |
| Zaznaczanie tła | `Environment.CommandBarHoverOverSelectedIcon` |
| Tło ikony | `Environment.CommandBarHoverOverSelected` |
| Obramowanie ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementy menu: stan wyłączenia**

![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Wyłączony element menu

![Zaznaczone menu wyłączone](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Wyłączony element menu ze znacznikiem wyboru

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Foreground (podmenu glyph) | `Environment.CommandBarMenuSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxDisabled` |
| Zaznaczanie tła | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Paski poleceń
Pasek poleceń może pojawić się w wielu miejscach w Visual Studio IDE, w szczególności na półce poleceń i osadzonych w oknach narzędzi lub dokumentów.

Ogólnie rzecz biorąc, zawsze używaj standardowej implementacji paska poleceń dostarczonej przez Visual Studio środowiska. Użycie mechanizmu standardowego gwarantuje, że wszystkie szczegóły wizualizacji będą wyświetlane poprawnie, a elementy interaktywne będą zachowywać się spójnie z innymi kontrolkami Visual Studio paska poleceń. Jeśli jednak konieczne jest skompilowanie własnego paska poleceń, upewnij się, że poprawnie go stylizuje się przy użyciu następujących nazw tokenów.

![Pasek poleceń ( redysline)](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Pasek poleceń (redline)

![Przepełnienie przycisku redline](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Przycisk Przepełnienie (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej Visual Studio implementacji paska poleceń. | ... Dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenu. |

#### <a name="command-bar-groups"></a>Grupy paska poleceń
Grupa paska poleceń składa się z powiązanego zestawu kontrolek paska poleceń i może zawierać dowolną liczbę przycisków, przycisków podziału, menu rozwijanych, pól kombi lub menu. Kolory dla tych kontrolek są regulowane przez osobne nazwy tokenów i są omawiane indywidualnie w innym miejscu tego przewodnika. Wiersz separatora służy do dzielenia grupy paska poleceń na powiązane podgrupy.

![Redline grupy paska poleceń](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Grupa paska poleceń (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w miejscach, w których potrzebny jest osadzony pasek poleceń, ale nie można użyć standardowej Visual Studio implementacji paska poleceń. | ... Dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla składników paska poleceń innych niż te, dla których określono nazwy tokenu. |

**Grupa paska poleceń: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Obramowanie | `Environment.CommandBarToolBarBorder` |
| Przeciąganie uchwytu | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony poleceń
![Ikona polecenia redline](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Ikona polecenia (redline)

![Ikona polecenia z czerwoną linią tekstu](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Ikona polecenia z tekstem (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla wszystkich przycisków, które zostaną umieszczone na pasku poleceń. | ... dla kontrolek, które mają własne nazwy tokenów. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Ikona polecenia: stan domyślny**

![Domyślna ikona polecenia](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Ikona polecenia domyślnego

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/D (dziedziczy z tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Nie dotyczy |

**Ikona polecenia: stan domyślny, wybrane**

![Domyślna, wybrana ikona polecenia](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Domyślna, wybrana ikona polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextSelected` |
| Obramowanie | `Environment.CommandBarSelectedBorder` |

**Ikona polecenia: stany aktywowania wskaźnika myszy lub fokusu**

![Ikona polecenia po najechaniu kursorem lub fokusie](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Ikona polecenia po najechaniu kursorem lub fokusie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: wybrane stany wskaźnika myszy lub fokusu**

![Ikona wybranego polecenia po najechaniu kursorem lub fokusie](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ikona wybranego polecenia po najechaniu kursorem lub fokusie

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarHoverOverSelected` |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHoverOverSelected` |
| Obramowanie | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona polecenia: stan naciśnięty**

![Ikona naciśniętego polecenia](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Ikona naciśniętego polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stan wyłączony**

![Ikona wyłączonego polecenia](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Ikona wyłączonego polecenia

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/D (dziedziczy z tła paska poleceń) |
| Pierwszy plan (tekst) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Pola kombi paska poleceń

> [!IMPORTANT]
> Pola kombi są podobne do pól rozwijanych, ale zawierają edytowalny region tekstu. Jeśli lista rozwijana nie zawiera edytowalnego obszaru tekstu, użyj tokenów kolorów dla menu [rozwijanych paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Linia ponownie pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Pole kombi paska poleceń (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych pól kombi. | ... dla wszystkich elementów, które nie mają być zawsze zgodne z interfejsem użytkownika paska poleceń. |
| ... podczas tworzenia kontrolki paska poleceń podobnej do pola kombi. | ... gdy masz dostęp do pola kombi ze stylami. |

**Pole wejściowe pola kombi paska poleceń: stan domyślny**

![Pole wejściowe pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Pole wejściowe pola kombi paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxText` |
| Obramowanie | `Environment.ComboBoxBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan domyślny**

![Przycisk rozwijany pola&#45;w dół](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | N/D (dziedziczy z tła paska poleceń) |
| Pierwszy plan (glif) | `Environment.ComboBoxGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Lista rozwijana paska poleceń](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Lista rozwijana paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxPopupBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.ComboBoxPopupBorder` |

**Pole wejściowe pola kombi paska poleceń: stan wskaźnika myszy**

![Pole wejściowe pola kombi paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Pole wejściowe pola kombi paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseOverText` |
| Obramowanie | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Przycisk listy rozwijanej na pasku poleceń: stan najechanie kursorem**

![Przycisk listy rozwijanej paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Przycisk listy rozwijanej na pasku poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseOverBackground` |
| Pierwszy plan (glif) | `Environment.ComboBoxMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan wskaźnika myszy**

 ![Lista rozwijana pola kombi paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Lista rozwijana paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (element menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wejściowe pola kombi paska poleceń: stan ukierunkowany**

![Pole wejściowe pola kombi z ukierunkowaną koncentrować się na](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Pole wejściowe pola kombi z ukierunkowaną koncentrować się na

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxFocusedText` |
| Obramowanie | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: stan ukierunkowany**

![Przycisk listy rozwijanej paska poleceń z koncentrować](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Przycisk listy rozwijanej paska poleceń z koncentrować

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedButtonBackground` |
| Pierwszy plan (glif) | `Environment.ComboBoxFocusedGlyph` |

 **Pole wejściowe pola kombi paska poleceń: stan naciśnięty**

![Pole wejściowe pola kombi na pasku poleceń naciśniętych](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Pole wejściowe pola kombi na pasku poleceń naciśniętych

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxMouseDownText` |
| Obramowanie | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan naciśnięty**

![Naciśnięty przycisk listy rozwijanej pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Naciśnięty przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseDownBackground` |
| Pierwszy plan (glif) | `Environment.ComboBoxMouseDownGlyph` |

**Pole wejściowe pola kombi paska poleceń: stan wyłączony**

![Wyłączone pole wejściowe pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Wyłączone pole wejściowe pola kombi paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ComboBoxDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxDisabledText` |
| Obramowanie | `Environment.ComboBoxDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan wyłączony**

![Wyłączony przycisk listy rozwijanej pola kombi paska poleceń](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Brak |
| Pierwszy plan (glif) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Listy rozwijane paska poleceń

> [!IMPORTANT]
> Listy rozwijane są podobne do pól kombi, ale nie mają edytowalnych regionów tekstu. Jeśli lista rozwijana zawiera edytowalny region tekstu, użyj tokenów kolorów dla pól kombi [paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Lista rozwijana paska poleceń (redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Lista rozwijana paska poleceń (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych kontrolek listy rozwijanej. | ... dla wszystkich elementów, które nie są podobne do listy rozwijanej. |
| | ... dla pól kombi lub przycisków podziału. |

**Pole wyboru listy rozwijanej paska poleceń: stan domyślny**

![Domyślne pole wyboru na pasku poleceń](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Domyślne pole wyboru na pasku poleceń

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
| Pierwszy plan (glif) | `Environment.DropDownGlyph` |

**Lista rozwijana paska poleceń: stan domyślny**

![Domyślna lista rozwijana paska poleceń](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Domyślna lista rozwijana paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownPopupBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.DropDownPopupBorder` |
| W tle | `Environment.DropShadowBackground` |

**Pole wyboru na pasku poleceń: stan najechanie kursorem**

![Pole wyboru listy rozwijanej na pasku poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Pole wyboru listy rozwijanej na pasku poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.DropDownMouseOverText` |
| Obramowanie | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: stan najechanie kursorem**

![Przycisk listy rozwijanej na pasku poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Przycisk listy rozwijanej na pasku poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseOverBackground` |
| Pierwszy plan (glif) | `Environment.DropDownMouseOverGlyph` |

**Lista rozwijana paska poleceń: stan wskaźnika myszy**

![Lista rozwijana paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Lista rozwijana paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (element menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole wyboru na pasku poleceń: stan naciśnięty**

![Wciśnięte&#45;rozwijanego pola wyboru](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Pole wyboru na pasku poleceń naciśniętych

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownMouseDownBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownMouseDownText` |
| Obramowanie | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Przycisk listy rozwijanej paska poleceń: stan naciśnięty**

![Naciśnięty przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Naciśnięty przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseDownBackground` |
| Pierwszy plan (glif) | `Environment.DropDownMouseDownGlyph` |

**Pole wyboru listy rozwijanej paska poleceń: stan wyłączony**

![Wyłączone pole wyboru listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Wyłączone pole wyboru listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DropDownDisabledBackground` |
| Pierwszy plan (tekst) | `Environment.DropDownDisabledText` |
| Obramowanie | `Environment.DropDownDisabledBorder` |
| Separator | Brak separatora |

**Przycisk listy rozwijanej paska poleceń: stan wyłączony**

![Wyłączony przycisk listy rozwijanej paska poleceń](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Wyłączony przycisk listy rozwijanej paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Przyciski podziału paska poleceń
Przyciski podziału współdzielą wiele nazw tokenów z innymi kontrolkami paska poleceń, takimi jak przyciski, menu i tekst paska poleceń. Dla wygody wszystkie niezbędne akcje i nazwy tokenów przycisków listy rozwijanej są powtarzane w tym miejscu. Listy rozwijane przycisku podziału to implementacje [menu paska poleceń](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Dzielenie przycisku na czerwono](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Przycisk podziału paska poleceń (czerwona linia)

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
| Pierwszy plan (glif) | `Environment.CommandBarSplitButtonGlyph` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: stan wskaźnika myszy**

![Przycisk podziału paska poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Przycisk podziału paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextHover` |
| Pierwszy plan (glif) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Przycisk podziału paska poleceń: stan naciśnięty**

![Naciśnięty przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Naciśnięty przycisk podziału paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.CommandBarTextMouseDown` |
| Pierwszy plan (glif) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | Nie dotyczy |

**Przycisk podziału paska poleceń: stan wyłączony**

![Wyłączony przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Wyłączony przycisk podziału paska poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (tekst) | `Environment.ComboBoxItemTextInactive` |
| Pierwszy plan (glif) | `Environment.CommandBarTextInactive` |
| Obramowanie | Nie dotyczy |
| Separator | Nie dotyczy |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Przyciski "Więcej opcji" i "Przepełnienie" paska poleceń
Przycisk "Więcej opcji" jest używany, gdy można dostosować grupę paska poleceń przez dodanie lub usunięcie powiązanych przycisków paska poleceń. Przycisk "Przepełnienie" jest wyświetlany, gdy pasek poleceń jest obcięty z powodu braku miejsca w poziomie, a po kliknięciu zostanie wyświetlone menu zawierające przyciski paska poleceń, których nie można wyświetlić. Kolory tych dwóch przycisków są kontrolowane przez ten sam zestaw nazw tokenów.

![Przycisk "Więcej opcji" na pasku poleceń (redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Przycisk "Więcej opcji" na pasku poleceń (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w przypadku niestandardowych przycisków "Więcej opcji" lub "Przepełnienie". | ... w przypadku przycisków, które nie mają podobnych funkcji jak przycisk "Więcej opcji" lub "Przepełnienie". |

**Przyciski "Więcej opcji" i "Przepełnienie" paska poleceń: stan domyślny**

![Domyślny przycisk "Więcej opcji" na pasku poleceń](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Domyślny przycisk "Więcej opcji" na pasku poleceń

![Domyślny przycisk paska poleceń "Przepełnienie"](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Domyślny przycisk paska poleceń "Przepełnienie"

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsBackground` |
| Pierwszy plan (glif) | `Environment.CommandBarOptionsGlyph` |

**Przyciski "Więcej opcji" i "Przepełnienie" paska poleceń: stan najechania kursorem**

![Przycisk "Więcej opcji" na pasku poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Przycisk "Więcej opcji" na pasku poleceń po najechaniu kursorem

![Przycisk "Przepełnienie" na pasku poleceń po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Przycisk "Przepełnienie" paska poleceń po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (glif) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Przyciski paska poleceń "Więcej opcji" i "Przepełnienie": naciśnięty stan**

![Naciśnięty przycisk "Więcej opcji" na pasku poleceń](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Naciśnięty przycisk "Więcej opcji" na pasku poleceń

![Naciśnięta przepełnienie](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Naciśnięty przycisk "Overflow" na pasku poleceń

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (glif) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentów
Nie ma potrzeby replikowania okien dokumentów, ponieważ są one udostępniane przez środowisko Visual Studio dokumentów. Możesz jednak zdecydować, że chcesz korzystać z kolorów używanych w oknach dokumentów, aby interfejs użytkownika zawsze był zgodny z tą częścią Visual Studio dokumentów.

W przypadku używania tokenów kolorów okna dokumentu należy ich używać tylko dla podobnych elementów i zawsze w parach. Jeśli tego nie zrobisz, możesz uzyskać nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frames"></a>Ramki okien dokumentów
Okna dokumentów mogą być zadokowane w idee lub przestawne jako oddzielne okno. Gdy okno dokumentu jest przestawne poza środowiskiem IDE, nadal znajduje się w dokumencie i ma tło, obramowanie, tekst i kolory kart, które są takie same jak w środowisku IDE. Jednak dokument znajduje się wewnątrz ramki, która ma własne tło, obramowanie i kolory tekstu. Gdy okna narzędzi są zadokowane w dokumencie, dziedziczą zachowanie i kolor kart z nazw tokenów okna dokumentu.

![Zadokowane okno dokumentu (redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Zadokowane okno dokumentu (redline)

![Okno dokumentu zmiennoprzecinkowego (redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Okno dokumentu zmiennoprzecinkowego (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który chcesz dopasować do okna dokumentu. | ...  dla dowolnego interfejsu użytkownika, którego nie chcesz automatycznie zmieniać, jeśli powłoka ma aktualizację motywu. |

**Zadokowane lub przestawne okno dokumentu: stan domyślny**

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Zależy od typu dokumentu |
| Pierwszy plan (tekst) | Zależy od typu dokumentu |
| Obramowanie | `Environment.ToolWindowBorder` |

**Ukierunkowana, przestawna ramka okna dokumentu: stan domyślny**

![Domyślna, skoncentrowana, przestawna ramka okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Domyślna, skoncentrowana, przestawna ramka okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrame` |
| Pierwszy plan (glif) | `Environment.RaftedWindowButtonActiveGlyph` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |
| Obramowanie (glif) | `Environment.RaftedWindowButtonActiveBorder`<br />(Ustaw przezroczystość) |

**Bez koncentracji, zmiennoprzecinkowa ramka okna dokumentu: stan domyślny**

![Domyślna bez koncentracji, przestawna ramka okna dokumentu](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Domyślna bez koncentracji, przestawna ramka okna dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (tekst) | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszy plan (glif) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |
| Obramowanie (glif) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Ustaw przezroczystość) |

**Ukierunkowana, przestawna ramka okna dokumentu: stan wskaźnika myszy**

![Ukierunkowana, przestawna ramka okna dokumentu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Ukierunkowana, przestawna ramka okna dokumentu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (glif) | `Environment.RaftedWindowButtonHoverActive` |
| Pierwszy plan (glif) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Obramowanie (glif) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Bez koncentracji, zmiennoprzecinkowa ramka okna dokumentu: stan wskaźnika myszy**

![Nienakcentowana, przestawna ramka okna dokumentu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Nienakcentowana, przestawna ramka okna dokumentu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (glif) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Pierwszy plan (glif) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Obramowanie (glif) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Ukierunkowana, przestawna ramka okna dokumentu: stan naciśnięty**

![Ukierunkowana, przestawna ramka okna dokumentu po naciśnięciu](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Ukierunkowana, przestawna ramka okna dokumentu po naciśnięciu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło (glif) | `Environment.RaftedWindowButtonDown` |
| Pierwszy plan (glif) | `Environment.RaftedWindowButtonDownGlyph` |
| Obramowanie (glif) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Karty dokumentów
Karty dokumentów znajdują się w kanale kart, aby wskazać, które dokumenty są obecnie otwarte, oraz który z nich jest aktualnie zaznaczonym lub aktywnym dokumentem. Okna narzędzi można również zadokować w kanale karty dokumentu, jeśli użytkownik je tam umieszcza. W takiej sytuacji używają tych samych kolorów kart co okna dokumentów. Jeśli tworzysz interfejs użytkownika, dla którego chcesz zawsze dopasować kolory okna dokumentu (w tym aktualizacje motywów lub jeśli są zainstalowane nowe motywy), odwołuj się do tych tokenów kolorów.

![Karty dokumentów (redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Karty dokumentów (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, w którym chcesz dopasować karty dokumentów i automatycznie pobierać aktualizacje motywu lub nowe kolory motywu. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, gdy powłoka ma aktualizację motywu. |

#### <a name="open-document-tabs"></a>Otwieranie kart dokumentów
Każdy otwarty dokument ma kartę w kanale karty dokumentu, która wyświetla jego nazwę. Dokumenty można wybrać lub otworzyć w tle, a ich karty odzwierciedlają następujące stany:

- Wybrana karta reprezentuje dokument, który jest obecnie wyświetlany w obszarze dokumentu. Wybrana karta ma obramowanie dokumentu, które rozciąga się na górną krawędź dokumentu.

- Karty tła to karty dokumentów, które nie są aktualnie wybraną kartą. Po kliknięciu stają się wybraną kartą i uzyskują wszystkie kolory tła, obramowania i tekstu z tych nazw tokenów.

![Otwieranie karty dokumentu (redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Otwieranie karty dokumentu (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowych kart dokumentów. | ... w przypadku kart tymczasowych (wersja zapoznawcza). |
| | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Wybrana, ukierunkowana karta dokumentu**

![Wybrana, ukierunkowana karta dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Wybrana, ukierunkowana karta dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabSelectedGradientTop`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.FileTabSelectedText` |
| Obramowanie | `Environment.FileTabSelectedBorder`<br />(Ustaw ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Karta wybranego dokumentu bez koncentracji na koncentracji**

![Karta wybranego dokumentu bez koncentracji na koncentracji](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Karta wybranego dokumentu bez koncentracji na koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabInactiveGradientTop`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.FileTabInactiveText` |
| Obramowanie | `Environment.FileTabInactiveBorder`<br />(Ustaw ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta Dokument w tle: stan domyślny**

![Domyślna karta dokumentu w tle](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Domyślna karta dokumentu w tle

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabBackground` |
| Pierwszy plan (tekst) | `Environment.FileTabText` |
| Obramowanie | `Environment.FileTabBorder`<br />(Ustaw ten sam kolor co tło). |

**Karta dokumentu w tle: stan wskaźnika myszy**

![Karta Dokument w tle po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Karta Dokument w tle po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabHotGradientTop`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.FileTabHotText` |
| Obramowanie | `Environment.FileTabHotBorder`<br />(Ustaw ten sam kolor co tło). |

#### <a name="preview-tab"></a>Karta Podgląd
Nazywana również kartą "tymczasowe". Karta podglądu jest wyświetlana po prawej stronie kanału karty dokumentu, gdy użytkownik kliknie element w Eksplorator rozwiązań narzędzi. Działa jako wersja zapoznawcza dokumentu, a także zapewnia użytkownikowi opcję pozostawić dokument otwarty po lewej stronie kanału karty dokumentu. W tym samym czasie można otworzyć tylko jedną otwartą kartę podglądu. Karty podglądu mają zarówno tło, jak i wybrane stany, takie jak otwarte karty, i mogą być skoncentrowane lub nieskoncentrowane w stanie aktywnym.

![Karta Podgląd (redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Karta Podgląd (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w którym tworzysz podgląd i chcesz, aby jakiś element był zgodne z bieżącym kolorem karty podglądu. | ... dla dowolnego rodzaju dokumentu lub karty, które nie są tymczasowe (wersja zapoznawcza). |
| | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Ukierunkowana, wybrana karta podglądu**

![Ukierunkowana, wybrana karta podglądu](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Ukierunkowana, wybrana karta podglądu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedActive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Ustaw ten sam kolor co tło). |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Bez koncentracji na koncentracji, wybrana karta podglądu**

![Bez koncentracji na koncentracji, wybrana karta podglądu](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Bez koncentracji na koncentracji, wybrana karta podglądu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Podgląd w tle: stan domyślny**

![Domyślna karta podglądu w tle](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Domyślna karta podglądu w tle

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalInactive` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalInactiveBorder`<br />(Ustaw na ten sam kolor co tło). |

**Karta Podgląd tła: stan wskaźnika myszy**

![Karta Podgląd tła po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Karta Podgląd tła po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalHover` |
| Pierwszy plan (tekst) | `Environment.FileTabProvisionalHoverForeground` |
| Obramowanie | `Environment.FileTabProvisionalHoverBorder`<br />(Ustaw na ten sam kolor co tło). |

#### <a name="document-overflow-button"></a>Przycisk Przepełnienie dokumentu
Przycisk przepełnienia dokumentu jest dostępny, jeśli co najmniej jeden dokument jest otwarty, niezależnie od tego, czy w bieżącej konfiguracji znajduje się spacja pionowa do dopasowania do wszystkich kart dokumentów. Menu rozwijane przepełnienia dokumentu, które jest kontrolowane przez kolory [menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) paska poleceń, wyświetla listę wszystkich otwartych dokumentów, widocznych i ukrytych, a przepełnienie zmienia się w zależności od tego, czy wszystkie otwarte dokumenty są wyświetlane w kanale karty.

![Przycisk przepełnienia dokumentu (redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Przycisk przepełnienia dokumentu (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas tworzenia niestandardowego przycisku przepełnienia dokumentu. | ... w przypadku interfejsu użytkownika, który nie jest podobny do przycisku przepełnienia. |
| | ... dla przycisków przepełniania paska poleceń. |

**Przycisk Przepełnienie dokumentu: stan domyślny**

![Domyślny przycisk przepełnienia dokumentu](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Domyślny przycisk przepełnienia dokumentu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonBackground` |
| Pierwszy plan (glif) | `Environment.DocWellOverflowButtonGlyph` |
| Obramowanie | Nie dotyczy |

**Przycisk przepełnienia dokumentu: stan wskaźnika myszy**

![Przycisk Przepełnienie dokumentu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Przycisk Przepełnienie dokumentu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Pierwszy plan (glif) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Przycisk Przepełnienie dokumentu: stan naciśnięty**

![Przycisk Przepełnienie dokumentu po naciśnięciu](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Przycisk Przepełnienie dokumentu po naciśnięciu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Pierwszy plan (glif) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Znakowanie
Visual Studio obsługuje tagowanie, które umożliwia użytkownikowi deklarowanie słów kluczowych z możliwość wyszukiwania na potrzeby śledzenia. Na przykład menedżerowie projektów i deweloperzy mogą używać Team Foundation Server (TFS) do tagów elementów roboczych. W poniższych tabelach nadajmy nazwy kolorów dla samego tagu i symbolu "zamknij ikonę", który pojawia się w stanach wskaźnika myszy i wybranych.

![Tagowanie w Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Tagowanie w Visual Studio (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla interfejsu użytkownika, który obsługuje tagowanie. | ... dla dowolnego innego typu interfejsu użytkownika. |

#### <a name="tags"></a>Tagi

**Tag: stan domyślny**

![Tag domyślny](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Tag domyślny

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.Background` |
| Pierwszy plan (tekst) | `Tag.Background` |

**Tag: stan wskaźnika myszy**

![Tagowanie po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Tagowanie po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.HoverBackground` |
| Pierwszy plan (tekst) | `Tag.HoverBackgroundText` |

**Tag: stan naciśnięty**

![Naciśnięty tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Naciśnięty tag

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.PressedBackground` |
| Pierwszy plan (tekst) | `Tag.PressedBackgroundText` |

**Tag: wybrany stan**

![Wybrany tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Wybrany tag

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.SelectedBackground` |
| Pierwszy plan (tekst) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Close ( &times; ) tag glyph

**Close ( &times; ) tag glyph: stan domyślny**

![Domyślny znacznik Close ( &times; )](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Domyślny znacznik Close ( &times; )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif) | `Tag.TagHoverGlyph` |

**Close ( &times; ) tag glyph: hover state**

![Zamknięcie ( &times; ) tagu po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Zamknięcie ( &times; ) tagu po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphHoverBackground` |
| Pierwszy plan (glif) | `Tag.TagHoverGlyphHover` |
| Obramowanie | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; ) tag glyph: pressed state**

![Glyph tagu Pressed Close &times; ()](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Glyph tagu Pressed Close &times; ()

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphPressedBackground` |
| Pierwszy plan (glif) | `Tag.TagHoverGlyphPressed` |
| Obramowanie | `Tag.TagHoverGlyphPressedBorder` |

**Wybrany tag z tagiem Zamknij ( &times; ) : stan domyślny**

![Domyślny wybrany tag z tagiem Zamknij ( &times; )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Domyślny wybrany tag z tagiem Zamknij ( &times; )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif) | `Tag.TagSelectedGlyph` |

**Wybrany tag z tagiem Zamknij ( &times; ) : stan wskaźnika myszy**

![Wybrany tag z tagiem Zamknij ( &times; ) po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Wybrany tag z tagiem Zamknij ( &times; ) po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphHoverBackground` |
| Pierwszy plan (glif) | `Tag.TagSelectedGlyphHover` |
| Obramowanie | `Tag.TagSelectedGlyphHoverBorder` |

**Wybrany tag z tagiem Zamknij ( &times; ) : stan naciśnięty**

![Wybrany, naciśnięty tag z glyphem Close ( &times; )](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Wybrany, naciśnięty tag z glyphem Close ( &times; )

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(Glyph) | `Tag.TagSelectedGlyphPressed` |
| Obramowanie | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna narzędzi
Nie ma potrzeby replikowania okien narzędzi, ponieważ są one udostępniane przez środowisko Visual Studio narzędzi. Można jednak zdecydować, że chcesz korzystać z kolorów używanych w oknach narzędzi, aby interfejs użytkownika zawsze był zgodny z tą częścią Visual Studio narzędzi.

![Okno narzędzia (redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Okno narzędzia (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w którym tworzysz interfejs użytkownika, do którego chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

### <a name="tool-window-frame"></a>Ramka okna narzędzi
Okna narzędzi w Visual Studio są używane do wielu różnych zadań i mogą istnieć w jednym z kilku różnych stanów. Jeśli okno narzędzi jest otwarte, można je przypisać do dowolnej z czterech stron obszaru dokumentu. Okna narzędzi mogą również być zmiennoprzecinkowy poza ideą IDE, co umożliwia ich zmiany położenia w dowolnym miejscu na ekranie użytkownika. Okna zmiennoprzecincze zawsze są w górnej części środowiska IDE. Ponadto okna narzędzi można zadokować jako okna dokumentów i wyświetlać jako kartę w obszarze dokumentu. Okna narzędzi, które zostały zadokowane jako okna dokumentów, mają częściowo kolor przy użyciu nazw tokenów okna dokumentu.

![Ramka okna narzędzia (czerwona linia)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Ramka okna narzędzia (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ...  w dowolnym miejscu, w którym tworzysz interfejs użytkownika, do którego chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Zadokowane okno narzędzi**

![Zadokowane okno narzędzi](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Zadokowane okno narzędzi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.ToolWindowBorder` |

**Zmiennoprzecinkowe, ukierunkowane okno narzędzi**

![Zmiennoprzecinkowe, ukierunkowane okno narzędzi](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Zmiennoprzecinkowe, ukierunkowane okno narzędzi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |

**Okno narzędzi zmiennoprzecinkowych bez koncentracji na koncentracji**

![Okno narzędzi zmiennoprzecinkowych bez koncentracji na koncentracji](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Okno narzędzi zmiennoprzecinkowych bez koncentracji na koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Okna podobne do przybornika
Przybornik jest jednym z najczęściej używanych typowych okien narzędzi w Visual Studio. Zasadniczo jest to kontrolka drzewa ze specjalnym motywem i zastosowanymi stylami.

![Okno podobne do przybornika (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Okno podobne do przybornika (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... podczas projektowania okna narzędzi, które ma być zawsze spójne z przybornikiem powłoki. | ... dla wszystkich elementów, które nie są podobne do interfejsu użytkownika przybornika, lub jeśli nie masz pewności, czy w interfejsie użytkownika występują problemy, jeśli zmienią się kolory przybornika powłoki. |

**Węzły przybornika: stan domyślny**

![Domyślny węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Domyślny węzeł nadrzędny przybornika

![Domyślny węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Domyślny węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContent`<br />(Nagłówki) |
| Tło | `Environment.ToolWindowBackground`<br />(Pojedyncze elementy lub całe okno, jeśli nie ma dostępnych kontrolek) |
| Obramowanie | Brak |
| Pierwszy plan (glif) | `Environment.ToolboxContent` |
| Pierwszy plan (tekst) | `Environment.ToolboxContent` |

**Węzły podrzędne przybornika: stan wskaźnika myszy**

![Węzeł podrzędny przybornika po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Węzeł podrzędny przybornika po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolboxContentMouseOver`<br />(Tylko pojedyncze elementy) |
| Obramowanie | Brak |
| Pierwszy plan (tekst) | `Environment.ToolboxContentMouseOver`<br />(Tylko pojedyncze elementy) |

**Wybrane węzły przybornika: stan skoncentrowany**

![Skoncentrowany, wybrany węzeł nadrzędny przybornika](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Skoncentrowany, wybrany węzeł nadrzędny przybornika

![Skoncentrowany, wybrany węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Skoncentrowany, wybrany węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |
| Obramowanie | `TreeView.FocusVisualBorder`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |
| Pierwszy plan (glif) | `TreeView.SelectedItemActive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |
| Pierwszy plan (tekst) | `TreeView.SelectedItemActive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |

**Wybrane węzły przybornika: stan bez koncentracji**

![Wybrany węzeł nadrzędny przybornika bez koncentracji](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Wybrany węzeł nadrzędny przybornika bez koncentracji

![Wybrany, nieskoncentrowany węzeł podrzędny przybornika](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Wybrany, nieskoncentrowany węzeł podrzędny przybornika

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |
| Obramowanie | Brak |
| Pierwszy plan (glif) | `TreeView.SelectedItemInactive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |
| Pierwszy plan (tekst) | `TreeView.SelectedItemInactive`<br />Z [kategorii Widok](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) drzewa |

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi
Obramowanie paska tytułu nie jest prawdziwym obramowaniem, ale grubą linią w górnej części paska tytułu. Nie ma nazwy tokenu dla stanu bez koncentracji.

![Pasek tytułu okna narzędzi (czerwona linia)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Pasek tytułu okna narzędzi (czerwona linia)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w którym tworzysz interfejs użytkownika, do którego chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Pasek tytułu z ukierunkowaną koncentrować**

![Pasek tytułu z ukierunkowaną koncentrować](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Pasek tytułu z ukierunkowaną koncentrować

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarActiveGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.TitleBarActiveText` |
| Obramowanie | `Environment.TitleBarActiveBorder`<br />(Ustaw na ten sam kolor co tło). |
| Przeciąganie uchwytu | `Environment.TitleBarDragHandleActive` |

**Pasek tytułu bez koncentracji**

![Pasek tytułu bez koncentracji](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Pasek tytułu bez koncentracji

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.TitleBarInactiveGradientBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.TitleBarInactiveText` |
| Obramowanie | Nie dotyczy |
| Przeciąganie uchwytu | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Przyciski paska tytułu okna narzędzi
![Przycisk paska tytułu (redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Przycisk paska tytułu (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... dla przycisków wyświetlanych w interfejsie użytkownika, które wykorzystują tokeny kolorów z pasków tytułu okna narzędzi. | ... dla przycisków wyświetlanych w innych lokalizacjach. |
| | ... w dowolnej kombinacji tła/pierwszego planu innej niż określona. |

**Przyciski paska tytułu z ukierunkowaną koncentrować się na: stan domyślny**

![Domyślne, ukierunkowane przyciski paska tytułu](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Domyślne, ukierunkowane przyciski paska tytułu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonActiveGlyph` |
| Obramowanie | Nie dotyczy |

**Przyciski paska tytułu bez koncentracji: stan domyślny**

![Domyślne, nieskoncentrowane przyciski paska tytułu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Domyślne, nieskoncentrowane przyciski paska tytułu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | Nie dotyczy |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonInactiveGlyph` |
| Obramowanie | Nie dotyczy |

**Przyciski paska tytułu z ukierunkowaną koncentrować się na: stan wskaźnika myszy**

![Przyciski paska tytułu z ukierunkowaną koncentrować się na najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Przyciski paska tytułu z ukierunkowaną koncentrować się na najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverActive` |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverActiveBorder` |

**Przyciski paska tytułu bez koncentracji koncentracji: stan wskaźnika myszy**

![Przyciski paska tytułu bez koncentracji na najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Przyciski paska tytułu bez koncentracji na najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverInactive` |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Przyciski paska tytułu z ukierunkowaną koncentrować się na: stan naciśnięty**

![Przyciski paska tytułu z ukierunkowaną koncentrować się na naciśnięciu](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Przyciski paska tytułu z ukierunkowaną koncentrować się na naciśnięciu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

**Przyciski paska tytułu bez koncentracji koncentracji: naciśnięty stan**

![Przyciski paska tytułu bez koncentracji na naciśnięciu](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Przyciski paska tytułu bez koncentracji na naciśnięciu

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszy plan (glif) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna narzędzi
![Karta okna narzędzi (redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Karta okna narzędzi (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu, w którym tworzysz interfejs użytkownika, do którego chcesz dopasować okna narzędzi. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Wybrana, ukierunkowana karta okna narzędzi**

![Wybrana, ukierunkowana karta okna narzędzi](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Wybrana, ukierunkowana karta okna narzędzi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedActiveText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw ten sam kolor co tło). |

**Karta wybranego, nieskoncentrowego okna narzędzi**

![Karta wybranego, nieskoncentrowego okna narzędzi](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Karta wybranego, nieskoncentrowego okna narzędzi

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabSelectedText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustaw ten sam kolor co tło). |

**Karta okna narzędzia w tle: stan domyślny**

![Domyślna karta okna narzędzia w tle](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Domyślna karta okna narzędzia w tle

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient zatrzymuje się na tę samą wartość koloru w Visual Studio 2013). |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabText` |
| Obramowanie | `Environment.ToolWindowTabBorder` |

**Karta okna narzędzia w tle: stan wskaźnika myszy**

![Karta okna narzędzia tła po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Karta okna narzędzia tła po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient zatrzymuje się na tę samą wartość koloru w Visual Studio 2013). |
| Pierwszy plan (tekst) | `Environment.ToolWindowTabMouseOverText` |
| Obramowanie | `Environment.ToolWindowTabMouseOverBorder`<br />(Ustaw ten sam kolor co tło). |

### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart

![Automatyczne ukrywanie kart (redline)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Automatyczne ukrywanie kart (redline)

| Używać... | Nie używaj ... |
| --- | --- |
| ... w dowolnym miejscu tworzenia interfejsu użytkownika, który ma odpowiadać automatycznie ukrytym kartom okna narzędzi. | ... dla dowolnego interfejsu użytkownika, którego nie chcesz zmieniać automatycznie, jeśli powłoka ma aktualizację motywu. |

**Automatyczne ukrywanie kart: stan domyślny**

![Domyślna karta automatycznego ukrywania](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Domyślna karta automatycznego ukrywania

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.AutoHideTabText` |
| Obramowanie | `Environment.AutoHideTabBorder` |

**Automatyczne ukrywanie kart: stan wskaźnika myszy**

![Karta Automatycznego ukrywania po najechaniu kursorem](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Karta Automatycznego ukrywania po najechaniu kursorem

| Element | Nazwa tokenu: Category.color |
| --- | --- |
| Tło | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Gradient zatrzymuje się dla tego tokenu, który nie jest używany w interfejsie użytkownika z tematami). |
| Pierwszy plan (tekst) | `Environment.AutoHideTabMouseOverText` |
| Obramowanie | `Environment.AutoHideTabMouseOverBorder` |
