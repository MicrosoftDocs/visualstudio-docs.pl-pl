---
title: Wzorce formantów wspólnych dla programu Visual Studio | Microsoft Docs
description: Dowiedz się więcej na temat sposobu, w jaki program Visual Studio Common Controls postępuje zgodnie ze wskazówkami dotyczącymi interakcji z pulpitem systemu Windows, a szczególnie
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c1caccebf1dc14146bef214a4d33e1216243780
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715889"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolek dla programu Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Formanty standardowe

### <a name="overview"></a>Omówienie
Formanty standardowe składają się na większość interfejsu użytkownika w programie Visual Studio. Większość typowych kontrolek używanych w interfejsie programu Visual Studio powinna być zgodna z [zaleceniami interakcji z pulpitem systemu Windows](/windows/desktop/uxguide/controls). Ten temat dotyczy programu Visual Studio i obejmuje specjalne sytuacje lub szczegóły, które rozszerzają te wskazówki systemu Windows.

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

#### <a name="visual-style"></a>Styl wizualny
Pierwszy aspekt, który należy wziąć pod uwagę, gdy kontrolki określają, czy kontrolki będą używane w interfejsie użytkownika. Kontrolki w standardowym interfejsie użytkownika są nienależącymi do siebie interfejsami użytkownika i muszą być zgodne z [normalnym stylem pulpitu systemu Windows](/windows/desktop/uxguide/controls), co oznacza, że nie są ponownie obsługiwane i powinny być wyświetlane w domyślnym wyglądzie formantu.

- **Okna dialogowe standardowe (narzędzia):** nie są one jeszcze obsługiwane. Nie należy powtarzać szablonu. Użyj podstawowych ustawień domyślnych stylu formantu.

