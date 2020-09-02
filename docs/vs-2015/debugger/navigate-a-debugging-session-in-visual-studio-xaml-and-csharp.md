---
title: Nawigowanie po sesji debugowania (XAML i C#) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156890"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Nawigowanie po sesji debugowania w programie Visual Studio (Xaml i C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik Szybki Start przedstawia sposób nawigowania po sesjach debugowania programu Visual Studio oraz sposobu wyświetlania i zmieniania stanu programu w sesji.

 Ten przewodnik Szybki Start jest przeznaczony dla deweloperów, którzy są nowym programem do debugowania w programie Visual Studio i dla deweloperów, którzy chcą dowiedzieć się więcej na temat nawigowania w sesji debugowania programu Visual Studio. Nie uczy się grafiki samego debugowania. Metody w przykładowym kodzie są przeznaczone tylko do zademonstrowania procedur debugowania opisanych w tym temacie. Metody nie wykorzystują najlepszych praktyk dotyczących projektowania aplikacji lub funkcji. W rzeczywistości będziesz szybko wykryć, że metody i sama aplikacja nie wykonują wiele wszystkiego wcale.

 Sekcje tego przewodnika Szybki Start zostały zaprojektowane tak, aby były tak niezależne, aby można było pominąć każdą sekcję, która zawiera informacje, które już znasz. Nie trzeba również tworzyć przykładowej aplikacji; zaleca się jednak, aby proces był możliwie łatwy, jak to możliwe.

 **Skróty klawiaturowe debugera.** Nawigacja w debugerze programu Visual Studio jest zoptymalizowana zarówno dla myszy, jak i klawiatury. Wiele kroków tego tematu obejmuje akcelerator klawiatury lub klawisz skrótu w uwagach. Na przykład (klawiatura: F5) wskazuje, że wpisanie klawisza F5 spowoduje rozpoczęcie lub kontynuowanie wykonywania debugera.

## <a name="in-this-topic"></a>W tym temacie:
 Możesz dowiedzieć się, jak:

- [Tworzenie przykładowej aplikacji](#BKMK_CreateTheApplication)

- [Ustaw i uruchom punkt przerwania, Wkrocz do metody i Przejrzyj dane programu](#BKMK_StepInto)

- [Wkroczenie, przekroczenie i wyjście z metod](#BKMK_StepIntoOverOut)

- [Ustaw punkt przerwania warunkowego, Uruchom do kursora i Wizualizuj zmienną](#BKMK_ConditionCursorVisualize)

- [Edytuj i Kontynuuj, Odzyskaj z wyjątku](#BKMK_EditContinueRecoverExceptions)

## <a name="create-the-sample-app"></a><a name="BKMK_CreateTheApplication"></a> Tworzenie przykładowej aplikacji
 Debugowanie dotyczy kodu, więc przykładowa aplikacja korzysta z struktury aplikacji ze sklepu Windows tylko w celu utworzenia pliku źródłowego, w którym można zobaczyć, jak działa przechodzenie przez sesję debugowania oraz jak sprawdzić i zmienić stan programu. Cały kod, który zostanie wywołany, jest wywoływany z konstruktora strony głównej; nie dodano żadnych kontrolek i żadne zdarzenia nie są obsługiwane.

 **Utwórz domyślną aplikację ze sklepu Windows w języku C#.** Otwórz program Visual Studio. Na stronie głównej wybierz łącze **Nowy projekt** . W oknie dialogowym Nowy projekt wybierz pozycję **Visual C#** na liście **zainstalowane** , a następnie wybierz pozycję **Sklep Windows**. Na liście szablonów projektu wybierz pozycję **aplikacja**. Program Visual Studio tworzy nowe rozwiązanie i projekt, a następnie wyświetla projektanta MainPage. XAML i Edytor kodu XAML.

 **Otwórz plik źródłowy MainPage.xaml.cs.** Kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze XAML i wybierz polecenie **Wyświetl kod**. Zostanie wyświetlony plik związany z kodem MainPage.xaml.cs. Należy zauważyć, że w pliku znajduje się tylko jedna metoda, `MainPage()` Konstruktor.

 **Zastąp Konstruktor MainPage z przykładowym kodem.** Usuń metodę MainPage (). Użyj tego linku: [kod przykładowy nawigacji debugera (XAML i C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md), a następnie skopiuj kod wymieniony w sekcji C# do Schowka. (Wybierz z **powrotem** w przeglądarce lub Podgląd pomocy, aby powrócić do tej strony szybkiego startu). W edytorze programu Visual Studio Wklej kod w `partial class MainPage` bloku. Naciśnij kombinację klawiszy CTRL + s, aby zapisać plik.

 Teraz można postępować zgodnie z przykładami w tym temacie.

## <a name="set-and-run-to-a-breakpoint-step-into-a-method-and-examine-program-data"></a><a name="BKMK_StepInto"></a> Ustaw i uruchom punkt przerwania, Wkrocz do metody i Przejrzyj dane programu
 Najczęstszym sposobem uruchomienia sesji debugowania jest wybranie opcji **Rozpocznij debugowanie** z menu **Debuguj** (klawiatura: F5). Wykonywanie rozpocznie się i kontynuuje do momentu, gdy zostanie osiągnięty punkt przerwania, zostanie ręcznie zawieszone wykonanie, wystąpił wyjątek lub aplikacja zostanie zakończona.

 Gdy wykonywanie jest zawieszone w debugerze, można wyświetlić wartość aktywnej zmiennej w poradach danych, aktywując wskaźnik myszy nad zmienną. Możesz również otworzyć okna lokalne i okna podsystemy, aby wyświetlić listy aktywnych zmiennych i ich bieżących wartości. Dodanie co najmniej jednej zmiennej do okna czujki umożliwia skoncentrowanie się na wartości zmiennych, gdy aplikacja kontynuuje wykonywanie.

 Po wstrzymaniu wykonywania aplikacji (która jest również wywoływana w debugerze) można kontrolować sposób wykonywania reszty kodu programu. Możesz kontynuować wiersz po wierszu, poruszając się z wywołania metody do samej metody lub można wykonać wywołaną metodę w jednym kroku. Te procedury są nazywane przechodzeniem przez aplikację. Możesz również wznowić standardowe wykonywanie aplikacji, uruchamiając do następnego punktu przerwania ustawionego lub do wiersza, w którym znajduje się kursor. Sesja debugowania można zatrzymać w dowolnym momencie. Debuger został zaprojektowany w celu wykonania niezbędnych operacji czyszczenia i zakończenia wykonywania.

### <a name="example-1"></a>Przykład 1
 W tym przykładzie ustawisz punkt przerwania w konstruktorze MainPage pliku MainPage.xaml.cs, Wkrocz do pierwszej metody, Wyświetl wartości zmiennych, a następnie Zatrzymaj debugowanie.

 **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `methodTrack = "Main Page";` w konstruktorze MainPage. Wybierz wiersz w cieniowanym marginesie edytora kodu źródłowego (klawiatura: Umieść kursor w wierszu i wybierz klawisz F9).

 ![Wkrocz do](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Ikona punktu przerwania pojawia się na oprawie.

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

 Aplikacja rozpoczyna wykonywanie i wstrzymuje wykonywanie natychmiast przed instrukcją, w której ustawiono punkt przerwania. Ikona bieżącego wiersza w obszarze odstępu identyfikuje lokalizację i jest wyróżniona Bieżąca instrukcja.

 ![Ustawianie punktu przerwania](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Teraz masz kontrolę nad wykonywaniem aplikacji i sprawdzanie stanu programu w trakcie wykonywania instrukcji dotyczących programu.

 **Wkrocz do metody.** W menu **debugowanie** wybierz pozycję **krok do** (klawiatura: F11).

 ![Bieżący wiersz](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Należy zauważyć, że debuger przechodzi do następnego wiersza, który jest wywołaniem metody example1. Wybierz krok ponownie. Debuger przechodzi do punktu wejścia metody example1. Oznacza to, że metoda została załadowana na stosie wywołań, a pamięć dla zmiennych lokalnych została przypisana.

 Po przekroczeniu wiersza kodu debuger wykonuje jedną z następujących czynności:

- Jeśli następna instrukcja nie jest wywołaniem funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie wstrzymuje wykonywanie.

- Jeśli instrukcja jest wywołaniem funkcji w rozwiązaniu, debuger przechodzi do punktu wejścia wywołanej funkcji, a następnie zawiesza wykonywanie.

  Kontynuuj wkroczenie do instrukcji example1, dopóki nie osiągniesz punktu wyjścia. Debuger podświetla zamykający nawias klamrowy metody.

  **Sprawdzanie wartości zmiennych w etykietkach danych.** Po umieszczeniu wskaźnika myszy nad nazwą zmiennej, nazwa, wartość i typ zmiennej są wyświetlane w etykietce danych.

  ![Etykietka danych debugera](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Umieść wskaźnik myszy nad zmienną `a` . Zanotuj nazwę, wartość i typ danych. Umieść wskaźnik myszy nad zmienną `methodTrack` . Ponownie Zanotuj nazwę, wartość i typ danych.

  **Sprawdzanie wartości zmiennych w oknie zmiennych lokalnych.** W menu **Debuguj** wskaż pozycję **Windows**, a następnie wybierz pozycję **Ustawienia regionalne**. (Klawiatura: Alt + 4).

  ![okno zmiennych lokalnych](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Okna lokalne są widokiem drzewa parametrów i zmiennych funkcji. Właściwości zmiennej obiektu są węzłami podrzędnymi samego obiektu. `this`Zmienna to ukryty parametr w każdej metodzie obiektu, która reprezentuje sam obiekt. W tym przypadku reprezentuje klasę MainPage. Ponieważ `methodTrack` jest elementem członkowskim klasy MainPage, jego wartość i typ danych są wymienione w wierszu poniżej `this` . Rozwiń `this` węzeł, aby wyświetlić `methodTrack` informacje.

  **Dodaj czujkę dla zmiennej methodTrack.** `methodWatch`Ta zmienna jest używana w tym przewodniku szybki start do wyświetlania metod wywoływanych w przykładach. Aby ułatwić Wyświetlanie wartości zmiennej, należy dodać ją do okna Czujka. Kliknij prawym przyciskiem myszy nazwę zmiennej w oknie zmiennych lokalnych, a następnie wybierz polecenie **Dodaj czujkę**.

  ![okno czujki](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Można obejrzeć wiele zmiennych w oknie czujki. Wartości zmiennych obserwowanych, takich jak wartości w oknach lokalnych i etykietek danych, są aktualizowane po każdym wstrzymaniu wykonywania. Możesz również dodać zmienne do okna czujki z edytora kodu. Wybierz zmienną do obejrzenia, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Dodaj czujkę**.

## <a name="step-into-over-and-out-of-methods"></a><a name="BKMK_StepIntoOverOut"></a> Wkroczenie, przekroczenie i wyjście z metod
 W przeciwieństwie do przechodzenia do metody wywoływanej przez metodę nadrzędną, przechodzenie przez metodę jest wykonywana przez metodę podrzędną, a następnie wstrzymuje wykonywanie w metodzie wywołującej jako wznowienie elementu nadrzędnego. Możesz przekroczyć metodę, gdy znasz sposób działania metody i upewnij się, że jej wykonanie nie będzie miało wpływu na badany problem.

 Przechodzenie przez wiersz kodu, który nie zawiera wywołania metody, wykonuje wiersz tak samo jak w wierszu.

 Przechodzenie poza metodę podrzędną kontynuuje wykonywanie metody, a następnie wstrzymuje wykonywanie po powrocie metody do metody wywołującej. Po ustaleniu, że pozostała część funkcji nie jest istotna, można wypróbować długą funkcję.

 Przechodzenie między funkcją i przechodzenie z niej wykonuje funkcję.

 ![Wkroczenie, przekroczenie i wyjście z metod](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Przykład 2
 W tym przykładzie przeprowadzono kroki, przekroczenia i z metod.

 **Wywołaj metodę example2 w konstruktorze MainPage.** Edytuj Konstruktor MainPage i Zastąp wiersz następujący: `methodTrack = String.Empty;` `Example2();` .

 ![Wywołaj metodę example2 z metody demonstracyjnej](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5). Debuger wstrzymuje wykonywanie w punkcie przerwania.

 **Przekrocz wiersz kodu.** W menu **debugowanie** wybierz pozycję **krok nad** (klawiatura: F10). Debuger wykonuje `methodTrack = "MainPage";` instrukcję w taki sam sposób, jak w instrukcji.

 **Wkrocz do example2 i Example2_A.** Wybierz klawisz F11, aby przejść do metody przykład 2. Kontynuuj wykonywanie kroków do instrukcji example2 do momentu uzyskania dostępu do wiersza `int x = Example2_A();` . Ponownie przejdź do tego wiersza, aby przejść do punktu wejścia Example2_A. Przejdź do kolejnych instrukcji Example2_A do momentu powrotu do example2.

 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Przekrocz funkcję.** Należy zauważyć, że następny wiersz w example2, `int y = Example2_A();` jest zasadniczo taki sam jak w poprzednim wierszu. Możesz bezpiecznie przekroczyć ten wiersz. Wybierz klawisz F10, aby przejść od wznawiania example2 do tego drugiego wywołania do Example2_A. Wybierz F10, aby przekroczyć tę metodę. Należy zauważyć, że `methodTrack` ciąg wskazuje, że metoda example2_a została wykonana dwa razy. Zauważ również, że debuger natychmiast przejdzie do następnego wiersza. Nie wstrzymuje wykonywania w punkcie example2.

 **Wyjdź z funkcji.** Wybierz klawisz F11, aby przejść do Example2_B metody. Należy pamiętać, że Example2_B nie różni się od Example2_A. Aby wypróbować metodę, wybierz pozycję **Wyjdź** z menu **debugowanie** (klawiatura: Shift + F11). Należy zauważyć, że `methodTrack` zmienna wskazuje, że Example2_B zostało wykonane i że debuger wrócił do punktu, w którym example2 wznawia.

 **Zatrzymaj debugowanie.** W menu Debuguj wybierz polecenie Zatrzymaj debugowanie (klawiatura: Shift + F5). Spowoduje to zakończenie sesji debugowania.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_ConditionCursorVisualize"></a> Ustaw punkt przerwania warunkowego, Uruchom do kursora i Wizualizuj zmienną
 Warunkowy punkt przerwania określa warunek, który powoduje zawieszenie wykonywania przez debuger. Warunek jest określany przez dowolne wyrażenie kodu, które może być oceniane jako true lub false. Na przykład można użyć warunkowego punktu przerwania do sprawdzenia stanu programu w często wywoływanej metodzie tylko wtedy, gdy zmienna osiągnie określoną wartość.

 Uruchamianie do kursora przypomina Ustawianie punktu przerwania jednorazowego. Po wstrzymaniu wykonywania można wybrać wiersz w źródle i wznowić wykonywanie do momentu osiągnięcia wybranego wiersza. Na przykład można przechodzenie przez pętlę w metodzie i określić, że kod w pętli działa poprawnie. Zamiast przechodzić przez każdą iterację pętli, można uruchomić kursor, który jest umieszczony po wykonaniu pętli.

 Czasami trudno jest wyświetlić wartość zmiennej w wierszu etykietki danych lub okna zmiennych. Debuger może wyświetlać ciągi, HTML i XML w wizualizatorze tekstu, który przedstawia sformatowany widok wartości w przewijanym oknie.

### <a name="example-3"></a>Przykład 3
 W tym przykładzie ustawisz warunkowy punkt przerwania do przerwania w określonej iteracji pętli, a następnie uruchomisz kursor do kursora, który jest umieszczony po pętli. Możesz również wyświetlić wartość zmiennej w wizualizatorze tekstu.

 **Wywołaj metodę example3 w konstruktorze MainPage.** Edytuj Konstruktor MainPage i Zastąp wiersz następujący wierszem `methodTrack = String.Empty;` `Example3();` .

 ![Wywołaj example3 z metody demonstracyjnej](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Uruchom do punktu przerwania.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5). Debuger wstrzymuje wykonywanie w punkcie przerwania w metodzie MainPage.

 **Wkrocz do metody example3.** Wybierz pozycję **Wkrocz** do w menu **debugowanie** (klawiatura: F11), aby przejść do punktu wejścia metody example3. Kontynuuj przechodzenie do metody do momentu iteracji jednej lub dwóch pętli `for` bloku. Pamiętaj, że zajmiesz dużo czasu, aby przekroczyć wszystkie iteracje 1000.

 **Ustaw punkt przerwania warunkowego.** Na lewym marginesie okna kod kliknij prawym przyciskiem myszy wiersz, `x += i;` a następnie wybierz pozycję **warunek**. Zaznacz pole wyboru **warunek** , a następnie wpisz `i == 500;` w polu tekstowym. Wybierz opcję **jest true** , a następnie wybierz **przycisk OK**. Punkt przerwania umożliwia sprawdzenie wartości w iteracji 500th `for` pętli.

 ![Okno dialogowe warunek punktu przerwania](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Możesz określić ikonę punktu przerwania warunkowego przez jego biały krzyżyk.

 ![Warunkowy punkt przerwania](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Uruchom do punktu przerwania.** W menu Debugowanie wybierz polecenie Kontynuuj (klawiatura: F5). W oknie zmiennych lokalnych upewnij się, że bieżąca wartość `i` to 500. Należy zauważyć, że zmienna `s` jest reprezentowana jako pojedynczy wiersz i jest znacznie dłuższa niż okno.

 **Wizualna zmienna ciągu.** Kliknij ikonę lupy w kolumnie **wartość** `s` .

 Zostanie wyświetlone okno wizualizator tekstu, a wartość ciągu jest prezentowana jako ciąg wielowierszowy.

 **Uruchom do kursora.** Kliknij prawym przyciskiem myszy wiersz `methodTrack += "->Example3";` , a następnie wybierz polecenie **Uruchom do kursora** (klawiatura: Przesuń kursor do wiersza; CTRL + F10). Debuger wykonuje iteracje pętli, a następnie wstrzymuje wykonywanie w wierszu.

 **Zatrzymaj debugowanie.** W menu Debuguj wybierz polecenie Zatrzymaj debugowanie (klawiatura: Shift + F5). Spowoduje to zakończenie sesji debugowania.

## <a name="edit-and-continue-recover-from-an-exception"></a><a name="BKMK_EditContinueRecoverExceptions"></a> Edytuj i Kontynuuj, Odzyskaj z wyjątku
 W niektórych sytuacjach po przebicie na kod w debugerze programu Visual Studio można zmienić wartość zmiennych, a nawet logiki instrukcji. Ta funkcja jest nazywana Edytuj i Kontynuuj.

 Edycja i kontynuowanie może być szczególnie przydatne w przypadku przerwania wyjątku. Zamiast zatrzymywać i ponownie uruchamiać debugowanie długotrwałej i objętej procedury w celu uniknięcia wyjątku, można "wycofać" wyjątek, aby przenieść wykonywanie do punktu bezpośrednio przed wystąpieniem wyjątku, a następnie zmienić zmienną lub instrukcję powodującą wystąpienie problemu i kontynuować bieżącą sesję debugowania w stanie, który nie zgłasza wyjątku.

 Chociaż można korzystać z funkcji Edytuj i Kontynuuj w wielu różnych sytuacjach, określone warunki, które nie obsługują funkcji Edytuj i Kontynuuj, są trudne do określenia, ponieważ warunki są zależne od języka programowania, bieżącego stanu stosu programu oraz zdolności debugera do zmiany stanu bez uszkodzenia procesu. Najlepszym sposobem, aby ustalić, czy zmiana w edycji jest obsługiwana, jest tylko jej próba. Debuger umożliwia natychmiastowe sprawdzenie, czy zmiana nie jest obsługiwana.

### <a name="example-4"></a>Przykład 4
 W tym przykładzie należy uruchomić debuger, aby przewinąć wyjątek, poprawić logikę metody, a następnie zmienić wartość zmiennej, aby można było kontynuować wykonywanie metody.

 **Wywołaj metodę example4 w konstruktorze MainPage.** Edytuj Konstruktor MainPage () i Zastąp wiersz następujący wierszem `methodTrack = String.Empty;` `Example4();` .

 ![Wywołaj example4 z metody demonstracyjnej](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Uruchom na wyjątek.** Rozpocznij sesję debugowania, wybierając pozycję **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5). Naciśnij ponownie klawisz F5, aby wznowić wykonywanie. Debuger wstrzymuje wykonywanie od wyjątku w metodzie Example4 i wyświetla okno dialogowe wyjątku.

 ![Wyjątek — okno dialogowe](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Zmień logikę programu.** Oczywiste jest, że błąd jest w `if` stanie: wartość `x` powinna zostać zmieniona, gdy `x` jest równa 0, nie `x` jest równa zero. Wybierz opcję **Przerwij** , aby naprawić logikę metody. Gdy próbujesz edytować wiersz, pojawi się inne okno dialogowe.

 ![Edytuj i Kontynuuj — okno dialogowe](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Wybierz pozycję **Edytuj** , a następnie zmień wiersz `if (x != 0)` na `if (x == 0)` . Debuger zachowuje zmiany w logice programu do pliku źródłowego.

 **Zmień wartość zmiennej.** Zapoznaj się z wartością `x` w podanej etykietce lub w oknie zmiennych lokalnych. Nadal jest równa 0 (zero). Jeśli spróbujesz wykonać instrukcję, która spowodowała pierwotny wyjątek, zostanie ona ponownie wyrzucana. Można zmienić wartość `x` . W oknie zmiennych lokalnych kliknij dwukrotnie kolumnę **wartość** wiersza **x** . Zmień wartość z 0 na 1.

 ![Edytowanie wartości w oknie zmiennych lokalnych](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Wybierz klawisz F11, aby przejść do instrukcji, która wcześniej wywołała wyjątek. Należy zauważyć, że wiersz jest wykonywany bez błędu. Ponownie wybierz polecenie F11.

 **Zatrzymaj debugowanie.** W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: Shift + F5). Spowoduje to zakończenie sesji debugowania.

## <a name="see-also"></a>Zobacz też
 [Rozpocznij sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [Wyzwalaj wstrzymanie, wznowienie i zdarzenia w tle dla aplikacji do sklepu Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
