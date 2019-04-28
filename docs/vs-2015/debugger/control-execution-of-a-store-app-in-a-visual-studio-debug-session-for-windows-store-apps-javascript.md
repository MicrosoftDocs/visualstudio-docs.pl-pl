---
title: Kontrolowanie wykonywania aplikacji Store w trakcie sesji debugowania dla aplikacji Windows Store (JavaScript) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9238bd4f42291af23a1279c9caa83f1039c8f249
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437758"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Kontrolowanie wykonywania aplikacji Store w trakcie sesji debugowania programu Visual Studio dla aplikacji Windows Store (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik Szybki start pokazuje, jak przechodzić w debugerze programu Visual Studio i jak wyświetlić stan programu w sesji.

 Ten przewodnik Szybki start jest dla deweloperów, którzy są nowe debugowanie przy użyciu programu Visual Studio, a sesja debugowania dla deweloperów, którzy chcą dowiedzieć się więcej o przechodząc w programie Visual Studio. Techniki debugowania sam nie jest nauka. Funkcje w przykładowym kodzie są przeznaczone tylko do zademonstrowania debugowania procedur opisanych w tym temacie. Funkcje nie stosować najlepsze rozwiązania projekt aplikacji lub funkcji. W rzeczywistości zostanie szybko odkryjesz, że funkcje i aplikacji oraz nie wykonać wiele niczego na wszystkich.

 Części tego przewodnika Szybki start zostały zaprojektowane jako jako niezależny, jak to możliwe, dzięki czemu można pominąć dowolną sekcję, która zawiera informacje, które już znasz z. Ponadto nie są wymagane do tworzenia przykładowej aplikacji. Jednak firma Microsoft zaleca, aby go i wprowadziliśmy proces tak proste, jak to możliwe.

 **Debuger skróty klawiaturowe.** Nawigacja w debugerze programu Visual Studio jest zoptymalizowany, myszy i klawiatury. Wiele z tych kroków w tym temacie obejmują klawiszem skrótu lub klawisza skrótu w nawiasach uwagi. Na przykład (klawiatury: F5) wskazuje, że wpisanie klawisza F5 rozpoczyna się lub kontynuuje wykonywanie debugera.

> [!NOTE]
> **Wzorzec modułu**
>
> Aplikacje Windows Store często używają JavaScript *wzorzec modułu* do hermetyzacji danych i funkcji na stronie. Wzorzec modułu używa zamknięcia pojedynczego własnym wykonywania i anonimowe być oddzielone od globalnej przestrzeni nazw funkcji strony. W tym temacie nazywamy tej funkcji *modułu*.