- Okna **narzędzi, Edytory dokumentów, powierzchnie projektowe i dialogi z motywem:** Korzystaj z wyspecjalizowanego wyglądu przy użyciu usługi Color Service.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Paski przewijania
 Paski przewijania powinny być zgodne ze [typowymi wzorcami interakcji dla pasków przewijania systemu Windows](/windows/desktop/Controls/about-scroll-bars) , chyba że zostaną rozszerzone o informacje o zawartości, takie jak w edytorze kodu.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Pola wejściowe
 W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami pulpitu systemu Windows dla pól tekstowych](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Styl wizualny

- Pola wejściowe nie powinny mieć stylu w oknach dialogowych. Użyj podstawowego stylu do kontrolki.

- Pola wejściowe z motywami powinny być używane tylko w oknach dialogowych i oknach narzędzi.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Pola tylko do odczytu będą miały szare (wyłączone) tło, ale domyślny (aktywny) pierwszy plan.

- Wymagane pola powinny zawierać **\<Required>** jako znaki wodne. Nie należy zmieniać koloru tła, z wyjątkiem rzadkich sytuacji.

- Sprawdzanie poprawności błędu: zobacz [powiadomienia i postęp dla programu Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Pola wejściowe powinny mieć rozmiar, aby dopasować do zawartości, nie dopasowują szerokości okna, w którym są wyświetlane, ani nie mają arbitralnie dopasowanej długości długiego pola, takiego jak ścieżka. Długość może wskazywać użytkownikowi ograniczenia dotyczące liczby znaków dozwolonych w polu.

     ![Nieprawidłowa długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie taka długa.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 — 01_IncorrectInputFieldControl")<br />Nieprawidłowa długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie taka długa.

     ![Poprawna długość pola wejściowego: pole wejściowe jest rozsądną szerokością dla oczekiwanej zawartości.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 — 02_CorrectInputFieldControl")<br />Poprawna długość pola wejściowego: pole wejściowe jest rozsądną szerokością dla oczekiwanej zawartości.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Pola kombi i listy rozwijane
W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows, aby uzyskać listę rozwijaną i pola kombi](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Styl wizualny

- W oknie dialogowym narzędzia nie należy zmienić szablonu kontrolki. Użyj podstawowego stylu do kontrolki.

- W tym interfejsie użytkownika pola kombi i listy rozwijane są zgodne ze standardowymi motywami dla kontrolek.

#### <a name="layout"></a>Layout
Pola kombi i listy rozwijane powinny mieć rozmiar w celu dopasowania do zawartości, nie dopasowują szerokości okna, w którym są wyświetlane, ani nie są arbitralnie zgodne z długością długiego pola, na przykład ścieżką.

![Nieprawidłowe: Szerokość listy rozwijanej jest zbyt długa dla zawartości, która zostanie wyświetlona.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 — 03_IncorrectDropDownLayout")<br />Nieprawidłowe: Szerokość listy rozwijanej jest zbyt długa dla zawartości, która zostanie wyświetlona.

![Poprawna wartość: Lista rozwijana ma rozmiar, aby umożliwić wzrostowi tłumaczenia, ale nie jest to konieczne.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 — 04_CorrectDropDownLayout")<br />Poprawna wartość: Lista rozwijana ma rozmiar, aby umożliwić wzrostowi tłumaczenia, ale nie jest to konieczne.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Pola wyboru
W przypadku typowego zachowania interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Styl wizualny

- W oknie dialogowym narzędzia nie należy zmienić szablonu kontrolki. Użyj podstawowego stylu do kontrolki.

- W interfejsie użytkownika z motywem pola wyboru są zgodne ze standardowymi motywami dla kontrolek.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Interakcja z polem wyboru nigdy nie może przechodzić do okna dialogowego ani do innego obszaru.

- Wyrównaj pola wyboru z linią bazową pierwszego wiersza tekstu.

     ![Nieprawidłowe: pole wyboru jest wyśrodkowane w tekście.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 — 05_IncorrectCheckBoxAlign")<br />Nieprawidłowe: pole wyboru jest wyśrodkowane w tekście.

     ![Poprawne: pole wyboru jest wyrównane z pierwszym wierszem tekstu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 — 06_CorrectCheckBoxAlign")<br />Poprawne: pole wyboru jest wyrównane z pierwszym wierszem tekstu.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Przyciski radiowe
W przypadku typowych zachowań interakcji postępuj zgodnie z [zaleceniami dla komputerów stacjonarnych z systemem Windows](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych narzędzi, nie należy określać przycisków radiowych. Użyj podstawowego stylu do kontrolki.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje
Nie jest konieczne użycie ramki grupy w celu zamieszczenia opcji radiowych, chyba że trzeba zachować rozróżnienie grupy w ścisłym układzie.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Grupuj ramki
W przypadku typowych zachowań interakcji postępuj zgodnie ze [wskazówkami dla komputerów z systemem Windows dla ramek grup](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych, nie należy grupować ramek. Użyj podstawowego stylu do kontrolki.

#### <a name="layout"></a>Layout

- Nie jest konieczne użycie ramki grupy w celu zamieszczenia opcji radiowych, chyba że trzeba zachować rozróżnienie grupy w ścisłym układzie.

- Nigdy nie używaj ramki grupy dla pojedynczej kontrolki.

- Czasami jest akceptowalne użycie reguły poziomej zamiast kontenera ramek grupy.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Kontrolki tekstu

### <a name="static-text-fields"></a>Statyczne pola tekstowe

Statyczne pole tekstowe prezentuje informacje tylko do odczytu i nie może zostać wybrane przez użytkownika. Unikaj używania jej w przypadku tekstu, który użytkownik może chcieć skopiować do Schowka. Jednak tekst statyczny tylko do odczytu może ulec zmianie w celu odzwierciedlenia zmiany stanu. W poniższym przykładzie, nazwa wyjściowa tekst statyczny w grupie informacji zmienia się w celu odzwierciedlenia zmian wprowadzonych w polu tekstowym głównego obszaru nazw.

Istnieją dwa sposoby wyświetlania informacji o tekście statycznym.

Tekst statyczny może być własny w oknie dialogowym bez żadnych brakujących konfliktów w przypadku braku konfliktu grupowania. Zdecyduj, czy dodatkowe linie pola są naprawdę konieczne. Przykładem jest wyświetlanie ścieżki katalogu w sekcji utworzonej przez wiersz grupy, jak pokazano poniżej:

![Statyczne informacje tekstowe w kontrolkach tekstu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statyczne informacje tekstowe w kontrolkach tekstu

W oknie dialogowym, w którym istnieją inne zgrupowane obszary i zawiera informacje mogą pomóc w czytelności i gdy sekcja może być ukryta lub pokazana (jak w okienku opis **okno właściwości** ) lub chcesz mieć spójność z PODOBNYm interfejsem użytkownika, umieść statyczny tekst wewnątrz pola. To pole grupy powinno być jedną regułą i być kolorowe przy użyciu `ButtonShadow` :

![Tekst statyczny w okno Właściwości](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Tekst statyczny w okno Właściwości

### <a name="read-only-text-box"></a>Pole tekstowe tylko do odczytu

Umożliwia to użytkownikowi wybranie tekstu wewnątrz pola, ale nie jego edytowanie. Te pola tekstowe są obramowane według zwykłej linii trójwymiarowej z `ButtonShadow` wypełnieniem.

Pole tekstowe może stać się aktywne (można je edytować), gdy użytkownik zmienia skojarzoną kontrolkę, taką jak zaznaczenie/odzaznaczenie pola wyboru lub wybranie/odzaznaczenie przycisku radiowego. Na przykład na stronie **&gt; Opcje narzędzi** pokazanej poniżej pole tekstowe **strony głównej** jest aktywne po usunięciu zaznaczenia pola wyboru **Użyj domyślnego** .

![Pole tekstowe tylko do odczytu, zawierające Stany nieaktywne i aktywne](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Pole tekstowe tylko do odczytu, zawierające Stany nieaktywne i aktywne

### <a name="using-text-in-dialogs"></a>Korzystanie z tekstu w oknach dialogowych

Najważniejsze wskazówki dotyczące tekstu w oknach dialogowych:

- Etykiety dla pól tekstowych, pól listy i ramek w oknach dialogowych niezwiązanych z motywem zaczynają się od czasownika, mają początkowo wielką część pierwszego wyrazu i kończą się dwukropkiem.

    > Kontrolki tekstu w oknach dialogowych, które są zgodne z [zaleceniami użytkownika pulpitu systemu Windows](/windows/desktop/uxguide/top-violations) i nie przyjmują końcowej interpunkcji, z wyjątkiem znaków zapytania w łączach pomocy.

- Etykiety dla pól wyboru i przycisków opcji zaczynają się od czasownika, początkowego kapitału pierwszego wyrazu i nie mają kończących się interpunkcji.

- Etykiety przycisków, menu, elementów menu i kart mają początkowe wersaliki dla każdego wyrazu (przypadek tytułowy).

- Terminologia etykiety powinna być zgodna z podobnymi etykietami w innych oknach dialogowych.

- Jeśli to możliwe, zanotuj lub Zatwierdź tekst przed przejściem do dewelopera w celu wdrożenia.

- Wszystkie kontrolki powinny mieć etykiety, z wyjątkiem szczególnych okoliczności, w których karta jest wystarczająca.
W razie potrzeby użyj tekstu pomocnika.

### <a name="helper-text"></a>Tekst pomocnika

Zawarte w oknach dialogowych, aby pomóc użytkownikowi zrozumieć cel okna dialogowego lub wskazać, która akcja ma zostać podjęta. Tekst pomocnika powinien być używany tylko wtedy, gdy jest to konieczne, aby uniknąć bałaganu prostych okien dialogowych. Dwie Wariacje tekstu pomocnika to okno dialogowe i znak wodny.

Obserwuj wspólne lokalizacje tekstu pomocnika i ostrożnie wprowadzaj nowe obszary. Typowe scenariusze dla tekstu pomocnika są następujące:

- Tekst pomocnika w oknach dialogowych, aby uzyskać dodatkowy kierunek współpracy ze złożonym oknem dialogowym.

- Tekst znaku wodnego w pustych oknach narzędzi lub oknach dialogowych, aby wyjaśnić, dlaczego żadna zawartość nie jest widoczna.

- Okienko opisu, takie jak u dołu **okno właściwości**.

- Tekst znaku wodnego w pustym edytorze, aby wyjaśnić działanie, które użytkownik powinien wykonać, aby rozpocząć pracę.

### <a name="dialog-helper-text"></a>Tekst pomocnika okna dialogowego

Projektant środowiska użytkownika może pomóc w ustaleniu, kiedy tekst pomocnika jest odpowiedni. Projektant może zdefiniować, gdzie pojawia się tekst pomocnika oraz jego ogólna zawartość. Pomoc dla użytkowników może zapisywać/edytować rzeczywisty tekst.

### <a name="watermarks"></a>Znaki wodne

Okna dialogowe korzystają z nieco różnych wytycznych dotyczących znaku wodnego. Ponieważ okno dialogowe może być zajęte za pomocą wielu elementów interfejsu użytkownika (etykiet, tekstu wskazówki, przycisków i innych kontrolek kontenera z tekstem), zwłaszcza gdy pojawiają się one w czerni, znaki wodne są lepiej ciemne w kolorze szarym (VSColor: `ButtonShadow` ). Zwykle znak wodny pojawia się wewnątrz kontrolki, takiej jak pole listy z białym tłem (VSColor: `Window` ).

- Tekst jest wyświetlany w kolorze ciemnoszarym (VSColor: `ButtonShadow` ). Jeśli jednak znak wodny pojawia się na średnim szarym lub innym kolorze (VSColor: `ButtonFace` ) w tle, a jego czytelność jest istotna, przejdź z czarnym tekstem (VSColor: `WindowText` ).

- Znaki wodne można wyśrodkować lub opróżnić z lewej strony. Stosuj standardowe reguły projektowania podczas podejmowania decyzji o wyrównaniu. Nie można wybrać znaku wodnego w tle.

![Przykładowy tekst znaku wodnego](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Przykładowy tekst znaku wodnego

### <a name="context-specific-dynamic-text"></a>Tekst specyficzny dla kontekstu (dynamiczny)

Tekst dynamiczny może być używany jeden z dwóch sposobów w oknie dialogowym lub niemodalny interfejs użytkownika: jako etykieta dynamiczna lub zawartość dynamiczna.

- Etykieta dynamiczna: typowym zastosowaniem dynamicznego tekstu jest w panelach opisowych, które oferują więcej informacji na temat wybranego elementu, na przykład w oknie dialogowym zawierającym listę elementów i właściwości dla tych elementów wyświetlanych w siatce po prawej stronie. Etykieta siatki właściwości może być dynamiczna, aby po zaznaczeniu elementu po lewej stronie siatka z prawej strony pokazywała informacje dla danego elementu.

- Tekst dynamiczny: może być przydatny w sytuacjach, w których konieczne jest wyświetlenie określonych informacji, a nie ogólnych informacji w ten sposób, ale należy zachować ostrożność.

Jeśli chcesz, aby użytkownicy mieli możliwość kopiowania informacji, tekst dynamiczny powinien znajdować się w polu tekstowym tylko do odczytu.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Przyciski i hiperlinki

### <a name="overview"></a>Omówienie
Przyciski i kontrolki łączy (Hyperlinks) powinny być zgodne z [podstawowymi wskazówkami systemu Windows dotyczącymi hiperłączy](/windows/desktop/uxguide/ctrl-links) do użycia, wyrazów, rozmiarów i odstępów.

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
![Linki poleceń używane na pasku informacji po wyświetleniu komunikatu o stanie](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 — 01_CommandLinkInfobar")<br />Linki poleceń używane na pasku informacji po wyświetleniu komunikatu o stanie

![Linki używane w menu podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 — 02_LinksInCodeLens")<br />Linki używane w menu podręcznym CodeLens

![Linki używane dla poleceń pomocniczych, w których przyciski byłyby przyciągane zbyt wiele uwagi](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 — 03_LinksAsSecondaryCommands")<br />Linki używane dla poleceń pomocniczych, w których przyciski byłyby przyciągane zbyt wiele uwagi

### <a name="common-buttons"></a>Typowe przyciski

#### <a name="text"></a>Tekst
Postępuj zgodnie z instrukcjami dotyczącymi pisania w [tekście i terminologii interfejsu użytkownika](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Styl wizualny

##### <a name="standard-unthemed"></a>Standardowa (niemotywnie)
Większość przycisków w programie Visual Studio będzie wyświetlana w oknach dialogowych narzędzi i nie powinna mieć stylu. Powinny one odzwierciedlać standardowy wygląd przycisków, które są podyktowane przez system operacyjny.

##### <a name="themed"></a>Tematyczne
W niektórych przypadkach przyciski mogą być używane w interfejsie użytkownika z stylem, a te przyciski muszą mieć odpowiednio styl. Zobacz [okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) , aby uzyskać informacje o kontrolkach z nimi.

### <a name="special-buttons"></a>Przyciski specjalne

#### <a name="browse-buttons"></a>Przeglądaj... przyciski
**[Przeglądaj...]** przyciski są używane w siatkach, oknach dialogowych i oknach narzędzi i innych niemodalnych elementów interfejsu użytkownika. Wyświetla selektor, który pomaga użytkownikowi w wypełnianiu wartości do kontrolki. Istnieją dwie odmiany tego przycisku, Long i Short.

![Przycisk Long [Przeglądaj...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 — 04_BrowseLong")<br />Przycisk Long [Przeglądaj...]

![Wielokropek — przycisk krótki [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 — 05_BrowseShort")<br />Wielokropek — przycisk krótki [...]

Kiedy używać przycisku skróconego tylko do wielokropka:

- Jeśli w oknie dialogowym istnieje więcej niż jeden długi przycisk **[Przeglądaj...]** , tak jak w przypadku, gdy kilka pól umożliwia przeglądanie. Użyj krótkiego przycisku **[...]** dla każdej z nich, aby uniknąć pomylenia kluczy dostępu utworzonych w tej sytuacji (**&przeglądać** i **B&rzeglądaj** w tym samym oknie dialogowym).

- W ścisłym oknie dialogowym lub w przypadku braku uzasadnionego miejsca na umieszczenie długiego przycisku.

- Jeśli przycisk pojawi się w kontrolce siatki.

Wskazówki dotyczące korzystania z przycisku:

- Nie używaj klucza dostępu. Aby uzyskać do niego dostęp przy użyciu klawiatury, użytkownik musi nawiązać kontrolę nad sąsiednim formantem. Upewnij się, że kolejność tabulacji jest taka, że dowolny przycisk przeglądania jest przypadał natychmiast po polu, które zostanie wypełnione. Nigdy nie używaj znaku podkreślenia poniżej pierwszego okresu.

- Ustaw właściwość **Nazwa** usługi Microsoft Active ACCESSIBILITY (MSAA) na wartość **Przeglądaj...** (w tym wielokropek), aby czytelnicy ekranu odczytali ją jako "Przeglądaj", a nie "kropka-kropka" lub "okres-okresowo". W przypadku formantów zarządzanych oznacza to ustawienie właściwości **accessibleName** .

- Nigdy nie używaj przycisku wielokropka **[...]** dla niczego poza akcją przeglądania. Na przykład jeśli potrzebujesz przycisku **[New...]** , ale nie masz wystarczającej ilości miejsca na tekst, należy ponownie zaprojektować okno dialogowe.

##### <a name="sizing-and-spacing"></a>Ustalanie wielkości i odstępów
![Ustawianie wielkości [Przeglądaj...] przyciski: wersja standardowa to 75x23 pikseli, krótka wersja to 26x23 pikseli](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 — 06_BrowseSizing")<br />Zmienianie rozmiarów przycisków [Przeglądaj...]

![Przyciski odstępów [Przeglądaj...]: odstępy między powiązanymi kontrolkami i standardowym przyciskiem przeglądania 7 pikseli, odstępy między kontrolką powiązaną a krótkim przyciskiem przeglądania 5 pikseli](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 — 07_BrowseSpacing")<br />Przyciski odstępów [Przeglądaj...]

#### <a name="graphical-buttons"></a>Przyciski graficzne
Niektóre przyciski powinny zawsze używać graficznego obrazu i nigdy nie zawierają tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacją. Są one często używane w przypadku selektorów pól i innych list z sortowaniem.

> [!NOTE]
> Użytkownicy muszą należeć do tych przycisków (nie ma kluczy dostępu), dlatego należy umieścić je w kolejności rozsądnej. Mapuj `name` Właściwość przycisku do akcji, którą wykonuje, tak aby czytniki ekranu prawidłowo interpretują akcję przycisku.

| Funkcja | Przycisk |
| --- | --- |
| Dodaj | ![Graficzny przycisk "Dodaj"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 — 08_ButtonAdd") |
| Usuń | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 — 09_ButtonRemove") |
| Dodaj wszystko | ![Graficzny przycisk "Dodaj wszystko"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 — 10_ButtonAddAll") |
| Usuń wszystko | ![Graficzny przycisk "Usuń wszystko"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 — 11_ButtonRemoveAll") |
| Przenieś w górę | ![Graficzny przycisk "Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 — 12_ButtonMoveUp") |
| Przenieś w dół | ![Graficzny przycisk "Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 — 13_ButtonMoveDown") |
| Usuń | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 — 14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ustalanie wielkości i odstępów
Ustalanie rozmiarów przycisków graficznych jest takie samo jak w przypadku krótkiej wersji przycisku **[Przeglądaj...]** (26x23 pikseli):

![Wygląd obrazu graficznego na przycisku, z widocznym kolorem przezroczystym i bez niego](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 — 15_GraphicalButtonSpacing")<br />Wygląd obrazu graficznego na przycisku, z widocznym kolorem przezroczystym i bez niego

### <a name="hyperlinks"></a>Hiperlinki
Hiperłącza są dobrze dopasowane do akcji opartych na nawigacji, takich jak otwieranie tematu pomocy, modalnego okna dialogowego lub kreatora. Jeśli hiperłącze jest używane dla polecenia, powinno zawsze wyświetlać widoczną i zauważalną zmianę w interfejsie użytkownika. Ogólnie rzecz biorąc, akcje zatwierdzające akcję (na przykład zapisywanie, anulowanie i usuwanie) są lepiej przekazane przy użyciu przycisku.

#### <a name="writing-style"></a>Styl pisania
Postępuj zgodnie ze [wskazówkami dla pulpitu systemu Windows dotyczącymi tekstu interfejsu użytkownika](/windows/desktop/uxguide/text-ui). Nie używaj "Dowiedz się więcej na temat", "" więcej informacji o "lub" Uzyskaj pomoc dotyczącą tego "sformułować". Zamiast tego fraza Pomoc dotycząca łączenia tekstu w postaci pytania podstawowego odpowiada treści pomocy. Na przykład "**Jak mogę dodać serwer do Eksplorator serwera?**"

#### <a name="visual-style"></a>Styl wizualny

- Hiperlinki powinny zawsze używać [usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperłącze nie ma poprawnie stylu, błyskuje kolor czerwony, gdy aktywny lub pokazuje inny kolor po odwiedzeniu.

- Nie dołączaj podkreśleń pod stanem spoczynku formantu, chyba że łącze jest fragmentem zdania w obrębie pełnego zdania, takiego jak w przypadku znaku wodnego.

- Podkreślenia nie powinny być wyświetlane po aktywowaniu. Zamiast tego informacje zwrotne dla użytkownika, że łącze jest aktywne, to niewielka zmiana koloru i odpowiedni kursor linku.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Widoki drzewa

Widoki drzewa zapewniają sposób organizowania list złożonych w grupy nadrzędny-podrzędny. Użytkownik może rozwinąć lub zwinąć grupy nadrzędne, aby pokazać lub ukryć bazowe elementy podrzędne. Każdy element w widoku drzewa można wybrać, aby zapewnić dalsze działanie.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Styl wizualizacji widoku drzewa

#### <a name="expanders"></a>Ekspanderów znajdujących
Kontrolki widoku drzewa powinny być zgodne z projektem ekspandera używanym przez system Windows i program Visual Studio. Każdy węzeł używa kontrolki ekspandera, aby odsłonić lub ukryć elementy bazowe. Użycie kontrolki Ekspander zapewnia spójność dla użytkowników, którzy mogą napotkać różne widoki drzewa w systemie Windows i programie Visual Studio.

![Poprawne: odpowiedni styl węzła widoku drzewa przy użyciu kontrolki ekspandera](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 — 1_TreeViewCorrect")<br />Poprawne: odpowiedni styl węzła widoku drzewa przy użyciu kontrolki ekspandera

![Nieprawidłowy: niewłaściwy styl węzła widoku drzewa](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 — 2_TreeViewIncorrect1")<br />Nieprawidłowy: niewłaściwy styl węzła widoku drzewa

#### <a name="selection"></a>Wybór
Po wybraniu węzła w widoku drzewa, podświetla powinna rozwijać do pełnej szerokości kontrolki widoku drzewa. Dzięki temu użytkownicy mogą jasno określić, który element został wybrany. Kolory zaznaczenia powinny odzwierciedlać bieżącą kompozycję programu Visual Studio.

![Poprawna: wyróżnienie wybranego węzła dopasowuje całą szerokość kontrolki widoku drzewa.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 — 1_TreeViewCorrect")<br />Poprawna: wyróżnienie wybranego węzła dopasowuje całą szerokość kontrolki widoku drzewa.

![Nieprawidłowe: wyróżnienie wybranego węzła nie pasuje do całej szerokości kontrolki widoku drzewa.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 — 3_TreeViewIncorrect2")<br />Nieprawidłowe: wyróżnienie wybranego węzła nie pasuje do całej szerokości kontrolki widoku drzewa.

#### <a name="icons"></a>Ikony
Ikon należy używać tylko w formantach widoku drzewa, jeśli pomagają w wizualnym identyfikacji różnic między elementami. Ogólnie rzecz biorąc, ikony powinny być używane tylko na listach heterogenicznych, w których ikony zawierają informacje pozwalające na odróżnienie typów elementów. Na jednorodnej liście przy użyciu ikon można często postrzegać jako szum i należy je unikać. W takim przypadku ikona grupy (element nadrzędny) może przekazywać typ elementów w tym elemencie. Wyjątkiem od tej reguły jest to, że ikona jest dynamiczna i jest używana do wskazania stanu.

#### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania powinny być zawsze ukrywane, jeśli zawartość mieści się w kontrolce widoku drzewa. Pasek przewijania może być ukryty lub częściowo przezroczysty w przewijanym oknie i pojawia się, gdy okno zawierające widok drzewa ma fokus lub po umieszczeniu w nim samego widoku drzewa.

![Wyświetlane są pionowe i poziome paski przewijania, ponieważ zawartość przekroczyła limity kontrolki widok drzewa.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 — 4_Scrollbars")<br />Wyświetlane są pionowe i poziome paski przewijania, ponieważ zawartość przekroczyła limity kontrolki widok drzewa.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interakcje widoku drzewa

#### <a name="context-menus"></a>Menu kontekstowe
Węzeł widoku drzewa może ujawnić opcje podmenu w menu kontekstowym. Zazwyczaj dzieje się tak, gdy użytkownik kliknie prawym przyciskiem myszy element lub naciśnie klawisz menu na klawiaturze systemu Windows z wybranym elementem. Należy pamiętać, że węzeł zyskuje fokus i jest wybierany. Dzięki temu użytkownik może określić, do którego elementu podmenu należy.

![Element generujący menu kontekstowe zyskuje fokus, aby poinformować użytkownika o wybranym elemencie.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 — 5_ContextMenu")<br />Element generujący menu kontekstowe zyskuje fokus, aby poinformować użytkownika o wybranym elemencie.

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

![Kontrolka TrID w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 — 6_Trid")<br />Kontrolka TrID w programie Visual Studio
