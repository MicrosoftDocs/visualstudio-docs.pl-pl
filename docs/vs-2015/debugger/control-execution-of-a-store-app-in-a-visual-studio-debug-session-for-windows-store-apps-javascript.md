---
title: Sterowanie wykonywaniem aplikacji ze sklepu w sesji debugowania dla aplikacji ze sklepu Windows (JavaScript) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828616"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Kontrolowanie wykonywania aplikacji ze Sklepu w trakcie sesji debugowania programu Visual Studio dla aplikacji ze Sklepu Windows (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik Szybki Start przedstawia sposób nawigowania w debugerze programu Visual Studio oraz sposób wyświetlania stanu programu w sesji.

 Ten przewodnik Szybki Start jest przeznaczony dla deweloperów, którzy są nowym programem do debugowania w programie Visual Studio i dla deweloperów, którzy chcą dowiedzieć się więcej na temat nawigowania w sesji debugowania programu Visual Studio. Nie uczy się grafiki samego debugowania. Funkcje w przykładowym kodzie są przeznaczone tylko do zademonstrowania procedur debugowania opisanych w tym temacie. Funkcje nie wykorzystują najlepszych rozwiązań dotyczących projektowania aplikacji lub funkcji. W rzeczywistości będziesz szybko wykryć, że funkcje i sama aplikacja nie wykonują wielu wszystkich elementów.

 Sekcje tego przewodnika Szybki Start zostały zaprojektowane tak, aby były tak niezależne, aby można było pominąć każdą sekcję, która zawiera informacje, które już znasz. Nie trzeba również tworzyć przykładowej aplikacji. Zaleca się jednak, aby proces był możliwie łatwy, jak to możliwe.

 **Skróty klawiaturowe debugera.** Nawigacja w debugerze programu Visual Studio jest zoptymalizowana zarówno dla myszy, jak i klawiatury. Wiele kroków tego tematu obejmuje akcelerator klawiatury lub klawisz skrótu w uwagach. Na przykład (klawiatura: F5) wskazuje, że wpisanie klawisza F5 spowoduje rozpoczęcie lub kontynuowanie wykonywania debugera.

> [!NOTE]
> **Wzorzec modułu**
>
> Aplikacje ze sklepu Windows często używają *wzorca modułu* JavaScript do hermetyzowania danych i funkcji na stronie. Wzorzec modułu używa jednego, samoobsługowego i anonimowego zamknięcia, aby zachować funkcjonalność strony niezależnie od globalnej przestrzeni nazw. W tym temacie wywołujemy funkcję *modułu*.

