---
title: Dowiedz się, jak debugowanie aplikacji wielowątkowych
description: Debugowanie za pomocą okna stosów równoległych i równoległego wyrażenia kontrolnego w programie Visual Studio
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f07791a02c5e84722e8193f21b7ed2fe37bdd7f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849622"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Rozpoczynanie debugowania aplikacji wielowątkowych (C#, Visual Basic, C++)

Program Visual Studio udostępnia wiele narzędzi i elementów interfejsu użytkownika w celu ułatwienia debugowania aplikacji wielowątkowych. W tym samouczku pokazano, jak i używaj znaczników wątków **stosów równoległych** oknie **równoległego wyrażenia kontrolnego** okien, warunkowe punkty przerwania i filtr punktów przerwania. Ten samouczek umożliwia zapoznanie się z funkcjami programu Visual Studio do debugowania aplikacji wielowątkowych.

Dwa następujące tematy zawierają dodatkowe informacje na temat korzystania z innymi narzędziami debugowania wielowątkowe:

- Aby użyć **Lokalizacja debugowania** narzędzi i **wątków** okna, zobacz [wskazówki: Debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

- Dla przykładu, który używa <xref:System.Threading.Tasks.Task> (kodu zarządzanego) i środowisko uruchomieniowe współbieżności (C++), zobacz [instruktażu: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md). Aby uzyskać ogólne debugowania porady, które mają zastosowanie do najbardziej wielowątkowe typów aplikacji przeczytaj tego tematu i ten zestaw.

Musisz mieć projekt aplikacji wielowątkowych. Poniżej przedstawiono przykład.

## <a name="create-a-multithreaded-app-project"></a>Tworzenie projektu aplikacji wielowątkowych

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **konsoli** (lub **c ++**), wybierz **szablony**, a następnie:

    - Aby uzyskać C# lub Visual Basic, wybierz **Utwórz nowy projekt aplikacji konsoli (.NET Framework)** dla dowolnego C# lub Visual Basic. W oknie dialogowym wybierz **Utwórz**.
    - Dla języka C++, wybierz **Tworzenie nowego projektu aplikacji Konsolowej** dla języka C++. W oknie dialogowym wybierz **Utwórz**.

    Następnie wpisz nazwę, takich jak **MyThreadWalkthroughApp** i kliknij przycisk **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okna dialogowego pole, wybierz następujące opcje:

    - Dla C# aplikacji, w obszarze **Visual C#** , wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET Framework)**.
    - Dla aplikacji w języku Visual Basic w obszarze **języka Visual Basic**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET Framework)**.
    - Dla aplikacji w języku C++ w obszarze **Visual C++**, wybierz **pulpitu Windows**,, a następnie wybierz **aplikacji konsoli Windows**.

    Następnie wpisz nazwę, takich jak **MyThreadWalkthroughApp** i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz **aplikacja Konsolowa** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** lub **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj**.

1. Kliknij przycisk **OK**.

    Pojawi się nowy projekt konsoli. Po utworzeniu projektu pojawia się pliku źródłowego. W zależności od języka, które zostały wybrane, może mieć nazwę pliku źródłowego *Program.cs*, *MyThreadWalkthroughApp.cpp*, lub *Module1.vb*.

1. Usuń kod, który pojawia się w pliku źródłowym i Zastąp kod przykładowy odpowiednie poniżej.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. Na **pliku** menu, wybierz opcję **Zapisz wszystko**.

1. (Tylko Visual Basic) W Eksploratorze rozwiązań (w okienku po prawej stronie), kliknij prawym przyciskiem myszy węzeł projektu, wybierz polecenie **właściwości**. W obszarze **aplikacji** kartę, zmień **obiekt początkowy** do **proste**.

## <a name="debug-the-multithreaded-app"></a>Debugowanie aplikacji wielowątkowych

1. Edytor kodu źródłowego poszukaj jedną z następujących fragmentów kodu:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Kliknięcie lewym przyciskiem myszy na oprawę po lewej stronie `Thread.Sleep` lub `std::this_thread::sleep_for` instrukcję, aby wstawić nowy punkt przerwania.

    Na oprawę czerwone kółko wskazuje, że punkt przerwania jest ustawiony w tej lokalizacji.

2. Na **debugowania** menu, wybierz opcję **Rozpocznij debugowanie** (**F5**).

    Program Visual Studio tworzy rozwiązanie, aplikacja zaczyna być uruchamiana w debugerze i zatrzymywany aplikacji w punkcie przerwania.

3. W Edytor kodu źródłowego zlokalizuj wiersz zawierający punkt przerwania.

### <a name="ShowThreadsInSource"></a>Odkryj znacznika wątku  

1. Na pasku narzędzi debugowania, wybierz **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Naciśnij klawisz **F11** raz, aby awansować debugera jednego wiersza kodu.

