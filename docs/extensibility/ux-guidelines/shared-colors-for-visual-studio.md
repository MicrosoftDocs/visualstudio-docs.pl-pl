---
title: Udostępnione kolory dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f31912d5528c38374aafd1212767bfb850a8b976
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723581"
---
# <a name="shared-colors-for-visual-studio"></a>Udostępnione kolory dla programu Visual Studio
Podczas projektowania interfejsu użytkownika, który używa wspólnych elementów powłoki programu Visual Studio lub chcesz, aby Twoje element interfejsu, aby były zgodne z podobne funkcje, umożliwia już istniejącymi nazwami tokenu w plikach definicji pakietu wybierz i przypisania kolorów. Gwarantuje to, że Twój interfejs użytkownika pozostaje zgodny z całego środowiska programu Visual Studio i że jest aktualizowana automatycznie po motywy są dodawane lub aktualizowane.

W tym artykule opisano typowe elementy interfejsu użytkownika i token nazwy które używają, które można odwoływać się podczas kompilowania z podobnym interfejsem użytkownika. Dla określonych informacji dotyczących tych kolorów tokeny dostępu, zobacz [usługa VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Upewnij się, że prawidłowo używać nazw tokenu:

-   **Użyj tokenu nazw na podstawie funkcji, nie na samego koloru.** Typowe udostępnione kolory są skojarzone z elementami określonego interfejsu i są przeznaczone wyłącznie do użytku takie same lub podobne funkcje. Na przykład nie używaj ponownie plików kolor po naciśnięciu kombi dla Animacja postępu rotowania tylko dlatego, jak kolor. Funkcje pola kombi i animacji są różne, a Jeśli kolor skojarzony z zmiany pola kombi, może nie być odpowiedni kolor w odniesieniu do danego elementu animacji. Spójnego używania koloru pomaga w poznaniu użytkowników i uniknąć pomyłek.

-   **Użyj kolorów tła i tekstu w poprawnej kombinacji.** Kolory tła, które są przeznaczone do użycia z tekstem będzie miał kolor tekstu. Nie używaj kolorów tekstu innego niż został określony dla w tle. Jeśli nie ma kolor skojarzony tekst, nie należy używać tego kolor tła dla dowolnego powierzchni, w którym oczekujesz, że do wyświetlania tekstu. Inne kombinacje kolorów tekstu i tła może prowadzić do interfejsu nie można go odczytać.

-   **Użyj kolorów kontrolki, które są odpowiednie dla ich lokalizacji.** W określonych stanach niektóre formanty programu Visual Studio nie ma osobnych obramowanie i kolory tła. Zamiast tego przejmą ich te kolory z powierzchni spodem. Upewnij się, zawsze używaj tokenów nazwy, które są odpowiednie dla lokalizacji, w którym umieszcza się kontrolka.

> [!IMPORTANT]
> Nie używaj tokenów w kategorii "Stronę startową" lub "Jabłecznik."

## <a name="common-shared-controls"></a>Typowe kontrolki udostępnionego

Gdy używasz standardowego paska poleceń programu Visual Studio w Twojej funkcji, będziesz mieć dostęp do kontrolek powłoki ze stylem. Nie jest to zalecane szablonu re tych wspólnych formantów. Jednak jeśli potrzebujesz do tworzenia paska poleceń niestandardowych, może być konieczne do tworzenia kontrolek niestandardowych również. W takim przypadku upewnij się, że Użyj poprawne nazwy tokenu dla każdego z następujących formantów interfejsu użytkownika jest zgodne z pozostałą częścią programu Visual Studio.

### <a name="button-controls"></a>formanty przycisków

![Kontrolka przycisku poprawek](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku przycisków w źródle dokumentu, którą chcesz zintegrować z kompozycji programu Visual Studio (światło, ciemny, niebieski lub kompozycję Duży kontrast systemu). | ... dla przycisków, które będą wyświetlane na tle niestandardowego, który nie jest częścią motywu programu Visual Studio. |

**Przycisku: standardowa stanu**

![Przycisk standardowy](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Przycisk standardowy

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.Button` |
| Obramowanie przycisku | `CommonControls.ButtonBorder` |

**Przycisk: stan domyślny**

![Przycisk domyślny](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Przycisk domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDefault` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDefault` |

**Przycisk: wyłączona**

![Przycisk wyłączone](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Przycisk wyłączone

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonDisabled` |
| Obramowanie przycisku | `CommonControls.ButtonBorderDisabled` |

**Przycisk: stan aktywowanego**

![Przycisk po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Przycisk po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonHover` |
| Obramowanie przycisku | `CommonControls.ButtonBorderHover` |

**Przycisku: stan naciśnięcia**

![Po naciśnięciu przycisku](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Po naciśnięciu przycisku

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonPressed` |
| Obramowanie przycisku | `CommonControls.ButtonBorderPressed` |

**Przycisk: stan wąsko zdefiniowany**

![Przycisk ukierunkowanych](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Przycisk fokusem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Przycisk | `CommonControls.ButtonFocused` |
| Obramowanie przycisku | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Formanty pól wyboru
![Pole wyboru (poprawek)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Pole wyboru (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w przypadku kontrolek pole wyboru, również znajdujących się w dokumencie. | ... dla wszelkich elementów interfejsu użytkownika nie jest to kontrolka pola wyboru. |

**Pole wyboru: domyślny stan**

![Pole wyboru](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Pole wyboru domyślnego

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackground` |
| Obramowanie | `CommonControls.CheckBoxBorder` |
| Tekst | `CommonControls.CheckBoxText` |
| Symbol | `CommonControls.CheckBoxGlyph` |

**Pole wyboru: wyłączone**

![Wyłączone pole wyboru](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Wyłączone pole wyboru

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.CheckBoxBorderDisabled` |
| Tekst | `CommonControls.CheckBoxTextDisabled` |
| Symbol | `CommonControls.CheckBoxGlyphDisabled` |

**Pole wyboru: Umieść kursor stanu**

 ![Pole wyboru po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Pole wyboru po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundHover` |
| Obramowanie | `CommonControls.CheckBoxBorderHover` |
| Tekst | `CommonControls.CheckBoxTextHover` |
| Symbol | `CommonControls.CheckBoxGlyphHover` |

**Pole wyboru: naciśnięty stanu**

![Po naciśnięciu pola wyboru](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Po naciśnięciu pola wyboru

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Obramowanie | `CommonControls.CheckBoxBorderPressed` |
| Tekst | `CommonControls.CheckBoxTextPressed` |
| Symbol | `CommonControls.CheckBoxGlyphPressed` |

**Pole wyboru: skupia się stan**

![Pole wyboru ukierunkowanych](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Pole wyboru fokusem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundFocused` |
| Obramowanie | `CommonControls.CheckBoxBorderFocused` |
| Tekst | `CommonControls.CheckBoxTextFocused` |
| Symbol | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listy rozwijane i pole kombi pola
![Pole kombi down/upuszczania (poprawek)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Pole kombi down/upuszczania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... list rozwijanych i pole kombi pola w dokumencie dobrze. | ... dla żadnych interfejsów użytkownika, którego nie ma listy rozwijanej lub pola kombi. |
| | ... dla paska poleceń [list rozwijanych](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) lub [pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listy rozwijane i pole kombi pola: domyślny stan**

![Domyślne listy — dół/kombi](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Domyślne listy — dół/kombi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackground` |
| Obramowanie | `CommonControls.ComboBoxBorder` |
| Tekst | `CommonControls.ComboBoxText` |
| Separator | `CommonControls.ComboBoxSeparator` |
| Symbol | `CommonControls.ComboBoxGlyph` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackground` |

**Listy rozwijane i pole kombi pola: wyłączone**

![Wyłączone pole listy — dół/kombi](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Wyłączone pole listy — dół/kombi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundDisabled` |
| Obramowanie | `CommonControls.ComboBoxBorderDisabled` |
| Tekst | `CommonControls.ComboBoxTextDisabled` |
| Separator | `CommonControls.ComboBoxSeparatorDisabled` |
| Symbol | `CommonControls.ComboBoxGlyphDisabled` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listy rozwijane i pole kombi pola: Umieść kursor stanu**

![Pola listy — dół/kombi po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Pola listy — dół/kombi po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundHover` |
| Obramowanie | `CommonControls.ComboBoxBorderHover` |
| Tekst | `CommonControls.ComboBoxTextHover` |
| Separator | `CommonControls.ComboBoxSeparatorHover` |
| Symbol | `CommonControls.ComboBoxGlyphHover` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listy rozwijane i pole kombi pola: naciśnięty stanu**

![Naciśnięciu pola kombi — dół/upuszczania](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Po naciśnięciu pola listy — dół/kombi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundPressed` |
| Obramowanie | `CommonControls.ComboBoxBorderPressed` |
| Tekst | `CommonControls.ComboBoxTextPressed` |
| Separator | `CommonControls.ComboBoxSeparatorPressed` |
| Symbol | `CommonControls.ComboBoxGlyphPressed` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Listy rozwijane i pole kombi pola widoku elementu listy: naciśnięty stanu**

 ![Listy — dół/kombi naciśnięty widoku elementu listy](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Listy — dół/kombi naciśnięty widoku elementu listy

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Tekst elementu | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Tło w tle | `CommonControls.ComboBoxListBackgroundShadow` |

**Listy rozwijane i pole kombi pola: skupia się stan**

![Pola listy — dół/kombi z fokusem](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Pola listy — dół/kombi z fokusem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.ComboBoxBackgroundFocused` |
| Obramowanie | `CommonControls.ComboBoxBorderFocused` |
| Tekst | `CommonControls.ComboBoxTextFocused` |
| Separator | `CommonControls.ComboBoxSeparatorFocused` |
| Symbol | `CommonControls.ComboBoxGlyphFocused` |
| Tło glifów | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listy rozwijane i pole kombi pola: wybór wprowadzania tekstu**

![Wybór wprowadzania tekstu pola kombi — dół/upuszczania](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Wybór danych wejściowych tekst pola kombi — dół/upuszczania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Wyróżnij | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Formanty danych tabelarycznych (siatki)
Formanty danych tabelarycznych, znany także jako formantach siatki są wspólnych formantów dla programu Visual Studio, który może służyć do prezentowania dużych ilości danych w wielu kolumnach. Formanty standardowe dane tabelaryczne znajdują się w wielu miejscach w programie Visual Studio: Lista błędów okna narzędzia, raporty funkcji IntelliTrace i widok sterty w pamięci, między innymi. Zawsze używaj kontrolek standardowych danych tabelarycznych, pod warunkiem. W sporadycznych przypadkach możesz utracić dostęp do formantów standardowych danych tabelarycznych. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika jest zgodne z innymi formantami danych tabelarycznych w programie Visual Studio.

![Formant siatki/danych tabelarycznych (poprawek)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Formant siatki/danych tabelarycznych (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla tabelarycznych lub kontrolki siatki. | ... dla wszelkich elementów interfejsu użytkownika, który nie jest formantem tabelarycznych lub siatkę. |

#### <a name="column-headers"></a>Nagłówki kolumn
Nagłówki kolumn składają się z tło, obramowanie, tekst tytułu i opcjonalnie symbol zwykle używany podczas siatki są posortowane według tej kolumny.

**Nagłówek kolumny: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Header.Default` |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Pierwszego planu (symbol) | `Header.Glyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: Umieść kursor stanu**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Header.MouseOver` |
| Pierwszego planu (tekst) | `Environment.CommandBarTextHover` |
| Pierwszego planu (symbol) | `Header.MouseOverGlyph` |
| Obramowanie | `Header.SeparatorLine` |

**Nagłówek kolumny: naciśnięty stanu**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `CommonControls.CheckBoxBackgroundPressed` |
| Pierwszego planu (tekst) | `CommonControls.CheckBoxBorderPressed` |
| Pierwszego planu (symbol) | `CommonControls.CheckBoxTextPressed` |
| Obramowanie | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementy widoku listy
 Elementy widoku listy składają się z tła i jego zawartość. Zawartość może być tekst i/lub ikonę.

**Wyświetl elementy listy: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Przezroczyste |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Wyświetl elementy listy: stanu aktywnego**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemActiveText` |
| Obramowanie | Brak |

**Wyświetl elementy listy: stan nieaktywny**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemInactiveText` |
| Obramowanie | Brak |

### <a name="ui-text"></a>Tekst interfejsu użytkownika

#### <a name="instructional-text"></a>Tekst
Tekst zawiera wyraźną wyjaśnienie głównym, co można zrobić na stronie okna dialogowego lub dokumentu.

![Domyślny tekst](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Tekst domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Tekst pomocniczy
Na stronach dokumentu z dużą liczbą tekstu i formantów instruktażowy tekst używa wartości inny kolor. Pomaga to obejmują informacje, które są najbardziej istotne i przyczynić gęstość elementów interfejsu użytkownika. (Zobacz też poniżej sekcji dotyczącej tekst wskazówki.)

![Tekst pomocniczy](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Tekst pomocniczy

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Tekst wskazówki
Tekst wskazówki wyświetlany w kontrolce pusty, poniżej kontrolki lub powierzchni pusty dokument, aby pokazać mu, co należy zrobić dalej. Za pomocą tekst wskazówki tła okna lub formant.

**Domyślny tekst wskazówki**

![Domyślny tekst wskazówki](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Domyślny tekst wskazówki

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.ControlEditHintText` |

**Tekst wskazówki wymagane**

![Wymagany tekst wskazówki](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Tekst wskazówki wymagane

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.ControlRequiredHintText` |
| Tło | `Environment.ControlRequiredBackground` |

**Tekst kontrolki pola wyszukiwania**

> Zobacz [pola wyszukiwania](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) innych tokenów kolor związane z kontrolka wyszukiwania.

![Wyszukaj tekst kontrolki pola](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Tekst kontrolki pola wyszukiwania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Hiperlink jest jeden formant, który nie ma parę tła/na pierwszym planie. We wszystkich przypadkach należy użyć hiperłącze kolor pierwszego planu, który pojawi się prawidłowo na ciemny, biały i szary tła. Jeśli token kolorów nie jest używany do kontrolki hiperlinku, zobaczysz domyślnego systemu koloru "naciśnięty", który czerwono. To sygnał, że kontrolka nie jest przy użyciu tokenu kolor odpowiednie środowisko.

![Hiperlink (poprawek)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />Hiperlink (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... kiedy należy utworzyć niestandardowy hiperlink. | ... dla wszystkich elementów, które nie są hiperłącze. |

**Hiperłącze: stan domyślny**

![Domyślnego hiperlinku](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Domyślnego hiperlinku

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.PanelHyperlink` |

**Hiperłącze: stan aktywowanego**

![Hiperłącza po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Hiperłącza po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.PanelHyperlinkHover` |

**Hiperłącze: stan naciśnięcia**

![Po naciśnięciu hiperłącze](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Po naciśnięciu hiperłącza

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.PanelHyperlinkPressed` |

**Hiperłącze: stan wyłączenia**

![Wyłączone hiperłącze](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Hiperłącze wyłączone

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Infobars są używane do Podaj więcej informacji na temat danego kontekstu i zawsze pojawiają się w górnej części okna dokumentu lub okna narzędzi.

![Informacyjny (poprawek)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Informacyjny (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowego infobars. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska informacyjnego. |

**Pasek informacyjny: stan domyślny**

![Domyślnie pasek informacyjny](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Domyślne informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.InfoBarBackground` |
| Pierwszego planu (tekst) | `InfoBar.InfoBar` |
| Obramowanie | `InfoBar.InfoBarBorder` |

**Zamknij pasek informacyjny (&times;) przycisku: domyślny stan**

![Zamknij pasek informacyjny domyślne (&times;) przycisk](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Zamknij pasek informacyjny domyślne (&times;) przycisku

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.CloseButton` |
| Obramowanie | `InfoBar.CloseButtonBorder` |
| Symbol | `InfoBar.CloseButtonGlyph` |

**Zamknij pasek informacyjny (&times;) przycisku: Umieść kursor stanu**

![Zamknij pasek informacyjny (&times;) przycisku po umieszczeniu na](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Zamknij pasek informacyjny (&times;) przycisku po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.CloseButtonHover` |
| Obramowanie | `InfoBar.CloseButtonHoverBorder` |
| Symbol | `InfoBar.CloseButtonHoverGlyph` |

**Zamknij pasek informacyjny (&times;) przycisku: naciśnięty stanu**

![Naciśnięto Zamknij pasek informacyjny (&times;) przycisk](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Naciśnięto Zamknij pasek informacyjny (&times;) przycisku

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.CloseButtonDown` |
| Obramowanie | `InfoBar.CloseButtonDownBorder` |
| Symbol | `InfoBar.CloseButtonDownGlyph` |

**Przycisk hiperłącza informacyjny: domyślny stan**

![Przycisk hiperłącze informacyjnym domyślny](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny przycisk hiperłącze pasek informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `InfoBar.Hyperlink` |

**Przycisk hiperłącza informacyjny: Umieść kursor stanu**

![Przycisk hiperłącza informacyjny po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Przycisk hiperłącza informacyjny po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreślenie) |

**Przycisk hiperłącza informacyjny: naciśnięty stanu**

![Przycisk hiperłącza po naciśnięciu informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Przycisk hiperłącza po naciśnięciu pasek informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreślenie) |

**Hiperłącze wbudowany pasek informacyjny (w zdaniu): domyślny stan**

![Domyślny wbudowany pasek informacyjny hiperłącze przycisk](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Domyślny wbudowany pasek informacyjny hiperłącze przycisk

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `InfoBar.Hyperlink` |

**Hiperłącze wbudowany pasek informacyjny (w zdaniu): Umieść kursor stanu**

![Przycisk hiperłącza wbudowany pasek informacyjny po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Przycisk hiperłącza wbudowany pasek informacyjny po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Infobar.HyperlinkMouseOver`<br />(Z podkreślenie) |

**Hiperłącze wbudowany pasek informacyjny (w zdaniu): naciśnięty stanu**

![Przycisk hiperłącza wbudowany pasek informacyjny po naciśnięciu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Naciśnięty przycisk hiperłącza wbudowany pasek informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Infobar.HyperlinkMouseDown`<br />(Z podkreślenie) |

**Przycisk paska informacyjnego: domyślny stan**

![Domyślny przycisk paska informacyjnego](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Przycisk paska informacyjnego domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.Button` |
| Pierwszego planu (tekst) | `InfoBar.Button` |
| Obramowanie | `InfoBar.ButtonBorder` |

**Przycisk paska informacyjnego: Umieść kursor stanu**

![Przycisk paska informacyjnego po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Przycisk paska informacyjnego po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseOver` |
| Pierwszego planu (tekst) | `InfoBar.ButtonMouseOver` |
| Obramowanie | `InfoBar.ButtonMouseOverBorder` |

**Przycisk paska informacyjnego: naciśnięty stanu**

![Informacyjny po naciśnięciu przycisku](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Informacyjny po naciśnięciu przycisku

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.ButtonMouseDown` |
| Pierwszego planu (tekst) | `InfoBar.ButtonMouseDown` |
| Obramowanie | `InfoBar.ButtonMouseDownBorder` |

**Przycisk paska informacyjnego: wyłączone**

![Przycisk wyłączone informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Przycisk wyłączone pasek informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.ButtonDisabled` |
| Pierwszego planu (tekst) | `InfoBar.ButtonDisabled` |
| Obramowanie | `InfoBar.ButtonDisabledBorder` |

**Przycisk paska informacyjnego: skupia się stan**

![Przycisk ukierunkowanych informacyjnym](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Przycisk ukierunkowanych pasek informacyjny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `InfoBar.ButtonFocus` |
| Pierwszego planu (tekst) | `InfoBar.ButtonFocus` |
| Obramowanie | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania mają różne przez środowisko Visual Studio i nie będzie już konieczne, można zastosować motywu. Jednak można zdecydować, czy chcesz korzystać kolorów używanych na paski przewijania, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

![Pasek przewijania (poprawek)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Pasek przewijania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia interfejsu użytkownika, której chcesz dopasować pasków przewijania w programie Visual Studio. | dla wszystkich elementów, nie chcesz, aby zawsze być zgodna z... interfejsu użytkownika — paska przewijania. |

**Pasek przewijania: domyślny stan**

![Pasek przewijania domyślne](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Domyślne paska przewijania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszego planu (przycisku przewijania) | `Environment.ScrollBarThumbBackground` |

**Pasek przewijania: Umieść kursor stanu**

![Pasek przewijania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Pasek przewijania po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszego planu (przycisku przewijania) | `Environment.ScrollBarThumbMouseOverBackground` |

*Pasek przewijania: naciśnięty stanu**

![Pasek przewijania po naciśnięciu](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Naciśnięto paska przewijania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pasek przewijania | `Environment.ScrollBarBackground` |
| Pierwszego planu (przycisku przewijania) | `Environment.ScrollBarThumbPressedBackground` |

**Paska strzałki przewijania: domyślny stan**

![Strzałki paska przewijania domyślne](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Strzałki paska przewijania domyślne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowBackground`<br />(Ustawione na ten sam kolor jak pasek przewijania). |
| Pierwszego planu (symbol) | `Environment.ScrollBarArrowGlyph` |

**Paska strzałki przewijania: Umieść kursor stanu**

![Przewiń w pasku strzałkę po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Strzałki paska przewijania po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowMouseOverBackground`<br />(Ustawione na ten sam kolor jak pasek przewijania). |
| Pierwszego planu (symbol) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Paska strzałki przewijania: naciśnięty stanu**

![Strzałki paska przewijania po naciśnięciu](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Kliknięciu strzałki paska przewijania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ScrollBarArrowPressedBackground`<br />(Ustawione na ten sam kolor jak pasek przewijania). |
| Pierwszego planu (symbol) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Pola wyszukiwania
Możliwe, używaj wspólnej kontroli wyszukiwania oferowanych przez środowisko Visual Studio. Kolory pole wyszukiwania znajdują się w kategorii "SearchControl" **ShellColors.pkgdef** pliku, który zawiera token nazwy pola wejściowego, przycisk akcji, przycisk listy rozwijanej i menu rozwijanego.

Pole wyszukiwania może być jednym z kilku Państw, z których niektóre są wzajemnie wykluczających się:

-   "Skupia się" lub "po przeniesieniu fokusu" odnosi się do czy kursor znajduje się w polu tekstowym.

-   "Active" lub "nieaktywne" odnosi się do tego, czy użytkownik wprowadził zapytania wyszukiwania w polu tekstowym.

-   "Aktywowaniu" oznacza, że użytkownik ma moused w polu wyszukiwania za pomocą myszy (ten stan zastępuje inne stany).

-   "Wyłączone" oznacza, że funkcja wyszukiwania jest wyłączone dla bieżącego kontekstu.

![Pole wyszukiwania (poprawek)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Pole wyszukiwania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania pole wyszukiwania niestandardowego. | ... dla wszystkich elementów, który nie jest pole wyszukiwania. |
| | ... dla wszystkich elementów, które nie chcesz zawsze odpowiada wyszukiwaniu polu interfejsu użytkownika. |

**Koncentruje się pole wejściowe wyszukiwania**

![Pole wejściowe wyszukiwania ukierunkowanych](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Koncentruje się pole wejściowe wyszukiwania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.FocusedBackground` |
| Pierwszego planu (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | `SearchControl.FocusedBorder` |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Pole wejściowe wyszukiwania po przeniesieniu fokusu, aktywne**

![Po przeniesieniu fokusu pole wejściowe wyszukiwania](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Pole wejściowe wyszukiwania po przeniesieniu fokusu, aktywne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.SearchActiveBackground` |
| Pierwszego planu (tekst) | `SearchControl.SearchActiveBackground` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Pole wejściowe wyszukiwania po przeniesieniu fokusu, nieaktywne**

![Pole wejściowe wyszukiwania po przeniesieniu fokusu, nieaktywne](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Pole wejściowe wyszukiwania po przeniesieniu fokusu, nieaktywne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.Unfocused` |
| Pierwszego planu (tekst) | `SearchControl.Unfocused` |
| Obramowanie | `SearchControl.UnfocusedBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Pole wejściowe podświetlony wyszukiwany (tylko tekst)**

![Pole wejściowe podświetlony wyszukiwany](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Podświetlony wyszukiwany pola wejściowego

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.Selection` |
| Pierwszego planu (tekst) | `SearchControl.FocusedBackground` |
| Obramowanie | Brak |
| Separator | `SearchControl.FocusedDropDownSeparator` |

**Pole wejściowe wyszukiwania wyłączone**

![Pole wejściowe wyszukiwania wyłączone](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Pole wejściowe wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.Disabled` |
| Pierwszego planu (tekst) | `SearchControl.Disabled` |
| Obramowanie | `SearchControl.DisabledBorder` |
| Separator | `SearchControl.DropDownSeparator` |

**Przycisk akcji ukierunkowane wyszukiwanie**

![Fokus przycisku akcji Wyszukaj](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Przycisk akcji ukierunkowane wyszukiwanie

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszego planu (Zatrzymaj symbol) | `SearchControl.StopGlyph` |
| Pierwszego planu (Wyczyść symbol) | `SearchControl.ClearGlyph` |
| Obramowanie | Brak |

**Przycisk akcji wyszukiwania po przeniesieniu fokusu**

![Przycisk akcji po przeniesieniu fokusu wyszukiwania](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Przycisk akcji wyszukiwania po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol wyszukiwania) | `SearchControl.SearchGlyph` |
| Pierwszego planu (Zatrzymaj symbol) | `SearchControl.StopGlyph` |
| Pierwszego planu (Wyczyść symbol) | `SearchControl.ClearGlyph` |
| Obramowanie | Brak |

**Naciśnięty przycisk Akcja wyszukiwania**

![Przycisk akcji po naciśnięciu wyszukiwania](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Naciśnięty przycisk Akcja wyszukiwania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.ActionButtonMouseDown` |
| Pierwszego planu (symbol) | `SearchControl.ActionButtonMouseDownGlyph` |
| Obramowanie | `SearchControl.ActionButtonMouseDownBorder` |

**Przycisk akcji wyszukiwania wyłączone**

![Wyszukiwanie akcji przycisk wyłączone](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Przycisk akcji wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `SearchControl.ActionButtonDisabledGlyph` |
| Obramowanie | Brak |

**Przycisk listy rozwijanej ukierunkowane wyszukiwanie**

![Przycisk listy rozwijanej wyszukiwania ukierunkowanych](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Przycisk listy rozwijanej ukierunkowane wyszukiwanie

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.FocusedDropDownButton` |
| Pierwszego planu (symbol) | `SearchControl.FocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.FocusedDropDownButtonBorder` |

**Przycisk listy rozwijanej wyszukiwania po przeniesieniu fokusu**

![Przycisk listy rozwijanej wyszukiwania po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Przycisk listy rozwijanej wyszukiwania po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.UnfocusedDropDownButton` |
| Pierwszego planu (symbol) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Obramowanie | `SearchControl.UnfocusedDropDownButtonBorder` |

**Naciśnięty przycisk listy rozwijanej wyszukiwania**

![Wyszukiwanie po naciśnięciu przycisku rozwijanego](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Naciśnięty przycisk listy rozwijanej wyszukiwania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.MouseDownDropDownButton` |
| Pierwszego planu (symbol) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Obramowanie | `SearchControl.MouseDownDropDownButtonBorder` |

**Przycisk listy rozwijanej wyszukiwania wyłączone**

![Przycisk listy rozwijanej wyszukiwania wyłączone](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Przycisk listy rozwijanej wyszukiwania wyłączone

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `SearchControl.DisabledDownButtonGlyph` |
| Obramowanie | Brak |

#### <a name="search-drop-down-lists"></a>Listy rozwijane wyszukiwania
Menu rozwijane pole wyszukiwania ma być nieco bardziej skomplikowane niż inne menu rozwijane w programie Visual Studio. "Sugerowane wyszukiwania" i "Opcje wyszukiwania" sekcje mogą być wyświetlane osobno lub razem w menu i każdej z nich jest kolorowe oddzielnie. Wiersz również oddziela te dwie sekcje, gdy pojawiają się ze sobą i obramowanie wokół menu rozwijane całego.

![Listy rozwijanej wyszukiwania (poprawek)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Listy rozwijanej wyszukiwania (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia listy rozwijanej wyszukiwania niestandardowego. | ... dla listy rozwijane, które pojawiają się w innych kontekstach. |
| ... poprawne nazwy tokenu dla składników poprawnej listy. | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Elementy listy rozwijanej wyszukiwania**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Obramowanie | `SearchControl.PopupBorder` |
| Separator | `SearchControl.PopupSectionHeaderSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Zalecane wyszukiwania: domyślny stan**

![Domyślne wyszukiwanie sugerowane](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Domyślne sugerowane wyszukiwania

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `SearchControl.PopupItemText` |

**Zalecane wyszukiwania: Umieść kursor stanu**

![Zalecane wyszukiwania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Sugerowane wyszukiwania po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `SearchControl.PopupMouseOverItemText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: domyślny stan**

![Pole wyboru wyszukiwania](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Domyślne opcje wyszukiwania (pole)

![Opcje wyszukiwania](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Domyślne opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (pole tekstowe) | `SearchControl.PopupCheckboxText` |
| Pierwszego planu (tekst łącza) | `SearchControl.PopupButtonText` |
| Tło nagłówka | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst nagłówka) | `SearchControl.PopupSectionHeaderText` |

**Opcje wyszukiwania: Umieść kursor stanu**

![Opcje (pole) wyszukiwania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Opcje wyszukiwania (pole) po najechaniu wskaźnikiem

![Opcje (link) wyszukiwania po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Opcje wyszukiwania (link) po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (pole tekstowe) | `SearchControl.PopupCheckboxMouseDownText` |
| Pierwszego planu (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |
| Obramowanie | `SearchControl.PopupControlMouseOverBorder` |

**Opcje wyszukiwania: naciśnięty stanu**

![Naciśnięto opcje wyszukiwania (pole)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Naciśnięto opcje wyszukiwania (pole)

![Naciśnięto opcje wyszukiwania (link)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Naciśnięto opcje wyszukiwania (link)

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło pola wyboru | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (pole tekstowe) | `SearchControl.PopupCheckboxMouseDownText` |
| Tło łącza | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst łącza) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Widok drzewa
Kilkoma oknami narzędzi, w tym Eksploratora rozwiązań, Eksploratora serwera i widoku klasy implementuje hierarchiczne schematu organizacyjnego którego kolory są kontrolowane przez nazw kolorów w `TreeView` kategorii. Wszystkie elementy w widoku drzewa mają kolor tła i tekstu. Elementy, które zostały zagnieżdżone elementy podrzędne mają także symbole, które wskazują, czy element jest rozwijane czy zwijane.

![Widok drzewa (poprawek)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Widok drzewa (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym muszą implementować hierarchiczny widok organizacji. | ... dla wszystkich elementów, które nie są podobne do widoku drzewa. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Element widoku drzewa: domyślny stan**

![Element widoku drzewa domyślny](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Element widoku drzewa domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszego planu (tekst) | `TreeView.Background` |
| Pierwszego planu (symbol) | `TreeView.Glyph` |
| Obramowanie | Brak |

**Element widoku drzewa: Umieść kursor stanu**

![Element widoku drzewa po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Element widoku drzewa po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.Background` |
| Pierwszego planu (tekst) | `TreeView.Background` |
| Pierwszego planu (symbol) | `TreeView.GlyphMouseOver` |
| Obramowanie | Brak |

**Element widoku drzewa: przeciągnij kursor nad stanu**

![Drzewo elementu widoku w sprawie przeciągnij za pośrednictwem](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Przeciągnij element widoku drzewa w

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.DragOverItem` |
| Pierwszego planu (tekst) | `TreeView.DragOverItem` |
| Pierwszego planu (symbol) | `TreeView.DragOverItemGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: zaznaczone, skupia się stan**

![Zaznaczone, a podczas projektowania położono elementu widoku drzewa](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Element widoku drzewa wybranego i skupionego projektu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemActive` |
| Pierwszego planu (symbol) | `TreeView.SelectedItemActiveGlyph` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan zaznaczona, po przeniesieniu fokusu**

![Element widoku drzewa wybranych i po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Element widoku drzewa wybranych i po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszego planu (symbol) | `TreeView.SelectedItemInactiveGlyph` |
| Obramowanie | Brak |

**Element widoku drzewa: aktywowany, zaznaczone, a następnie koncentruje się stan**

![Zaznaczone, a podczas projektowania położono elementu widoku drzewa po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Element widoku drzewa wybranego i skupionego projektu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemActive` |
| Pierwszego planu (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | `TreeView.FocusVisualBorder` |

**Element widoku drzewa: stan aktywowanego, wybrany, a po przeniesieniu fokusu**

![Element widoku drzewa wybranych i po przeniesieniu fokusu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Element widoku drzewa wybranych i po przeniesieniu fokusu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive` |
| Pierwszego planu (tekst) | `TreeView.SelectedItemInactive` |
| Pierwszego planu (symbol) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Obramowanie | Brak |

## <a name="shell-appearance"></a>Wygląd powłoki

### <a name="background"></a>Tło
Tło środowiska składa się z dwóch warstw. Dolna warstwa jest jednolitego koloru, który obejmuje całe środowisko IDE. Górną warstwę mieści się w obszarze półki polecenia i między kanałami automatycznego ukrywania okna narzędzia na lewej lub prawej krawędzi środowiska IDE. Warstwy tła górny i dolny są ustawione na ten sam kolor w motywy jasny i ciemny motyw.

![Visual Studio shell tła (poprawek)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Visual Studio shell tła (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla miejsc, w której chcesz dopasować tło środowiska Visual Studio. | ... jako wypełnienia dla miejsc, które nie są tła powierzchni. |
| | ... jako tło do elementów pierwszego planu. |

**Dolnej warstwie powłoki wyglądu**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.EnvironmentBackground` |

**Wygląd powłoki górną warstwę**

> Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Polecenie Półka
Dwa zestawy token nazwy są używane do tła półki polecenia: on ustawiony, na którym znajduje się na pasku menu, a drugi dla gdzie znajdują się paski poleceń. Grupa pasek indywidualne polecenie ma swoje własne wartości kolorów tła, które zostały omówione bardziej szczegółowo w sekcji "polecenie bar". Menu paska i polecenia paska tekstu omówiono w sekcji pasek menu i poleceń, odpowiednio.

![Visual Studio polecenie półki (poprawek)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio polecenie półki (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla obszarów, w którym umieszcza się menu i paski narzędzi. | ... dla obszarów, które nie są podobne do półki polecenia. |
|... with — kombinacja nazwa tokenu poprawne tła/pierwszego planu. | |

**Pasek menu półki poleceń**

> Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Polecenie półki polecenia pasek **

> Ustaw na tę samą wartość koloru w Visual Studio 2013 jasny i ciemny motyw motywy zatrzymania gradientu.

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Manifest Designer
Manifest Designer został zaprojektowany jako sposób, aby ułatwić edytowanie pliku manifestu w projektach systemu Windows 8 i Windows Phone 8. Gdy nie ma udostępnionego framework dostępne do użycia, może być odpowiednia dla Ciebie dopasować układ i kolory kart orientacji/nawigacji i ogólną strukturę. Aby uzyskać więcej informacji na temat szczegółów układ zobacz [układu dla programu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest Designer (poprawek)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Manifest Designer (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla projektantów, które są podobne do projektanta manifestu. | ... w przypadku więcej niż sześć kart. |
| ... zamiast przy użyciu karty wspólne kontrolki w górnej części edytora w dokumencie dobrze. | ... dla wszelkich elementów interfejsu użytkownika, nie jest struktury, takich jak projektant manifestów. |

**Karta wybranego projektanta manifestu: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `ManifestDesigner.TabActive` |
| Obramowanie | Brak |

**Okienko projektanta manifestu w opis wybranej: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `ManifestDesigner.DescriptionPane` |

**Manifest Designer wybranej strony zawartości: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `ManifestDesigner.Background` |
| Tekst pomocy w oknie dialogowym | `ManifestDesigner.WatermarkText`<br />(Ta nazwa tokenu nie odpowiada jego funkcji.) |

**Karta projektanta manifestu: Usunięto zaznaczenie stanu**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Inactive` |

**Karta projektanta manifestu: Umieść kursor stanu**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Polecenie struktury

###  <a name="BKMK_CommandMenus"></a> Menu
Menu może wystąpić w kilku miejscach w programie Visual Studio: główny pasek menu, osadzony w dokumencie lub narzędzia systemu windows lub kliknij prawym przyciskiem myszy w różnych miejscach w całej IDE. Implementacje menu skojarzone z innymi elementami interfejsu użytkownika zostały omówione w sekcji dla odpowiednich elementów. Zawsze należy używać implementacji standardowe menu oferowanych przez środowisko Visual Studio. Jednak w sporadycznych przypadkach możesz utracić dostęp do standardowego menu programu Visual Studio. W takich sytuacjach należy stosować następujących nazw tokenu, aby upewnić się, że Twój interfejs użytkownika są spójne z innych menu w programie Visual Studio.

![Menu programu Visual Studio (poprawek)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Menu programu Visual Studio (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... kiedy należy utworzyć niestandardowe menu.| ... samodzielnie kolor tła. Zawsze użyj kombinacji tła/pierwszego planu, jak określono. |
| ... przypadku nowy składnik interfejsu użytkownika, który chcesz dopasować menu programu Visual Studio.| |

#### <a name="menu-titles"></a>Tytuły menu
Tytuły menu składają się z tła, obramowania i tekst tytułu, a także opcjonalnie symbol, zwykle w przypadku, gdy menu znajduje się na pasku poleceń.

![Tytuł menu (poprawek)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Tytuł menu (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... zawsze, gdy tworzysz tytuł menu niestandardowe. | ... dla wszystkich elementów, które nie chcesz zawsze odpowiada tytuł menu. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Tytuł menu: domyślny stan**

![Domyślny tytuł menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Tytuł menu Domyślny

![Domyślny tytuł menu z symbol](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />Domyślny tytuł menu z glifów

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Pierwszego planu (symbol) | `Environment.CommandBarMenuGlyph` |
| Obramowanie | Brak |

**Tytuł menu: Umieść kursor stanu**

![Tytuł menu, po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Tytuł menu, po najechaniu wskaźnikiem

![Tytuł menu z symbol po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Tytuł menu z symbol po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextHover` |
| Pierwszego planu (symbol) | `Environment.CommandBarMenuMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |

**Tytuł menu: naciśnięty stanu**

![Naciśnięto tytuł menu](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Tytuł menu po naciśnięciu

![Naciśnięto tytuł menu z symbol](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Naciśnięto tytuł menu z glifów

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Pierwszego planu (symbol) | `Environment.CommandBarMenuMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder`<br />(Tylko po lewej stronie, górnej i prawej stronie.) |

**Tytuł menu: wyłączone**

![Tytuł menu przy użyciu symbolu wyłączone](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Tytuł menu wyłączone z glifów

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszego planu (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

#### <a name="menu-items"></a>Elementy menu
Element menu poszczególnych składa się z tekst menu i opcjonalnej ikony, pole wyboru lub symbol podmenu. Jego tekstu i tła kolorów zmiana po najechaniu wskaźnikiem. Token ten kolor to para tła/pierwszego planu.

![Elementy menu poprawek](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")

| Użyj... | Nie używaj... |
|---|---|
| ... dla dowolnego z listy rozwijanej, jest uruchamiane z paska menu i paska poleceń. | ... Aby uzyskać wszystkie listy rozwijanej w innym kontekście. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Elementy menu: domyślny stan**

![Domyślne elementy menu](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Domyślne elementy menu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Pierwszego planu (podmenu symbol) | `Environment.CommandBarMenuSubmenuGlyph` |
| Obramowanie | `Environment.CommandBarMenuBorder` |
| Tło kanału ikony | `Environment.CommandBarMenuIconBackground` |
| Separator | `Environment.CommandBarMenuSeparator` |
| W tle | `Environment.DropShadowBackground` |

**Elementy menu: zaznaczone, a wybrane Stany**

![Menu zaznaczone](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Element menu zaznaczone

![Wybrane menu](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Wybrany element menu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Znacznik wyboru | `Environment.CommandBarCheckBox` |
| Znacznik wyboru tła | `Environment.CommandBarSelectedIcon` |
| Tło ikony | `Environment.CommandBarSelected` |
| Ikona obramowania | `Environment.CommandBarSelectedBorder` |

**Elementy menu: Umieść kursor stanu**

![Po wskazaniu wskaźnikiem menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Element menu, po najechaniu wskaźnikiem

![Po wskazaniu wskaźnikiem menu zaznaczone](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Zaznaczone elementu menu, po najechaniu wskaźnikiem

![Po wskazaniu wskaźnikiem menu wybrane](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Wybrany element menu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMenuItemMouseOver` |
| Pierwszego planu (tekst) | `Environment.CommandBarMenuItemMouseOver` |
| Pierwszego planu (podmenu symbol) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxMouseOver` |
| Znacznik wyboru tła | `Environment.CommandBarHoverOverSelectedIcon` |
| Tło ikony | `Environment.CommandBarHoverOverSelected` |
| Ikona obramowania | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Elementy menu: wyłączone**

![Menu wyłączone](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Wyłączony element menu

![Zaznaczone wyłączone menu](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Wyłączony element menu znacznika wyboru

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Pierwszego planu (tekst) | `Environment.CommandBarTextInactive` |
| Pierwszego planu (podmenu symbol) | `Environment.CommandBarMenuSubmenuGlyph` |
| Znacznik wyboru | `Environment.CommandBarCheckBoxDisabled` |
| Znacznik wyboru tła | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Paski poleceń
Pasek poleceń może znajdować się w wielu miejscach w programie Visual Studio IDE, głównie półki polecenia i narzędzia embedded na platformie lub okna dokumentu.

Ogólnie rzecz biorąc należy zawsze używać implementacja paska poleceń standardowych, które są dostarczane przez środowisko Visual Studio. Przy użyciu standardowego mechanizmu zapewnia, są poprawnie wyświetlane wszystkie szczegóły visual i że elementów interaktywnych będą zachowywać się spójne z innymi formantami paska poleceń programu Visual Studio. Jednak jeśli jest to niezbędne do tworzenia własnego paska poleceń, upewnij się, że poprawnie za pomocą następujących nazw tokenu stylu.

![Pasek poleceń poprawek](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Pasek poleceń (poprawek)

![Przycisk przepełnienie poprawek](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Przycisk przepełnienie (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w miejscach paska poleceń osadzony, ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla innych niż te, dla których token nazwy zostały określone składniki paska poleceń. |

#### <a name="command-bar-groups"></a>Grup pasek poleceń
Grupy pasek poleceń zawiera zestaw powiązanych formantów paska poleceń i może zawierać dowolną liczbę przyciski, Podziel przyciski, menu rozwijane, pola kombi lub menu. Kolory dla tych formantów jest regulowane przez oddzielne nazwy tokenu i są omówione oddzielnie w innym miejscu, w tym przewodniku. Linii separatora jest używane do dzielenia grupy pasek poleceń do powiązanych podgrupy.

![Grupa paska poleceń poprawek](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Grupa paska poleceń (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w miejscach paska poleceń osadzony, ale są one nie można użyć standardowego implementacja paska poleceń programu Visual Studio. | ... dla elementów interfejsu użytkownika, które nie są podobne do paska poleceń. |
| | ... dla innych niż te, dla których token nazwy zostały określone składniki paska poleceń. |

**Grupa paska poleceń: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Obramowanie | `Environment.CommandBarToolBarBorder` |
| Przeciągnij uchwyt | `Environment.CommandBarDragHandle` |
| Separator | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony poleceń
![Ikona polecenia poprawek](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Ikona polecenia (poprawek)

![Ikona polecenia tekstem poprawek](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Ikona polecenia z tekstem (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla przycisków, które zostaną umieszczone na pasku poleceń. | ... w przypadku formantów, które mają własne nazwy tokenu. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Ikona polecenia: domyślny stan**

![Polecenie domyślną ikonę](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Domyślna ikona polecenia

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | N/d (dziedziczy tło paska poleceń) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Obramowanie | Brak |

**Ikona polecenia: domyślny stan, zaznaczone**

![Domyślnie, ikona wybranego polecenia](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />Domyślnie, ikona wybranego polecenia

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarSelected` |
| Pierwszego planu (tekst) | `Environment.CommandBarTextSelected` |
| Obramowanie | `Environment.CommandBarSelectedBorder` |

**Ikona polecenia: stany po wskazaniu wskaźnikiem lub fokus**

![Ikona polecenia po wskazaniu wskaźnikiem lub fokus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Ikona polecenia po wskazaniu wskaźnikiem lub koncentracji uwagi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextHover` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: stany po wskazaniu wskaźnikiem lub fokus, zaznaczone**

![Wybrana ikona polecenia po wskazaniu wskaźnikiem lub fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Ikona wybranego polecenia po wskazaniu wskaźnikiem lub koncentracji uwagi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarHoverOverSelected` |
| Pierwszego planu (tekst) | `Environment.CommandBarTextHoverOverSelected` |
| Obramowanie | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona polecenia: naciśnięty stanu**

![Naciśnięto ikona polecenia](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Ikona po naciśnięciu polecenia

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextMouseDown` |
| Obramowanie | `Environment.CommandBarBorder` |

**Ikona polecenia: wyłączone**

![Ikona polecenia wyłączenia](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Ikona polecenia wyłączenia

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | N/d (dziedziczy tło paska poleceń) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |

####  <a name="BKMK_CommandComboBox"></a> Pola kombi na pasku poleceń

> [!IMPORTANT]
> Pola kombi są podobne do list rozwijanych, ale zawierają region tekst do edycji. Jeśli z listy rozwijanej nie obejmuje regionu tekst do edycji, Użyj kolorów tokeny zabezpieczające [polecenia paska list rozwijanych](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Polecenie paska pola kombi poprawek](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Pole kombi na pasku poleceń (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia pola kombi niestandardowych. | ... dla wszystkich elementów, nie należy zawsze dopasować polecenia paska. |
| ... podczas tworzenia formantu paska poleceń, która jest podobna do pola kombi. | ... Jeśli mają dostęp do pola kombi ze stylem. |

**Polecenie Pasek danych wejściowych polu kombi: domyślny stan**

![Polecenie Pasek danych wejściowych polu kombi](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Pole wejściowe pole kombi pasek poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxText` |
| Obramowanie | `Environment.ComboBoxBorder` |
| Separator | Nie separatora |

**Przycisk listy rozwijanej na pasku poleceń: domyślny stan**

![Listy pola kombi&#45;naciśnięty przycisk](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Przycisk listy rozwijanej na pasku poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | N/d (dziedziczy tło paska poleceń) |
| Pierwszego planu (symbol) | `Environment.ComboBoxGlyph` |

**Listy rozwijanej na pasku poleceń: domyślny stan**

![Listy rozwijanej na pasku poleceń](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Listy rozwijanej na pasku poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxPopupBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.ComboBoxPopupBorder` |

**Polecenie Pasek danych wejściowych polu kombi: Umieść kursor stanu**

![Polecenie Pasek danych wejściowych polu kombi po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Polecenie Pasek danych wejściowych polu kombi po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.ComboBoxMouseOverText` |
| Obramowanie | `Environment.ComboBoxMouseOverBorder` |
| Separator | `Environment.ComboBoxMouseOverSeparator` |

 **Przycisk listy rozwijanej na pasku poleceń: Umieść kursor stanu**

![Przycisk listy rozwijanej paska poleceń po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseOverBackground` |
| Pierwszego planu (symbol) | `Environment.ComboBoxMouseOverGlyph` |

**Listy rozwijanej na pasku poleceń: Umieść kursor stanu**

 ![Lista listę rozwijaną paska poleceń po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Lista listę rozwijaną paska poleceń po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| W tle (element Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Polecenie Pasek danych wejściowych polu kombi: skupia się stan**

![Fokus pasku pole wejściowe pola kombi poleceń](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Koncentruje się pole wejściowe pole kombi pasek poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxFocusedText` |
| Obramowanie | `Environment.ComboBoxFocusedBorder` |
| Separator | `Environment.ComboBoxFocusedButtonSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: skupia się stan**

![Fokus pasku przycisk listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Polecenie ukierunkowanych paska przycisk listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxFocusedButtonBackground` |
| Pierwszego planu (symbol) | `Environment.ComboBoxFocusedGlyph` |

 **Polecenie Pasek danych wejściowych polu kombi: naciśnięty stanu**

![Naciśnięto polecenia paska pole wejściowe pola kombi](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Naciśnięciu pola wejściowego pole kombi pasek poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxMouseDownBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxMouseDownText` |
| Obramowanie | `Environment.ComboBoxMouseDownBorder` |
| Separator | `Environment.ComboBoxMouseDownSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: naciśnięty stanu**

![Naciśnięto pasku przycisk listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Naciśnięto polecenia paska przycisk listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxButtonMouseDownBackground` |
| Pierwszego planu (symbol) | `Environment.ComboBoxMouseDownGlyph` |

**Polecenie Pasek danych wejściowych polu kombi: wyłączone**

![Wyłączone pasku pole wejściowe pola kombi poleceń](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Polecenia wyłączonego paska pole wejściowe pola kombi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ComboBoxDisabledBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxDisabledText` |
| Obramowanie | `Environment.ComboBoxDisabledBorder` |
| Separator | Nie separatora |

**Przycisk listy rozwijanej na pasku poleceń: wyłączone**

![Wyłączone pasku przycisk listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Polecenie wyłączonego paska przycisk listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Pasek poleceń list rozwijanych

> [!IMPORTANT]
>  Listy rozwijane są podobne do pola kombi, ale brak regionów tekst do edycji. Jeśli z listy rozwijanej zawiera tekst do edycji regionu, należy użyć tokenów kolorów dla [polecenia paska pola kombi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Polecenie paska listy rozwijanej (poprawek)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Polecenie paska listy rozwijanej (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia kontrolki niestandardowej listy rozwijanej. | ... dla wszystkich elementów, które nie są podobne do listy rozwijanej. |
| | ... w odniesieniu do pola kombi lub przyciski dzielone. |

**Pole listy rozwijanej wyboru pasku polecenia: domyślny stan**

![Domyślnie polecenia paska pola wyboru z listy rozwijanej](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Domyślne polecenia pasek wyboru z listy rozwijanej pole

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownBackground` |
| Pierwszego planu (tekst) | `DropDownText` |
| Obramowanie | `DropDownBorder` |
| Separator | Nie separatora |

**Przycisk listy rozwijanej na pasku poleceń: domyślny stan**

![Domyślnie polecenia paska przycisk listy rozwijanej](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Przycisk listy rozwijanej paska poleceń domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Environment.DropDownGlyph` |

**Listy rozwijanej na pasku poleceń: domyślny stan**

![Domyślnie polecenia paska menu rozwijanego](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Domyślne polecenia pasek menu rozwijanego

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownPopupBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.ComboBoxItemText` |
| Obramowanie | `Environment.DropDownPopupBorder` |
| W tle | `Environment.DropShadowBackground` |

**Pole listy rozwijanej wyboru pasku polecenia: Umieść kursor stanu**

![Polecenie pasek wyboru z listy rozwijanej pola po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Polecenie pasek wyboru z listy rozwijanej pola po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.DropDownMouseOverText` |
| Obramowanie | `Environment.DropDownMouseOverBorder` |
| Separator | `Environment.DropDownButtonMouseOverSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: Umieść kursor stanu**

![Przycisk listy rozwijanej paska poleceń po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Przycisk listy rozwijanej paska poleceń po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseOverBackground` |
| Pierwszego planu (symbol) | `Environment.DropDownMouseOverGlyph` |

**Listy rozwijanej na pasku poleceń: Umieść kursor stanu**

![Lista listę rozwijaną paska poleceń po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Lista listę rozwijaną paska poleceń po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| W tle (element Menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Pierwszego planu (tekst) | `Environment.ComboBoxItemMouseOverText` |
| Obramowanie (element Menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Pole listy rozwijanej wyboru pasku polecenia: naciśnięty stanu**

![Upuść&#45;w dół do pola wyboru naciśnięty](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Naciśnięto polecenia paska pola wyboru z listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownMouseDownBackground` |
| Pierwszego planu (tekst) | `Environment.DropDownMouseDownText` |
| Obramowanie | `Environment.DropDownMouseDownBorder` |
| Separator | `Environment.DropDownButtonMouseDownSeparator` |

**Przycisk listy rozwijanej na pasku poleceń: naciśnięty stanu**

![Naciśnięto pasku przycisk listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Naciśnięto polecenia paska przycisk listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownButtonMouseDownBackground` |
| Pierwszego planu (symbol) | `Environment.DropDownMouseDownGlyph` |

**Pole listy rozwijanej wyboru pasku polecenia: wyłączone**

![Wyłączone pasku pola wyboru z listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Polecenie wyłączonego paska pola wyboru z listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DropDownDisabledBackground` |
| Pierwszego planu (tekst) | `Environment.DropDownDisabledText` |
| Obramowanie | `Environment.DropDownDisabledBorder` |
| Separator | Nie separatora |

**Przycisk listy rozwijanej na pasku poleceń: wyłączone**

![Wyłączone pasku przycisk listy rozwijanej poleceń](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Polecenie wyłączonego paska przycisk listy rozwijanej

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Pasek poleceń podziału przycisków
Przyciski dzielone udostępniać wiele tokenów nazwy inne kontrolki paska poleceń, takich jak przyciski, menu i tekst paska poleceń. Wszystkie niezbędne działania i przycisk listy rozwijanej token nazwy są powtarzane tutaj dla wygody. Listy rozwijane w przycisku podziału stanowią implementacje [polecenia paska menu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Przycisk podziału poprawek](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Przycisk podziału paska poleceń (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia przycisku podziału niestandardowych. | ... w przypadku innych typów przycisków. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Przycisk podziału paska poleceń: domyślny stan**

![Domyślny przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Przycisk podziału paska poleceń domyślne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (tekst) | `Environment.CommandBarTextActive` |
| Pierwszego planu (symbol) | `Environment.CommandBarSplitButtonGlyph` |
| Obramowanie | Brak |
| Separator | Brak |

**Przycisk podziału paska poleceń: Umieść kursor stanu**

![Przycisk, po najechaniu wskaźnikiem podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Pasek poleceń podziału przycisku po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextHover` |
| Pierwszego planu (symbol) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | `Environment.CommandBarSplitButtonSeparator` |

**Przycisk podziału paska poleceń: naciśnięty stanu**

![Naciśnięty przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Przycisk podziału paska poleceń po naciśnięciu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.CommandBarTextMouseDown` |
| Pierwszego planu (symbol) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Obramowanie | `Environment.CommandBarBorder` |
| Separator | Brak |

**Przycisk podziału paska poleceń: wyłączone**

![Wyłączony przycisk podziału paska poleceń](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Przycisk podziału wyłączonego paska poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (tekst) | `Environment.ComboBoxItemTextInactive` |
| Pierwszego planu (symbol) | `Environment.CommandBarTextInactive` |
| Obramowanie | Brak |
| Separator | Brak |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Polecenie "Więcej opcji" i "Overflow" paska przycisków
Przycisk "Więcej opcji" jest używany, gdy grupy pasek poleceń jest możliwe do dostosowania, albo dodając lub usuwając przyciski paska poleceń powiązanych. Przycisk "Overflow" jest wyświetlany, gdy pasek poleceń zostały obcięte ze względu na Brak miejsca w poziomie, a po kliknięciu pokazuje menu zawierające przyciski paska poleceń nie może być wyświetlany. Kolory dla tych dwóch przycisków są kontrolowane przez ten sam zestaw tokenów nazwy.

![Polecenie paska przycisku "Więcej opcji" (poprawek)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Polecenie paska przycisku "Więcej opcji" (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... w odniesieniu do niestandardowe "więcej opcji" lub "Overflow" przycisków. | ... dla przycisków, które nie mają podobne funkcje do bardziej opcji lub przycisku "Overflow". |

**Polecenie "Więcej opcji" i "Overflow ma wartość" przycisków paska: domyślny stan**

![Domyślnie polecenia paska przycisku "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Przycisk "Więcej opcji" domyślne pasek poleceń

![Domyślnie polecenia paska przycisku "Overflow ma wartość"](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Domyślnym przyciskiem "Overflow ma" pasku polecenia

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsBackground` |
| Pierwszego planu (symbol) | `Environment.CommandBarOptionsGlyph` |

**Polecenie "Więcej opcji" i "Overflow ma wartość" przycisków paska: Umieść kursor stanu**

![Polecenie paska przycisku "Więcej opcji" po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Polecenie paska przycisku "Więcej opcji" po najechaniu wskaźnikiem

![Pasek poleceń "Overflow ma wartość" przycisku, po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />Pasek poleceń "Overflow ma wartość" przycisku, po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Polecenie "Więcej opcji" i "Overflow ma wartość" przycisków paska: naciśnięty stanu**

![Naciśnięto polecenia paska przycisku "Więcej opcji"](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Naciśnięto pasku przycisku "Więcej opcji" poleceń

![Przepełnienie naciśnięty](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Naciśnięty przycisk "Overflow ma wartość" pasek poleceń

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (symbol) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentów
Nie ma potrzeby replikowanie okna dokumentu, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolory używane w oknach dokumentów, tak, aby Twój interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

Korzystając z tokenów kolor okna dokumentu, uważaj ich używać tylko w przypadku podobnych elementów, zawsze w pary. Jeśli to nie zrobisz, możesz otrzymać nieoczekiwane wyniki w interfejsie użytkownika.

### <a name="document-window-frames"></a>Ramki okna dokumentu
Okna dokumentów może być zadokowane w IDE lub zmiennoprzecinkową jako oddzielne okno. Gdy okno dokumentu jest liczb zmiennoprzecinkowych poza IDE, ona nadal znajduje się w źródle dokumentu i ma tła, obramowania, tekstu i kolorów karty, które są takie same jak, gdy jest on częścią środowiska IDE. Jednak dokumentu znajduje się wewnątrz ramki, który ma swój własny tło obramowania i kolorów tekstu. Gdy okna narzędziowe są zadokowane w źródle dokumentu, dziedziczą zachowanie i koloru dla swoich kart z nazwy tokenu okien dokumentu.

![Okno zadokowane dokumentu (poprawek)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Okno zadokowane dokumentu (poprawek)

![Przestawne okno dokumentu (poprawek)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Przestawne okno dokumentu (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować okno dokumentu. | ... żadnych interfejsów użytkownika, których nie chcesz automatycznie umożliwia zmianę powłoki ma aktualizacji motywu. |

**Okno dokumentu zadokowany lub przestawny: domyślny stan**

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Zależy od typu dokumentu |
| Pierwszego planu (tekst) | Zależy od typu dokumentu |
| Obramowanie | `Environment.ToolWindowBorder` |

**Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu: domyślny stan**

![Domyślne fokus, liczb zmiennoprzecinkowych ramki okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Domyślne fokus, liczb zmiennoprzecinkowych ramki okna dokumentu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrame` |
| Pierwszego planu (tekst) | `Environment.ToolWindowFloatingFrame` |
| Pierwszego planu (symbol) | `Environment.RaftedWindowButtonActiveGlyph` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonActiveBorder`<br />(Ustawienie przezroczystego) |

**Po przeniesieniu fokusu dokument zmiennoprzecinkowy ramki okna: domyślny stan**

![Ramka okna po przeniesieniu fokusu zmiennoprzecinkowy dokument domyślny](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Domyślnie po przeniesieniu fokusu dokument zmiennoprzecinkowy ramki okna

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszego planu (tekst) | `Environment.ToolWindowFloatingFrameInactive` |
| Pierwszego planu (symbol) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Ustawienie przezroczystego) |

**Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu: Umieść kursor stanu**

![Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonHoverActive` |
| Pierwszego planu (symbol) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Po przeniesieniu fokusu dokument zmiennoprzecinkowy ramki okna: Umieść kursor stanu**

![Po przeniesieniu fokusu dokument zmiennoprzecinkowy ramki okna po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Po przeniesieniu fokusu, liczb zmiennoprzecinkowych ramki okna dokumentu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło (symbol) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Pierwszego planu (symbol) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu: naciśnięty stanu**

![Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu przy naciśnięciu](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Ukierunkowane liczb zmiennoprzecinkowych ramki okna dokumentu przy naciśnięciu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło (symbol) | `Environment.RaftedWindowButtonDown` |
| Pierwszego planu (symbol) | `Environment.RaftedWindowButtonDownGlyph` |
| Obramowanie (symbol) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Karty dokumentów
Karty dokumentów znajdują się w kanale kartę, aby wskazać, które dokumenty są obecnie otwarte, oraz które z nich jest bieżąca wybrane lub aktywnego dokumentu. Okna narzędzi również może być zadokowane w kanale kartę dokumentu, jeśli użytkownik przełączy je ma. W takiej sytuacji używają takich samych kolorów karty jako okna dokumentu. Czy tworzenie interfejsu użytkownika chcesz zawsze odpowiada kolory okna dokumentu (w tym aktualizacje motywu lub jeśli są zainstalowane nowe motywy), a następnie odwoływać się do tych tokenów kolorów.

![Karty dokumentów (poprawek)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Karty dokumentów (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować karty dokumentów i automatycznie pobierał kompozycję aktualizacje lub nowe kolory motywu. | ... dla żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma motyw aktualizacji. |

#### <a name="open-document-tabs"></a>Otwórz dokument karty
Każdy otwarty dokument ma kartę w kanale kartę dokumentu, który wyświetla jego nazwę. Dokumenty można albo wybrać lub otworzyć w tle, a ich karty odzwierciedlać te stany:

-   Wybrane karta reprezentuje dokument, który jest aktualnie wyświetlany w dokumencie dobrze. Kartę wybraną ma obramowanie dokumentu, które dobrze rozszerza między górną krawędzią dokumentu.

-   Karty w tle są żadnych kart dokumentu, które nie są aktualnie wybrana karta. Po kliknięciu stają się wybranej karty i uzyskania wszystkich obramowania, tekstu i tła kolorów z tymi nazwami tokenu.

![Karta otwartego dokumentu (poprawek)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Karta otwartego dokumentu (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia karty niestandardowego dokumentu. | ... dla kart tymczasowe (wersja zapoznawcza). |
| | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Karty wybrane, ukierunkowane dokumentu**

![Zaznaczone, fokus karty dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Karty wybrane, ukierunkowane dokumentu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabSelectedGradientTop`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.FileTabSelectedText` |
| Obramowanie | `Environment.FileTabSelectedBorder`<br />(Ustawia kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Karta wybrany dokument po przeniesieniu fokusu**

![Karta wybrany dokument po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Karta wybrany dokument po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabInactiveGradientTop`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.FileTabInactiveText` |
| Obramowanie | `Environment.FileTabInactiveBorder`<br />(Ustawia kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karty dokumentu w tle: domyślny stan**

![Karta dokumentu tło domyślne](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Karta dokumentu tło domyślne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabBackground` |
| Pierwszego planu (tekst) | `Environment.FileTabText` |
| Obramowanie | `Environment.FileTabBorder`<br />(Ustawia kolor tła). |

**Karty dokumentu w tle: Umieść kursor stanu**

![Karty dokumentu w tle po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Karty dokumentu w tle po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabHotGradientTop`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.FileTabHotText` |
| Obramowanie | `Environment.FileTabHotBorder`<br />(Ustawia kolor tła). |

#### <a name="preview-tab"></a>Karta (wersja zapoznawcza)
Skrót "tymczasowe" kartę. Karta (wersja zapoznawcza) pojawia się po prawej stronie kanału kartę dokumentu, gdy użytkownik kliknie element w oknie narzędzia Eksploratora rozwiązań. On działa w wersji zapoznawczej dokumentu, a także zapewnia możliwość nie zamykaj dokumentu po lewej stronie kanału karty dokumentu. Otwórz kartę tylko jeden (wersja zapoznawcza) może być otwarty naraz. Podgląd karty mają zarówno w tle i wybranych stanów, takie jak karty i może być ukierunkowane lub po przeniesieniu fokusu w ich stanie aktywnym.

![Karta (wersja zapoznawcza) (poprawek)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Karta (wersja zapoznawcza) (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... gdziekolwiek tworzysz tymczasowego w wersji zapoznawczej i ma pewien element, aby dopasować bieżący kolor karcie podglądu. | ... dla każdego typu dokumentu lub kartę, która nie jest tymczasowe (wersja zapoznawcza). |
| | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Karta ukierunkowanych, wybrane (wersja zapoznawcza)**

![Karcie podglądu ukierunkowanych, wybrane](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Karta ukierunkowanych, wybrane (wersja zapoznawcza)

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedActive` |
| Pierwszego planu (tekst) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Ustawia kolor tła). |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Karta po przeniesieniu fokusu, wybrane (wersja zapoznawcza)**

![Karcie podglądu po przeniesieniu fokusu, wybrane](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Karta po przeniesieniu fokusu, wybrane (wersja zapoznawcza)

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalSelectedInactive` |
| Pierwszego planu (tekst) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Obramowanie dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Tło karcie podglądu: domyślny stan**

![Karta Podgląd tło domyślne](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Karta Podgląd tło domyślne

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalInactive` |
| Pierwszego planu (tekst) | `Environment.FileTabProvisionalInactiveForeground` |
| Obramowanie | `Environment.FileTabProvisionalInactiveBorder`<br />(Ustawia kolor tła). |

**Tło karcie podglądu: Umieść kursor stanu**

![Tło karcie podglądu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Tło karcie podglądu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.FileTabProvisionalHover` |
| Pierwszego planu (tekst) | `Environment.FileTabProvisionalHoverForeground` |
| Obramowanie | `Environment.FileTabProvisionalHoverBorder`<br />(Ustawia kolor tła). |

#### <a name="document-overflow-button"></a>Przycisk przepełnienie dokument
Przycisk przepełnienie dokument jest obecny, jeśli istnieje jeden lub więcej dokumentów otworzyć, niezależnie od tego, czy brak miejsca w pionie w bieżącej konfiguracji, aby dopasować wszystkich kartach dokumentów. Menu rozwijanego przepełnienie dokumentu, które są kontrolowane przez [polecenia menu paska](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) kolory, wyświetla listę wszystkich otwartych dokumentach widoczna i ukryta, i zmienia symbol przepełnienie w zależności od tego, czy są otwarte dokumenty wyświetlane w kanale kartę.

![Przycisk przepełnienie dokument (poprawek)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Przycisk przepełnienie dokument (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas tworzenia niestandardowego dokumentu przycisku przepełnienia. | ... dla interfejsu użytkownika, które nie są podobne do przycisku przepełnienia. |
| | ... dla przycisków przepełnienie paska poleceń. |

**Przycisk przepełnienie dokument: domyślny stan**

![Przycisk przepełnienie dokument domyślny](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Przycisk przepełnienie dokument domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonBackground` |
| Pierwszego planu (symbol) | `Environment.DocWellOverflowButtonGlyph` |
| Obramowanie | Brak |

**Przycisk przepełnienie dokument: Umieść kursor stanu**

![Przycisk przepełnienie dokument po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Przycisk przepełnienie dokument po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Pierwszego planu (symbol) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Przycisk przepełnienie dokument: naciśnięty stanu**

![Przycisk przepełnienie dokument przy naciśnięciu](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Przycisk przepełnienie dokument przy naciśnięciu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Pierwszego planu (symbol) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Obramowanie | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Znakowanie
Program Visual Studio obsługuje, tagowanie, co pozwala użytkownikowi zadeklarować można wyszukiwać słowa kluczowe na potrzeby śledzenia. Na przykład menedżerów projektów i programistów umożliwia Team Foundation Server (TFS) tagów elementów roboczych. W poniższych tabelach podać nazw kolorów zarówno samego znacznika, jak i "zamknąć ikonę" symbol, umieść kursor i wybranych stanów.

![Znakowanie w programie Visual Studio (poprawek)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Znakowanie w programie Visual Studio (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla interfejsu użytkownika, który obsługuje znakowanie. | ... dla wszystkich innych typów interfejsu użytkownika. |

#### <a name="tags"></a>Znaczniki

**Tag: stan domyślny**

![Znacznik domyślny](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Tag domyślny

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.Background` |
| Pierwszego planu (tekst) | `Tag.Background` |

**Tag: stan aktywowanego**

![Tag po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Tag po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.HoverBackground` |
| Pierwszego planu (tekst) | `Tag.HoverBackgroundText` |

**Tag: naciśnięty stanu**

![Naciśnięto tag](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Po naciśnięciu tagu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.PressedBackground` |
| Pierwszego planu (tekst) | `Tag.PressedBackgroundText` |

**Tag: wybrany stan**

![Zaznaczony tag](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Wybrany tag

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.SelectedBackground` |
| Pierwszego planu (tekst) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zamknij (&times;) symbol tagu

**Zamknij (&times;) symbol tagu: domyślny stan**

![Domyślne Zamknij (&times;) symbol tagu](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Domyślne Zamknij (&times;) symbol tagu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Tag.TagHoverGlyph` |

**Zamknij (&times;) symbol tagu: Umieść kursor stanu**

![Zamknij (&times;) tag symbol po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Zamknij (&times;) tag symbol po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphHoverBackground` |
| Pierwszego planu (symbol) | `Tag.TagHoverGlyphHover` |
| Obramowanie | `Tag.TagHoverGlyphHoverBorder` |

**Zamknij (&times;) symbol tagu: naciśnięty stanu**

![Naciśnięto Zamknij (&times;) symbol tagu](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Naciśnięto Zamknij (&times;) symbol tagu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.TagHoverGlyphPressedBackground` |
| Pierwszego planu (symbol) | `Tag.TagHoverGlyphPressed` |
| Obramowanie | `Tag.TagHoverGlyphPressedBorder` |

**Zaznaczony tag z Zamknij (&times;) symbol: domyślny stan**

![Domyślnie wybrany tag opcją Zamknij (&times;) symbol](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Domyślnie wybrany tag opcją Zamknij (&times;) glifów

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Tag.TagSelectedGlyph` |

**Zaznaczony tag z Zamknij (&times;) symbol: Umieść stanu**

![Zaznaczony tag z Zamknij (&times;) symbol po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Zaznaczony tag z Zamknij (&times;) symbol po najechaniu wskaźnikiem


| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphHoverBackground` |
| Pierwszego planu (symbol) | `Tag.TagSelectedGlyphHover` |
| Obramowanie | `Tag.TagSelectedGlyphHoverBorder` |

**Zaznaczony tag z Zamknij (&times;) symbol: naciśnięty stanu**

![Zaznaczone, naciśnięciu oznaczanie numerem Zamknij (&times;) symbol](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Zaznaczone, naciśnięciu oznaczanie numerem Zamknij (&times;) glifów

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(Glyph) | `Tag.TagSelectedGlyphPressed` |
| Obramowanie | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna narzędzi
Nie ma potrzeby replikowanie okien narzędziowych, ponieważ są one udostępniane przez środowisko Visual Studio. Jednak można zdecydować, czy chcesz korzystać kolorów używanych w oknach narzędzi, dzięki czemu interfejs użytkownika zawsze wyświetlana jest zgodny z tej części środowiska Visual Studio.

![Okno narzędzi (poprawek)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Okno narzędzi (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować okna narzędzi. | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

### <a name="tool-window-frame"></a>Ramki okna narzędzi
Okna narzędzi w programie Visual Studio są używane w przypadku wielu różnych zadań, a może znajdować się w jednej z kilku różnych stanów. Jeśli okno narzędzi jest otwarty, można przypisać do dowolnego z czterech bokach obszar dokumentu. Okna narzędzi można również liczb zmiennoprzecinkowych poza IDE, co pozwala na można zmieniać pozycji w dowolnym miejscu w ramach ekranu użytkownika. Zmiennoprzecinkowe systemu windows zawsze znajdują się na górze IDE. Na koniec okna narzędzi może być zadokowane jako okien dokumentu i są wyświetlane na karcie w dokumencie dobrze. Okna narzędzi, które zostały zadokowane jako okien dokumentu mają kolor w części za pomocą nazwy tokenu okien dokumentu.

![Ramka okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Ramka okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować okna narzędzi. | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Okno zadokowane**

![Okna narzędzi zadokowanych](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Okno zadokowane

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.ToolWindowBorder` |

**Opływanie, skupia się okna narzędzi**

![Opływanie, skupia się okna narzędzia](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Opływanie, skupia się okna narzędzi

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowActiveDefaultBorder` |

**Przestawne okna narzędzi po przeniesieniu fokusu**

![Przestawne, po przeniesieniu fokusu okna narzędzi](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Przestawne okna narzędzi po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowBackground` |
| Obramowanie | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Windows podobne do przybornika
Przybornik jest jednym z najczęściej używanych typowych okien narzędzi w programie Visual Studio. Jest zasadniczo kontrolki drzewa za pomocą specjalnych motywu i stylów zastosowana.

![Okno przybornika przypominającej (poprawek)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Okno przybornika przypominającej (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... podczas projektowania okna narzędzi, które chcesz, aby zawsze były zgodne z przybornika powłoki. | ... dla wszystkich elementów, które nie są podobne do przybornika interfejsu użytkownika lub jeśli wiesz, czy interfejs użytkownika będą mieć problemy, jeśli Przybornik powłoki kolory zmiany. |

**Węzły przybornika: domyślny stan**

![Węzeł nadrzędny przybornika domyślnego](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Węzeł nadrzędny przybornika domyślnego

![Węzeł podrzędny przybornika domyślnego](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Węzeł podrzędny przybornika domyślnego

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolboxContent`<br />(Nagłówki) |
| Tło | `Environment.ToolWindowBackground`<br />(Pojedynczych elementów lub całe okno, jeśli brak dostępnych kontrolek) |
| Obramowanie | Brak |
| Pierwszego planu (symbol) | `Environment.ToolboxContent` |
| Pierwszego planu (tekst) | `Environment.ToolboxContent` |

**Węzły podrzędne przybornika: Umieść kursor stanu**

![Węzeł podrzędny przybornika po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Węzeł podrzędny przybornika po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolboxContentMouseOver`<br />(Tylko w pojedynczych elementów) |
| Obramowanie | Brak |
| Pierwszego planu (tekst) | `Environment.ToolboxContentMouseOver`<br />(Tylko w pojedynczych elementów) |

**Wybrane węzły przybornika: skupia się stan**

![Węzeł nadrzędny przybornika ukierunkowanych, wybrane](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Węzeł nadrzędny ukierunkowanych, wybrane przybornika

![Węzeł podrzędny przybornika ukierunkowanych, wybrane](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Węzeł podrzędny ukierunkowanych, wybrane przybornika

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemActive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Obramowanie | `TreeView.FocusVisualBorder`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Pierwszego planu (symbol) | `TreeView.SelectedItemActive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Pierwszego planu (tekst) | `TreeView.SelectedItemActive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |

**Wybrane węzły przybornika: stan po przeniesieniu fokusu**

![Węzeł nadrzędny przybornika zaznaczona, po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Węzeł nadrzędny przybornika zaznaczona, po przeniesieniu fokusu

![Węzeł podrzędny przybornika zaznaczona, po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Węzeł podrzędny przybornika zaznaczona, po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `TreeView.SelectedItemInactive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Obramowanie | Brak |
| Pierwszego planu (symbol) | `TreeView.SelectedItemInactive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |
| Pierwszego planu (tekst) | `TreeView.SelectedItemInactive`<br />Z [widoku drzewa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorii |

### <a name="tool-window-title-bar"></a>Pasek tytułu okna narzędzi
Obramowania paska tytułu, nie ma wartość true, obramowanie okazał się Gruba linia wzdłuż górnej krawędzi paska tytułu. Nie ma tokenu nazwę stanu po przeniesieniu fokusu.

![Pasek tytułu okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Pasek tytułu okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować okna narzędzi. | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Pasek tytułu fokusem**

![Pasek tytułu ukierunkowanych](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Pasek tytułu fokusem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.TitleBarActiveGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.TitleBarActiveText` |
| Obramowanie | `Environment.TitleBarActiveBorder`<br />(Ustawia kolor tła). |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandleActive` |

**Pasek tytułu po przeniesieniu fokusu**

![Po przeniesieniu fokusu paska tytułu](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Pasek tytułu po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.TitleBarInactiveGradientBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.TitleBarInactiveText` |
| Obramowanie | Brak |
| Przeciągnij uchwyt | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Przyciski paska tytułu okna narzędzi
![Tytuł paska przycisku (poprawek)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Tytuł paska przycisku (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dla przycisków, które są wyświetlane w interfejsie użytkownika, używający tokenów kolor z paski tytułu okna narzędzia. | ... w przypadku przycisków, które pojawiają się w innych lokalizacjach. |
| | ... w dowolnej kombinacji tła/pierwszego planu, inny niż określony. |

**Fokus przycisków na pasku tytułu: domyślny stan**

![Domyślnie, skupia się przycisków na pasku tytułu](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />Domyślnie przycisków na pasku tytułu fokusem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonActiveGlyph` |
| Obramowanie | Brak |

**Przyciski paska tytułu po przeniesieniu fokusu: domyślny stan**

![Domyślnie, przycisków na pasku tytułu po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />Domyślnie przycisków na pasku tytułu po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | Brak |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonInactiveGlyph` |
| Obramowanie | Brak |

**Fokus przycisków na pasku tytułu: Umieść kursor stanu**

![Fokus przycisków na pasku tytułu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Przyciski paska tytułu ukierunkowanych po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverActive` |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverActiveBorder` |

**Przyciski paska tytułu po przeniesieniu fokusu: Umieść kursor stanu**

![Przyciski paska tytułu po przeniesieniu fokusu po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Przyciski paska tytułu po przeniesieniu fokusu po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonHoverInactive` |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Fokus przycisków na pasku tytułu: naciśnięty stanu**

![Poświęcone przycisków na pasku tytułu naciśnij](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Przyciski paska tytułu wąsko zdefiniowany przy naciśnięciu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

**Przyciski paska tytułu po przeniesieniu fokusu: naciśnięty stanu**

![Przy naciśnięciu przycisków na pasku tytułu po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Przy naciśnięciu przycisków na pasku tytułu po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowButtonDown` |
| Pierwszego planu (symbol) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Obramowanie | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna narzędzi
![Karta okna narzędzia (poprawek)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Karta okna narzędzia (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować okna narzędzi. | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Karta okna narzędzia wybrane, ukierunkowane**

![Zaznaczone, skupia się karta w oknie narzędzia](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Karta okna narzędzia wybrane, ukierunkowane

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszego planu (tekst) | `Environment.ToolWindowTabSelectedActiveText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustawia kolor tła). |

**Karta okna narzędzia zaznaczona, po przeniesieniu fokusu**

![Karta okna narzędzia zaznaczona, po przeniesieniu fokusu](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Karta okna narzędzia zaznaczona, po przeniesieniu fokusu

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabSelectedTab` |
| Pierwszego planu (tekst) | `Environment.ToolWindowTabSelectedText` |
| Obramowanie | `Environment.ToolWindowTabSelectedBorder`<br />(Ustawia kolor tła). |

**Karta okna narzędzia tło: domyślny stan**

![Karta okna narzędzia tło domyślne](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Karta w oknie narzędzia domyślne tło

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Zatrzymania gradientu Ustaw na tę samą wartość koloru w programie Visual Studio 2013.) |
| Pierwszego planu (tekst) | `Environment.ToolWindowTabText` |
| Obramowanie | `Environment.ToolWindowTabBorder` |

**Karta okna narzędzia tło: Umieść kursor stanu**

![Karta okna narzędzia tło po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Karta okna narzędzia tło po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Zatrzymania gradientu Ustaw na tę samą wartość koloru w programie Visual Studio 2013.) |
| Pierwszego planu (tekst) | `Environment.ToolWindowTabMouseOverText` |
| Obramowanie | `Environment.ToolWindowTabMouseOverBorder`<br />(Ustawia kolor tła). |

### <a name="auto-hide-tabs"></a>Automatyczne ukrywanie kart

![Automatyczne ukrywanie kart (poprawek)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")automatyczne ukrywanie kart (poprawek)

| Użyj... | Nie używaj... |
| --- | --- |
| ... dowolnym tworzymy interfejs użytkownika, który chcesz dopasować karty okna ukryte automatycznie narzędzi. | ... żadnych interfejsów użytkownika, których nie chcesz, aby zmienić automatycznie, gdy powłoka ma aktualizacji motywu. |

**Autoukrywanie kart: domyślny stan**

![Karta Autoukrywanie domyślne](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Domyślną kartę autoukrywanie

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.AutoHideTabBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.AutoHideTabText` |
| Obramowanie | `Environment.AutoHideTabBorder` |

**Autoukrywanie kart: Umieść kursor stanu**

![Automatyczne ukrywanie karty po najechaniu wskaźnikiem](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Autoukrywanie kartę po najechaniu wskaźnikiem

| Element | Nazwa tokenu: Category.Color |
| --- | --- |
| Tło | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Ograniczniki gradientu dla tego tokenu nie jest używany w interfejsie użytkownika motywem.) |
| Pierwszego planu (tekst) | `Environment.AutoHideTabMouseOverText` |
| Obramowanie | `Environment.AutoHideTabMouseOverBorder` |
