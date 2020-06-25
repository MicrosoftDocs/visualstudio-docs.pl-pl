---
title: Informacje o debugowaniu aplikacji wielowątkowych
description: Debuguj przy użyciu stosów równoległych i równoległych okien zegarków w programie Visual Studio
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
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
ms.openlocfilehash: 30fd29357ab8b42ea6a8baa6412f9ccf7eafed28
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350514"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Rozpocznij debugowanie aplikacji wielowątkowych (C#, Visual Basic, C++)

Program Visual Studio udostępnia kilka narzędzi i elementów interfejsu użytkownika, które ułatwiają debugowanie aplikacji wielowątkowych. W tym samouczku pokazano, jak używać znaczników wątków, okna **stosów równoległych** , okna **zegarków równoległych** , warunkowych punktów przerwania i znaczników punktów przerwania. Wykonanie tego samouczka zapoznaje się z funkcjami programu Visual Studio na potrzeby debugowania aplikacji wielowątkowych.

Te dwa tematy zawierają dodatkowe informacje dotyczące korzystania z innych narzędzi debugowania wielowątkowego:

- Aby użyć paska narzędzi **lokalizacji debugowania** i okna **wątki** , zobacz [Przewodnik: debugowanie aplikacji wielowątkowej](../debugger/how-to-use-the-threads-window.md).

- Przykład wykorzystujący <xref:System.Threading.Tasks.Task> (kod zarządzany) i środowisko uruchomieniowe współbieżności (C++), zobacz [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md). Ogólne porady dotyczące debugowania, które mają zastosowanie do większości typów aplikacji wielowątkowych, można znaleźć w tym temacie i ten temat.

Najpierw musisz mieć projekt aplikacji wielowątkowej. Poniżej przedstawiono przykład.

## <a name="create-a-multithreaded-app-project"></a>Tworzenie projektu aplikacji wielowątkowych

1. Otwórz program Visual Studio i Utwórz nowy projekt.

   ::: moniker range=">=vs-2019"

   Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik** > **startowy**.

   W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#**, **C++** lub **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz **aplikację konsolową (.NET Core)** lub, dla języka C++, szablon **aplikacji konsolowej** , a następnie wybierz **dalej**.

   > [!NOTE]
   > Jeśli nie widzisz poprawnego szablonu, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych dla platformy .NET** lub **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

   W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *MyThreadWalkthroughApp* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** wybierz następujące opcje:

   - W przypadku aplikacji C# w obszarze **Visual C#** wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)**.
   - W przypadku aplikacji Visual Basic w obszarze **Visual Basic**wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)**.
   - W przypadku aplikacji w języku C++ w obszarze **Visual C++** wybierz pozycję **Windows Desktop**, a następnie wybierz pozycję **Aplikacja konsolowa systemu Windows**.

   Jeśli nie widzisz **aplikacji konsolowej (.NET Core)** lub, dla języka C++, szablonu projektu **aplikacji konsoli** , przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych dla platformy .NET** lub **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

   Następnie wpisz nazwę, na przykład *MyThreadWalkthroughApp* , i kliknij przycisk **OK**.

   Wybierz przycisk **OK**.
   ::: moniker-end

   Zostanie wyświetlony nowy projekt konsoli. Po utworzeniu projektu zostanie wyświetlony plik źródłowy. W zależności od wybranego języka plik źródłowy może mieć nazwę *program.cs*, *MyThreadWalkthroughApp. cpp*lub *Module1. vb*.

1. Usuń kod, który pojawia się w pliku źródłowym i zastąp go odpowiednią przykładową listą poniżej.

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
                "The instance method called by the worker thread has ended. " + data);
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
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
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
                    "The instance method called by the worker thread has ended. " + data)
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

1. W menu **plik** wybierz pozycję **Zapisz wszystko**.

1. (Tylko Visual Basic) W Eksplorator rozwiązań (prawego okienka) kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Właściwości**. Na karcie **aplikacja** Zmień **obiekt startowy** na **prosty**.

## <a name="debug-the-multithreaded-app"></a>Debugowanie aplikacji wielowątkowej

1. W edytorze kodu źródłowego poszukaj jednego z następujących fragmentów kodu:

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

1. Kliknij lewym przyciskiem myszy na lewym marginesie `Thread.Sleep` instrukcji lub, `std::this_thread::sleep_for` Aby wstawić nowy punkt przerwania.

    Na marginesie czerwony okrąg wskazuje, że punkt przerwania jest ustawiony w tej lokalizacji.

2. W menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie** (**F5**).

    Program Visual Studio kompiluje rozwiązanie, rozpocznie się uruchamianie aplikacji z dołączonym debugerem, a następnie aplikacja zostaje zatrzymana w punkcie przerwania.

3. W edytorze kodu źródłowego Zlokalizuj wiersz zawierający punkt przerwania.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Odnajdź znacznik wątku  

1. Na pasku narzędzi debugowania wybierz pozycję **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Naciśnij klawisz **F11** raz, aby przejść do debugera o jeden wiersz kodu.

