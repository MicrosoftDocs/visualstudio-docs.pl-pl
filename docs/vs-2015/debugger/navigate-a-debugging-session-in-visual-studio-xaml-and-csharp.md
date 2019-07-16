---
title: Nawigowanie po sesji debugowania (Xaml i C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8d24f01f7882e8c760918119a03a1c489c727
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156890"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Nawigowanie po sesji debugowania w programie Visual Studio (Xaml i C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik Szybki start pokazuje, jak nawigować po sesji debugowania programu Visual Studio i jak wyświetlić i zmienić stan programu w sesji.

 Ten przewodnik Szybki start jest dla deweloperów, którzy są nowe debugowanie przy użyciu programu Visual Studio, a sesja debugowania dla deweloperów, którzy chcą dowiedzieć się więcej o przechodząc w programie Visual Studio. Techniki debugowania sam nie jest nauka. Metody w przykładowym kodzie są przeznaczone tylko do zademonstrowania debugowania procedur opisanych w tym temacie. Metody nie stosować najlepsze rozwiązania projekt aplikacji lub funkcji. W rzeczywistości zostanie szybko odkryjesz, że metody i aplikacji, nie wykonuj ilości niczego na wszystkich.

 Części tego przewodnika Szybki start zostały zaprojektowane jako jako niezależny, jak to możliwe, dzięki czemu można pominąć dowolną sekcję, która zawiera informacje, które już znasz z. Ponadto nie należy utworzyć przykładowej aplikacji; Jednak firma Microsoft zaleca, aby go i wprowadziliśmy proces tak proste, jak to możliwe.

 **Debuger skróty klawiaturowe.** Visual Studio debugger nawigacji jest zoptymalizowany, myszy i klawiatury. Wiele z tych kroków w tym temacie obejmują klawiszem skrótu lub klawisza skrótu w nawiasach uwagi. Na przykład (klawiatury: F5) wskazuje, że wpisanie klawisza F5 rozpoczyna się lub kontynuuje wykonywanie debugera.

## <a name="in-this-topic"></a>W tym temacie:
 Możesz dowiedzieć się jak:

- [Tworzenie przykładowej aplikacji](#BKMK_CreateTheApplication)

- [Ustaw i uruchom do punktu przerwania, krok po kroku do metody i zbadaj dane do programu](#BKMK_StepInto)

- [Krok do, przez niego lub poza metody](#BKMK_StepIntoOverOut)

- [Ustawianie warunkowego punktu przerwania, uruchom do kursora i wizualizować zmienną](#BKMK_ConditionCursorVisualize)

- [Edytuj i Kontynuuj, odzyskanie wyjątek](#BKMK_EditContinueRecoverExceptions)

## <a name="BKMK_CreateTheApplication"></a> Tworzenie przykładowej aplikacji
 Debugowanie jest dotyczące kodu, więc Przykładowa aplikacja używa strukturę aplikacji Windows Store, tylko w celu utworzenia pliku źródłowego, w którym widać, jak działa nawigowanie sesji debugowania i jak sprawdzić i zmienić stan programu. Cały kod, który będzie wywoływał jest wywoływana z konstruktora strona główna; Brak kontrolek są dodawane, a żadne zdarzenia nie są obsługiwane.

 **Utwórz domyślną aplikację w języku C# Windows Store.** Otwórz program Visual Studio. Na stronie głównej wybierz **nowy projekt** łącza. W oknie dialogowym Nowy projekt, wybierz **Visual C#** w **zainstalowane** listy, a następnie wybierz **Windows Store**. Na liście szablonów projektu wybierz **aplikacji**. Visual Studio tworzy nowe rozwiązanie i projekt i wyświetla MainPage.xaml projektanta i edytora kodu XAML.

 **Otwórz plik źródłowy MainPage.xaml.cs.** Kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XAML, a następnie wybierz **Wyświetl kod**. Zostanie wyświetlony plik CodeBehind MainPage.xaml.cs. Należy pamiętać, że tylko jedna metoda `MainPage()` konstruktora, znajduje się w pliku.

 **Zamień Konstruktor MainPage z przykładowym kodem.** DELETE, metoda MainPage(). Skorzystaj z tego linku: [Przykładowy kod nawigacji debugera (Xaml i C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md), a następnie skopiuj kod przedstawiony w C# sekcji do Schowka. (Wybierz **ponownie** w przeglądarce lub podglądu pomocy, aby powrócić do tej strony szybki start.) W edytorze programu Visual Studio, Wklej kod w `partial class MainPage` bloku. Wybierz kombinację klawiszy CTRL + s, aby zapisać plik.

 Teraz można wykonać wraz z przykładami w tym temacie.

## <a name="BKMK_StepInto"></a> Ustaw i uruchom do punktu przerwania, krok po kroku do metody i zbadaj dane do programu
 Najbardziej popularny sposób, że możesz rozpocząć sesję debugowania jest wybranie **Rozpocznij debugowanie** z **debugowania** menu (klawiatury: F5). Wykonanie rozpoczyna się i jest powtarzany do momentu punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi wyjątek, lub kończy się w aplikacji.

 Zawieszenia wykonania w debugerze, ustawiając kursor myszy nad zmienną można wyświetlić wartość zmiennej active w oknie z poradami danych. Można również otworzyć okna zmiennych lokalnych i automatycznych, aby wyświetlić listę aktywnych zmienne oraz ich bieżących wartości. Dodanie co najmniej jednej zmiennej, do umożliwia okno czujki, skoncentrować się na wartości zmiennych, jak aplikacja kontynuuje wykonywanie.

 Po wstrzymaniu wykonywania aplikacji (zwaną również przerwanie w debugerze), możesz kontrolować sposób, który jest wykonywany w pozostałej części kodu programu. Przenoszenie z wywołania metody do metody, można kontynuować wiersz po wierszu lub można wykonać metody o nazwie w jednym kroku. Te procedury są nazywane krokowe wykonywanie aplikacji. Można również wznowić standardowa wykonywanie aplikacji, systemem do następnego punktu przerwania, które zostały ustawione lub do wiersza, w której umieszczony kursor. Można zatrzymać sesji debugowania w dowolnym momencie. Debuger jest przeznaczony do wykonania niezbędnych operacji czyszczenia i zakończyć wykonywanie.

### <a name="example-1"></a>Przykład 1
 W tym przykładzie należy ustawić punkt przerwania w Konstruktorze MainPage w pliku MainPage.xaml.cs, wkroczenia do pierwszej metody, wyświetlanie wartości zmiennych i następnie zatrzymasz debugowanie.

 **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `methodTrack = "Main Page";` w Konstruktorze MainPage. Wybierz wiersz w zacieniowane odstępu Edytor kodu źródłowego (klawiatury: Umieść kursor w wierszu i wybierz klawisz F9).

 ![Wejdź do](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Ikona punktu przerwania pojawia się na marginesie.

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).

 Aplikacja rozpoczyna wykonywanie i zawiesza wykonywanie tuż przed instrukcji, w którym można ustawić punkt przerwania. Bieżąca ikona wierszu na marginesie identyfikuje Twojej lokalizacji i bieżącej instrukcji jest wyróżniona.

 ![Ustaw punkt przerwania](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Teraz masz kontrolę nad wykonywanie aplikacji i sprawdzić stan programu podczas wykonywania kroków za pomocą instrukcji programu.

 **Wejdź do metody.** Na **debugowania** menu, wybierz **Step Into** (klawiatury: F11).

 ![Bieżący wiersz](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Należy pamiętać, że debuger przechodzi do następnego wiersza, który jest wywołanie metody przykład1. Ponownie wybierz Step Into. Debuger przenosi przykład1 metody punktu wejścia. Oznacza to, że metoda została załadowana w stosie wywołań i przydzielonych pamięci dla zmiennych lokalnych.

 Gdy wchodzisz do wiersza kodu debuger wykonuje jedną z następujących czynności:

- Następna instrukcja nie jest wywołanie funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie zawiesza wykonywanie.

- Jeśli instrukcja jest wywołaniem funkcji w rozwiązaniu, debuger przechodzi do punktu wejścia wywoływanej funkcji, a następnie zawieszenie wykonywania.

  Kontynuuj wkraczać do instrukcji przykład1, aż do osiągnięcia punktu wyjścia. Do usuwania błędów podkreśli zamykający nawias klamrowy metody.

  **Sprawdź wartości zmiennych w poradach dotyczących danych.** Po umieszczeniu wskaźnika myszy nazwę zmiennej, nazwę, wartość i typ zmiennej jest wyświetlany w oknie z poradami danych.

  ![Porada danych debugera](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Umieść kursor myszy nad zmienną `a`. Należy pamiętać, wpisz nazwę, wartość i dane. Umieść kursor myszy nad zmienną `methodTrack`. Ponownie należy pamiętać, wpisz nazwę, wartość i dane.

  **Sprawdź wartości zmiennej w oknie zmienne lokalne.** Na **debugowania** menu wskaż **Windows**, a następnie wybierz **lokalne**. (Klawiatura: ALT+ 4).

  ![Okno zmiennych lokalnych](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Zmienne lokalne systemu windows jest widok drzewa, parametrów i zmiennych w funkcji. Węzły podrzędne samego obiektu są właściwości zmiennej obiektu. `this` Zmienna jest ukryty parametr w każdej metody obiektu, który reprezentuje sam obiekt. W tym przypadku reprezentuje klasy MainPage. Ponieważ `methodTrack` jest elementem członkowskim typu klasy, jego wartość i dane MainPage są wymienione w wierszu poniżej `this`. Rozwiń `this` węzeł, aby wyświetlić `methodTrack` informacji.

  **Dodaj wyrażenie kontrolne dla zmiennej methodTrack.** `methodWatch` Zmienna jest używana w tym przewodniku Szybki start, aby pokazać metody o nazwie w przykładach. Aby ułatwić wyświetlić wartość zmiennej, należy go dodać do okna czujki. Kliknij prawym przyciskiem myszy nazwę zmiennej w oknie zmienne lokalne, a następnie wybierz **Dodaj czujkę**.

  ![W oknie czujki](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Możesz obejrzeć wiele zmiennych w oknie czujki. Wartości zmiennych obserwowana, takie jak wartości zmiennych lokalnych i okien Porada danych, są aktualizowane, zawsze wtedy, gdy wykonanie programu jest zawieszone. Zmienne można również dodać do okna czujki, z poziomu edytora kodu. Wybierz zmienną, aby obejrzeć, kliknij prawym przyciskiem myszy, a następnie wybierz **Dodaj czujkę**.

## <a name="BKMK_StepIntoOverOut"></a> Krok do, przez niego lub poza metody
 W przeciwieństwie do przechodzenie krok po kroku, do metody wywoływane przez metody nadrzędnego, pominięcie metody wykonuje metodę podrzędnej, a następnie zawieszenie wykonywania w przypadku wywoływania metody jako element nadrzędny wznawia działanie. Jeśli znasz sposób metoda działa i pewności, czy jego wykonanie nie ma wpływu na problem, który badania, może przekraczanie metody.

 Pominięcie wiersza kodu, który nie zawiera wywołania metody wykonuje wiersza, podobnie jak przechodzenie do wiersza.

 Przechodzenie krok po kroku, poza metodę podrzędnej kontynuuje wykonywanie metody, a następnie zawiesza wykonywanie po powrocie z metody do wywołania metody. Może być wychodzenia z funkcję długo, gdy już wiesz, pozostała część funkcji nie jest znaczący.

 Pominięcie i przechodzenie krok po kroku z funkcji wykonanie funkcji.

 ![Krok do, przez niego lub poza metody](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Przykład 2
 W tym przykładzie kroku do, przez niego lub poza metody.

 **Wywołaj metodę przykład2 w Konstruktorze MainPage.** Zmodyfikuj konstruktora MainPage i Zastąp następujący wiersz `methodTrack = String.Empty;` z `Example2();`.

 ![Wywołaj metodę przykład2 z metody pokaz](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger zawiesza wykonywanie w punkcie przerwania.

 **Przekrocz nad wiersz kodu.** Na **debugowania** menu, wybierz **Step Over** (klawiatury: F10). Debuger wykonuje `methodTrack = "MainPage";` instrukcji w taki sam sposób jak przechodzenie do instrukcji.

 **Krok po kroku przykład2 i Example2_A.** Wciśnij klawisz F11, aby można było wkroczyć do metody przykład 2. Wejdź do instrukcji przykład2, aż do wiersza w dalszym ciągu `int x = Example2_A();`. Ponownie krok po kroku do tego wiersza, aby przejść do punktu wejścia Example2_A. Kontynuuj wkraczać do każdej instrukcji Example2_A, aż powrócisz do przykład2.

 ![Przykład2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Przekrocz nad funkcją.** Należy zauważyć, że następnego wiersza w przykład2, `int y = Example2_A();` jest zasadniczo taki sam jak w poprzednim wierszu. Możesz bezpiecznie wejść na tym wierszu. Wybierz klawisz F10, aby przenieść z wznowienie przykład2 to drugie wywołanie Example2_A. Wybierz F10, aby przejść przez tę metodę. Należy pamiętać, że `methodTrack` ciąg wskazuje metodę Example2_A wykonano dwa razy. Można również zauważyć, że debuger natychmiast przechodzi do następnego wiersza. Wstrzymuje wykonywanie w wznawia przykład2 punktu.

 **Wyjdź z funkcji.** Wciśnij klawisz F11, aby można było wkroczyć do metody Example2_B. Należy pamiętać, że nie jest bardzo różnią się od Example2_A Example2_B. Aby wkraczać poza metodę, wybierz **Step Out** na **debugowania** menu (klawiatury: Shift + F11). Należy pamiętać, że `methodTrack` zmiennej wskazuje wykonano Example2_B i zwróciła w punkcie, gdzie wznawia przykład2 debugera.

 **Zatrzymaj debugowanie.** W menu debugowanie, wybierz polecenie Zatrzymaj debugowanie (klawiatury: Shift+F5). Kończy sesję debugowania.

## <a name="BKMK_ConditionCursorVisualize"></a> Ustawianie warunkowego punktu przerwania, uruchom do kursora i wizualizować zmienną
 Warunkowego punktu przerwania określa warunek, który powoduje, że debuger w celu wstrzymania wykonywania. Warunek jest określona przez dowolne wyrażenie kodu, które mogą być obliczane jako wartość true lub false. Może na przykład użyć warunkowego punktu przerwania, aby sprawdzić stan programu w przypadku często wywołanej metody tylko wtedy, gdy zmienna osiągnie określoną wartość.

 Wykonywanie do kursora działa jak ustawienie jednorazowe punktu przerwania. Gdy wykonanie programu jest zawieszone, można zaznacz wiersz w źródle i wznowić wykonywanie aż do osiągnięcia wybrany wiersz. Na przykład możesz może być krokowe wykonywanie pętli w metodzie i określić, że kod w pętli działa prawidłowo. Zamiast krokowe wykonywanie każdej iteracji pętli, można uruchomić do kursora, który jest umieszczony po wykonaniu pętli.

 Czasami trudno jest wyświetlanie wartości zmiennej w wierszu danych porada lub oknie zmiennej. Debuger może wyświetlać ciągów, HTML i Xml w Wizualizator tekstu, który przedstawia widok sformatowanych wartości w oknie przewijany.

### <a name="example-3"></a>Przykład 3
 W tym przykładzie można ustawić warunkowego punktu przerwania Przerwij przy określonej iteracji pętli, a następnie uruchom do kursora, który jest umieszczony po pętli. Możesz również wyświetlić wartość zmiennej w Wizualizator tekstu.

 **Wywołaj metodę przykład3 w Konstruktorze MainPage.** Zmodyfikuj konstruktora MainPage i Zastąp następujący wiersz `methodTrack = String.Empty;` z linią `Example3();`.

 ![Wywołaj przykład3 z metody pokaz](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger zawiesza wykonywanie w punkcie przerwania w metodzie MainPage.

 **Metoda przykład3 krok po kroku.** Wybierz **Step Into** na **debugowania** menu (klawiatury: F11), aby przejść do punktu wejścia metody przykład3. Kontynuuj przechodzenie do metody, dopóki nie mają postanowiliśmy jednego lub dwóch pętli `for` bloku. Należy pamiętać, że może upłynąć możesz dużo czasu, aby przejść przez wszystkie iteracje 1000.

 **Ustaw warunkowego punktu przerwania.** W lewym marginesie na oprawę okna kodu, kliknij prawym przyciskiem myszy wiersz `x += i;` , a następnie wybierz **warunek**. Wybierz **warunek** pole wyboru, a następnie wpisz `i == 500;` w polu tekstowym. Wybierz **ma wartość true** opcji, a następnie wybierz **OK**. Punkt przerwania pozwala sprawdzić wartość iteracji 500th `for` pętli.

 ![Warunek punktu przerwania, okno dialogowe](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Ikona warunkowego punktu przerwania są identyfikowane przez jego między białe.

 ![Warunkowego punktu przerwania](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Uruchom do punktu przerwania.** W menu debugowanie, wybierz opcję Kontynuuj (klawiatury: F5). W oknie zmienne lokalne, upewnij się, że bieżąca wartość `i` wynosi 500. Należy pamiętać, że zmienna `s` jest reprezentowany jako jeden wiersz i jest znacznie dłuższy niż okno.

 **Zmienna string wizualizacji.** Kliknij ikonę lupy w **wartość** kolumny `s`.

 Zostanie wyświetlone okno Wizualizator tekstu i wartość ciągu jest przedstawiany jako ciąg wielowierszowy.

 **Uruchom do kursora.** Kliknij prawym przyciskiem myszy wiersz `methodTrack += "->Example3";` , a następnie wybierz **Uruchom do kursora** (klawiatury: Przenieś kursor do linii; CTRL + F10). Debuger kończy iteracji pętli, a następnie zawiesza wykonywanie w wierszu.

 **Zatrzymaj debugowanie.** W menu debugowanie, wybierz polecenie Zatrzymaj debugowanie (klawiatury: Shift+F5). Kończy sesję debugowania.

## <a name="BKMK_EditContinueRecoverExceptions"></a> Edytuj i Kontynuuj, odzyskanie wyjątek
 W niektórych sytuacjach po wejściu do kodu w debugerze programu Visual Studio masz możliwość zmiany wartości zmiennych i nawet warunki logiczne instrukcji. Ta funkcja nosi nazwę Edytuj i Kontynuuj.

 Edytuj i Kontynuuj może być szczególnie przydatne po przerwaniu wyjątek. Nie trzeba zatrzymać i ponownie uruchomić debugowanie długich i zaangażowane procedury w celu uniknięcia wyjątek, możesz mogą "Odwiń" wyjątku, który można przenieść wykonania do punktu, bezpośrednio przed wykonaniem Wystąpił wyjątek, a następnie zmień naruszającym zmiennej lub instrukcji i Przejdź do bieżącej sesji debugowania w stanie, który nie zgłasza wyjątku.

 Używanie funkcji Edytuj i Kontynuuj w wielu różnych sytuacjach można, szczególnych warunków, które nie obsługuje opcji Edytuj i Kontynuuj trudno jest określić, ponieważ warunki są zależne od języka programowania, bieżący stan stos programu i możliwość debugera można zmienić stanu bez uszkodzenia procesu. Najlepszym sposobem ustalenia, czy jest obsługiwana zmiana edycji jest po prostu spróbuj; Debuger poinformuje Cię natychmiast, jeśli zmiany nie jest obsługiwane.

### <a name="example-4"></a>Przykład 4
 W tym przykładzie, można uruchomić debugera, aby wyjątek, przewiń do tyłu wyjątek, poprawić logikę metody, a następnie zmień wartość zmiennej, tak, aby można kontynuować wykonywania metody.

 **Wywołaj metodę przykład4 w Konstruktorze MainPage.** Zmodyfikuj konstruktora MainPage() i Zastąp następujący wiersz `methodTrack = String.Empty;` z linią `Example4();`.

 ![Wywołaj przykład4 z metody pokaz](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Uruchom do wyjątku.** Rozpocznij sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Naciśnij klawisz F5, aby wznowić wykonywanie. Debuger zawiesza wykonywanie w wyjątek w metodzie przykład4 i wyświetla okno dialogowe wyjątku.

 ![Okno dialogowe wyjątku](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Zmień logiki programu.** Jest oczywiste, że błąd znajduje się w `if` warunek: wartość `x` powinna zostać zmieniona po `x` jest równa 0; nie wtedy, gdy `x` nie jest równa zero. Wybierz **Przerwij** naprawić logiki metody. Podczas próby Edytuj wiersz, pojawi się inne okno dialogowe.

 ![Edytuj i Kontynuuj — okno dialogowe](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Wybierz **Edytuj** , a następnie zmień wiersz `if (x != 0)` do `if (x == 0)`. Debuger będzie się powtarzał zmiany logiki programu w pliku źródłowym.

 **Zmień wartość zmiennej.** Sprawdź wartość `x` etykietki danych lub w oknie zmienne lokalne. Nadal jest 0 (zero). Jeśli próbujesz wykonać instrukcję, który spowodował wyjątek, oryginalnym go tylko zgłosi ponownie. Można zmienić wartość `x`. W oknie zmienne lokalne kliknij dwukrotnie **wartość** kolumny **x** wiersza. Zmień wartość z zakresu od 0 do 1.

 ![Edytowanie wartości w oknie zmienne lokalne](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Wybierz klawisz F11, aby wkraczać do instrukcji, która wcześniej zgłosiła wyjątek. Należy pamiętać, że wiersz jest wykonywany bez błędów. Ponownie wybierz F11.

 **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: Shift+F5). Kończy sesję debugowania.

## <a name="see-also"></a>Zobacz też
 [Rozpocznij sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
