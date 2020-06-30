---
title: Typowe wzorce kontrolki
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547449"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolek dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Formanty standardowe

### <a name="overview"></a>Omówienie
 Formanty standardowe składają się na większość interfejsu użytkownika w programie Visual Studio. Większość typowych kontrolek używanych w interfejsie programu Visual Studio powinna być zgodna z [zaleceniami interakcji z pulpitem systemu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ten dokument jest przeznaczony dla programu Visual Studio i zawiera specjalne sytuacje lub szczegóły, które rozszerzają te wskazówki systemu Windows.

#### <a name="common-controls-in-this-topic"></a>Formanty wspólne w tym temacie

- [Paski przewijania](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Pola wejściowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Pola kombi i listy rozwijane](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Pola wyboru](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Przyciski radiowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Grupuj ramki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Przyciski i hiperlinki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Widoki drzewa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Styl wizualizacji
 Pierwszy aspekt, który należy wziąć pod uwagę, gdy kontrolki określają, czy kontrolki będą używane w interfejsie użytkownika. Kontrolki w standardowym interfejsie użytkownika są nienależącymi do siebie interfejsami użytkownika i muszą być zgodne z [normalnym stylem pulpitu systemu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), co oznacza, że nie są ponownie obsługiwane i powinny być wyświetlane w domyślnym wyglądzie formantu.

- **Okna dialogowe standardowe (narzędzia):** nie są one jeszcze obsługiwane. Nie należy powtarzać szablonu. Użyj podstawowych ustawień domyślnych stylu formantu.

- Okna **narzędzi, Edytory dokumentów, powierzchnie projektowe i dialogi z motywem:** Korzystaj z wyspecjalizowanego wyglądu przy użyciu usługi Color Service.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Paski przewijania
 Paski przewijania powinny być zgodne ze [typowymi wzorcami interakcji dla pasków przewijania systemu Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , chyba że zostały rozszerzone o informacje o zawartości, takie jak w edytorze kodu.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Pola wejściowe
 W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami pulpitu systemu Windows dla pól tekstowych](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualizacji

- Pola wejściowe nie powinny mieć stylu w oknach dialogowych. Użyj podstawowego stylu do kontrolki.

- Pola wejściowe z motywami powinny być używane tylko w oknach dialogowych i oknach narzędzi.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Pola tylko do odczytu będą miały szare (wyłączone) tło, ale domyślny (aktywny) pierwszy plan.

- Wymagane pola powinny zawierać **\<Required>** jako znaki wodne. Nie należy zmieniać koloru tła, z wyjątkiem rzadkich sytuacji.

- Sprawdzanie poprawności błędu: zobacz [powiadomienia i postęp dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Pola wejściowe powinny mieć rozmiar w celu dopasowania do zawartości, nie dopasowują szerokości okna, w którym są wyświetlane, ani nie mogą być arbitralnie zgodne z długością długiego pola, na przykład ścieżką. Długość może wskazywać użytkownikowi ograniczenia dotyczące liczby znaków dozwolonych w polu.

     ![Nieprawidłowa szerokość kontrolki pola wejściowego](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 — 01_IncorrectInputFieldControl") **nieprawidłowej długości pola wejściowego: jest mało prawdopodobne, że nazwa będzie taka długa.**

     ![Popraw szerokość kontrolki pola](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 — 02_CorrectInputFieldControl") wejściowego **Popraw długość pola wejściowego: pole wejściowe jest rozsądną szerokością dla oczekiwanej zawartości.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Pola kombi i listy rozwijane
 W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows, aby uzyskać listę rozwijaną i pola kombi](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualizacji

- W oknie dialogowym narzędzia nie należy zmienić szablonu kontrolki. Użyj podstawowego stylu do kontrolki.

- W tym interfejsie użytkownika pola kombi i listy rozwijane są zgodne ze standardowymi motywami dla kontrolek.

#### <a name="layout"></a>Layout
 Pola kombi i listy rozwijane powinny mieć rozmiar w celu dopasowania do zawartości, nie dopasowują szerokości okna, w którym są wyświetlane, ani nie są arbitralnie zgodne z długością długiego pola, na przykład ścieżką.

 ![Nieprawidłowy układ usuwania&#45;w dół](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 — 03_IncorrectDropDownLayout")

 **Niepoprawna długość pola dla kontrolki rozwijalnej**

 ![Poprawna&#45;w dół układu](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 — 04_CorrectDropDownLayout")

 **Prawidłowa długość pola dla kontrolki rozwijanej**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Pola wyboru
 W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualizacji

- W oknie dialogowym narzędzia nie należy zmienić szablonu kontrolki. Użyj podstawowego stylu do kontrolki.

- W interfejsie użytkownika z motywem pola wyboru są zgodne ze standardowymi motywami dla kontrolek.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Interakcja z polem wyboru nigdy nie może przechodzić do okna dialogowego ani do innego obszaru.

- Wyrównaj pola wyboru z linią bazową pierwszego wiersza tekstu.

     Nieprawidłowe wyrównanie pola wyboru nieprawidłowe ![wyrównanie pola](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 — 05_IncorrectCheckBoxAlign") wyboru **: pole wyboru jest wyśrodkowane w tekście.**

     Poprawne wyrównanie pola wyboru poprawna ![wyrównanie pola](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 — 06_CorrectCheckBoxAlign") wyboru **: pole wyboru jest wyrównane z linią bazową pierwszego wiersza tekstu.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Przyciski radiowe
 W przypadku typowych zachowań interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualizacji
 W oknach dialogowych narzędzi, nie należy określać przycisków radiowych. Użyj podstawowego stylu do kontrolki.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje
 Nie jest konieczne użycie ramki grupy w celu zawrzeć opcji radiowych.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Grupuj ramki
 W przypadku typowych zachowań interakcji postępuj zgodnie ze [wskazówkami dla komputerów z systemem Windows dla ramek grup](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Styl wizualizacji
 W oknach dialogowych, nie należy grupować ramek. Użyj podstawowego stylu do kontrolki.

#### <a name="layout"></a>Layout

- Nie jest konieczne użycie ramki grupy w celu zamieszczenia opcji radiowych, chyba że trzeba zachować rozróżnienie grupy w ścisłym układzie.

- Nigdy nie używaj ramki grupy dla pojedynczej kontrolki.

- Czasami jest akceptowalne użycie reguły poziomej zamiast kontenera ramek grupy.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Kontrolki tekstu

### <a name="labels"></a>Etykiety

#### <a name="active-label-state"></a>Stan aktywnej etykiety

##### <a name="utility-standard-dialogs"></a>Narzędzia (standardowe) — okna dialogowe

- Ogólnie rzecz biorąc, postępuj zgodnie ze wskazówkami dla komputerów z systemem Windows.

- W oknach dialogowych, etykiety powinny wyglądać bez pogrubienia, w standardowym kolorze czcionki i tekstu. Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Wielokropek powinny zawsze podążać za etykietami.

##### <a name="signature-themed-dialogs"></a>Okna dialogowe podpisu (z motywem))
 Kontrolki etykiety mogą być pogrubione lub lekko szare.

#### <a name="disabled-label-state"></a>Stan wyłączonej etykiety
 Etykiety powinny odzwierciedlać wygląd kontrolki, z którą są skojarzone. Na przykład, jeśli skojarzony formant jest wyłączony, etykieta powinna być wyszarzona i wyłączona. Jest to zwykle obsługiwane przez system operacyjny i nie wymaga specjalnego traktowania.

#### <a name="dynamic-labels"></a>Etykiety dynamiczne
 Etykiety dynamiczne zmieniają się w zależności od bieżącego zaznaczenia. Jeśli to możliwe, użyj dynamicznych etykiet w układach wzorzec/szczegóły, aby pomóc użytkownikowi zrozumieć, że wyświetlane informacje dotyczą określonego wyboru, a nie ogólnych informacji.

 ![Etykieta dynamiczna używana z zawartością dynamiczną](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 — 01_DynamicLabel")

 **Przykład etykiety dynamicznej używanej z zawartością dynamiczną**

#### <a name="instructional-text"></a>Tekst instruktażowy
 Niektóre elementy interfejsu korzystają z tekstu instruktażowego, aby pomóc użytkownikowi zrozumieć cel interfejsu użytkownika lub wskazać, która akcja ma zostać podjęta.

- Tekst instruktażowy jest najbardziej typowy u góry okien dialogowych, ale może być wyświetlany w innych obszarach, aby można było wykonać instrukcje dla złożonego grupowania formantów.

- Tekst instruktażowy nie jest interaktywny, ale może zawierać hiperłącze do tematów pomocy.

- Używaj tekstu instruktażowego i tylko wtedy, gdy jest to wymaganie.

##### <a name="formatting"></a>Formatowanie
 Tekst instruktażowy powinien być czcionką środowiskową, standardowym (niezgodnym) tekstem kontrolnym. Zobacz [czcionki i formatowanie dla programu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Aby uzyskać szczegółowe informacje na temat pisania tekstu instruktażowego, zobacz [tekst interfejsu użytkownika i terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formatowanie tekstu instruktażowego](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 — 02_InstructionalTextFormatting")

 **Tekst instruktażowy w oknie dialogowym programu Visual Studio**

#### <a name="informational-text"></a>Tekst informacyjny
 Tekst informacyjny jest tekstem, który daje użytkownikowi informacje dodatkowe. Może być on statyczny lub dynamiczny albo używany jako powiadomienie. Jest zawsze tylko do odczytu, ale jeśli jest przydatne, aby użytkownik miał możliwość kopiowania informacji, tekst dynamiczny powinien być umieszczony w kontenerze sterowania, takim jak pole tekstowe tylko do odczytu.

##### <a name="dynamic-context-specific-text"></a>Tekst dynamiczny (specyficzny dla kontekstu)
 Tekst informacji dynamicznych zmienia się w zależności od kontekstu, na przykład gdy użytkownik przełącza fokus. Często, ale nie zawsze, zawartość dynamiczna jest sparowana z etykietą dynamiczną.

 ![Tekst informacji dynamicznych](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 — 03_InformationalDynamicText")

 **Dynamiczne zmiany tekstu informacyjnego w zależności od kontekstu.**

##### <a name="formatting"></a>Formatowanie
 Istnieją dwa sposoby wyświetlania pól tekstowych tylko do odczytu: bezpośrednio na powierzchni interfejsu użytkownika (patrz powyżej) lub zawarte w innej kontrolce, takiej jak ramka grupy lub pole tekstowe. Jest on poprawny w zależności od sytuacji. Aby określić, jak przedstawić informacje tylko do odczytu, należy do projektanta funkcji.

 Tekst może znajdować się wewnątrz pola tekstowego tylko do odczytu. Zazwyczaj oznacza to, że można wybrać i skopiować zawartość, chociaż nie można jej edytować.

 ![Formatowanie tekstu informacyjnego dla pól tylko do odczytu&#45;](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 — 04_InformationalFormatting")

 **Formatowanie tekstu informacyjnego dla pól tylko do odczytu**

#### <a name="watermarks"></a>Znaki wodne
 Chociaż słowa mogą być takie same, różnica między znakami wodnymi a tekstem instruktażowym oznacza, że znaki wodne są zastępowane zawartością, gdy formant/okno nie jest puste, a tekst instruktażowy pozostaje widoczny przez cały czas.

 Nie należy używać znaków wodnych, gdy okno lub kontrolka są puste. Wskazują, co należy zrobić, aby wypełnić obszar i może zawierać linki akcji do otwierania odpowiednich okien, takich jak źródło przeciągania.

##### <a name="visual-style"></a>Styl wizualizacji

- Znaki wodne powinny być wyśrodkowane w poziomie w oknie.

- Znaki wodne powinny być wyrównane do środka, a nie wyrównane do lewej.

- Znaki wodne mogą być wyśrodkowane w pionie lub umieszczone w górnej części obszaru. Jeśli znajduje się w górnej części obszaru, musi być wystarczająco dużo miejsca, aby wyróżnić znak wodny.

- Użyj `Environment.GrayText` czcionki tokenu koloru i standardowego środowiska. Hiperłącza powinny używać standardowych tokenów udostępnionych hiperlinków: `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , `Environment.PanelHyperlinkPressed` , i `Environment.PanelHyperlinkDisabled` .

- Nie można wybierać znaków wodnych w tle

- Jeśli to możliwe, Dołącz linki w znaku wodnym, aby ułatwić użytkownikom rozpoczęcie pracy.

  ![Tekst znaku wodnego w oknie projektanta](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 — 05_Watermark1")

  ![Tekst znaku wodnego w oknie narzędzia](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 — 06_Watermark2")

  **Przykłady tekstu wodnego w programie Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Przyciski i hiperlinki

### <a name="overview"></a>Omówienie
 Przyciski i kontrolki łączy (Hyperlinks) powinny być zgodne z [podstawowymi wskazówkami systemu Windows dotyczącymi hiperłączy](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) do użycia, wyrazów, rozmiarów i odstępów.

### <a name="choosing-between-buttons-and-links"></a>Wybieranie między przyciskami i łączami
 Tradycyjnie przyciski zostały użyte w przypadku akcji i hiperlinków zostały zarezerwowane do nawigacji. Przyciski mogą być używane we wszystkich przypadkach, ale rola linków została rozwinięta w programie Visual Studio, dzięki czemu przyciski i linki są bardziej zamienne w pewnych warunkach.

 Kiedy używać przycisków poleceń:

- Polecenia podstawowe

- Wyświetlanie okien służących do zbierania danych wejściowych lub dokonywania wyboru, nawet jeśli są poleceniami pomocniczymi

- Destrukcyjne lub nieodwracalne akcje

- Przyciski zobowiązań w ramach kreatorów i przepływów stron

  Unikaj przycisków poleceń w oknach narzędzi lub jeśli potrzebujesz więcej niż dwóch wyrazów dla etykiety. Linki mogą mieć dłuższe etykiety.

  Kiedy używać łączy:

- Nawigacja do innego okna, dokumentu lub strony sieci Web

- Sytuacje, które wymagają dłuższej etykiety lub krótkiego zdania do opisywania zamiaru akcji

- Przyległe miejsca, w których przycisk może przeciążać interfejs użytkownika, pod warunkiem, że działanie nie jest szkodliwe ani nieodwracalne

- Wyróżnianie poleceń pomocniczych w sytuacjach, gdy istnieje wiele poleceń

#### <a name="examples"></a>Przykłady
 ![Linki do poleceń na pasku informacji po wyświetleniu komunikatu o stanie](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 — 01_CommandLinkInfobar")

 **Linki poleceń używane na pasku informacji po wyświetleniu komunikatu o stanie**

 ![Linki używane w menu podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 — 02_LinksInCodeLens")

 **Linki używane w menu podręcznym CodeLens**

 ![Linki używane jako polecenia pomocnicze](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 — 03_LinksAsSecondaryCommands")

 **Linki używane dla poleceń pomocniczych, w których przyciski byłyby przyciągane zbyt wiele uwagi**

### <a name="common-buttons"></a>Typowe przyciski

#### <a name="text"></a>Tekst
 Postępuj zgodnie z instrukcjami dotyczącymi pisania w [tekście i terminologii interfejsu użytkownika](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Styl wizualizacji

##### <a name="standard-dialogs"></a>Standardowe okna dialogowe
 Większość przycisków w programie Visual Studio pojawi się w standardowych oknach dialogowych i nie należy mieć stylów. Powinny one odzwierciedlać standardowy wygląd przycisków, które są podyktowane przez system operacyjny.

##### <a name="themed"></a>Tematyczne
 W niektórych przypadkach przyciski mogą być używane w interfejsie użytkownika z stylem, a te przyciski muszą mieć odpowiednio styl. Zobacz [okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) , aby uzyskać informacje o kontrolkach z nimi.

### <a name="special-buttons"></a>Przyciski specjalne

#### <a name="browse-buttons"></a>Przeglądaj... przyciski
 **[Przeglądaj...]** przyciski są używane w siatkach, oknach dialogowych i oknach narzędzi i innych niemodalnych elementów interfejsu użytkownika. Wyświetla selektor, który pomaga użytkownikowi w wypełnianiu wartości do kontrolki. Istnieją dwie odmiany tego przycisku, Long i Short.

 ![Długi &#91;Przeglądaj... &#93; przycisk](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 — 04_BrowseLong")

 **Przycisk Long [Przeglądaj...]**

 ![Krótka wielokropek&#45;tylko &#91;przeglądania... &#93; przycisk](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 — 05_BrowseShort")

 **Wielokropek — przycisk krótki [...]**

 Kiedy używać przycisku skróconego tylko do wielokropka:

- Jeśli w oknie dialogowym istnieje więcej niż jeden długi przycisk **(Przeglądaj...])** , na przykład gdy kilka pól umożliwia przeglądanie. Użyj krótkiego przycisku **[...]** dla każdej z nich, aby uniknąć pomylenia kluczy dostępu utworzonych w tej sytuacji (**&przeglądać** i **B&rzeglądaj** w tym samym oknie dialogowym).

- W ścisłym oknie dialogowym lub w przypadku braku uzasadnionego miejsca na umieszczenie długiego przycisku.

- Jeśli przycisk pojawi się w kontrolce siatki.

  Wskazówki dotyczące korzystania z przycisku:

- Nie należy używać klucza dostępu. Aby uzyskać do niego dostęp przy użyciu klawiatury, użytkownik musi nawiązać kontrolę nad sąsiednim formantem. Upewnij się, że kolejność tabulacji jest taka, że dowolny przycisk przeglądania jest przypadał natychmiast po polu, które zostanie wypełnione. Nigdy nie używaj znaku podkreślenia poniżej pierwszego okresu.

- Ustaw właściwość **Nazwa** usługi Microsoft Active ACCESSIBILITY (MSAA) na wartość **Przeglądaj...** (w tym wielokropek), aby czytelnicy ekranu odczytali ją jako "Przeglądaj", a nie "kropka-kropka" lub "okres-okresowo". W przypadku formantów zarządzanych oznacza to ustawienie właściwości **accessibleName** .

- Nigdy nie używaj przycisku wielokropka **[...]** dla niczego poza akcją przeglądania. Na przykład jeśli potrzebujesz przycisku **[New...]** , ale nie masz wystarczającej ilości miejsca na tekst, należy ponownie zaprojektować okno dialogowe.

##### <a name="sizing-and-spacing"></a>Ustalanie wielkości i odstępów
 ![Ustalanie rozmiarów &#91;przyciski Przeglądaj... &#93;](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 — 06_BrowseSizing")

 **Zmienianie rozmiarów przycisków [Przeglądaj...]**

 ![Odstępy &#91;Przeglądaj... &#93; przyciski](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 — 07_BrowseSpacing")

 **Przyciski odstępów [Przeglądaj...]**

#### <a name="graphical-buttons"></a>Przyciski graficzne
 Niektóre przyciski powinny zawsze używać graficznego obrazu i nigdy nie zawierają tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacją. Są one często używane w przypadku selektorów pól i innych list z sortowaniem.

> [!NOTE]
> Użytkownicy muszą należeć do tych przycisków (nie ma kluczy dostępu), dlatego należy umieścić je w kolejności rozsądnej. Mapuj Właściwość Name przycisku na akcję, którą wykonuje, aby czytniki ekranu prawidłowo interpretują akcję przycisku.

|Nazwa|Image (Obraz)|
|-|-|
|Dodaj|![Graficzny przycisk "Dodaj"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 — 08_ButtonAdd")|
|Usuń|![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 — 09_ButtonRemove")|
|Dodaj wszystko|![Graficzny przycisk "Dodaj wszystko"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 — 10_ButtonAddAll")|
|Usuń wszystko|![Graficzny przycisk "Usuń wszystko"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 — 11_ButtonRemoveAll")|
|Przenieś w górę|![Graficzny przycisk "Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 — 12_ButtonMoveUp")|
|Przenieś w dół|![Graficzny przycisk "Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 — 13_ButtonMoveDown")|
|Usuń|![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 — 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Ustalanie wielkości i odstępów
 Ustalanie rozmiarów przycisków graficznych jest takie samo jak w przypadku krótkiej wersji przycisku **[Przeglądaj...]** (26x23 pikseli):

 ![Przycisk z widocznym kolorem przezroczystym i bez niego](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 — 15_GraphicalButtonSpacing")

 **Wygląd obrazu graficznego na przycisku, z widocznym kolorem przezroczystym i bez niego**

### <a name="hyperlinks"></a>Hiperlinki
 Hiperłącza są dobrze dopasowane do akcji opartych na nawigacji, takich jak otwieranie tematu pomocy, modalnego okna dialogowego lub kreatora. Jeśli hiperłącze jest używane dla polecenia, powinno zawsze wyświetlać widoczną i zauważalną zmianę w interfejsie użytkownika. Ogólnie rzecz biorąc, akcje zatwierdzające akcję (takie jak Save, Cancel i Delete) są lepiej przekazane przy użyciu przycisku.

#### <a name="writing-style"></a>Styl pisania
 Postępuj zgodnie ze [wskazówkami dla pulpitu systemu Windows dotyczącymi tekstu interfejsu użytkownika](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Nie używaj "Dowiedz się więcej na temat", "" więcej informacji o "lub" Uzyskaj pomoc dotyczącą tego "sformułować". Zamiast tego fraza Pomoc dotycząca łączenia tekstu w postaci pytania podstawowego odpowiada treści pomocy. Na przykład "**Jak mogę dodać serwer do Eksplorator serwera?**"

#### <a name="visual-style"></a>Styl wizualizacji

- Hiperlinki powinny zawsze używać [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperłącze nie ma poprawnie stylu, błyskuje kolor czerwony, gdy aktywny lub pokazuje inny kolor po odwiedzeniu.

- Nie dołączaj podkreśleń pod stanem spoczynku formantu, chyba że łącze jest fragmentem zdania w obrębie pełnego zdania, takiego jak w przypadku znaku wodnego.

- Podkreślenia nie powinny być wyświetlane po aktywowaniu. Zamiast tego informacje zwrotne dla użytkownika, że łącze jest aktywne, to niewielka zmiana koloru i odpowiedni kursor linku.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Widoki drzewa

### <a name="overview"></a>Omówienie
 Widoki drzewa zapewniają sposób organizowania list złożonych w grupy nadrzędny-podrzędny. Użytkownik może rozwinąć lub zwinąć grupy nadrzędne, aby pokazać lub ukryć bazowe elementy podrzędne. Każdy element w widoku drzewa można wybrać, aby zapewnić dalsze działanie.

 Ten temat dotyczy akceptowalnego zastosowania, prawidłowego projektu i funkcjonalności widoków drzewa.

#### <a name="in-this-topic"></a>W tym temacie:

- [Styl wizualizacji](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interakcje](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Styl wizualizacji

#### <a name="expanders"></a>Ekspanderów znajdujących
 Kontrolki widoku drzewa powinny być zgodne z projektem ekspandera używanym przez system Windows i program Visual Studio. Każdy węzeł używa kontrolki ekspandera, aby odsłonić lub ukryć elementy bazowe. Użycie kontrolki Ekspander zapewnia spójność dla użytkowników, którzy mogą napotkać różne widoki drzewa w systemie Windows i programie Visual Studio.

 ![Poprawna kontrolka widoku drzewa](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 — 1_TreeViewCorrect")

 **Poprawne: odpowiedni styl węzła widoku drzewa przy użyciu kontrolki ekspandera**

 ![Niepoprawne węzły widoku drzewa](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 — 2_TreeViewIncorrect1")

 **Nieprawidłowy: niewłaściwy styl węzła widoku drzewa**

#### <a name="selection"></a>Wybór
 Po wybraniu węzła w widoku drzewa, podświetla powinna rozwijać do pełnej szerokości kontrolki widoku drzewa. Dzięki temu użytkownicy mogą jasno określić, który element został wybrany. Kolory zaznaczenia powinny odzwierciedlać bieżącą kompozycję programu Visual Studio.

 ![Poprawna kontrolka widoku drzewa](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 — 1_TreeViewCorrect")

 **Poprawna: wyróżnienie wybranego węzła dopasowuje całą szerokość kontrolki widoku drzewa.**

 ![Niewłaściwe wyróżnienie widoku drzewa](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 — 3_TreeViewIncorrect2")

 **Nieprawidłowe: wyróżnienie wybranego węzła nie pasuje do całej szerokości kontrolki widoku drzewa.**

#### <a name="icons"></a>Ikony
 Ikon należy używać tylko w formantach widoku drzewa, jeśli pomagają w wizualnym identyfikacji różnic między elementami. Ogólnie rzecz biorąc, ikony powinny być używane tylko na listach heterogenicznych, w których ikony zawierają informacje pozwalające na odróżnienie typów elementów. Na jednorodnej liście przy użyciu ikon można często postrzegać jako szum i należy je unikać. W takim przypadku ikona grupy (element nadrzędny) może przekazywać typ elementów w tym elemencie. Wyjątkiem od tej reguły jest to, że ikona jest dynamiczna i jest używana do wskazania stanu.

#### <a name="scroll-bars"></a>Paski przewijania
 Paski przewijania powinny być zawsze ukrywane, jeśli zawartość mieści się w kontrolce widoku drzewa. Pasek przewijania może być ukryty lub częściowo przezroczysty w przewijanym oknie i pojawia się, gdy okno zawierające widok drzewa ma fokus lub po umieszczeniu w nim samego widoku drzewa.

 ![Widok drzewa z paskami przewijania](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 — 4_Scrollbars")

 **Wyświetlane są pionowe i poziome paski przewijania, ponieważ zawartość przekroczyła limity kontrolki widok drzewa.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Zależności

#### <a name="context-menus"></a>Menu kontekstowe
 Węzeł widoku drzewa może ujawnić opcje podmenu w menu kontekstowym. Zazwyczaj dzieje się tak, gdy użytkownik kliknie prawym przyciskiem myszy element lub naciśnie klawisz menu na klawiaturze systemu Windows z wybranym elementem. Należy pamiętać, że węzeł zyskuje fokus i jest wybierany. Dzięki temu użytkownik może określić, do którego elementu podmenu należy.

 ![Wybrany węzeł drzewa i menu kontekstowe](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 — 5_ContextMenu")

 **Element generujący menu kontekstowe zyskuje fokus, aby poinformować użytkownika o wybranym elemencie.**

#### <a name="keyboard"></a>Klawiatura
 Widok drzewa powinien umożliwiać zaznaczanie elementów i rozszerzanie/zwijanie węzłów przy użyciu klawiatury. Dzięki temu Nawigacja spełnia nasze wymagania dotyczące ułatwień dostępu.

##### <a name="tree-view-control"></a>Kontrolka widoku drzewa
 Kontrolki drzewa programu Visual Studio powinny być zgodne ze wspólną nawigacją na klawiaturze:

- **Strzałka w górę:** Zaznacz elementy, przenosząc drzewo

- **Strzałka w dół:** Zaznaczanie elementów przez przeniesienie drzewa

- **Strzałka w prawo:** Rozwiń węzeł drzewa

- **Strzałka w lewo:** Zwiń węzeł w drzewie

- **Wprowadź klucz:** Inicjowanie, ładowanie i wykonywanie wybranego elementu

##### <a name="trid-tree-view-and-grid-view"></a>TrID (widok drzewa i widok siatki)
 Formant TrID to złożona kontrolka, która zawiera widok drzewa w obrębie siatki. Rozwijanie, zwijanie i nawigowanie po drzewie powinno uwzględniać te same polecenia klawiatury jak widok drzewa, z następującymi dodatkami:

- **Strzałka w prawo:** Rozwiń węzeł. Po rozwinięciu węzła powinien on kontynuować nawigowanie do najbliższej kolumny po prawej stronie. Nawigacja powinna zostać zatrzymana na końcu wiersza.

- **Karta:** Nawiguje do najbliższej komórki po prawej stronie.  Na końcu wiersza Nawigacja przechodzi do następnego wiersza.

- **SHIFT + TAB:** Nawiguje do najbliższej komórki po lewej stronie.  Na początku wiersza Nawigacja przechodzi do prawej komórki w poprzednim wierszu.

  ![Kontrolka TrID w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 — 6_Trid")

  **Kontrolka TrID w programie Visual Studio**