3. Spójrz na odstępy po lewej stronie okna. W tym wierszu zostanie wyświetlony ![znacznik](../debugger/media/dbg-thread-marker.png "ThreadMarker") wątku ikony *znacznika wątku* , który przypomina dwa przykręcone wątki. Znacznik wątku wskazuje, że wątek jest zatrzymany w tej lokalizacji.

    Znacznik wątku może być częściowo ukrywany przez punkt przerwania.

4. Umieść wskaźnik myszy nad znacznikiem wątku. Etykietki danych pojawia się, informując o nazwie i numerze wątku dla każdego zatrzymanego wątku. W takim przypadku nazwa jest prawdopodobnie `<noname>` .

5. Wybierz znacznik wątku, aby wyświetlić dostępne opcje w menu skrótów.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Wyświetlanie lokalizacji wątków

W oknie **stosów równoległych** można przełączać się między widokiem wątków i widokiem zadań (w przypadku programowania opartego na zadaniach), a informacje stosu wywołań dla każdego wątku. W tej aplikacji możemy użyć widoku wątki.

1. Otwórz okno **stosów równoległych** , wybierając pozycję **Debuguj**  >  **Windows**  >  **równoległe stosy**systemu Windows. Powinna zostać wyświetlona coś podobnego do poniższego. Dokładne informacje będą się różnić w zależności od bieżącej lokalizacji każdego wątku, sprzętu i języka programowania.

    ![Okno stosów równoległych](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    W tym przykładzie od lewej do prawej zobaczymy te informacje dla kodu zarządzanego:

    - Wątek główny (po lewej stronie) został zatrzymany `Thread.Start` , gdzie punkt zatrzymania jest wskazywany przez ![znacznik wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker")ikony znacznika wątku.
    - Dwa wątki przeszły `ServerClass.InstanceMethod` , z których jeden jest bieżącym wątkiem (żółta strzałka), podczas gdy drugi wątek został zatrzymany w `Thread.Sleep` .
    - Nowy wątek (po prawej) jest również uruchamiany, ale jest zatrzymany na `ThreadHelper.ThreadStart` .

2. Kliknij prawym przyciskiem myszy pozycje w oknie **stosów równoległych** , aby wyświetlić dostępne opcje w menu skrótów.

    W tym samouczku można wykonać różne akcje, ale w przypadku tej czynności pozostanie więcej informacji w oknie **równoległe** (kolejne sekcje).

    > [!NOTE]
    > Aby wyświetlić widok listy z informacjami o każdym wątku, zamiast tego użyj okna **wątki** . Zobacz [Przewodnik: debugowanie aplikacji wielowątkowej](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Ustawianie czujki na zmiennej

1. Otwórz okno **czujki równoległej** , wybierając kolejno opcje **Debuguj**  >  **Windows**  >  **Parallel Watch**  >  **Parallel Watch 1**.

2. Wybierz komórkę, w której widzisz `<Add Watch>` tekst (lub pustą komórkę nagłówka w czwartej kolumnie), a następnie wprowadź `data` .

    Wartości dla zmiennej danych dla każdego wątku pojawiają się w oknie.

3. Wybierz komórkę, w której widzisz `<Add Watch>` tekst (lub pustą komórkę nagłówka w piątej kolumnie), a następnie wprowadź `count` .

    Wartości dla `count` zmiennej dla każdego wątku pojawiają się w oknie. Jeśli nie widzisz jeszcze więcej informacji, spróbuj nacisnąć klawisz **F11** kilka razy, aby przejść do wykonywania wątków w debugerze.

    ![Okno czujki równoległej](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Kliknij prawym przyciskiem myszy jeden z wierszy w oknie, aby wyświetlić dostępne opcje.

### <a name="flag-and-unflag-threads"></a>Oflagowanie i usuwanie oflagowania wątków
Można oflagować wątki, aby śledzić ważne wątki i ignorować pozostałe wątki.

1. W oknie **czujki równoległej** , przytrzymaj wciśnięty klawisz **SHIFT** i wybierz wiele wierszy.

2. Kliknij prawym przyciskiem myszy i wybierz pozycję **Flaga**.

    Wszystkie wybrane wątki są oflagowane. Teraz można filtrować, aby pokazać tylko wątki oflagowane.

3. W oknie **czujki równoległej** wybierz przycisk **Pokaż tylko Oflagowane wątki** ![Pokaż oflagowane wątki](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Na liście są wyświetlane tylko Oflagowane wątki.

    > [!TIP]
    > Po oflagowaniu niektórych wątków można kliknąć prawym przyciskiem myszy wiersz kodu w edytorze kodu i wybrać polecenie **Uruchom oflagowane wątki do kursora**. Upewnij się, że wybrano kod, który będzie sięgał wszystkich oflagowanych wątków. Program Visual Studio wstrzyma wątki w wybranym wierszu kodu, ułatwiając sterowanie kolejnością wykonywania przez [zamrożenie i rozmrażanie wątków](#bkmk_freeze).

4. Wybierz ponownie przycisk **Pokaż tylko Oflagowane wątki** , aby przełączyć z powrotem do trybu **Pokaż wszystkie wątki** .

5. Aby usunąć flagę wątków, kliknij prawym przyciskiem myszy jeden lub więcej oflagowanych wątków w oknie **czujki równoległej** i wybierz polecenie Usuń **flagę**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a>Zamrażanie i odblokowywanie wykonywania wątku

> [!TIP]
> Można zablokować i odrozmrażać wątki (Wstrzymywanie i wznawianie), aby kontrolować kolejność, w jakiej wątki działają. Może to pomóc w rozwiązywaniu problemów współbieżności, takich jak zakleszczenie i sytuacje wyścigu.

1. W oknie **czujki równoległej** ze wszystkimi wybranymi wierszami kliknij prawym przyciskiem myszy i wybierz pozycję **Zablokuj**.

    W drugiej kolumnie pojawia się ikona pauzy dla każdego wiersza. Ikona Wstrzymaj oznacza, że wątek jest zablokowany.

2. Usuń zaznaczenie wszystkich pozostałych wierszy, zaznaczając tylko jeden wiersz.

3. Kliknij prawym przyciskiem myszy wiersz i wybierz polecenie **rozmrażanie**.

    Ikona Wstrzymaj odnosi się do tego wiersza, wskazując, że wątek nie jest już zablokowany.

4. Przejdź do edytora kodu i naciśnij klawisz **F11**. Tylko niezablokowany wątek jest uruchamiany.

    Aplikacja może również tworzyć wystąpienia niektórych nowych wątków. Wszystkie nowe wątki nie są oflagowane i nie są zamrożone.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a>Wykonaj jeden wątek z warunkowymi punktami przerwania

Pomocne może być wykonanie jednego wątku w debugerze. Jednym ze sposobów jest zamarzanie wątków, które nie są interesujące. W niektórych scenariuszach może być konieczne wykonanie jednego wątku bez zamarzania innych wątków, na przykład w celu odtworzenia konkretnego błędu. Aby obserwować wątek bez zamarzania innych wątków, należy unikać dzielenia na kod, z wyjątkiem wątku, który Cię interesuje. Można to zrobić przez ustawienie [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Można ustawić punkty przerwania w różnych warunkach, takich jak nazwa wątku lub identyfikator wątku. Pomocne może być ustawienie warunku dla danych, które wiadomo, że są unikatowe dla każdego wątku. Jest to typowy scenariusz debugowania, w którym są bardziej interesujące pewne wartości danych niż w żadnym z określonych wątków.

1. Kliknij prawym przyciskiem myszy wcześniej utworzony punkt przerwania i wybierz pozycję **warunki**.

2. W oknie **Ustawienia punktu przerwania** wprowadź `data == 5` wartość wyrażenia warunkowego.

    ![Warunkowy punkt przerwania](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Jeśli jesteś bardziej interesujący w określonym wątku, użyj nazwy wątku lub identyfikatora wątku dla warunku. Aby to zrobić, w oknie **Ustawienia punktu przerwania** wybierz opcję **Filtr** zamiast **wyrażenia warunkowego**i postępuj zgodnie ze wskazówkami dotyczącymi filtru. Możesz chcieć nazwać wątki w kodzie aplikacji, ponieważ identyfikatory wątków zmieniają się po ponownym uruchomieniu debugera.

3. Zamknij okno **Ustawienia punktu przerwania** .

4. Wybierz przycisk Uruchom ponownie ![aplikację](../debugger/media/dbg-tour-restart.png "RestartApp") , aby ponownie uruchomić sesję debugowania.

    Spowoduje to uszkodzenie kodu w wątku, w którym wartość zmiennej danych to 5. W oknie **czujki równoległej** poszukaj żółtej strzałki wskazującej bieżący kontekst debugera.

5. Teraz możesz przekroczyć kod (**F10**) i Wkrocz do kodu (**F11**) i postępować zgodnie z wykonywaniem pojedynczego wątku.

    Tak długo, jak warunek punktu przerwania jest unikatowy dla wątku, a debuger nie trafi żadnych innych punktów przerwania w innych wątkach (może być konieczne ich wyłączenie), można przekroczyć kod i przejść do kodu bez przełączania się na inne wątki.

    > [!NOTE]
    > Po przejściu do debugera zostanie uruchomione wszystkie wątki. Jednak debuger nie będzie zawijany do kodu w innych wątkach, chyba że jeden z innych wątków trafi punkt przerwania.

## <a name="see-also"></a>Zobacz też

- [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Instrukcje: przełączanie na inny wątek w trakcie debugowania](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Instrukcje: korzystanie z okna stosu równoległego](../debugger/using-the-parallel-stacks-window.md)
- [Instrukcje: korzystanie z okna równoległego wyrażenia kontrolnego](../debugger/how-to-use-the-parallel-watch-window.md)