## <a name="in-this-topic"></a>W tym temacie:
 Możesz dowiedzieć się jak:

 [Tworzenie przykładowej aplikacji](#BKMK_Create_the_sample_app)

 [Ustaw i uruchom do punktu przerwania, krok po kroku do funkcji i zbadaj dane do programu](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [Krok do, za pośrednictwem i z funkcji](#BKMK_Step_into__over__and_out_of_functions)

 [Ustawianie warunkowego punktu przerwania, uruchom do kursora i wizualizować zmienną](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Wyświetlanie danych zmiennej w oknie zmienne lokalne](#BKMK_View_variable_data_in_the_Locals_window)

- [Wyświetlanie danych zmiennej i łańcuch prototypów obiektu](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Sprawdzanie danych łańcucha zakresu](#BKMK_Examine_scope_chain_data)

  [Nawigowanie do kodu przy użyciu okna stosu wywołań](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

## <a name="BKMK_Create_the_sample_app"></a> Tworzenie przykładowej aplikacji
 Debugowanie jest dotyczące kodu, więc Przykładowa aplikacja używa strukturę aplikacji Windows Store, tylko w celu utworzenia pliku źródłowego, w którym widać, jak działa nawigowanie sesji debugowania oraz sposób sprawdzić stan programu. Cały kod, który będzie wywoływał jest wywoływana z `module` funkcja pliku default.js kod. Brak kontrolek są dodawane, a żadne zdarzenia nie są obsługiwane.

1. **Tworzenie pustej aplikacji JavaScript Windows Store.** Otwórz program Visual Studio. Na stronie głównej wybierz **nowy projekt** łącza. Na **nowy projekt** okna dialogowego wybierz **JavaScript** w **zainstalowane** listy, a następnie wybierz **Windows Store**. Na liście szablonów projektu wybierz **pusta aplikacja**. Visual Studio tworzy nowe rozwiązanie i projekt i wyświetla plik default.htm w edytorze kodu.

    Należy pamiętać, pliki skryptów, które są ładowane do strony.

   - `base.js` i `ui.js` utworzyć pliki **biblioteki Windows dla JavaScript**. Biblioteka Windows dla języka JavaScript jest zestaw JavaScript i plików CSS, które ułatwiają tworzenie aplikacji Windows Store przy użyciu języka JavaScript. Umożliwia ona wraz z HTML, CSS i środowisko wykonawcze Windows tworzenie aplikacji.

   - Kod uruchamia się w `default.js` pliku.

2. **Otwórz plik default.js źródła.** W Eksploratorze rozwiązań Otwórz **js** węzeł i wybierz polecenie `default.js`.

3. **Zastąp zawartość strony z przykładowym kodem.** Usuń całą zawartość z `default.js` pliku. Skorzystaj z tego linku: [Przykładowy kod nawigacji (JavaScript) debugera](../debugger/debugger-navigation-sample-code-javascript.md), a następnie skopiuj kod przedstawiony w sekcji kodu JavaScript do Schowka. (Wybierz **ponownie** w przeglądarce lub podglądu pomocy, aby powrócić do tej strony szybki start.) W edytorze programu Visual Studio, Wklej kod do pustych teraz `default.js`. Wybierz **Ctrl + S** można zapisać pliku.

   Teraz można wykonać wraz z przykładami w tym temacie.

## <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Ustaw i uruchom do punktu przerwania, krok po kroku do funkcji i zbadaj dane do programu
 Najczęstszym sposobem, aby rozpocząć sesję debugowania jest wybranie **Rozpocznij debugowanie** z **debugowania** menu (klawiatury: F5). Aplikacja rozpoczyna się i kontynuuje wykonywanie dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi wyjątek, lub kończy się w aplikacji.

 Zawieszenia wykonania w debugerze, możesz wyświetlić wartość zmiennej active w oknie z poradami danych przez umieszczenie wskaźnika myszy na zmiennej.

 Po wstrzymaniu wykonywania aplikacji (zwaną również przerwanie w debugerze), możesz kontrolować sposób, który wykonuje w pozostałej części kodu programu. Przenoszenie z wywołania funkcji do funkcji, można kontynuować wiersz po wierszu lub wywołana funkcja może wykonać w jednym kroku. Te procedury są nazywane krokowe wykonywanie aplikacji. Można również wznowić standardowa wykonywanie aplikacji, systemem do następnego punktu przerwania, które zostały ustawione lub do wiersza, w której umieszczony kursor. Można zatrzymać sesji debugowania w dowolnym momencie. Debuger jest przeznaczony do wykonania niezbędnych operacji czyszczenia i zakończyć wykonywanie.

### <a name="BKMK_Example_1"></a> Przykład 1
 W tym przykładzie ustaw punkt przerwania w treści `module` działa w programach `default.js` ponieważ wywołuje pierwszej instrukcji naszych użytkowników. Następnie wejdź do funkcji, wyświetlanie wartości zmiennych w poradach dotyczących debugera, a następnie zatrzymasz debugowanie.

1. **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `callTrack = "module function";` występuje tuż po wywołaniu `app.start()`. Wybierz wiersz w zacieniowane odstępu Edytor kodu źródłowego (klawiatury: Umieść kursor w wierszu, a następnie wybierz **F9** klucza).

    ![Ustaw punkt przerwania w przykład1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Ikona punktu przerwania pojawia się na marginesie.

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).

    Aplikacja rozpoczyna wykonywanie i zawiesza wykonywanie tuż przed instrukcji, w którym można ustawić punkt przerwania. Bieżąca ikona wierszu na marginesie identyfikuje Twojej lokalizacji i bieżącej instrukcji jest wyróżniona.

    ![Uruchom do punktu przerwania](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Teraz masz kontrolę nad wykonywanie aplikacji i sprawdzić stan programu podczas wykonywania kroków za pomocą instrukcji programu.

3. **Wejdź do funkcji.** Na **debugowania** menu, wybierz **Step Into** (klawiatury: **F11**).

    ![Wiersz kodu krok po kroku](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Należy zauważyć, że debuger przechodzi do następnego wiersza, który jest wywołanie `example1` funkcji. Wybierz **Step Into** ponownie. Debuger przenosi do pierwszego wiersza kodu `example1` funkcji. Wyróżniony wiersz nie został wykonany, ale funkcja została załadowana w stosie wywołań i przydzieliła pamięć dla zmiennych lokalnych.

4. Gdy wchodzisz do wiersza kodu debuger wykonuje jedną z następujących czynności:

   - Następna instrukcja nie jest wywołanie funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie zawiesza wykonywanie.

   - Jeśli instrukcja jest wywołaniem funkcji w rozwiązaniu, debuger przenosi do pierwszego wiersza wywoływanej funkcji, a następnie zawiesza wykonywanie.

     Wejdź do instrukcje w dalszym ciągu `example1` aż do osiągnięcia punktu wyjścia. Do usuwania błędów podkreśli zamykający nawias klamrowy funkcji.

5. **Wyświetlanie wartości zmiennych w poradach dotyczących danych.** Wejdź do instrukcje w dalszym ciągu `example1` aż do osiągnięcia punktu wyjścia. Do usuwania błędów podkreśli zamykający nawias klamrowy funkcji. Po wstrzymaniu myszą na nazwę zmiennej, nazwę i wartość zmiennej są wyświetlane w oknie z poradami danych.

    ![Wyświetlanie wartości zmiennych w oknie z poradami danych](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **Dodaj wyrażenie kontrolne dla zmiennej callTrack.** `callTrack` Zmienna jest używana w tym przewodniku Szybki start, aby pokazać funkcji wywoływanych w przykładach. Aby ułatwić wyświetlić wartość zmiennej, należy go dodać do okna czujki. Wybierz nazwę zmiennej w edytorze, a następnie wybierz **Dodaj czujkę** z menu skrótów.

    ![Obejrzyj zmienną](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Możesz obejrzeć wiele zmiennych w oknie czujki. Wartości zmiennych obserwowana, takie jak wartości w systemie windows Porada danych, są aktualizowane, zawsze wtedy, gdy wykonanie programu jest zawieszone. Obserwowana zmiennych są zapisywane między sesjami debugowania.

7. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift+F5**). Kończy sesję debugowania.

## <a name="BKMK_Step_into__over__and_out_of_functions"></a> Krok do, za pośrednictwem i z funkcji
 W przeciwieństwie do przechodzenie krok po kroku do funkcji wywoływanych przez funkcję nadrzędnego, przechodzenie krok po kroku, za pośrednictwem funkcji wykonuje funkcję podrzędnych, a następnie zawieszenie wykonywania w funkcji wywołującej, jako element nadrzędny wznawia działanie. Może być Przekrocz nad funkcja, przypadku wiedzą, jak funkcja działa i pewności, czy jego wykonanie nie ma wpływu na problem, który badania.

 Pominięcie wiersza kodu, który nie zawiera wywołanie funkcji wykonuje wiersza, podobnie jak przechodzenie do wiersza.

 Przechodzenie krok po kroku z funkcji podrzędnych kontynuuje wykonywanie funkcji, a następnie zawiesza wykonywanie po funkcja zwraca dla jej funkcji wywołującej. Może być wychodzenia z funkcję długo, gdy już wiesz, pozostała część funkcji nie jest znaczący.

 Pominięcie i przechodzenie krok po kroku z funkcji wykonanie funkcji.

 ![Krok do, przez niego lub poza metody](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="BKMK_Example_2"></a> Przykład 2
 W tym przykładzie kroku do, za pośrednictwem i z funkcji.

1. **Wywołaj funkcję przykład2 w funkcji modułu.** Edytuj `module` działać, a następnie zastąp następujący wiersz `var callTrack = "module function"` z `example2();`.

     ![Wywołaj funkcję przykład2](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger zawiesza wykonywanie w punkcie przerwania.

3. **Przekrocz nad wiersz kodu.** Na **debugowania** menu, wybierz **Step Over** (klawiatury: F10). Debuger wykonuje `var callTrack = "module function"` instrukcji w taki sam sposób jak przechodzenie do instrukcji.

4. **Wejdź do przykład2 i example2_a.** Wybierz **F11** klucza, aby wejść do `example2` funkcji. Wkrocz w dalszym ciągu `example2` instrukcjami aż do wiersza `var x = example2_a();`. Ponownie, wejdź do tego wiersza, aby przejść do punktu wejścia `example2_a`. Przejdź do kroku do każdej instrukcji z `example2_a` aż powrócisz do `example2`.

     ![Przekrocz nad funkcją](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5. **Przekrocz nad funkcją.** Należy zauważyć, że następnego wiersza w `example2`, `var y = example2_a();` jest zasadniczo taki sam jak w poprzednim wierszu. Możesz bezpiecznie wejść na tym wierszu. Wybierz **F10** klawisz, aby przejść z wznowienie `example2` do tego drugie wywołanie `example2_a`. Należy pamiętać, że `callTrack` ciąg wskazuje `example2_a` funkcja była wykonywana dwa razy.

6. **Wyjdź z funkcji.** Wybierz **F11** klucza, aby wejść do `example2_b` funkcji. Należy pamiętać, że `example2_b` nie jest bardzo różnią się od `example2_a`. Aby wychodzenie z funkcji, wybierz opcję **Step Out** na **debugowania** menu (klawiatury: **Shift+F11**). Należy pamiętać, że `callTrack` zmienna oznacza, że `example2_b` została wykonana i zwróconą przez debuger do punktu gdzie `example2` wznawia działanie.

7. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift+F5**). Kończy sesję debugowania.

## <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Ustawianie warunkowego punktu przerwania, uruchom do kursora i wizualizować zmienną
 Warunkowego punktu przerwania określa warunek, który powoduje, że debuger w celu wstrzymania wykonywania. Warunek jest określona przez dowolne wyrażenie kodu, które mogą być obliczane jako wartość true lub false. Może na przykład użyć warunkowego punktu przerwania, aby sprawdzić stan programu w często wywoływana funkcja tylko wtedy, gdy zmienna osiągnie określoną wartość.

 Wykonywanie do kursora działa jak ustawienie jednorazowe punktu przerwania. Gdy wykonanie programu jest zawieszone, można zaznacz wiersz w źródle i wznowić wykonywanie aż do osiągnięcia wybrany wiersz. Na przykład możesz może być krokowe wykonywanie pętli w funkcji i określić, że kod w pętli działa prawidłowo. Zamiast krokowe wykonywanie każdej iteracji pętli, można uruchomić do kursora, który jest umieszczony po wykonaniu pętli.

 Czasami trudno jest wyświetlanie wartości zmiennej w wierszu etykietki danych lub inne okno danych. Debuger może wyświetlać ciągów, HTML i Xml w Wizualizator tekstu, który przedstawia widok sformatowanych wartości w oknie przewijany.

### <a name="BKMK_Example_3"></a> Przykład 3
 W tym przykładzie można ustawić warunkowego punktu przerwania Przerwij przy określonej iteracji pętli, a następnie uruchom do kursora, który jest umieszczony po pętli. Możesz również wyświetlić wartość zmiennej w Wizualizator tekstu.

1. **Wywołaj funkcję przykład3 w funkcji modułu.** Edytuj `module` działać, a następnie zastąp następujący wiersz `var callTrack = "module function";` z linią `example3();`.

     ![Wywołaj przykład3](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger zawiesza wykonywanie w punkcie przerwania w `module` funkcji.

3. **Wejdź do funkcji przykład3.** Wybierz **Step Into** na **debugowania** menu (klawiatury: **F11**) można przenieść do punktu wejścia `example3` funkcji. Kontynuuj przechodzenie do funkcji, dopóki nie mają postanowiliśmy jednego lub dwóch pętli `for` bloku. Należy pamiętać, że może upłynąć możesz dużo czasu, aby przejść przez wszystkie iteracje 1000.

4. **Ustaw warunkowego punktu przerwania.** W lewym marginesie na oprawę okna kodu, kliknij prawym przyciskiem myszy wiersz `s += i.toString() + "\n";` , a następnie wybierz **warunek** w menu skrótów.

     Wybierz **warunek** pole wyboru, a następnie wpisz `i == 500;` w polu tekstowym. Wybierz **ma wartość true** opcji, a następnie wybierz **OK**. Punkt przerwania pozwala sprawdzić wartość iteracji 500th `for` pętli. Ikona warunkowego punktu przerwania są identyfikowane przez jego między białe.

     ![Ikona punktu przerwania blokada](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5. **Uruchom do punktu przerwania.** Na **debugowania** menu, wybierz **Kontynuuj** (klawiatury: **F5**). Zatrzymaj się na `i` do upewnij się, że bieżąca wartość `i` wynosi 500. Należy również zauważyć, że zmienna `s` jest reprezentowany jako jeden wiersz i jest znacznie dłuższy niż okno porad danych.

6. **Umożliwia wizualizację zmiennej ciągu.** Kliknij ikonę lupy w oknie z poradami danych z `s`.

     Zostanie wyświetlone okno Wizualizator tekstu i wartość ciągu jest przedstawiany jako ciąg wielowierszowy.

     ![Debugowanie Wizualizator tekstu](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7. **Uruchom do kursora.** Zaznacz wiersz `callTrack += "->example3";` , a następnie wybierz **Uruchom do kursora** w menu kontekstowym (klawiatura: **Ctrl+F10**). Debuger kończy iteracji pętli, a następnie zawiesza wykonywanie w wierszu.

8. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift+F5**). Kończy sesję debugowania.

### <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Użyj Uruchom do kursora, aby powrócić do kodu i Usuń punkt przerwania
 Wykonywanie do kursora może być bardzo przydatne, gdy masz schodkowego do biblioteki kodu od firmy Microsoft lub innych firm. Krokowe wykonywanie kodu biblioteki mogą być informacyjne, często może potrwać dłuższy czas. I na ogół interesuje Cię o wiele bardziej we własnym kodzie. To ćwiczenie dowiesz się, jak to zrobić.

1. **Ustaw punkt przerwania w wywołaniu app.start.** W `module` funkcji, ustaw punkt przerwania w wierszu `app.start()`

2. **Uruchom do punktu przerwania i wejdź do funkcji biblioteki.**

     Gdy wkroczyć do `app.start()`, w edytorze są wyświetlane kod w `base.js`. Wejdź do kilku więcej wierszy.

3. **Krok na i z funkcji.** Jak Przekrocz nad (**F10**) i przejść z (**SHIFT + F11**) możesz pisać kod w `base.js`, można trafić do wniosku, sprawdzając złożoności i długość funkcja start jest nieodpowiednia do realizacji.

4. **Ustaw kursor w kodzie, a następnie uruchom do niego.** Przejdź z powrotem do `default.js` plik w edytorze kodu. Wybierz pierwszy wiersz kodu po `app.start()` (nie można uruchomić komentarz lub pusty wiersz). Wybierz **Uruchom do kursora** z menu skrótów. Debuger kontynuuje wykonywanie funkcji app.start i zawiesza wykonywanie w punkcie przerwania.

## <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Wyświetlanie danych zmiennej w oknie zmienne lokalne
 System windows zmiennych lokalnych jest widok drzewa parametry i zmienne w łańcuchu zakresu aktualnie wykonywanej funkcji.

### <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Wyświetlanie danych zmiennej i łańcuch prototypów obiektu

1. **Dodaj obiekt array funkcji modułu.** Edytuj `module` działać, a następnie zastąp następujący wiersz `var callTrack = "module function"` z `var myArray = new Array(1, 2, 3);`

     ![Definicja myArray](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger zawiesza wykonywanie w punkcie przerwania. Wkrocz do wiersza.

3. **Otwórz okno zmiennych lokalnych.** Na **debugowania** menu wskaż **Windows**, a następnie wybierz **lokalne**. (Klawiatura: ALT+ 4).

4. **Sprawdź zmienne lokalne w funkcji modułu** zmiennych lokalnych w system windows Wyświetla zmienne aktualnie wykonywanej funkcji ( `module` funkcji) jako najwyższego poziomu węzła drzewa. Podczas wprowadzania funkcji JavaScript tworzy wszystkie zmienne i umożliwia im wartość `undefined`. Funkcje, które są zdefiniowane w funkcji ma ich tekst jako wartość.

     ![Okno zmiennych lokalnych](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5. **Krokowo callTrack i myArray definicje.** Zmienne callTrack i myArray można znaleźć w oknie zmienne lokalne. Przekrocz nad (**F10**) dwie definicje i zwróć uwagę, że **wartość** i **typu** pola są zmieniane. Okno zmiennych lokalnych wyróżniono wartości zmiennych, które uległy zmianie od ostatniej przerwy.

6. **Sprawdź obiektu myArray** rozwiń `myArray` zmiennej. Każdy element tablicy znajduje się na liście **[prototypu]** węzeł, który zawiera hierarchii dziedziczenia `Array` obiektu. Rozwiń ten węzeł.

     ![Łańcuch prototypów w oknie zmienne lokalne](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    - **Metody** węzła zawiera listę wszystkich metod `Array` obiektu.

    - **[Prototypu]** węzeł zawiera prototyp `Object` obiektu, z którego `Array` pochodzi. **[prototypu]**  węzły mogą być cykliczne. Każdego obiektu nadrzędnego w hierarchii obiektów jest opisana w **[prototypu]** węzła jego podrzędny.

7. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: Shift+F5). Kończy sesję debugowania.

## <a name="BKMK_Examine_scope_chain_data"></a> Sprawdzanie danych łańcucha zakresu
 *Zakresu łańcucha* funkcji obejmuje wszystkie zmienne, które są aktywne i osiągalny przez funkcję. Zmienne globalne są częścią łańcucha zakres, są wszystkie obiekty (w tym funkcji), które są zdefiniowane w funkcji, która definiuje aktualnie wykonywanej funkcji. Na przykład `callTrack` zmiennej, która jest zdefiniowana w `module` funkcji `default.js` jest dostępny za pomocą dowolnej funkcji, która jest zdefiniowana w `module` funkcji. Każdego zakresu jest wyświetlany osobno w oknie zmienne lokalne.

- Zmienne aktualnie wykonywanej funkcji są wyświetlane w górnej części okna.

- Zmienne każdego zakresu funkcji w łańcuchu zakresu są wyświetlane w obszarze **[zakresu]** węzła dla tej funkcji. Zasięg funkcje są wyświetlane według ich kolejność w łańcuchu z funkcji, który definiuje bieżącą funkcję najbardziej zewnętrzną funkcję łańcucha.

- **[Globals]** węzła zawiera listę obiektów globalnych, które są zdefiniowane poza jakąkolwiek funkcją.

  Łańcuchy zakres może być mylące i najlepiej są przedstawione według przykładu. W poniższym przykładzie można zobaczyć jak `module` funkcja tworzy własnego zakresu i sposób tworzenia drugiego poziomu zakresu, tworząc zamknięcie.

### <a name="BKMK_Example_4"></a> Przykład 4

1. **Wywołaj funkcję przykład4 z funkcji modułu.** Edytuj `module` działać, a następnie zastąp następujący wiersz `var callTrack = "module function"` z `example4()`:

     ![Wywołaj przykład4](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger zawiesza wykonywanie w punkcie przerwania.

3. **Otwórz okno zmiennych lokalnych.** Jeśli to konieczne, na **debugowania** menu wskaż **Windows**, a następnie wybierz **zmiennych lokalnych**. (Klawiatura: **Alt+4**). Pamiętaj, że okno wyświetla wszystkie zmienne i funkcje w `module` funkcji, a także **[Globals]** węzła.

4. **Sprawdź zmienne globalne.** Rozwiń **[Globals]** węzła. Obiekty i zmienne globalne zostały określone przez biblioteki Windows dla języka JavaScript. Możesz dodać własne zmienne do globalnego zakresu.

5. **Wejdź do przykład4 i sprawdź jego lokalnego i zakres zmiennych** Wkrocz do (klawiatury: **F11**) `example4` funkcji. Ponieważ `example4` jest zdefiniowany w `module` funkcji `module` funkcji staje się w zakresie nadrzędnym. `example4` można wywołać funkcje w `module` funkcji i uzyskać dostęp do swoich zmiennych. Rozwiń **[zakresu]** węzła w oknie zmienne lokalne i zwróć uwagę, że zawiera takie same i zmienne `module` funkcji.

     ![Zakresy metody przykład4](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6. **Wejdź do example4_a i sprawdź jego lokalnego i zakres zmiennych** Wkrocz w dalszym ciągu `example4` do wywołania `example4_a`. Należy zauważyć, że zmienne lokalne są teraz z `example4_a`oraz że **[zakresu]** węzła w dalszym ciągu przechowywania zmiennych z `module` funkcji. Mimo że zmienne `example4` są aktywne, nie można osiągnąć przez `example4_a` i nie są już częścią łańcucha zakresu.

7. **Wejdź do multiplyByA i sprawdź jego lokalnego i zakres zmiennych** kroku przez pozostałą część `example4_a` i w wierszu `var x = multiplyByA(b);`.

     Zmienna funkcja `multiplyByA` został ustawiony na `multiplyClosure` funkcja, która jest *zamknięcia*. `multiplyClosure` definiuje i zwraca funkcję wewnętrzny `multiplyXby`i przechwytuje (zamyka za pośrednictwem) jego parametrów i zmiennych. W przypadku zamknięcia zwracanej funkcji wewnętrznego ma dostęp do danych funkcji zewnętrznej i tak więc tworzy poziomu zakresu.

     Gdy wkroczyć do `var x = multiplyByA(b);`, Przenieś do `return a * b;` linię `multiplyXby` wewnętrznej funkcji.

8. W oknie zmienne lokalne tylko parametr `b` znajduje się w zmiennej lokalnej w `multiplyXby`, ale jest to nowy **[zakresu]** poziomie został dodany. Rozwinięcie tego węzła, zobaczysz, że zawiera parametry, funkcje i zmienne `multiplyClosure`, w tym `a` zmiennej o nazwie w pierwszym wierszu metody `multiplyXby`. Szybkie sprawdzenie drugiej **[zakresu]** węzeł, co spowoduje wyświetlenie zmiennych funkcji modułu, który `multiplyXby` uzyskuje dostęp do jego następnego wiersza.

9. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift+F5**). Kończy sesję debugowania.

## <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Nawigowanie do kodu przy użyciu okna stosu wywołań
 Stos wywołań jest strukturą danych, który zawiera informacje na temat funkcji, które są wykonywane w bieżącym wątku aplikacji. Po osiągnięciu punktu przerwania w oknie wywołania stosu Wyświetla listę wszystkich funkcji, które są aktywne na stosie. Aktualnie wykonywanej funkcji znajduje się na górze listy okno stosu wywołań. Funkcja, która inicjuje wątek znajduje się w dolnej części listy. Funkcje pomiędzy Pokaż ścieżkę wywołania funkcji inicjujący do bieżącej funkcji.

 Oprócz wyświetlania ścieżki wywołania do aktualnie wykonywanej funkcji, oknie wywołania stosu, może służyć do nawigowanie do kodu w edytorze kodu. Ta funkcja może być przydatne, gdy pracujesz z wieloma plikami i chcesz szybko przejść do określonej funkcji.

### <a name="BKMK_Example_5"></a> Przykład 5
 W tym przykładzie kroku do ścieżki wywołań, który zawiera pięć funkcje zdefiniowane przez użytkownika.

1. **Wywołaj funkcję example5 w funkcji modułu.** Edytuj `module` działać, a następnie zastąp następujący wiersz `var callTrack = "module function";` z linią `example5();`.

     ![Wywołaj example5](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger zawiesza wykonywanie w punkcie przerwania w funkcji modułu.

3. **Otwórz okno stosu wywołań.** Na **debugowania** menu, wybierz **Windows**, a następnie wybierz **stos wywołań** (klawiatury: ALT+ 7). Należy zwrócić uwagę na to, że w oknie stos wywołań są wyświetlane dwie funkcje:

    - **Kod globalny** jest punktem wejścia `module` funkcji w dolnej części stosu wywołań.

    - **Funkcja anonimowa** wyświetlany jest wiersz w `module` funkcja, której wykonanie programu jest zawieszone. Jest to góra stosu wywołań.

4. **Wejdź do funkcji, aby dotrzeć do funkcji example5_d.** Wybierz **Step Into** na **debugowania** menu (klawiatury: **F11**) do wykonania wywołania w ścieżce wywołania, aż do punktu wejścia funkcji example5_d. Należy pamiętać, że każdorazowo, funkcja wywołuje funkcję, numer wiersza funkcji wywołującej jest zapisywana i wywołanej funkcji jest umieszczany na górze stosu. Numer wiersza funkcji wywołującej jest punkt, w którym funkcja wywołująca wstrzymał wykonywanie. Żółta strzałka wskazuje aktualnie wykonywanej funkcji.

     ![Okno stosu wywołań](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5. **Korzystanie z okna stosu wywołań do nawigowania w kodzie example5_a i ustaw punkt przerwania.** W oknie wywołania stosu, wybierz `example5_a` elementu listy, a następnie wybierz **przejdź do źródła** w menu skrótów. Edytor kodu ustawia jego kursor w wierszu zwrotny funkcji. Ustaw punkt przerwania w tym wierszu. Należy pamiętać, że bieżący wiersz wykonania nie ulega zmianie. Tylko kursora w edytorze został przeniesiony.

6. **Wejdź do funkcji, a następnie uruchom do punktu przerwania.** Kontynuuj przechodzenie do `example5_d`. Należy pamiętać, że po powrocie z tej funkcji jest traktowana stosu wywołań. Naciśnij klawisz **F5** do kontynuowania wykonywania programu. Można zatrzymać w punkcie przerwania, utworzony w poprzednim kroku.

7. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift+F5**). Kończy sesję debugowania.

## <a name="see-also"></a>Zobacz też
 [Rozpocznij sesję debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [Szybki Start: Debuger nawigacji (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
