---
title: Typowe wzorce kontrolek dla Visual Studio | Microsoft Docs
description: Dowiedz się, Visual Studio formanty są zgodne z wytycznymi dotyczącymi interakcji z pulpitem systemu Windows oraz o specjalnych sytuacjach, które rozszerzają te wytyczne.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899306"
---
# <a name="common-control-patterns-for-visual-studio"></a>Typowe wzorce kontrolek dla programu Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Typowe kontrolki

### <a name="overview"></a>Omówienie
Typowe kontrolki stanowią większość interfejsu użytkownika w Visual Studio. Najbardziej typowe kontrolki używane w interfejsie Visual Studio powinny być zgodne z wytycznymi dotyczącymi interakcji [z programem Windows Desktop.](/windows/desktop/uxguide/controls) Ten temat jest specyficzny dla Visual Studio i obejmuje specjalne sytuacje lub szczegóły, które rozszerzają te wytyczne dotyczące systemu Windows.

#### <a name="common-controls-in-this-topic"></a>Typowe kontrolki w tym temacie

- [Paski przewijania](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Pola wejściowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Pola kombi i listy rozwijane](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Pola wyboru](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Przycisków](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Grupowanie ramek](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Przyciski i hiperlinki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Widoki drzewa](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Styl wizualny
Pierwszą rzeczą, którą należy wziąć pod uwagę podczas stylów kontrolek, jest to, czy kontrolki będą używane w interfejsie użytkownika z tematami. Kontrolki w standardowym interfejsie użytkownika nie mają tematu i muszą być zgodne z normalnym stylem pulpitu systemu [Windows,](/windows/desktop/uxguide/controls)co oznacza, że nie są ponownie szablonowane i powinny pojawiać się w domyślnym wyglądzie kontrolki.

- **Standardowe (narzędzia) okna dialogowe:** nie ma tematu. Nie należy ponownie szablonu. Użyj podstawowych ustawień stylu kontrolki.

- **Okna narzędzi, edytory dokumentów, powierzchnie projektowe i okna dialogowe z tematami:** Użyj wyspecjalizowanego wyglądu z zastosowaniem usługi kolorów.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Paski przewijania
 Paski przewijania powinny być zgodne ze wspólnymi wzorcami interakcji dla pasków przewijania systemu [Windows,](/windows/desktop/Controls/about-scroll-bars) chyba że zostaną one rozszerzone o informacje o zawartości, takie jak w edytorze kodu.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Pola wejściowe
 Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z wytycznymi dla [programu Windows Desktop dotyczącymi pól tekstowych](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Styl wizualny

- W oknach dialogowych narzędzi nie należy stosować stylu pól wejściowych. Użyj stylu podstawowego, który jest wewnętrzny dla kontrolki.

- Pola wejściowe z tematami powinny być używane tylko w oknach dialogowych i oknach narzędzi z tematami.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Pola tylko do odczytu będą mieć szare (wyłączone) tło, ale domyślny (aktywny) pierwszy plan.

- Wymagane pola powinny mieć **\<Required>** w nich znaki wodne. Nie należy zmieniać koloru tła z wyjątkiem rzadkich sytuacji.

- Walidacja błędu: zobacz [Powiadomienia i postęp dla Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Pola wejściowe powinny mieć rozmiar dopasowany do zawartości, a nie szerokość okna, w którym są wyświetlane, ani dowolnie dopasować długość długiego pola, takiego jak ścieżka. Długość może być wskazówką dla użytkownika o ograniczeniach dotyczących dozwolonej długości znaków w polu.

     ![Nieprawidłowa długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie tak długa.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Nieprawidłowa długość pola wejściowego: jest mało prawdopodobne, że nazwa będzie tak długa.

     ![Poprawna długość pola wejściowego: pole wejściowe ma rozsądną szerokość dla oczekiwanej zawartości.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Poprawna długość pola wejściowego: pole wejściowe ma rozsądną szerokość dla oczekiwanej zawartości.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Pola kombi i listy rozwijane
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z wytycznymi dla programu [Windows Desktop dotyczącymi list rozwijanych](/windows/desktop/uxguide/ctrl-drop)i pól kombi.

#### <a name="visual-style"></a>Styl wizualny

- W oknach dialogowych narzędzi nie należy ponownie szablonować kontrolki. Użyj stylu podstawowego, który jest wewnętrzny dla kontrolki.

- W interfejsie użytkownika z tematami pola kombi i listy rozwijane są zgodne ze standardowymi tematami dla kontrolek.

#### <a name="layout"></a>Layout
Pola kombi i listy rozwijane powinny mieć rozmiar dopasowany do zawartości, a nie pasować do szerokości okna, w którym są wyświetlane, ani do dowolnie dopasowanej długości długiego pola, takiego jak ścieżka.

![Niepoprawne: szerokość listy rozwijanej jest zbyt długa dla zawartości, która będzie wyświetlana.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Niepoprawne: szerokość listy rozwijanej jest zbyt długa dla zawartości, która będzie wyświetlana.

![Odpowiedź prawidłowa: rozmiar listy rozwijanej umożliwia wzrost tłumaczenia, ale nie jest niepotrzebnie długi.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Odpowiedź prawidłowa: rozmiar listy rozwijanej umożliwia wzrost tłumaczenia, ale nie jest niepotrzebnie długi.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Pola wyboru
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z wytycznymi dla [programu Windows Desktop dotyczącymi pól wyboru](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Styl wizualny

- W oknach dialogowych narzędzi nie należy ponownie szablonować kontrolki. Użyj stylu podstawowego, który jest wewnętrzny dla kontrolki.

- W interfejsie użytkownika z tematami pola wyboru są zgodne ze standardowymi tematami dla kontrolek.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje

- Interakcja z polem wyboru nigdy nie może zawierać okna dialogowego ani przechodzić do innego obszaru.

- Wyrównaj pola wyboru z punktem odniesienia pierwszego wiersza tekstu.

     ![Niepoprawne: pole wyboru jest wyśrodkowane na tekście.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Niepoprawne: pole wyboru jest wyśrodkowane na tekście.

     ![Odpowiedź prawidłowa: pole wyboru jest wyrównane do pierwszego wiersza tekstu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Odpowiedź prawidłowa: pole wyboru jest wyrównane do pierwszego wiersza tekstu.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Przycisków
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z wytycznymi dla [pulpitu systemu Windows dotyczącymi przycisków radiowych](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych narzędzi nie styliuj przycisków radiowych. Użyj stylu podstawowego, który jest wewnętrzny dla kontrolki.

#### <a name="specialized-interactions"></a>Wyspecjalizowane interakcje
Nie trzeba używać ramki grupy do ująć opcje radiowe, chyba że trzeba zachować rozróżnienie grup w ścisłej układu.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Grupowanie ramek
Aby uzyskać typowe zachowanie interakcji, postępuj zgodnie z wytycznymi dla programu [Windows Desktop dotyczącymi ramek grup.](/windows/desktop/uxguide/ctrl-group-boxes)

#### <a name="visual-style"></a>Styl wizualny
W oknach dialogowych narzędzi nie styliuj ramek grup. Użyj stylu podstawowego, który jest wewnętrzny dla kontrolki.

#### <a name="layout"></a>Layout

- Nie trzeba używać ramki grupy do ująć opcje radiowe, chyba że trzeba zachować rozróżnienie grup w ścisłej układu.

- Nigdy nie używaj ramki grupy dla jednej kontrolki.

- Czasami akceptowalne jest użycie reguły poziomej zamiast kontenera ramek grupy.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Kontrolki tekstu

### <a name="static-text-fields"></a>Statyczne pola tekstowe

Statyczne pole tekstowe zawiera informacje tylko do odczytu i nie może zostać wybrane przez użytkownika. Unikaj używania go do dowolnego tekstu, który użytkownik może chcieć skopiować do schowka. Jednak tekst statyczny tylko do odczytu może ulec zmianie, aby odzwierciedlić zmianę stanu. W poniższym przykładzie tekst statyczny Nazwa danych wyjściowych w grupie Informacje zostanie zmieniany w celu odzwierciedlenia wszelkich zmian wprowadzonych w polu tekstowym Główna przestrzeń nazw nad nim.

Istnieją dwa sposoby wyświetlania informacji o tekście statycznym.

Tekst statyczny może być samodzielnie w oknie dialogowym bez żadnego zawierania, gdy nie występuje konflikt grupowania. Zdecyduj, czy dodatkowe wiersze pola są naprawdę niezbędne. Przykładem jest wyświetlanie ścieżki katalogu w sekcji utworzonej przez wiersz grupy, jak pokazano poniżej:

![Informacje o tekście statycznym w kontrolkach tekstu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informacje o tekście statycznym w kontrolkach tekstu

W oknie dialogowym, w którym istnieją inne pogrupowane obszary i zawierają informacje, można je odczytać, a gdy sekcja może być ukryta lub wyświetlana (jak w okienku opisu usługi **okno Właściwości)** lub chcesz zapewnić spójność z podobnym interfejsem użytkownika, umieść tekst statyczny wewnątrz pola. To pole grupy powinno być pojedynczą regułą i mieć kolor `ButtonShadow` :

![Tekst statyczny w okno Właściwości](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Tekst statyczny w okno Właściwości

### <a name="read-only-text-box"></a>Pole tekstowe tylko do odczytu

Dzięki temu użytkownik może wybrać tekst wewnątrz pola, ale nie będzie go edytować. Te pola tekstowe są obramowane przez zwykłe pośmięć 3D z `ButtonShadow` wypełnieniem.

Pole tekstowe może stać się aktywne (edytowalne), gdy użytkownik zmieni skojarzoną kontrolkę, na przykład zaznaczanie/usuwanie zaznaczenia pola wyboru lub zaznaczanie/usuwanie zaznaczenia przycisku radiowego. Na przykład na stronie **Opcje &gt; narzędzi**  pokazanej poniżej pole tekstowe  Strona główna stanie się aktywne, gdy pole wyboru Użyj domyślnego nie będzie zaznaczone.

![Pole tekstowe tylko do odczytu z wyświetlaniem stanów nieaktywnych i aktywnych](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Pole tekstowe tylko do odczytu z wyświetlaniem stanów nieaktywnych i aktywnych

### <a name="using-text-in-dialogs"></a>Używanie tekstu w oknach dialogowych

Najważniejsze wskazówki dotyczące tekstu w oknach dialogowych:

- Etykiety pól tekstowych, pól listy i ramek w niezaumianych oknach dialogowych rozpoczynają się od czasownika, mają początkową literę tylko w pierwszym wyrazie i kończą się dwukropkiem.

    > Kontrolki tekstu w oknach dialogowych z tematami są zgodne ze wskazówkami dotyczącymi środowiska użytkownika aplikacji klasycznych systemu [Windows](/windows/desktop/uxguide/top-violations) i nie mają końca interpunkcji, z wyjątkiem znaków zapytania w linkach pomocy.

- Etykiety pól wyboru i przycisków opcji zaczynają się od czasownika, początkowego znaku capital tylko w pierwszym wyrazie i nie mają końcowej interpunkcji.

- Etykiety przycisków, menu, elementów menu i kart mają początkowe stolice każdego wyrazu (litera tytułu).

- Terminologia dotycząca etykiet powinna być spójna z podobnymi etykietami w innych oknach dialogowych.

- Jeśli to możliwe, zapisuj lub zatwierdź tekst przed jego wdrożeniem do dewelopera.

- Wszystkie kontrolki powinny mieć etykiety z wyjątkiem szczególnych okoliczności, w których klawisz Tabbing jest wystarczający.
W razie potrzeby użyj tekstu pomocnika.

### <a name="helper-text"></a>Tekst pomocnika

Uwzględnione w oknach dialogowych, aby ułatwić użytkownikowi zrozumienie przeznaczenia okna dialogowego lub wskazanie akcji do podjęcia. Tekstu pomocnika należy używać tylko w razie potrzeby, aby uniknąć zaśmiecania prostych okien dialogowych. Dwie odmiany tekstu pomocnika to okno dialogowe i znak wodny.

Śledź typowe lokalizacje tekstu pomocnika i selektywnie wprowadzaj nowe obszary. Typowe scenariusze dotyczące tekstu pomocnika to:

- Tekst pomocnika w oknach dialogowych, aby podać dodatkowy kierunek interakcji ze złożonym oknem dialogowym.

- Tekst znaku wodnego w pustych oknach narzędzi lub oknach dialogowych, aby wyjaśnić, dlaczego żadna zawartość nie jest widoczna.

- Okienko opisu, takie jak w dolnej części **okno Właściwości**.

- Tekst znaku wodnego w pustym edytorze, aby wyjaśnić, jaką akcję użytkownik powinien podjąć, aby rozpocząć pracę.

### <a name="dialog-helper-text"></a>Tekst pomocnika okna dialogowego

Projektant interfejsu użytkownika może pomóc w ustaleniu, kiedy tekst pomocnika jest odpowiedni. Projektant może określić, gdzie pojawia się tekst pomocnika oraz jaka jest jego ogólna zawartość. Pomoc dla użytkowników może zapisywać/edytować rzeczywisty tekst.

### <a name="watermarks"></a>Znaki wodne

Okna dialogowe korzystają z nieco innych wytycznych dotyczących limitu. Ponieważ okno dialogowe może być zajęte wieloma elementami interfejsu użytkownika (etykietami, tekstem wskazówek, przyciskami i innymi kontrolkami kontenera z tekstem), szczególnie gdy są one wyświetlane w kolorze czarnym, znaki wodne wyróżniają się lepiej w kolorze ciemnoszarym (VSColor: `ButtonShadow` ). Zazwyczaj znak wodny pojawia się wewnątrz kontrolki jak pole listy z białym tłem (VSColor: `Window` ).

- Tekst jest wyświetlany w kolorze ciemnoszarym (VSColor: `ButtonShadow` ). Jeśli jednak znak wodny pojawia się na średnim szarym lub innym tle (VSColor: ), a jego czytelność jest inna, przejdź do tekstu w kolorze czarnym `ButtonFace` (VSColor: `WindowText` ).

- Znaki wodne można wyśrodkowywać lub opróżniać w lewo. Stosowanie standardowych reguł projektowania podczas podejmowania decyzji dotyczących wyrównania. Nie można wybrać limitu w tle.

![Przykładowy tekst znaku wodnego](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Przykładowy tekst znaku wodnego

### <a name="context-specific-dynamic-text"></a>Tekst kontekstowy (dynamiczny)

Tekstu dynamicznego można używać na jeden z dwóch sposobów w oknie dialogowym lub w trybie interfejsu użytkownika: jako etykiety dynamicznej lub jako zawartości dynamicznej.

- Etykieta dynamiczna: typowe zastosowanie tekstu dynamicznego jest w panelach opisowych, które oferują więcej informacji dla wybranego elementu, na przykład w oknie dialogowym zawierającym listę elementów i właściwości dla tych elementów wyświetlanych w siatce po prawej stronie. Etykieta siatki właściwości może być dynamiczna, dlatego po wybraniu elementu po lewej stronie siatka po prawej stronie zawiera informacje dotyczące tego konkretnego elementu.

- Tekst dynamiczny: może być przydatny w przypadkach, w których należy wyświetlać w ten sposób określone informacje, a nie ogólne, ale należy zadbać o to, aby nie używać ich zbyt wiele.

Jeśli chcesz, aby użytkownicy mieli możliwość kopiowania informacji, tekst dynamiczny powinien być w polu tekstowym tylko do odczytu.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Przyciski i hiperlinki

### <a name="overview"></a>Omówienie
Przyciski i kontrolki linków (hiperlinki) powinny być zgodne z podstawowymi wskazówkami aplikacji Windows Desktop w zakresie [hiperlinków](/windows/desktop/uxguide/ctrl-links) dotyczących użycia, słów, rozmiarów i odstępów.

### <a name="choosing-between-buttons-and-links"></a>Wybieranie między przyciskami i linkami
Tradycyjnie przyciski były używane do akcji, a hiperlinki były zarezerwowane do nawigacji. Przyciski mogą być używane we wszystkich przypadkach, ale w niektórych przypadkach rola linków została rozszerzona na Visual Studio tak, aby przyciski i linki były bardziej wymienne w niektórych warunkach.

Kiedy używać przycisków poleceń:

- Polecenia podstawowe

- Wyświetlanie okien używanych do zbierania danych wejściowych lub podejmowania wyborów, nawet jeśli są to polecenia pomocnicze

- Akcje destrukcyjne lub nieodwracalne

- Przyciski zobowiązania w ramach kreatorów i przepływów stron

Unikaj przycisków poleceń w oknach narzędzi lub jeśli etykieta wymaga więcej niż dwóch wyrazów. Linki mogą mieć dłuższe etykiety.

 Kiedy używać linków:

- Nawigacja do innego okna, dokumentu lub strony internetowej

- Sytuacje, które wymagają dłuższej etykiety lub krótkiego zdania w celu opisania intencji akcji

- Ciasne miejsca, w których przycisk przeciąży interfejs użytkownika, pod warunkiem, że akcja nie jest destruktywna ani nieodwracalna

- Cofanie podkreślania poleceń pomocniczych w sytuacjach, w których istnieje wiele poleceń

#### <a name="examples"></a>Przykłady
![Linki poleceń używane na pasku informacji po komunikacie o stanie](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Linki poleceń używane na pasku informacji po komunikacie o stanie

![Linki używane w oknie podręcznym CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Linki używane w oknie podręcznym CodeLens

![Linki używane dla poleceń pomocniczych, w których przyciski przyciągnęłyby zbyt wiele uwagi](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Linki używane dla poleceń pomocniczych, w których przyciski przyciągnęłyby zbyt wiele uwagi

### <a name="common-buttons"></a>Typowe przyciski

#### <a name="text"></a>Tekst
Postępuj zgodnie z wytycznymi dotyczącymi pisania [w tekście interfejsu użytkownika i terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Styl wizualny

##### <a name="standard-unthemed"></a>Standardowa (bez)
Większość przycisków w Visual Studio będzie wyświetlana w oknach dialogowych narzędzi i nie powinna mieć stylu. Powinny one odzwierciedlać standardowy wygląd przycisków zgodnie z dyktowaniami systemu operacyjnego.

##### <a name="themed"></a>Tematyczne
W niektórych przypadkach przyciski mogą być używane w stylu interfejsu użytkownika, a te przyciski muszą mieć odpowiedni styl. Zobacz [okna dialogowe,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) aby uzyskać informacje na temat kontrolek z tematami.

### <a name="special-buttons"></a>Przyciski specjalne

#### <a name="browse-buttons"></a>Przeglądaj... Przyciski
**[Przeglądaj...]** Przyciski są używane w siatkach, oknach dialogowych i oknach narzędzi oraz innych nie moderowych elementach interfejsu użytkownika. Wyświetlają s wyboru, który pomaga użytkownikowi w wypełnieniu wartości w kontrolce. Istnieją dwie odmiany tego przycisku: długi i krótki.

![Długi przycisk [Przeglądaj...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Długi przycisk [Przeglądaj...]

![Przycisk wielokropka — tylko krótki [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Przycisk wielokropka — tylko krótki [...]

Kiedy używać krótkiego przycisku wielokropka:

- Jeśli w oknie dialogowym znajduje się więcej niż jeden długi przycisk **[Przeglądaj...],** na przykład gdy kilka pól zezwala na przeglądanie. Użyj krótkiego **przycisku [...]** dla każdego z **nich,** aby uniknąć mylących kluczy dostępu utworzonych w tej sytuacji (&**Przeglądaj** i B&wiersze w tym samym oknie dialogowym).

- W obcisłym oknie dialogowym lub gdy nie ma rozsądnego miejsca, aby umieścić długi przycisk.

- Jeśli przycisk pojawi się w kontrolce siatki.

Wskazówki dotyczące korzystania z przycisku:

- Nie używaj klucza dostępu. Aby uzyskać do niego dostęp przy użyciu klawiatury, użytkownik musi wykonać tabulator z sąsiedniej kontrolki. Upewnij się, że kolejność tabuł jest taka, aby każdy przycisk przeglądania przypadał bezpośrednio po polu, które zostanie wypełnine. Nigdy nie używaj podkreślenia poniżej pierwszego okresu.

- Ustaw właściwość Microsoft Active Accessibility (MSAA) **na** **Browse...** (z uwzględnieniem wielokropka), aby czytniki zawartości ekranu odczytały ją jako "Przeglądaj", a nie "kropka-kropka" lub "kropka-kropka". W przypadku kontrolek zarządzanych oznacza to ustawienie **właściwości AccessibleName.**

- Nigdy nie używaj przycisku wielokropka **[...]** dla niczego poza akcją przeglądania. Jeśli na przykład potrzebujesz **przycisku [Nowy...],** ale nie masz wystarczającej ilości miejsca na tekst, okno dialogowe musi zostać przeprojektowane.

##### <a name="sizing-and-spacing"></a>Zmiany rozmiaru i odstępy
![Przyciski zmiany rozmiaru [Przeglądaj...] : wersja standardowa to 75x23 piksele, krótka wersja to 26x23 piksele](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Przyciski zmiany rozmiaru [Przeglądaj...]

![Przyciski Odstępy [Przeglądaj...] : odstępy między powiązaną kontrolką i standardowym przyciskiem Przeglądaj 7 pikseli, odstępy między powiązaną kontrolką i krótkim przyciskiem Przeglądaj 5 pikseli](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Przyciski odstępów [Przeglądaj...]

#### <a name="graphical-buttons"></a>Przyciski graficzne
Niektóre przyciski powinny zawsze używać obrazu graficznego i nigdy nie zawierać tekstu, aby zaoszczędzić miejsce i uniknąć problemów z lokalizacji. Są one często używane w s pickerach pól i innych listach sortowalnych.

> [!NOTE]
> Użytkownicy muszą za pomocą klawisza Tab na tych przyciskach (nie ma kluczy dostępu), więc umieść je w rozsądnej kolejności. Zamapuj właściwość przycisku na akcję, która jest akcję, tak aby czytniki zawartości ekranu `name` prawidłowo zinterpretowały akcję przycisku.

| Funkcja | Przycisk |
| --- | --- |
| Dodaj | ![Graficzny przycisk "Dodaj"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Usuń | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Dodaj wszystko | ![Graficzny przycisk "Dodaj wszystko"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Usuń wszystko | ![Graficzny przycisk "Usuń wszystko"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Przenieś w górę | ![Graficzny przycisk "Przenieś w górę"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Przenieś w dół | ![Graficzny przycisk "Przenieś w dół"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Usuń | ![Graficzny przycisk "Usuń"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Zmiany rozmiaru i odstępy
Sposób zmiany rozmiaru przycisków graficznych jest taki sam jak w przypadku krótkiej wersji przycisku **[Przeglądaj...]** (26 x 23 piksele):

![Wygląd obrazu graficznego na przycisku z przezroczystym kolorem i bez niego](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Wygląd obrazu graficznego na przycisku z przezroczystym kolorem i bez niego

### <a name="hyperlinks"></a>Hiperlinki
Hiperlinki dobrze nadają się do akcji opartych na nawigacji, takich jak otwieranie tematu Pomocy, modalnego okna dialogowego lub kreatora. Jeśli dla polecenia jest używany hiperlink, zawsze powinna zostać w nim widoczna i zauważalna zmiana interfejsu użytkownika. Ogólnie rzecz biorąc, akcje, które zatwierdzają akcję (takie jak Zapisz, Anuluj i Usuń), lepiej komunikują się przy użyciu przycisku.

#### <a name="writing-style"></a>Styl pisania
Postępuj zgodnie ze [wskazówkami programu Windows Desktop, aby uzyskać tekst interfejsu użytkownika](/windows/desktop/uxguide/text-ui). Nie używaj fraz "Dowiedz się więcej o", "Powiedz mi więcej o" ani fraz "Uzyskaj pomoc w tym przypadku". Zamiast tego fraza Help link text (Pomoc) zawiera tekst linku w odniesieniu do podstawowego pytania, na które odpowiada zawartość Pomocy. Na przykład "**Jak mogę dodać serwer do Eksplorator serwera?**"

#### <a name="visual-style"></a>Styl wizualny

- Hiperlinki powinny zawsze [używać usługi VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService) Jeśli hiperlink nie ma poprawnego stylu, miga na czerwono, gdy jest aktywny, lub wyświetla inny kolor po odwiedzeniu.

- Nie dołączaj podkreśleń w stanie spoczynku kontrolki, chyba że link jest fragmentem zdania w pełnym zdaniu, na przykład w znaku wodnego.

- Podkreślenia nie powinny być wyświetlane po najechaniu kursorem. Zamiast tego opinie dla użytkownika, że link jest aktywny, to niewielka zmiana koloru i odpowiedni kursor linku.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Widoki drzewa

Widoki drzewa zapewniają sposób organizowania złożonych list w grupy nadrzędny-podrzędny. Użytkownik może rozwinąć lub zwinąć grupy nadrzędne, aby ujawnić lub ukryć bazowe elementy podrzędne. Każdy element w widoku drzewa można wybrać, aby zapewnić dalsze działania.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Styl wizualizacji widoku drzewa

#### <a name="expanders"></a>Ekspandery
Kontrolki widoku drzewa powinny być zgodne z projektem eksperatora używanym przez system Windows i Visual Studio. Każdy węzeł używa kontrolki eksperatora do ujawnienia lub ukrycia elementów bazowych. Używanie kontrolki eksperatora zapewnia spójność dla użytkowników, którzy mogą napotkać różne widoki drzewa w systemie Windows i Visual Studio.

![Odpowiedź prawidłowa: prawidłowy styl węzła widoku drzewa przy użyciu kontrolki eksperatora](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Odpowiedź prawidłowa: prawidłowy styl węzła widoku drzewa przy użyciu kontrolki eksperatora

![Niepoprawne: nieprawidłowy styl węzła widoku drzewa](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Niepoprawne: nieprawidłowy styl węzła widoku drzewa

#### <a name="selection"></a>Wybór
Po wybraniu węzła w widoku drzewa wyróżnienie powinno zostać rozwinięte do pełnej szerokości kontrolki widoku drzewa. Pomaga to użytkownikom w jasnym zidentyfikowaniu wybranego elementu. Kolory zaznaczenia powinny odzwierciedlać bieżący Visual Studio motywu.

![Odpowiedź prawidłowa: wyróżnienie wybranego węzła pasuje do całej szerokości kontrolki widoku drzewa.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Odpowiedź prawidłowa: wyróżnienie wybranego węzła pasuje do całej szerokości kontrolki widoku drzewa.

![Niepoprawnie: wyróżnienie wybranego węzła nie pasuje do całej szerokości kontrolki widoku drzewa.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Niepoprawnie: wyróżnienie wybranego węzła nie pasuje do całej szerokości kontrolki widoku drzewa.

#### <a name="icons"></a>Ikony
Ikony powinny być używane w kontrolkach widoku drzewa tylko wtedy, gdy pomagają wizualnie identyfikować różnice między elementami. Ogólnie rzecz biorąc, ikony powinny być używane tylko na listach heterogenicznych, w których ikony zawierają informacje w celu odróżnienia typów elementów. Na jednorodnej liście za pomocą ikon można często postrzegać jako szum i należy ich unikać. W takim przypadku ikona grupy (nadrzędna) może przekazać typ elementów w tej grupie. Wyjątkiem od tej reguły jest to, że ikona jest dynamiczna i służy do wskazywania stanu.

#### <a name="scroll-bars"></a>Paski przewijania
Paski przewijania powinny być zawsze ukryte, jeśli zawartość mieści się w kontrolce widoku drzewa. Paski przewijania mogą być ukryte lub półprzezroczyste w oknie przewijanym i wyświetlane, gdy okno zawierające widok drzewa ma fokus lub po najechaniu kursorem na sam widok drzewa.

![Wyświetlane są zarówno pionowe, jak i poziome paski przewijania, ponieważ zawartość przekroczyła limity kontrolki widoku drzewa.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Wyświetlane są zarówno pionowe, jak i poziome paski przewijania, ponieważ zawartość przekroczyła limity kontrolki widoku drzewa.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interakcje w widoku drzewa

#### <a name="context-menus"></a>Menu kontekstowe
Węzeł widoku drzewa może wyświetlać opcje podmenu w menu kontekstowym. Zwykle dzieje się tak, gdy użytkownik kliknął prawym przyciskiem myszy element lub nacisnął klawisz Menu na klawiaturze systemu Windows z wybranym elementem. Ważne jest, aby węzeł skupił się i został wybrany. Dzięki temu użytkownik może zidentyfikować element, do którego należy podmenu.

![Element, który wygenerował menu kontekstowe, koncentruje się na powiadamianiu użytkownika o tym, który element został wybrany.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Element, który wygenerował menu kontekstowe, koncentruje się na powiadamianiu użytkownika o tym, który element został wybrany.

#### <a name="keyboard"></a>Klawiatura
Widok drzewa powinien zapewniać możliwość wybierania elementów i rozwijania/zwijania węzłów przy użyciu klawiatury. Dzięki temu nawigacja spełnia nasze wymagania dotyczące ułatwień dostępu.

##### <a name="tree-view-control"></a>Kontrolka widoku drzewa
Visual Studio drzewa powinny być zgodne z pospolitą nawigacją za pomocą klawiatury:

- **Strzałka w górę:** Wybieranie elementów przez przeniesienie drzewa w górę

- **Strzałka w dół:** Wybieranie elementów przez przejście w dół drzewa

- **Strzałka w prawo:** Rozwijanie węzła w drzewie

- **Strzałka w lewo:** Zwijanie węzła w drzewie

- **Wprowadź klucz:** Inicjowanie, ładowanie, wykonywanie wybranego elementu

##### <a name="trid-tree-view-and-grid-view"></a>Trid (widok drzewa i widok siatki)
Tridowana kontrolka to złożona kontrolka, która zawiera widok drzewa w siatce. Rozwijanie, zwijanie i nawigowanie po drzewie powinno dotyczyć tych samych poleceń klawiatury co widok drzewa z następującymi dodatkami:

- **Strzałka w prawo:** Rozwiń węzeł. Po rozwinięciu węzła powinien on kontynuować przechodzenie do najbliższej kolumny po prawej stronie. Nawigacja powinna zatrzymać się na końcu wiersza.

- **Karta:** Przechodzi do najbliższej komórki po prawej stronie.  Na końcu wiersza nawigacja jest kontynuowana do następnego wiersza.

- **Shift + Tab:** Przechodzi do najbliższej komórki po lewej stronie.  Na początku wiersza nawigacja jest kontynuowana do prawej komórki w poprzednim wierszu.

![Kontrolka trydowana w Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Kontrolka trydowana w Visual Studio