3. Spójrz na oprawę w lewej części okna. W tym wierszu, zostanie wyświetlony *znacznika wątku* ikonę ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami skręconych. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Znacznika wątku może być częściowo zasłonięte przez punkt przerwania.

4. Umieść wskaźnik myszy nad znacznika wątku. Etykietki danych pojawi się numer identyfikacyjny nazwy i wątku dla każdego wątku zatrzymania. W takim przypadku nazwa jest prawdopodobnie `<noname>`.

5. Wybierz znacznik wątku, aby wyświetlić dostępne opcje w menu skrótów.

### <a name="ParallelStacks"></a>Wyświetlanie lokalizacji wątku

W **stosów równoległych** okna, można przełączać się między widokiem wątków i (w przypadku programowania opartego na zadaniach) widoku zadania, na które mogą wyświetlać informacje stosu wywołań dla każdego wątku. W tej aplikacji możemy użyć widoku wątków.

1. Otwórz **stosów równoległych** okna, wybierając **debugowania** > **Windows** > **stosów równoległych**. Powinien zostać wyświetlony podobny do następującego. Konkretne informacje będą się różnić w zależności od aktualnej lokalizacji każdego wątku, sprzętu i języka programowania.

    ![Parallel Stacks Window](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    W tym przykładzie od lewej do prawej możemy zobaczyć te informacje dla kodu zarządzanego:

    - Główny wątek (lewa strona) została zatrzymana na `Thread.Start`, gdzie punkt zatrzymania jest wskazywany przez ikonę znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Wprowadzono dwa wątki `ServerClass.InstanceMethod`, z których jedna jest bieżący wątek (żółta strzałka), podczas gdy inne wątku została zatrzymana w `Thread.Sleep`.
    - Nowy wątek (po prawej stronie) jest również uruchamiana, ale jest zatrzymana na `ThreadHelper.ThreadStart`.

2. Kliknij prawym przyciskiem myszy wpisy w **stosów równoległych** okna, aby wyświetlić dostępne opcje w menu skrótów.

    Możesz wykonywać różne akcje te menu kliknij prawym przyciskiem myszy, ale w tym samouczku pokazano, jeden z tych szczegółów w **równoległego wyrażenia kontrolnego** okna (w kolejnych sekcjach).

    > [!NOTE]
    > Aby wyświetlić widok listy ze informacji na temat każdego wątku, należy użyć **wątków** okna zamiast tego. Zobacz [instruktażu: Debugowanie aplikacji wielowątkowych](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Ustawianie wyrażenia kontrolnego na zmiennej

1. Otwórz **równoległego wyrażenia kontrolnego** okna, wybierając **debugowania** > **Windows** > **równoległego wyrażenia kontrolnego**  >  **Równoległe wyrażenie kontrolne 1**.

2. Wybierz komórkę, tam, gdzie zobaczysz `<Add Watch>` tekstu (lub komórki nagłówka puste kolumny 4) i wprowadź `data`.

    Wartości dla zmiennej danych dla każdego wątku są wyświetlane w oknie.

3. Wybierz komórkę, tam, gdzie zobaczysz `<Add Watch>` tekstu (lub komórki nagłówka puste kolumny 5) i wprowadź `count`.

    Wartości `count` zmiennej dla każdego wątku są wyświetlane w oknie. Jeśli nie widzisz jeszcze tym dużo informacji, spróbuj naciśnięcie **F11** kilka razy, aby awansować wykonywanie wątków w debugerze.

    ![Równoległe okno czujki](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Kliknij prawym przyciskiem myszy jeden z wierszy w oknie, aby wyświetlić dostępne opcje.

### <a name="flag-and-unflag-threads"></a>Oflagowanie i usuwanie oflagowania wątków
Może Flaga wątków, aby śledzić ważne wątków i Ignoruj inne wątki.

1. W **równoległego wyrażenia kontrolnego** okna, naciśnij i przytrzymaj klawisz **Shift** klucza i Zaznaczanie wielu wierszy.

2. Kliknij prawym przyciskiem myszy i wybierz **flagi**.

    Wybrane wątki są oflagowane. Teraz możesz filtrować Pokaż tylko oflagowane wątki.

3. W **równoległego wyrażenia kontrolnego** wybierz **Pokaż tylko oflagowane wątki** przycisk ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Tylko oflagowane wątki są wyświetlane na liście.

    > [!TIP]
    > Po flagą wątków, można kliknąć prawym przyciskiem myszy linię kodu w edytorze kodu i wybierz **Uruchom oflagowane wątki do kursora**. Upewnij się, że wybierz kod wszystkich wątków oflagowanych skontaktuje. Program Visual Studio spowoduje wstrzymanie wątków na wybrany wiersz kodu, dzięki czemu łatwiej jest kontrolować kolejność wykonywania przez [zawiesza się i odblokowania wątków](#bkmk_freeze).

4. Wybierz **Pokaż tylko oflagowane wątki** przycisk ponownie, aby powrócić do **Pokaż wszystkie wątki** trybu.

5. Usuwanie oflagowania wątków, kliknij prawym przyciskiem myszy jeden lub więcej wątków oflagowanych w **równoległego wyrażenia kontrolnego** okna, a następnie wybierz pozycję **Unflag**.

### <a name="bkmk_freeze"></a> Zablokuj i Odblokuj wątek wykonywania

> [!TIP]
> Można blokowanie i odblokowywanie (Wstrzymanie i wznowienie) wątków, aby kontrolować kolejność, w którym wątków wykonywania pracy. Może to pomóc Ci rozwiązać problemy ze współbieżnością, takich jak zakleszczenia i wyścigu.

1. W **równoległego wyrażenia kontrolnego** okna z wszystkich wybranych wierszy, kliknij prawym przyciskiem myszy i wybierz pozycję **Freeze**.

    W drugiej kolumnie ikona Wstrzymaj pojawia się dla każdego wiersza. Ikona Wstrzymaj wskazuje, że wątek jest zablokowane.

2. Usuń zaznaczenie wszystkich innych wierszy, wybierając tylko jeden wiersz.

3. Kliknij prawym przyciskiem myszy wiersz, a następnie wybierz pozycję **Odblokuj**.

    Ikona Wstrzymaj stanie się niepotrzebna ten wiersz, wskazujący, że wątek nie jest już jest zamrożona.

4. Przejdź do edytora kodu i naciśnij klawisz **F11**. Uruchamia odblokowanej wątku.

    Aplikacja może również tworzy kilka nowych wątków. Wszystkie nowe wątki są bez flagi i nie są zablokowane.

### <a name="bkmk_follow_a_thread"></a> Postępuj zgodnie z jednego wątku za pomocą warunkowe punkty przerwania

Przydatne może być z wykonywania jest jeden wątek w debugerze. Jest jednym ze sposobów, w tym zamrażanie wątki, które nie są zainteresowani. W niektórych scenariuszach może być konieczne postępuj zgodnie z jednym wątkiem, bez zawiesza się inne wątki, na przykład aby odtworzyć błąd określonej. Aby wykonać wątek bez zawiesza się inne wątki, można uniknąć wejście do kodu, z wyjątkiem w wątku, który Cię interesuje. Można to zrobić, ustawiając [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Możesz ustawić punkty przerwania dla różnych warunków, takich jak nazwa wątku lub identyfikator wątku. Może być pomocne jest ustawienie dla warunku na danych, który jest unikatowy dla każdego wątku. Jest to typowy scenariusz debugowania, w którym interesuje Cię bardziej niż w żadnym z wątków niektóre wartości określone dane.

1. Kliknij prawym przyciskiem myszy punkt przerwania został wcześniej utworzony, a następnie wybierz pozycję **warunki**.

2. W **ustawienia punktu przerwania** oknie wprowadź `data == 5` dla wyrażenia warunkowego.

    ![Warunkowego punktu przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Jeśli interesuje Cię bardziej w określonym wątku, należy następnie rozważyć Nazwa wątku lub identyfikator wątku dla warunku. Aby to zrobić w **ustawienia punktu przerwania** wybierz **filtru** zamiast **wyrażenia warunkowego**i postępuj zgodnie z poradami filtru. Może chcesz nazwać swoje wątków w kodzie aplikacji jako wątki identyfikatory zmiany po ponownym uruchomieniu debugera.

3. Zamknij **ustawienia punktu przerwania** okna.

4. Wybierz ponowne uruchomienie ![ponowne uruchomienie aplikacji](../debugger/media/dbg-tour-restart.png "RestartApp") przycisk, aby ponownie uruchomić sesję debugowania.

    Będzie podzielić kodu w wątku, w którym wartość zmiennej danych wynosi 5. W **równoległego wyrażenia kontrolnego** okna, zwróć uwagę na żółta strzałka wskazująca bieżący kontekst debugera.

5. Teraz użytkownik może przechodzić przez kod (**F10**) i kod krok po kroku (**F11**) i postępuj zgodnie z jednym wątkiem wykonywania.

    Tak długo, jak warunek punktu przerwania jest unikatowy dla wątku i debuger nie trafień inne punkty przerwania w innych wątkach (może być konieczne ich wyłączyć), możesz Przekrocz nad kodem i wejdź do kodu bez przełączania dla innych wątków.

    > [!NOTE]
    > Po dojściu jest debugera, zostaną uruchomione wszystkie wątki. Jednak debuger nie będzie Wejdź do kodu w innych wątkach, chyba że jeden z innych wątków trafienia punktu przerwania.

## <a name="see-also"></a>Zobacz także

- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: Przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Instrukcje: Korzystanie z okna równoległego stosu](../debugger/using-the-parallel-stacks-window.md)
- [Instrukcje: Korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)