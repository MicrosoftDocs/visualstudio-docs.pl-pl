---
title: Typowe wzorce sterowania dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698713"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolek dla programu Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Wspólne kontrole

### <a name="overview"></a>Omówienie
Typowe formanty stanowią większość interfejsu użytkownika w programie Visual Studio. Najczęściej używane formanty w interfejsie programu Visual Studio powinny być zgodne z [wytycznymi dotyczącymi interakcji pulpitu systemu Windows.](/windows/desktop/uxguide/controls) Ten temat jest specyficzny dla programu Visual Studio i obejmuje specjalne sytuacje lub szczegóły, które rozszerzają te wskazówki dotyczące systemu Windows.

#### <a name="common-controls-in-this-topic"></a>Typowe formanty w tym temacie

- [Paski przewijania](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Pola wejściowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Pola kombi i listy rozwijane](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Pola wyboru](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Przycisków](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Ramki grupowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Formanty tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Przyciski i hiperłącza](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Widoki drzewa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Styl wizualny
Pierwszą rzeczą, którą należy wziąć pod uwagę podczas formantów stylingu jest to, czy formanty będą używane w tematyce interfejsu użytkownika. Formanty w standardowym interfejsie użytkownika są nietematyzowanego interfejsu użytkownika i muszą być zgodne [z normalnym stylem pulpitu systemu Windows,](/windows/desktop/uxguide/controls)co oznacza, że nie są ponownie szablonowane i powinny być wyświetlane w ich domyślnym wyglądzie formantu.

- **Okna dialogowe standardowe (narzędzia):** nie tematyce. Nie re-szablon. Użyj podstawowych ustawień domyślnych stylu sterowania.

- **Okna narzędzi, edytory dokumentów, powierzchnie projektowe i okna dialogowe tematyce:** Użyj specjalistycznego wyglądu tematyzowego przy użyciu usługi kolorów.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Paski przewijania
 Paski przewijania powinny być zgodne [z typowymi wzorcami interakcji dla pasków przewijania systemu Windows,](/windows/desktop/Controls/about-scroll-bars) chyba że są one rozszerzone o informacje o zawartości, na przykład w edytorze kodu.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Pola wejściowe
 Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z [wytycznymi pulpitu systemu Windows dotyczącymi pól tekstowych](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Styl wizualny

- Pola wejściowe nie powinny być stylizowane w oknach dialogowych narzędzi. Użyj stylu podstawowego wewnętrznego do formantu.

- Tematyce pól wejściowych powinny być używane tylko w oknach dialogowych tematów i oknach narzędzi.

#### <a name="specialized-interactions"></a>Specjalistyczne interakcje

- Pola tylko do odczytu będą miały szare (wyłączone) tło, ale domyślne (aktywne) pierwszy plan.

- Wymagane pola powinny ** \<** mieć wymagane>jako znaki wodne w nich. Nie należy zmieniać koloru tła, z wyjątkiem rzadkich sytuacji.

- Sprawdzanie poprawności [błędów:](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) zobacz powiadomienia i postęp dla programu Visual Studio

- Pola wejściowe powinny być dopasowywane tak, aby pasowały do zawartości, a nie aby pasowały do szerokości okna, w którym są wyświetlane, ani aby dowolnie pasowały do długości długiego pola, takiego jak ścieżka. Długość może wskazywać użytkownikowi ograniczenia dotyczące liczby znaków dozwolonych w polu.

     ![Niepoprawna długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie tak długa.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Niepoprawna długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie tak długa.

     ![Poprawna długość pola wejściowego: pole wejściowe ma rozsądną szerokość dla oczekiwanej zawartości.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Poprawna długość pola wejściowego: pole wejściowe ma rozsądną szerokość dla oczekiwanej zawartości.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Pola kombi i listy rozwijane
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z [wytycznymi pulpitu systemu Windows dotyczącymi list rozwijanych i pól kombi](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Styl wizualny

- W oknach dialogowych narzędzia nie ponownie szablon formantu. Użyj stylu podstawowego wewnętrznego do formantu.

- W tematyce interfejsu użytkownika pola kombi i listy rozwijane są zgodne ze standardowym motywem dla formantów.

#### <a name="layout"></a>Układ
Pola kombi i listy rozwijane powinny być dopasowane do zawartości, a nie pasować do szerokości okna, w którym są wyświetlane, ani dowolnie dopasować długość długiego pola, jak ścieżka.

![Niepoprawna: szerokość listy rozwijanej jest zbyt długa dla zawartości, która zostanie wyświetlona.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Niepoprawna: szerokość listy rozwijanej jest zbyt długa dla zawartości, która zostanie wyświetlona.

![Poprawne: rozwijana jest dopasowywany, aby umożliwić wzrost tłumaczenia, ale nie niepotrzebnie długi.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Poprawne: rozwijana jest dopasowywany, aby umożliwić wzrost tłumaczenia, ale nie niepotrzebnie długi.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Pola wyboru
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z [wytycznymi pulpitu systemu Windows dla pól wyboru](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Styl wizualny

- W oknach dialogowych narzędzia nie ponownie szablon formantu. Użyj stylu podstawowego wewnętrznego do formantu.

- W tematyce interfejsu użytkownika pola wyboru są zgodne ze standardowym motywem dla formantów.

#### <a name="specialized-interactions"></a>Specjalistyczne interakcje

- Interakcja z polem wyboru nigdy nie może wysuwać okna dialogowego ani przechodzić do innego obszaru.

- Wyrównaj pola wyboru z linią bazową pierwszego wiersza tekstu.

     ![Niepoprawne: pole wyboru jest wyśrodkowane na tekście.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Niepoprawne: pole wyboru jest wyśrodkowane na tekście.

     ![Poprawne: pole wyboru jest wyrównane z pierwszym wierszem tekstu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Poprawne: pole wyboru jest wyrównane z pierwszym wierszem tekstu.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Przycisków
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z [wytycznymi pulpitu systemu Windows dotyczącymi przycisków radiowych](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych narzędzia nie należy stylizować przycisków radiowych. Użyj stylu podstawowego wewnętrznego do formantu.

#### <a name="specialized-interactions"></a>Specjalistyczne interakcje
Nie jest konieczne używanie ramki grupy do łączeniu opcji radiowych, chyba że konieczne jest zachowanie rozróżnienia grupy w ciasnym układzie.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Ramki grupowe
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z [wytycznymi pulpitu systemu Windows dotyczącymi ramek grupowych](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych narzędzia nie stylizować ramek grupowych. Użyj stylu podstawowego wewnętrznego do formantu.

#### <a name="layout"></a>Układ

- Nie jest konieczne używanie ramki grupy do łączeniu opcji radiowych, chyba że konieczne jest zachowanie rozróżnienia grupy w ciasnym układzie.

- Nigdy nie używaj ramki grupy dla pojedynczego formantu.

- Czasami dopuszczalne jest użycie reguły poziomej zamiast kontenera ramki grupy.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Formanty tekstu

### <a name="static-text-fields"></a>Statyczne pola tekstowe

Statyczne pole tekstowe przedstawia informacje tylko do odczytu i nie może być wybrane przez użytkownika. Unikaj używania go dla dowolnego tekstu, który użytkownik może chcieć skopiować do schowka. Jednak tekst statyczny tylko do odczytu można zmienić, aby odzwierciedlić zmianę stanu. W poniższym przykładzie tekst statyczny Nazwa wyjściowa w obszarze Grupa Informacje zmienia się w celu odzwierciedlenia wszelkich zmian wprowadzonych w polu tekstowym główny obszar nazw nad nim.

Istnieją dwa sposoby wyświetlania statycznych informacji tekstowych.

Tekst statyczny może być sam w oknie dialogowym bez żadnego zamknięcia, gdy nie ma konfliktu grupowania. Zdecyduj, czy dodatkowe linie pudełka są naprawdę konieczne. Przykładem jest wyświetlanie ścieżki katalogu w sekcji utworzonej przez linię grupy, jak pokazano poniżej:

![Statyczne informacje tekstowe w formanty tekstu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "WyświetlaniestaticText.png")<br />Statyczne informacje tekstowe w formanty tekstu

W oknie dialogowym, w którym istnieją inne zgrupowane obszary i zawieranie informacji, pomogłoby czytelność, a gdy sekcja może być ukryta lub pokazana (jak w okienku **opisu okna Właściwości)** lub chcesz być zgodna z podobnym interfejsem użytkownika, umieść tekst statyczny wewnątrz pola. To pole grupy powinno być jedną regułą i kolorowane za `ButtonShadow`pomocą:

![Tekst statyczny w oknie Właściwości](../../extensibility/ux-guidelines/media/PropertiesWindow.png "WłaściwościWindow.png")<br />Tekst statyczny w oknie Właściwości

### <a name="read-only-text-box"></a>Pole tekstowe tylko do odczytu

Dzięki temu użytkownik może zaznaczyć tekst wewnątrz pola, ale nie edytować go. Te pola tekstowe są otoczone zwykłym dłutem 3-D z wypełnieniem. `ButtonShadow`

Pole tekstowe może stać się aktywne (edytowalne), gdy użytkownik zmieni skojarzony formant, na przykład zaznaczając/odznaczając pole wyboru lub zaznaczając/odznaczając przycisk opcji. Na przykład na stronie **Opcje narzędzi &gt; ** pokazane poniżej pole tekstowe Strona **główna** staje się aktywne, gdy pole wyboru **Użyj domyślnego** nie jest zaznaczone.

![Pole tekstowe tylko do odczytu z nieaktywnymi i aktywnymi stanami](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Pole tekstowe tylko do odczytu z nieaktywnymi i aktywnymi stanami

### <a name="using-text-in-dialogs"></a>Korzystanie z tekstu w oknach dialogowych

Najważniejsze wskazówki dotyczące tekstu w oknach dialogowych:

- Etykiety dla pól tekstowych, pól listy i ramek w niekręgowych oknach dialogowych zaczynają się od zlecenia, mają kapitał początkowy tylko na pierwszym słowie i kończą się dwukropkiem.

    > Formanty tekstu w tematyce dialogowej są zgodne z [wytycznymi środowiska ux pulpitu systemu Windows](/windows/desktop/uxguide/top-violations) i nie przyjmują znaków interpunkcyjnych końcowych, z wyjątkiem znaków zapytania w łączach Pomocy.

- Etykiety pól wyboru i przycisków opcji zaczynają się od zlecenia, początkowego kapitału tylko na pierwsze słowo i nie mają końcowego interpunkcji.

- Etykiety przycisków, menu, elementów menu i kart mają początkowe litery na każdym słowie (wielkość liter tytułu).

- Terminologia etykiety powinna być zgodna z podobnymi etykietami w innych oknach dialogowych.

- Jeśli to możliwe, niech pisarz/edytor napisać lub zatwierdzić tekst, zanim trafi do dewelopera do implementacji.

- Wszystkie elementy sterujące powinny mieć etykiety, z wyjątkiem szczególnych okoliczności, w których tabulator jest wystarczający.
W razie potrzeby użyj tekstu pomocniczego.

### <a name="helper-text"></a>Tekst pomocnika

Zawarte w oknach dialogowych, aby pomóc użytkownikowi zrozumieć cel okna dialogowego lub wskazać, które działania należy podjąć. Tekst pomocnika powinien być używany tylko wtedy, gdy jest to konieczne, aby uniknąć zaśmiecania prostych okien dialogowych. Dwie odmiany tekstu pomocniczego to okno dialogowe i znak wodny.

Postępuj zgodnie ze wspólnymi lokalizacjami tekstu pomocniczego i bądź wybiórczy, wprowadzając nowe obszary. Typowe scenariusze tekstu pomocniczego to:

- Tekst pomocnika w oknach dialogowych, aby nadać dodatkowy kierunek interakcji ze złożonym dialogiem.

- Tekst znaku wodnego w pustych oknach narzędzi lub oknach dialogowych, aby wyjaśnić, dlaczego żadna zawartość nie jest widoczna.

- Okienko opisu, na przykład u dołu **okna Właściwości**.

- Tekst znaku wodnego w pustym edytorze, aby wyjaśnić, jakie działania użytkownik powinien podjąć, aby rozpocząć.

### <a name="dialog-helper-text"></a>Tekst pomocnika okna dialogowego

Projektant środowiska użytkownika może pomóc określić, kiedy tekst pomocnika jest odpowiedni. Projektant może określić, gdzie pojawia się tekst pomocnika, a także jego ogólna zawartość. Pomoc użytkownika może pisać/edytować rzeczywisty tekst.

### <a name="watermarks"></a>Znaki wodne

Okna dialogowe korzystają z nieco innych wytycznych dotyczących znaków wodnych. Ponieważ okno dialogowe może wydawać się zajęte wieloma elementami interfejsu użytkownika (etykiety, tekst podpowiedzi, przyciski i inne kontrolki `ButtonShadow`kontenera z tekstem), szczególnie gdy są wyświetlane w kolorze czarnym, znaki wodne lepiej wyróżniają się w kolorze ciemnoszarym (VSColor: ). Zazwyczaj znak wodny pojawia się wewnątrz formantu, jak pole `Window`listy z białym tłem (VSColor: ).

- Tekst jest wyświetlany w kolorze ciemnoszarym (VSColor: `ButtonShadow`). Jeśli jednak znak wodny pojawia się na średnim szarym lub `ButtonFace`innym kolorze (VSColor: ) tle i istnieje obawa o jego czytelność, przejdź z czarnym tekstem (VSColor: `WindowText`).

- Znaki wodne można wyśrodkować lub opróżnić w lewo. Podczas podejmowania decyzji dotyczących wyrównania stosowanie standardowych reguł projektowania. Nie można wybrać znaku wodnego w tle.

![Przykład tekstu znaku wodnego](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Przykład tekstu znaku wodnego

### <a name="context-specific-dynamic-text"></a>Tekst kontekstowy (dynamiczny)

Tekst dynamiczny może być używany na dwa sposoby w oknie dialogowym lub w trybie interfejsu użytkownika: jako etykieta dynamiczna lub jako zawartość dynamiczna.

- Etykieta dynamiczna: powszechne użycie tekstu dynamicznego odbywa się w panelach opisowych, które oferują więcej informacji dla zaznaczonego elementu, na przykład w oknie dialogowym, które zawiera listę elementów i właściwości tych elementów wyświetlanych w siatce po prawej stronie. Etykieta siatki właściwości może być dynamiczna, tak aby po wybraniu elementu po lewej stronie siatka po prawej stronie wyświetlała informacje dotyczące tego określonego elementu.

- Tekst dynamiczny: może być przydatny w przypadkach, w których trzeba wyświetlać określone informacje, a nie ogólne informacje w ten sposób, ale należy uważać, aby nie nadużywanie.

Jeśli chcesz, aby użytkownicy mieli możliwość kopiowania informacji, tekst dynamiczny powinien znajdować się w polu tekstowym tylko do odczytu.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Przyciski i hiperłącza

### <a name="overview"></a>Omówienie
Przyciski i kontrolki łączy (hiperłącza) powinny być zgodne z [podstawowymi wskazówkami pulpitu systemu Windows dotyczącymi użycia,](/windows/desktop/uxguide/ctrl-links) sformułowania, rozmiaru i odstępów.

### <a name="choosing-between-buttons-and-links"></a>Wybór między przyciskami i łączami
Tradycyjnie przyciski były używane do akcji, a hiperłącza zostały zarezerwowane do nawigacji. Przyciski mogą być używane we wszystkich przypadkach, ale rola łączy została rozwinięta w programie Visual Studio, dzięki czemu przyciski i łącza są bardziej wymienne w niektórych warunkach.

Kiedy używać przycisków poleceń:

- Polecenia podstawowe

- Wyświetlanie okien używanych do zbierania danych wejściowych lub dokonywania wyborów, nawet jeśli są to polecenia pomocnicze

- Destrukcyjne lub nieodwracalne działania

- Przyciski zobowiązań w kreatorach i przepływach stron

Unikaj przycisków poleceń w oknach narzędzi lub jeśli potrzebujesz więcej niż dwóch słów dla etykiety. Łącza mogą mieć dłuższe etykiety.

 Kiedy używać linków:

- Nawigacja do innego okna, dokumentu lub strony sieci Web

- Sytuacje wymagające dłuższej etykiety lub krótkiego zdania w celu opisania intencji działania

- Ciasne przestrzenie, w których przycisk przytłoczyłby interfejs użytkownika, pod warunkiem, że akcja nie jest destrukcyjna lub nieodwracalna

- Usuwanie podkreślenia poleceń pomocniczych w sytuacjach, gdy istnieje wiele poleceń

#### <a name="examples"></a>Przykłady
![Łącza poleceń używane na pasku informacyjnym po komunikacie o stanie](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Łącza poleceń używane na pasku informacyjnym po komunikacie o stanie

![Łącza używane w wyskakującym okienku CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Łącza używane w wyskakującym okienku CodeLens

![Linki używane do poleceń pomocniczych, w których przyciski przyciągałyby zbyt wiele uwagi](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Linki używane do poleceń pomocniczych, w których przyciski przyciągałyby zbyt wiele uwagi

### <a name="common-buttons"></a>Typowe przyciski

#### <a name="text"></a>Tekst
Postępuj zgodnie z wytycznymi dotyczącymi pisania w [tekście interfejsu użytkownika i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Styl wizualny

##### <a name="standard-unthemed"></a>Standard (bez sytema)
Większość przycisków w programie Visual Studio pojawi się w oknach dialogowych narzędzia i nie powinny być stylizowane. Powinny one odzwierciedlać standardowy wygląd przycisków podyktowany przez system operacyjny.

##### <a name="themed"></a>Tematyczne
W niektórych przypadkach przyciski mogą być używane w stylu interfejsu użytkownika i te przyciski muszą być odpowiednio stylizowane. Zobacz [okna dialogowe, aby](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) uzyskać informacje na temat formantów tematowych.

### <a name="special-buttons"></a>Przyciski specjalne

#### <a name="browse-buttons"></a>Przeglądaj... Przyciski
**[Przeglądaj...]** są używane w siatkach, oknach dialogowych i oknach narzędzi oraz innych niemodytnych elementach interfejsu użytkownika. Wyświetlają selektor, który pomaga użytkownikowi w wypełnianiu wartości do formantu. Istnieją dwie odmiany tego przycisku, długie i krótkie.

![Długi przycisk [Przeglądaj...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Długi przycisk [Przeglądaj...]

![Wielokropek tylko krótki przycisk [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Wielokropek tylko krótki przycisk [...]

Kiedy używać krótkiego przycisku wielokropka:

- Jeśli w oknie dialogowym znajduje się więcej niż jeden długi przycisk **[Przeglądaj...],** na przykład gdy kilka pól zezwala na przeglądanie. Użyj krótkiego przycisku **[...]** dla każdego, aby uniknąć mylących kluczy dostępu utworzonych przez tę sytuację (**&Browse** i **B&wierszy** w tym samym oknie dialogowym).

- W ciasnym oknie dialogowym lub gdy nie ma rozsądnego miejsca, aby umieścić długi przycisk.

- Jeśli przycisk pojawi się w formancie siatki.

Wskazówki dotyczące używania przycisku:

- Nie używaj klucza dostępu. Aby uzyskać do niego dostęp za pomocą klawiatury, użytkownik musi kartę z sąsiedniego formantu. Upewnij się, że kolejność tabulacji jest taka, że każdy przycisk przeglądania spada natychmiast po polu, które wypełni. Nigdy nie używaj podkreślenia poniżej pierwszego okresu.

- Ustaw właściwość Microsoft Active Accessibility (MSAA) **Name** to **Browse...** (w tym wielokropek), aby czytniki ekranu odczytywane były jako "Przeglądaj", a nie "kropka-kropka" lub "okres-okres". W przypadku formantów zarządzanych oznacza to ustawienie właściwości **AccessibleName.**

- Nigdy nie używaj przycisku wielokropek **[...]** do niczego poza akcją przeglądania. Na przykład, jeśli potrzebujesz przycisku **[Nowy...],** ale nie masz wystarczająco dużo miejsca na tekst, okno dialogowe musi zostać przeprojektowane.

##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy
![Rozmiar [Przeglądaj...] przyciski: wersja standardowa to 75x23 pikseli, krótka wersja to 26x23 pikseli](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Przyciski zmiany rozmiaru [Przeglądaj...]

![Odstępy [Przeglądaj...] przyciski: odstępy między powiązanym i standardowym przyciskiem Przeglądaj 7 pikseli, odstępy między powiązanym sterowaniem a krótkim przyciskiem Przeglądania 5 pikseli](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Przyciski Odstępy [Przeglądaj...]

#### <a name="graphical-buttons"></a>Przyciski graficzne
Niektóre przyciski powinny zawsze używać obrazu graficznego i nigdy nie dołączać tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacją. Są one często używane w selektorach pól i innych listach sortowalnych.

> [!NOTE]
> Użytkownicy muszą kartę do tych przycisków (nie ma kluczy dostępu), więc umieścić je w rozsądnej kolejności. Zamapuj `name` właściwość przycisku na czynność, którą wykonuje, aby czytniki ekranu poprawnie interpretować akcję przycisku.

| Funkcja | Button |
| --- | --- |
| Dodaj | ![Graficzny przycisk "Dodaj"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Dodaj wszystko | ![Graficzny przycisk "Dodaj wszystko"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Usuń wszystkie | ![Graficzny przycisk "Usuń wszystko"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Przenieś w górę | ![Graficzny przycisk "Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Przenieś w dół | ![Graficzny przycisk "Przesuń w dół"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Usuń | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Zmiana rozmiaru i odstępy
Rozmiar przycisków graficznych jest taki sam jak w przypadku krótkiej wersji przycisku **[Przeglądaj...]** (26x23 pikseli):

![Wygląd obrazu graficznego na przycisku, z i bez przezroczystego koloru](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Wygląd obrazu graficznego na przycisku, z i bez przezroczystego koloru

### <a name="hyperlinks"></a>Hiperlinki
Hiperłącza są dobrze dostosowane do akcji opartych na nawigacji, takich jak otwieranie tematu Pomocy, modalnego okna dialogowego lub kreatora. Jeśli hiperłącze jest używane dla polecenia, zawsze powinien wyświetlać widoczne i zauważalne zmiany w interfejsie użytkownika. Ogólnie rzecz biorąc akcje, które zobowiązują się do akcji (takich jak Zapisz, Anuluj i Usuń) są lepiej komunikowane za pomocą przycisku.

#### <a name="writing-style"></a>Styl pisania
Postępuj zgodnie ze [wskazówkami pulpitu systemu Windows dla tekstu interfejsu użytkownika](/windows/desktop/uxguide/text-ui). Nie używaj zwrotów "Dowiedz się więcej o", "Opowiedz mi więcej o" lub "Uzyskaj pomoc w tym zakresie". Zamiast tego fraza Pomoc link tekst w odniesieniu do pytania podstawowego, na które odpowiedział zawartość Pomocy. Na przykład "**Jak dodać serwer do Eksploratora serwera?**"

#### <a name="visual-style"></a>Styl wizualny

- Hiperłącza powinny zawsze korzystać [z usługi VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Jeśli hiperłącze nie jest poprawnie stylizowane, miga na czerwono, gdy jest aktywne lub pokazuje inny kolor po odwiedzeniu.

- Nie dołączaj podkreśleń w stanie spoczynku formantu, chyba że łącze jest fragmentem zdania w pełnym zdaniu, na przykład w znaku wodnym.

- Podkreślenia nie powinny być wyświetlane po najechaniu kursorem. Zamiast tego opinie do użytkownika, że łącze jest aktywne jest niewielka zmiana koloru i odpowiedni kursor łącza.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Widoki drzewa

Widoki drzewa umożliwiają organizowanie złożonych list w grupach nadrzędny-podrzędny. Użytkownik może rozwinąć lub zwinąć grupy nadrzędne, aby odsłonić lub ukryć leżące u podstaw elementów podrzędnych. Każdy element w widoku drzewa można wybrać, aby zapewnić dalsze działania.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Styl wizualny widoku drzewa

#### <a name="expanders"></a>Ekspandery
Formanty widoku drzewa powinny być zgodne z projektem expandera używanym przez systemy Windows i Visual Studio. Każdy węzeł używa formantu expandera do ujawniania lub ukrywania elementów leżących u podstaw. Za pomocą formantu expander zapewnia spójność dla użytkowników, którzy mogą napotkać różne widoki drzewa w systemie Windows i Visual Studio.

![Poprawny: prawidłowy styl węzła widoku drzewa przy użyciu kontrolki expandera](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Poprawny: prawidłowy styl węzła widoku drzewa przy użyciu kontrolki expandera

![Niepoprawny: nieprawidłowy styl węzła widoku drzewa](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Niepoprawny: nieprawidłowy styl węzła widoku drzewa

#### <a name="selection"></a>Wybór
Gdy węzeł jest zaznaczony w widoku drzewa, podświetlenie należy rozwinąć do pełnej szerokości formantu widoku drzewa. Pomaga to użytkownikom jasno określić, który element wybrali. Kolory zaznaczenia powinny odzwierciedlać bieżący motyw programu Visual Studio.

![Poprawne: podświetlenie wybranego węzła pasuje do całej szerokości formantu widoku drzewa.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Poprawne: podświetlenie wybranego węzła pasuje do całej szerokości formantu widoku drzewa.

![Niepoprawne: podświetlenie wybranego węzła nie pasuje do całej szerokości formantu widoku drzewa.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Niepoprawne: podświetlenie wybranego węzła nie pasuje do całej szerokości formantu widoku drzewa.

#### <a name="icons"></a>Ikony
Ikony powinny być używane tylko w formantach widoku drzewa, jeśli pomagają one w wizualnej identyfikacji różnic między elementami. Ogólnie rzecz biorąc ikony powinny być używane tylko na niejednorodnych listach, na których ikony zawierają informacje w celu rozróżnienia typów elementów. Na jednorodnej liście za pomocą ikon często można postrzegać jako hałas i należy go unikać. W takim przypadku ikona grupy (nadrzędna) może przekazać typ elementów w niej. Wyjątkiem od tej reguły byłoby, jeśli ikona jest dynamiczny i jest używany do wskazywania stanu.

#### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania powinny być zawsze ukryte, jeśli zawartość mieści się w formancie widoku drzewa. Jest dopuszczalne dla pasków przewijania, które mają być ukryte lub półprzezroczyste w oknie przewijane i pojawiają się, gdy okno zawierające widok drzewa ma fokus lub po najechaniu na sam widok drzewa.

![Wyświetlane są pionowe i poziome paski przewijania, ponieważ zawartość przekroczyła granice formantu widoku drzewa.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Wyświetlane są pionowe i poziome paski przewijania, ponieważ zawartość przekroczyła granice formantu widoku drzewa.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interakcje z widokiem drzewa

#### <a name="context-menus"></a>Menu kontekstowe
Węzeł widoku drzewa może ujawnić opcje podmenu w menu kontekstowym. Zazwyczaj dzieje się tak, gdy użytkownik kliknął prawym przyciskiem myszy element lub nacisnął klawisz Menu na klawiaturze systemu Windows z zaznaczonym elementem. Ważne jest, aby węzeł zyskał fokus i został wybrany. Pomaga to użytkownikowi zidentyfikować element, do którego należy podmenu.

![Element, który wygenerował menu kontekstowe zyskuje fokus, aby powiadomić użytkownika, który element został wybrany.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Element, który wygenerował menu kontekstowe zyskuje fokus, aby powiadomić użytkownika, który element został wybrany.

#### <a name="keyboard"></a>Klawiatura
Widok drzewa powinien umożliwiać zaznaczanie elementów i rozwijanie/zwijanie węzłów za pomocą klawiatury. Dzięki temu nawigacja spełnia nasze wymagania dotyczące ułatwień dostępu.

##### <a name="tree-view-control"></a>Kontrolka widoku drzewa
Kontrolki drzewa programu Visual Studio powinny być zgodne ze wspólną nawigacją za pomocą klawiatury:

- **Strzałka w górę:** Zaznaczanie elementów przez przesuwanie drzewa w górę

- **Strzałka w dół:** Zaznaczanie elementów, przesuwając się w dół drzewa

- **Strzałka w prawo:** Rozwijanie węzła w drzewie

- **Strzałka w lewo:** Zwijanie węzła w drzewie

- **Wprowadź klucz:** Inicjowanie, ładowanie, wykonywanie zaznaczonego elementu

##### <a name="trid-tree-view-and-grid-view"></a>Trid (widok drzewa i widok siatki)
Formant trid jest formantem złożonym, który zawiera widok drzewa w siatce. Rozwijanie, zwijanie i poruszanie się po drzewie powinno być zgodne z tymi samymi poleceniami klawiatury co widok drzewa, z następującymi dodatkami:

- **Strzałka w prawo:** Rozwiń węzeł. Po rozwinięciu węzła należy kontynuować nawigowanie do najbliższej kolumny po prawej stronie. Nawigacja powinna zatrzymać się na końcu wiersza.

- **Karta:** Przechodzi do najbliższej komórki po prawej stronie.  Na końcu wiersza nawigacja jest kontynuowana do następnego wiersza.

- **Shift + Karta:** Przechodzi do najbliższej komórki po lewej stronie.  Na początku wiersza nawigacja jest kontynuowana do prawej komórki w poprzednim wierszu.

![Kontrolka trid w programie Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Kontrolka trid w programie Visual Studio