## <a name="in-this-topic"></a>W tym temacie:
 Możesz dowiedzieć się, jak:

 [Tworzenie przykładowej aplikacji](#BKMK_Create_the_sample_app)

 [Ustaw i uruchom do punktu przerwania, Wkrocz do funkcji i Przeanalizuj dane programu](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [Wkroczenie, przekroczenie i wyjście z funkcji](#BKMK_Step_into__over__and_out_of_functions)

 [Ustaw punkt przerwania warunkowego, Uruchom do kursora i Wizualizuj zmienną](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Wyświetlanie danych zmiennej w oknie zmiennych lokalnych](#BKMK_View_variable_data_in_the_Locals_window)

- [Wyświetlanie danych zmiennych i łańcucha prototypów obiektu](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Sprawdzanie danych łańcucha zakresu](#BKMK_Examine_scope_chain_data)

  [Przejdź do kodu przy użyciu okna stosu wywołań](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

## <a name="create-the-sample-app"></a><a name="BKMK_Create_the_sample_app"></a> Tworzenie przykładowej aplikacji
 Debugowanie dotyczy kodu, więc przykładowa aplikacja używa struktury aplikacji ze sklepu Windows tylko w celu utworzenia pliku źródłowego, w którym można zobaczyć, jak działa przechodzenie do sesji debugowania i jak sprawdzić stan programu. Cały kod, który zostanie wywołany, jest wywoływany z `module` funkcji pliku default.js. Nie dodano żadnych kontrolek i żadne zdarzenia nie są obsługiwane.

1. **Utwórz pustą aplikację w Sklepie Windows dla języka JavaScript.** Otwórz program Visual Studio. Na stronie głównej wybierz łącze **Nowy projekt** . W oknie dialogowym **Nowy projekt** wybierz pozycję **JavaScript** na liście **zainstalowane** , a następnie wybierz pozycję **Sklep Windows**. Na liście szablonów projektu wybierz **pustą aplikację**. Program Visual Studio tworzy nowe rozwiązanie i projekt i wyświetla default.htm plik w edytorze kodu.

    Zanotuj pliki skryptów, które są ładowane na stronie.

   - `base.js`Pliki i `ui.js` tworzą **bibliotekę systemu Windows dla języka JavaScript**. Biblioteka systemu Windows dla języka JavaScript to zestaw plików JavaScript i CSS, które ułatwiają tworzenie aplikacji ze sklepu Windows przy użyciu języka JavaScript. Używasz go razem z językiem HTML, CSS i środowisko wykonawcze systemu Windows, aby utworzyć aplikację.

   - Kod rozpocznie się w `default.js`  pliku.

2. **Otwórz plik źródłowy default.js.** W Eksplorator rozwiązań otwórz węzeł **js** i wybierz polecenie `default.js` .

3. **Zamień zawartość strony na przykładowy kod.** Usuń całą zawartość z `default.js` pliku. Skorzystaj z tego linku: [kod przykładowy nawigacji debugera (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md), a następnie skopiuj kod wymieniony w sekcji JavaScript do Schowka. (Wybierz z **powrotem** w przeglądarce lub Podgląd pomocy, aby powrócić do tej strony szybkiego startu). W edytorze programu Visual Studio Wklej kod do teraz puste `default.js` . Naciśnij **kombinację klawiszy Ctrl + S** , aby zapisać plik.

   Teraz można postępować zgodnie z przykładami w tym temacie.

## <a name="set-and-run-to-a-breakpoint-step-into-a-function-and-examine-program-data"></a><a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Ustaw i uruchom do punktu przerwania, Wkrocz do funkcji i Przeanalizuj dane programu
 Najczęstszym sposobem uruchomienia sesji debugowania jest wybranie opcji **Rozpocznij debugowanie** z menu **Debuguj** (klawiatura: F5). Aplikacja uruchamia się i kontynuuje wykonywanie do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręczne wstrzymanie wykonywania, wystąpił wyjątek lub aplikacja zostanie zakończona.

 Gdy wykonywanie jest zawieszone w debugerze, można wyświetlić wartość aktywnej zmiennej w poradach danych, zatrzymując mysz na zmiennej.

 Po wstrzymaniu wykonywania aplikacji (która jest również wywoływana w debugerze) można kontrolować sposób wykonywania pozostałej części kodu programu. Możesz kontynuować wiersz po wierszu, poruszając się z wywołania funkcji do samej funkcji lub można wykonać wywołaną funkcję w jednym kroku. Te procedury są nazywane przechodzeniem przez aplikację. Możesz również wznowić standardowe wykonywanie aplikacji, uruchamiając do następnego punktu przerwania ustawionego lub do wiersza, w którym znajduje się kursor. Sesja debugowania można zatrzymać w dowolnym momencie. Debuger został zaprojektowany w celu wykonania niezbędnych operacji czyszczenia i zakończenia wykonywania.

### <a name="example-1"></a><a name="BKMK_Example_1"></a> Przykład 1
 W tym przykładzie ustawisz punkt przerwania w treści `module` funkcji w `default.js` trakcie wywołania pierwszej z naszych instrukcji użytkownika. Następnie możesz przejść do funkcji, wyświetlić wartości zmiennych w etykietkach danych debugera, a następnie zatrzymać debugowanie.

1. **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `callTrack = "module function";` , która występuje bezpośrednio po wywołaniu metody `app.start()` . Wybierz wiersz w cieniowanym marginesie edytora kodu źródłowego (klawiatura: Umieść kursor w wierszu i wybierz klawisz **F9** ).

    ![Ustaw punkt przerwania w example1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Ikona punktu przerwania pojawia się na oprawie.

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

    Aplikacja rozpoczyna wykonywanie i wstrzymuje wykonywanie natychmiast przed instrukcją, w której ustawiono punkt przerwania. Ikona bieżącego wiersza w obszarze odstępu identyfikuje lokalizację i jest wyróżniona Bieżąca instrukcja.

    ![Uruchom do punktu przerwania](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Teraz masz kontrolę nad wykonywaniem aplikacji i sprawdzanie stanu programu w trakcie wykonywania instrukcji dotyczących programu.

3. **Wkrocz do funkcji.** W menu **debugowanie** wybierz pozycję **krok do** (klawiatura: **F11**).

    ![Wkrocz do wiersza kodu](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Należy zauważyć, że debuger przechodzi do następnego wiersza, który jest wywołaniem `example1` funkcji. Wybierz **krok** ponownie. Debuger przechodzi do pierwszej linii kodu `example1` funkcji. Podświetlony wiersz nie został wykonany, ale funkcja została załadowana na stosie wywołań, a pamięć dla zmiennych lokalnych została przypisana.

4. Po przekroczeniu wiersza kodu debuger wykonuje jedną z następujących czynności:

   - Jeśli następna instrukcja nie jest wywołaniem funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie wstrzymuje wykonywanie.

   - Jeśli instrukcja jest wywołaniem funkcji w rozwiązaniu, debuger przechodzi do pierwszego wiersza wywołanej funkcji, a następnie zawiesza wykonywanie.

     Kontynuuj, aby przejść do instrukcji do `example1` momentu, aż punkt wyjścia został osiągnięty. Debuger podświetla zamykający nawias klamrowy funkcji.

5. **Wyświetlanie wartości zmiennych w etykietkach danych.** Kontynuuj, aby przejść do instrukcji do `example1` momentu, aż punkt wyjścia został osiągnięty. Debuger podświetla zamykający nawias klamrowy funkcji. Po wstrzymaniu myszy na nazwie zmiennej Nazwa i wartość zmiennej są wyświetlane w etykietce danych.

    ![Wyświetlanie wartości zmiennych w etykietce danych](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **Dodaj czujkę dla zmiennej callTrack.** `callTrack`Ta zmienna jest używana w tym przewodniku szybki start do wyświetlania funkcji wywoływanych w przykładach. Aby ułatwić Wyświetlanie wartości zmiennej, należy dodać ją do okno wyrażeń kontrolnych. Wybierz nazwę zmiennej w edytorze, a następnie wybierz polecenie **Dodaj czujkę** z menu skrótów.

    ![Obejrzyj zmienną](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Można obejrzeć wiele zmiennych w oknie czujki. Wartości zmiennych obserwowanych, takich jak wartości w oknach etykietek danych, są aktualizowane po każdym wstrzymaniu wykonywania. Twoje obserwowane zmienne są zapisywane w sesjach debugowania.

7. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: **Shift + F5**). Spowoduje to zakończenie sesji debugowania.

## <a name="step-into-over-and-out-of-functions"></a><a name="BKMK_Step_into__over__and_out_of_functions"></a> Wkroczenie, przekroczenie i wyjście z funkcji
 W przeciwieństwie do przechodzenia do funkcji wywoływanej przez funkcję nadrzędną, przechodzenie przez funkcję wykonuje funkcję podrzędną, a następnie wstrzymuje wykonywanie w funkcji wywołującej jako wznowienie elementu nadrzędnego. Można przekroczyć funkcję w przypadku znajomości sposobu działania funkcji i upewnić się, że jej wykonanie nie będzie miało wpływu na badany problem.

 Przechodzenie przez wiersz kodu, który nie zawiera wywołania funkcji wykonuje wiersz tak samo jak w wierszu.

 Przechodzenie poza funkcję podrzędną kontynuuje wykonywanie funkcji, a następnie wstrzymuje wykonywanie po powrocie funkcji do funkcji wywołującej. Po ustaleniu, że pozostała część funkcji nie jest istotna, można wypróbować długą funkcję.

 Przechodzenie między funkcją i przechodzenie z niej wykonuje funkcję.

 ![Wkroczenie, przekroczenie i wyjście z metod](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a><a name="BKMK_Example_2"></a> Przykład 2
 W tym przykładzie przeprowadzisz do, przekroczenie i wyjście z funkcji.

1. **Wywołaj funkcję example2 w funkcji module.** Edytuj `module` funkcję i Zastąp wiersz następującym `var callTrack = "module function"` elementem `example2();` .

     ![Wywoływanie funkcji example2](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5). Debuger wstrzymuje wykonywanie w punkcie przerwania.

3. **Przekrocz wiersz kodu.** W menu **debugowanie** wybierz pozycję **krok nad** (klawiatura: F10). Debuger wykonuje `var callTrack = "module function"` instrukcję w taki sam sposób, jak w instrukcji.

4. **Wkrocz do example2 i example2_a.** Wybierz klawisz **F11** , aby przejść do `example2` funkcji. Kontynuuj, aby przejść do `example2` instrukcji do momentu uzyskania dostępu do wiersza `var x = example2_a();` . Ponownie przejdź do tego wiersza, aby przejść do punktu wejścia `example2_a` . Przejdź do kolejnych instrukcji, `example2_a` aż powrócisz do programu `example2` .

     ![Krok nad funkcją](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5. **Przekrocz funkcję.** Należy zauważyć, że następny wiersz w `example2` , `var y = example2_a();` jest zasadniczo taki sam jak w poprzednim wierszu. Możesz bezpiecznie przekroczyć ten wiersz. Wybierz klawisz **F10** , aby przejść od wznawiania `example2` do tego drugiego wywołania do `example2_a` . Należy zauważyć, że `callTrack` ciąg wskazuje, że `example2_a` funkcja została wykonana dwa razy.

6. **Wyjdź z funkcji.** Wybierz klawisz **F11** , aby przejść do `example2_b` funkcji. Należy pamiętać, że `example2_b` nie różni się od `example2_a` . Aby wykroczyć funkcję, wybierz pozycję **Wyjdź** z menu **debugowanie** (klawiatura: **Shift + F11**). Należy zauważyć, że `callTrack` zmienna wskazuje, że `example2_b` został wykonany i że debuger wrócił do punktu, w którym `example2` wznawia.

7. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: **Shift + F5**). Spowoduje to zakończenie sesji debugowania.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Ustaw punkt przerwania warunkowego, Uruchom do kursora i Wizualizuj zmienną
 Warunkowy punkt przerwania określa warunek, który powoduje zawieszenie wykonywania przez debuger. Warunek jest określany przez dowolne wyrażenie kodu, które może być oceniane jako true lub false. Na przykład można użyć warunkowego punktu przerwania do sprawdzenia stanu programu w często wywołanej funkcji tylko wtedy, gdy zmienna osiągnie określoną wartość.

 Uruchamianie do kursora przypomina Ustawianie punktu przerwania jednorazowego. Po wstrzymaniu wykonywania można wybrać wiersz w źródle i wznowić wykonywanie do momentu osiągnięcia wybranego wiersza. Na przykład można przechodzenie przez pętlę w funkcji i określić, że kod w pętli działa poprawnie. Zamiast przechodzić przez każdą iterację pętli, można uruchomić kursor, który jest umieszczony po wykonaniu pętli.

 Czasami trudno jest wyświetlić wartość zmiennej w wierszu etykietki danych lub innego okna danych. Debuger może wyświetlać ciągi, HTML i XML w wizualizatorze tekstu, który przedstawia sformatowany widok wartości w przewijanym oknie.

### <a name="example-3"></a><a name="BKMK_Example_3"></a> Przykład 3
 W tym przykładzie ustawisz warunkowy punkt przerwania do przerwania w określonej iteracji pętli, a następnie uruchomisz kursor do kursora, który jest umieszczony po pętli. Możesz również wyświetlić wartość zmiennej w wizualizatorze tekstu.

1. **Wywołaj funkcję example3 w funkcji module.** Edytuj `module` funkcję i Zastąp wiersz poniższym wierszem `var callTrack = "module function";` `example3();` .

     ![Example3 wywołań](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: **F5**). Debuger wstrzymuje wykonywanie w punkcie przerwania w `module` funkcji.

3. **Wkrocz do funkcji example3.** Wybierz pozycję **Wkrocz** do w menu **debugowanie** (klawiatura: **F11**), aby przejść do punktu wejścia `example3` funkcji. Kontynuuj przechodzenie do funkcji do momentu iteracji jednej lub dwóch pętli `for` bloku. Pamiętaj, że zajmiesz dużo czasu, aby przekroczyć wszystkie iteracje 1000.

4. **Ustaw punkt przerwania warunkowego.** W lewym marginesie okna kod kliknij prawym przyciskiem myszy wiersz, `s += i.toString() + "\n";` a następnie wybierz pozycję **warunek** w menu skrótów.

     Zaznacz pole wyboru **warunek** , a następnie wpisz `i == 500;` w polu tekstowym. Wybierz opcję **jest true** , a następnie wybierz **przycisk OK**. Punkt przerwania umożliwia sprawdzenie wartości w iteracji 500th `for` pętli. Możesz określić ikonę punktu przerwania warunkowego przez jego biały krzyżyk.

     ![Ikona punktu przerwania blokada](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5. **Uruchom do punktu przerwania.** W menu **debugowanie** wybierz polecenie **Kontynuuj** (klawiatura: **F5**). Zatrzymaj na, `i` Aby potwierdzić, że bieżąca wartość `i` to 500. Należy również zauważyć, że zmienna `s` jest reprezentowana jako pojedynczy wiersz i jest znacznie dłuższa niż okno etykietki danych.

6. **Wizualizuj zmienną ciągu.** Kliknij ikonę lupy w podanej etykietce na stronie `s` .

     Zostanie wyświetlone okno wizualizator tekstu, a wartość ciągu jest prezentowana jako ciąg wielowierszowy.

     ![Wizualizator tekstu debugowania](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7. **Uruchom do kursora.** Zaznacz wiersz `callTrack += "->example3";` , a następnie wybierz polecenie **Uruchom do kursora** w menu skrótów (klawiatura: **CTRL + F10**). Debuger wykonuje iteracje pętli, a następnie wstrzymuje wykonywanie w wierszu.

8. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: **Shift + F5**). Spowoduje to zakończenie sesji debugowania.

### <a name="use-run-to-cursor-to-return-to-your-code-and-delete-a-breakpoint"></a><a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Użyj kursor do kursora, aby powrócić do kodu i usunąć punkt przerwania
 Uruchomienie do kursora może być bardzo przydatne, gdy użytkownik przeprowadził się do kodu biblioteki od firmy Microsoft lub innej firmy. Przechodzenie przez kod biblioteki może być niesformatowane, często może to zająć dużo czasu. Zazwyczaj użytkownik jest znacznie bardziej interesujący w swoim własnym kodzie. W tym ćwiczeniu pokazano, jak to zrobić.

1. **Ustaw punkt przerwania w aplikacji. Rozpocznij wywołanie.** W `module` funkcji Ustaw punkt przerwania w wierszu `app.start()`

2. **Uruchom punkt przerwania i przejdź do funkcji biblioteki.**

     Po przekroczeniu kroku `app.start()` Edytor wyświetla kod w `base.js` . Wkrocz do kilku wierszy.

3. **Przekrocz i wyjdź z funkcji.** Gdy przejdziesz nad (**F10**) i wyjdź z kodu (**Shift + F11**) w `base.js` , możesz przejść do wniosku, który bada złożoność i długość funkcji startowej nie jest tym, co chcesz zrobić.

4. **Ustaw kursor na swój kod i uruchom go.** Przełącz się z powrotem do `default.js` pliku w edytorze kodu. Wybierz pierwszy wiersz kodu po `app.start()` (nie można uruchomić do komentarza lub pustego wiersza). Wybierz polecenie **Uruchom do kursora** z menu skrótów. Debuger kontynuuje wykonywanie funkcji App. Start i wstrzymuje wykonywanie w punkcie przerwania.

## <a name="view-variable-data-in-the-locals-window"></a><a name="BKMK_View_variable_data_in_the_Locals_window"></a> Wyświetlanie danych zmiennej w oknie zmiennych lokalnych
 Okna lokalne są widokiem drzewa parametrów i zmiennych w łańcuchu zakresu obecnie wykonywanej funkcji.

### <a name="view-variable-data-and-the-prototype-chain-of-an-object"></a><a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Wyświetlanie danych zmiennych i łańcucha prototypów obiektu

1. **Dodaj obiekt Array funkcji modułu.** Edytuj `module` funkcję i Zastąp wiersz następujący: `var callTrack = "module function"``var myArray = new Array(1, 2, 3);`

     ![Definicja klasy webarray](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: **F5**). Debuger wstrzymuje wykonywanie w punkcie przerwania. Przejdź do wiersza.

3. **Otwórz okno zmienne lokalne.** W menu **Debuguj** wskaż pozycję **Windows**, a następnie wybierz pozycję **Ustawienia regionalne**. (Klawiatura: Alt + 4).

4. **Badanie zmiennych lokalnych w funkcji modułu** W oknach lokalnych są wyświetlane zmienne aktualnie wykonywanej funkcji ( `module` funkcji) jako węzły najwyższego poziomu drzewa. Gdy wprowadzasz funkcję, język JavaScript tworzy wszystkie zmienne i daje im wartość `undefined` . Funkcje, które są zdefiniowane w funkcji, mają swój tekst jako wartość.

     ![okno zmiennych lokalnych](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5. **Przejdź przez definicje callTrack i webarray.** Znajdź zmienne callTrack i Array w oknie zmiennych lokalnych. Przekrocz (**F10**) dwie definicje i zwróć uwagę na to, że pola **wartości** i **typu** są zmieniane. Okno zmienne lokalne wyróżnia wartości zmiennych, które uległy zmianie od czasu ostatniej przerwy.

6. **Badanie obiektu Webarray** Rozwiń `myArray` zmienną. Każdy element tablicy jest wymieniony w węźle **[Prototype]** , który zawiera hierarchię dziedziczenia `Array` obiektu. Rozwiń ten węzeł.

     ![Łańcuch prototypów w oknie zmiennych lokalnych](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    - Węzeł **metody** wyświetla wszystkie metody `Array` obiektu.

    - Węzeł **[Prototype]** zawiera prototyp `Object` obiektu, z którego `Array` pochodzi. węzły **[Prototype]** mogą być cykliczne. Każdy obiekt nadrzędny w hierarchii obiektów jest opisany w węźle **[Prototype]** jego elementu podrzędnego.

7. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: Shift + F5). Spowoduje to zakończenie sesji debugowania.

## <a name="examine-scope-chain-data"></a><a name="BKMK_Examine_scope_chain_data"></a> Sprawdzanie danych łańcucha zakresu
 *Łańcuch zakresu* funkcji zawiera wszystkie zmienne, które są aktywne i dostępne przez funkcję. Zmienne globalne są częścią łańcucha zakresu, podobnie jak wszystkie obiekty (w tym funkcje) zdefiniowane w funkcji, która definiuje aktualnie wykonywaną funkcję. Na przykład `callTrack` zmienna zdefiniowana w `module` funkcji `default.js` jest osiągalna przez każdą funkcję, która jest zdefiniowana w `module` funkcji. Każdy zakres jest wyszczególniony oddzielnie w oknie zmiennych lokalnych.

- Zmienne obecnie wykonywanej funkcji są wyświetlane w górnej części okna.

- Zmienne każdego zakresu funkcji w łańcuchu zakresu są wymienione w węźle **[Scope]** dla funkcji. Funkcje zakresu są wyświetlane według ich kolejności w łańcuchu, od funkcji, która definiuje bieżącą funkcję do zewnętrznej funkcji łańcucha.

- Węzeł **[Globals]** zawiera listę obiektów globalnych, które są zdefiniowane poza żadną funkcją.

  Łańcuchy zakresów mogą być mylące i najlepiej zilustrowane na przykład. W poniższym przykładzie można zobaczyć, jak `module` Funkcja tworzy własny zakres i jak można utworzyć inny poziom zakresu przez utworzenie zamknięcia.

### <a name="example-4"></a><a name="BKMK_Example_4"></a> Przykład 4

1. **Wywołaj funkcję example4 z funkcji modułu.** Edytuj `module` funkcję i Zastąp wiersz następujący `var callTrack = "module function"` `example4()` :

     ![Example4 wywołań](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: **F5**). Debuger wstrzymuje wykonywanie w punkcie przerwania.

3. **Otwórz okno zmienne lokalne.** W razie potrzeby w menu **debugowanie** wskaż pozycję **Windows**, a następnie wybierz pozycję **Ustawienia regionalne**. (Klawiatura: **Alt + 4**). Należy zauważyć, że okno zawiera wszystkie zmienne i funkcje w `module` funkcji, a także węzeł **[Globals]** .

4. **Przeanalizuj zmienne globalne.** Rozwiń węzeł **[Globals]** . Obiekty i zmienne w szablonie globalnym zostały ustawione przez bibliotekę systemu Windows dla języka JavaScript. Do zakresu globalnego można dodać własne zmienne.

5. **Wkrocz do example4 i Przeanalizuj zmienne lokalne i zakresowe** Wkrocz do (klawiatura: **F11**) `example4` funkcji. Ponieważ `example4` jest zdefiniowany w `module` funkcji, `module` Funkcja zostanie do zakresu nadrzędnego. `example4` może wywoływać dowolne funkcje w `module` funkcji i uzyskiwać dostęp do jej zmiennych. Rozwiń węzeł **[Scope]** w oknie zmiennych lokalnych i zwróć uwagę, że zawiera on te same i zmienne `module` funkcji.

     ![Zakresy metody example4](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6. **Wkrocz do example4_a i przeanalizować swoje zmienne lokalne i zakresowe** Kontynuuj krok po kroku `example4` i w wywołaniu metody `example4_a` . Należy zauważyć, że zmienne lokalne są teraz z `example4_a` i że węzeł **[Scope]** nadal przechowuje zmienne `module` funkcji. Mimo że zmienne `example4` są aktywne, nie mogą być osiągane przez `example4_a` i nie są już częścią łańcucha zakresów.

7. **Wkrocz do multiplyByA i Przeanalizuj zmienne lokalne i zakresowe** Krok po kroku `example4_a` i w wierszu `var x = multiplyByA(b);` .

     Zmienna funkcji `multiplyByA` została ustawiona na `multiplyClosure` funkcję, która jest *zamknięciem*. `multiplyClosure` definiuje i zwraca wewnętrzną funkcję, `multiplyXby` , i przechwytuje (zamyka) jej parametru i zmiennej. W zamknięciu zwrócona funkcja wewnętrzna ma dostęp do danych funkcji zewnętrznej i w związku z tym tworzy własny poziom zakresu.

     Gdy przejdziesz `var x = multiplyByA(b);` do, przenosisz się do `return a * b;` wiersza w `multiplyXby` funkcji wewnętrznej.

8. W oknie zmiennych lokalnych tylko parametr `b` jest wymieniony jako zmienna lokalna w `multiplyXby` , ale został dodany nowy poziom **[Scope]** . Rozszerzając ten węzeł, zobaczysz, że zawiera on parametry, funkcje i zmienne, w `multiplyClosure` tym `a` zmienna wywołana w pierwszym wierszu `multiplyXby` . Szybkie sprawdzenie drugiego węzła **[Scope]** ujawnia zmienne funkcji modułu, które `multiplyXby` uzyskują dostęp do następnego wiersza.

9. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: **Shift + F5**). Spowoduje to zakończenie sesji debugowania.

## <a name="navigate-to-code-by-using-the-call-stack-window"></a><a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Przejdź do kodu przy użyciu okna stosu wywołań
 Stos wywołań to struktura danych zawierająca informacje o funkcjach, które są wykonywane w bieżącym wątku aplikacji. Po trafieniu punktu przerwania w oknie stos wywołań zostanie wyświetlona lista wszystkich funkcji, które są aktywne na stosie. Obecnie wykonywana funkcja znajduje się w górnej części listy okna stosu wywołań. Funkcja inicjująca wątek znajduje się w dolnej części listy. Funkcja między wyświetlaniem ścieżki wywołania od funkcji inicjującej do bieżącej funkcji.

 Oprócz wyświetlania ścieżki wywołania do aktualnie wykonywanej funkcji, można użyć okna stosu wywołań, aby przejść do kodu w edytorze kodu. Ta funkcja może być cenna, gdy pracujesz z wieloma plikami i chcesz szybko przejść do określonej funkcji.

### <a name="example-5"></a><a name="BKMK_Example_5"></a> Przykład 5
 W tym przykładzie należy przejść do ścieżki wywołania zawierającej pięć funkcji zdefiniowanych przez użytkownika.

1. **Wywołaj funkcję example5 w funkcji module.** Edytuj `module` funkcję i Zastąp wiersz poniższym wierszem `var callTrack = "module function";` `example5();` .

     ![Example5 wywołań](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2. **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: **F5**). Debuger wstrzymuje wykonywanie w punkcie przerwania w funkcji modułu.

3. **Otwórz okno stosu wywołań.** W menu **debugowanie** wybierz pozycję **Windows**, a następnie wybierz polecenie **stos wywołań** (klawiatura: Alt + 7). Należy zauważyć, że okno stos wywołań zawiera dwie funkcje:

    - **Kod globalny** jest punktem wejścia `module` funkcji w dolnej części stosu wywołań.

    - **Funkcja anonimowa** pokazuje wiersz funkcji, w `module` której wykonywanie zostało zawieszone. Jest to Góra stosu wywołań.

4. **Wkrocz do funkcji, aby osiągnąć funkcję example5_d.** Wybierz pozycję **Wkrocz** w menu **debugowanie** (klawiatura: **F11**), aby wykonać wywołania w ścieżce wywołania do momentu osiągnięcia punktu wejścia funkcji example5_d. Należy pamiętać, że za każdym razem, gdy funkcja wywołuje funkcję, numer wiersza funkcji wywołującej jest zapisywany i wywoływana funkcja jest umieszczana w górnej części stosu. Numer wiersza funkcji wywołującej to punkt, w którym funkcja wywołująca zawiesiła wykonywanie. Żółta strzałka wskazuje na aktualnie wykonywaną funkcję.

     ![Okno stosu wywołań](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5. **Użyj okna stosu wywołań, aby przejść do kodu example5_a i ustawić punkt przerwania.** W oknie stos wywołań wybierz `example5_a` element listy, a następnie wybierz polecenie **Przejdź do źródła** w menu skrótów. Edytor kodu ustawia swój kursor w wierszu powrotu funkcji. Ustaw punkt przerwania w tym wierszu. Należy zauważyć, że bieżący wiersz wykonania nie został zmieniony. Przeniesiono tylko kursor edytora.

6. **Wkrocz do funkcji, a następnie Uruchom do punktu przerwania.** Kontynuuj krokowe wykonywanie kroków `example5_d` . Należy pamiętać, że po powrocie z funkcji jest ona pobierana z stosu wywołań. Naciśnij klawisz **F5** , aby kontynuować wykonywanie programu. Zatrzymano w punkcie przerwania utworzonym w poprzednim kroku.

7. **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: **Shift + F5**). Spowoduje to zakończenie sesji debugowania.

## <a name="see-also"></a>Zobacz też
 [Rozpocznij sesję debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [Szybki Start: pasek nawigacyjny debugera (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Szybki Start: debugowanie debugowania HTML i CSS](../debugger/quickstart-debug-html-and-css.md) [, wstrzymywanie, wznawianie i zdarzenia w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
