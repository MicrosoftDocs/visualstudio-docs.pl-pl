---
title: 'Samouczek: debugowanie kodu C++'
description: Poznaj funkcje debugera Visual Studio i dowiedz się, jak uruchomić debuger, przechodzić przez kod i sprawdzać dane w aplikacji języka C++.
ms.custom: debug-experiment,  vs-acquisition, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5d3b4e277fc7ab2c97ccf72b7b1dd7898160c8d
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725563"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Samouczek: nauka debugowania kodu C++ przy użyciu Visual Studio

W tym artykule przedstawimy funkcje Visual Studio w przewodniku krok po kroku. Jeśli potrzebujesz widoku wyższego poziomu funkcji debugera, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md). Podczas *debugowania aplikacji* zwykle oznacza to, że aplikacja jest uruchamiana z dołączonym debugerem. Gdy to zrobisz, debuger udostępnia wiele sposobów na zobaczenie działania kodu podczas jego działania. Możesz przejść przez kod i przyjrzeć się wartościom przechowywanym w zmiennych, ustawić czasy na zmienne, aby zobaczyć, kiedy zmieniają się wartości, zbadać ścieżkę wykonywania kodu, sprawdzić, czy gałąź kodu jest uruchomiona i tak dalej. Jeśli po raz pierwszy próbujesz debugować kod, przed rozpoczęciem tego artykułu warto przeczytać artykuł [Debugowanie](../debugger/debugging-absolute-beginners.md) dla bezwzględnych początkujących.

Mimo że aplikacja demonstracyjna jest w języku C++, większość funkcji ma zastosowanie do języków C#, Visual Basic, F#, Python, JavaScript i innych języków obsługiwanych przez program Visual Studio (język F# nie obsługuje funkcji Edytuj i kontynuuj. Język F# i język JavaScript nie obsługują **okna Automatyczne).** Zrzuty ekranu znajdują się w języku C++.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom debuger i naciśnij punkty przerwania.
> * Poznasz polecenia umożliwiające krok po kroku kod w debugerze
> * Sprawdzanie zmiennych w oknach porad dotyczących danych i debugera
> * Badanie stosu wywołań

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"

Musisz mieć zainstalowany program Visual Studio 2019 i tworzenie aplikacji **klasycznych z obciążeniem języka C++.**

::: moniker-end
::: moniker range="vs-2017"

Musisz mieć zainstalowany program Visual Studio 2017 i tworzenie aplikacji **klasycznych z obciążeniem języka C++.**

::: moniker-end

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022](https://visualstudio.microsoft.com/vs/preview/vs2022) (wersja zapoznawcza), aby zainstalować ją bezpłatnie.

::: moniker-end

Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Uruchomienie Instalator programu Visual Studio uruchomieniu. Wybierz obciążenie **Tworzenie aplikacji klasycznych w języku C++,** a następnie wybierz pozycję **Modyfikuj.**

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji konsolowej C++. Typ projektu zawiera wszystkie pliki szablonów, które będą potrzebne, zanim jeszcze cokolwiek do ciebie dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Nowy** plik >  > **Project.**

3. W **oknie dialogowym Project** aplikacji w okienku po lewej stronie rozwiń pozycję **Visual C++** a następnie wybierz pozycję **Windows Desktop.** W środkowym okienku wybierz pozycję **Windows konsoli** programu . Następnie nadaj projektowi *nazwę get-started-debugging.*

     Jeśli nie widzisz szablonu  projektu Aplikacja konsoli,  wybierz link Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Project** aplikacji. Uruchomienie Instalator programu Visual Studio uruchomieniu. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

4. Kliknij przycisk **OK**.

   Visual Studio spowoduje otwarcie nowego projektu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz Visual Studio 2019 r.

   Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję **Okno** > **uruchamiania pliku.**

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

1. W **oknie Create a new project (Tworzenie** nowego projektu) wprowadź lub wpisz *console* (konsola) w polu wyszukiwania. Następnie wybierz **pozycję C++** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsoli,** a następnie wybierz pozycję **Dalej.**

   ![Wybieranie szablonu języka C++ dla aplikacji konsolowej](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli,** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji. Następnie w Instalator programu Visual Studio wybierz obciążenie **Tworzenie aplikacji klasycznych w języku C++.**

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub wprowadź *get-started-debugging* w **Project nazwa** projektu. Następnie wybierz pozycję **Utwórz**.

   Visual Studio spowoduje otwarcie nowego projektu.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

1. W *pliku get-started-debugging.cpp* zastąp cały kod domyślny następującym kodem:

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Uruchom debuger!

1. Naciśnij **klawisz F5** **(> Rozpocznij debugowanie)** lub przycisk **Rozpocznij** debugowanie ![Rozpocznij](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") debugowanie na pasku narzędzi Debugowanie.

     **Klawisz F5** uruchamia aplikację z debugerem dołączonym do procesu aplikacji, ale w tej chwili nie zrobiliśmy niczego specjalnego, aby przeanalizować kod. Aplikacja po prostu się ładuje, a zobaczysz dane wyjściowe konsoli.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     W tym samouczku przyjrzymy się bliżej tej aplikacji przy użyciu debugera i zobaczymy funkcje debugera.

2. Zatrzymaj debuger, naciskając czerwony przycisk ![Zatrzymaj debugowanie](../debugger/media/dbg-tour-stop-debugging.png "Zatrzymywanie debugowania") **(Shift**  +  **F5).**

3. W oknie konsoli naciśnij klawisz i naciśnij **klawisz Enter,** aby zamknąć okno konsoli.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Ustawianie punktu przerwania i uruchamianie debugera

1. W pętli funkcji ustaw punkt przerwania, klikając lewy `for` `main` margines następującego wiersza kodu:

    `name += letters[i];`

    W miejscu ustawienia ![punktu](../debugger/media/dbg-breakpoint.png "Punkt przerwania") przerwania zostanie wyświetlony czerwony punkt przerwania.

    Punkty przerwania to jedna z najbardziej podstawowych i najważniejszych funkcji niezawodnego debugowania. Punkt przerwania wskazuje, gdzie Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub czy gałąź kodu jest uruchamiana.

2. Naciśnij **klawisz F5** lub przycisk **Rozpocznij** debugowanie Rozpocznij debugowanie, aplikacja zostanie uruchomiona, a debuger zostanie uruchomiony do wiersza kodu, w którym ustawisz punkt przerwania. ![](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie")

    ![Ustawianie i trafianie punktu przerwania](../debugger/media/get-started-set-breakpoint-cpp.png)

    Żółta strzałka reprezentuje instrukcje, na których debuger został wstrzymany, co również wstrzymuje wykonywanie aplikacji w tym samym momencie (ta instrukcja nie została jeszcze wykonana).

     Jeśli aplikacja nie jest jeszcze uruchomiona, **klawisz F5** uruchamia debuger i zatrzymuje się w pierwszym punkcie przerwania. W przeciwnym **razie klawisz F5** kontynuuje uruchamianie aplikacji do następnego punktu przerwania.

    Punkty przerwania są przydatną funkcją, gdy znasz wiersz kodu lub sekcję kodu, którą chcesz dokładnie zbadać. Aby uzyskać informacje na temat różnych typów punktów przerwania, które można ustawić, takich jak warunkowe punkty przerwania, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Nawigowanie po kodzie w debugerze przy użyciu poleceń kroku

W większości w tym miejscu używamy skrótów klawiaturowych, ponieważ jest to dobry sposób na szybkie wykonywanie aplikacji w debugerze (równoważne polecenia, takie jak polecenia menu, są wyświetlane w nawiasach).

1. Po wstrzymaniu w pętli w metodzie naciśnij klawisz `for` `main` **F11** (lub dwukrotnie wybierz pozycję **Debuguj** do > do ), aby przejść do wywołania `SendMessage` metody.

     Po **dwukrotnym naciśnięciu klawisza F11** powinien nasycić ten wiersz kodu:

     `SendMessage(name, a[i]);`

1. Naciśnij **jeszcze raz klawisz F11,** aby wejściować do metody `SendMessage` .

     Żółty wskaźnik przesuwa się do `SendMessage` metody .

     ![Używanie klawisza F11 do wejściowego do kodu](../debugger/media/get-started-f11-cpp.png "F10 Step Into")

     Klawisz F11 to polecenie **Step Into,** które umożliwia wykonanie aplikacji po jednej instrukcji na raz. F11 to dobry sposób na szczegółowe zbadanie przepływu wykonywania. (Aby szybciej przechodzić przez kod, pokazujemy również inne opcje). Domyślnie debuger pomija kod niebędący użytkownikiem (jeśli chcesz uzyskać więcej szczegółów, zobacz [Tylko mój kod](../debugger/just-my-code.md)).

     Załóżmy, że wszystko jest gotowe do zbadania metody i chcesz wyjść z `SendMessage` metody, ale pozostać w debugerze. Możesz to zrobić za pomocą polecenia **Wyetapuj.**

1. Naciśnij **klawisz Shift**  +  **F11** (lub **debuguj > wyjść).**

     To polecenie wznawia wykonywanie aplikacji (i umożliwia postęp debugera) do momentu, gdy bieżąca metoda lub funkcja zwróci wartość .

     Należy wrócić do pętli `for` w `main` metodzie , wstrzymanej przy `SendMessage` wywołaniu metody.

1. Naciśnij **klawisz F11** kilka razy, aż wrócisz ponownie do `SendMessage` wywołania metody.

1. Po wstrzymaniu w wywołaniu metody naciśnij **klawisz F10** (lub wybierz pozycję **> Krok powyżej**).

     ![Używanie klawisza F10 do przekłóceń kodu](../debugger/media/get-started-step-over-cpp.png "F10 Step Over")

     Zauważ, że tym razem debuger nie wchodzi do `SendMessage` metody . **Klawisz F10** umożliwia przechodzenie do debugera bez przechodzenia do funkcji lub metod w kodzie aplikacji (kod jest nadal wykonywany). Naciskając klawisz **F10** w wywołaniu metody `SendMessage` (zamiast **klawisza F11),** pominąliśmy kod implementacji (dla którego być może nie jesteśmy zainteresowani `SendMessage` w tej chwili). Aby uzyskać więcej informacji na temat różnych sposobów przechodzenia przez kod, zobacz Navigate code in the debugger (Nawigowanie po kodzie [w debugerze).](../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Nawigowanie po kodzie przy użyciu funkcji Uruchom do kliknięcia

1. Naciśnij **klawisz F5,** aby przejść do punktu przerwania.

1. W edytorze kodu przewiń w dół i umieść kursor nad funkcją w metodzie, aż po lewej stronie pojawi się zielony przycisk Uruchom do `std::wcout` `SendMessage` kliknięcia.  ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") Etykietka narzędzia przycisku zawiera tekst "Uruchom wykonywanie tutaj".

     ![Korzystanie z funkcji Uruchom do kliknięcia](../debugger/media/get-started-run-to-click-cpp.png "Uruchom do kliknięcia")

   > [!NOTE]
   > Przycisk **Uruchom do kliknięcia** jest nowy w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] . (Jeśli nie widzisz przycisku z zieloną strzałką, użyj **klawisza F11** w tym przykładzie, aby przejść debuger w odpowiednie miejsce).

2. Kliknij przycisk **Uruchom do kliknięcia,** ![a następnie kliknij przycisk Uruchom, aby kliknąć pozycję](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Debuger jest przekierowywyny do `std::wcout` funkcji .

    Użycie tego przycisku jest podobne do ustawiania tymczasowego punktu przerwania. **Funkcja Uruchom do kliknięcia** umożliwia szybkie poruszanie się w widocznym regionie kodu aplikacji (możesz kliknąć dowolny otwarty plik).

## <a name="restart-your-app-quickly"></a>Szybkie ponowne uruchamianie aplikacji

Kliknij przycisk **Restart** ![Restart App (Uruchom ponownie](../debugger/media/dbg-tour-restart.png "RestartApp") ponownie aplikację) na pasku narzędzi debugowania **(Ctrl**  +  **Shift**  +  **F5).**

Naciśnięcie przycisku **Uruchom ponownie** pozwala zaoszczędzić czas, a nie zatrzymać aplikację i ponownie uruchomić debuger. Debuger wstrzymuje się w pierwszym punkcie przerwania, który zostanie trafiony przez wykonanie kodu.

Debuger zatrzymuje się ponownie w punkcie przerwania wcześniej ustawionym wewnątrz `for` pętli.

## <a name="inspect-variables-with-data-tips"></a>Sprawdzanie zmiennych za pomocą porad dotyczących danych

Funkcje, które umożliwiają sprawdzanie zmiennych, są jedną z najbardziej przydatnych funkcji debugera i istnieją różne sposoby, aby to zrobić. Często podczas próby debugowania problemu próbujesz dowiedzieć się, czy zmienne przechowują wartości, których oczekujesz w określonym czasie.

1. Po wstrzymaniu instrukcji zatrzymaj wskaźnik myszy na zmiennej i zobaczysz, że `name += letters[i]` jest to wartość `letters` domyślna, `size={10}` .

1. Rozwiń `letters` zmienną, aby wyświetlić jej właściwości, które obejmują wszystkie elementy, które zawiera zmienna.

1. Następnie umieść kursor nad `name` zmienną i zobaczysz jej bieżącą wartość, czyli pusty ciąg.

1. Naciśnij kilka razy klawisz **F5** (lub Kontynuuj debugowanie), aby kilka razy iterować po pętli, wsłuchiwać się ponownie w punkcie przerwania i za każdym razem umieszczać kursor nad zmienną, aby sprawdzić jej  >   `for` `name` wartość.

     ![Wyświetlanie porady dotyczącej danych](../debugger/media/get-started-data-tip-cpp.png "Wyświetlanie porady dotyczącej danych")

     Wartość zmiennej zmienia się z każdą iteracją pętli, pokazując wartości `for` , następnie , następnie , i tak `f` `fr` `fre` dalej.

     Często podczas debugowania chcesz szybko sprawdzić wartości właściwości zmiennych, aby sprawdzić, czy przechowują one wartości, które powinny być przechowywane, a porady dotyczące danych są dobrym sposobem na to.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych za pomocą okien zmiennych automatycznych i zmiennych lokalnych

1. Spójrz na **okno Automatyczne** w dolnej części edytora kodu.

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając polecenie **Debuguj** Windows  >    >  **automatyczne.**

    W **oknie Automatyczne** zobaczysz zmienne i ich bieżącą wartość. Okno **Automatyczne wyświetla** wszystkie zmienne używane w bieżącym wierszu lub poprzednim wierszu (sprawdź dokumentację pod celu sprawdzenia zachowania specyficznego dla języka).

1. Następnie przyjrzyj się **oknie Locals (Ustawienia** lokalne) na karcie obok **okna Autos (Automatyczne).**

1. Rozwiń `letters` zmienną, aby wyświetlić elementy, które zawiera.

     ![Sprawdzanie zmiennych w oknie Zmiennych lokalnych](../debugger/media/get-started-locals-window-cpp.png "Okno lokalizacji lokalnych")

    Okno **Zmienne lokalne** zawiera zmienne, które znajdują się w bieżącym zakresie , czyli bieżącym kontekście wykonywania. [](https://www.wikipedia.org/wiki/Scope_(computer_science))

## <a name="set-a-watch"></a>Ustawianie zegarka

1. W głównym oknie edytora kodu kliknij prawym przyciskiem myszy `name` zmienną i wybierz polecenie **Dodaj czujkę.**

    W **dolnej** części edytora kodu zostanie otwarte okno Czujka. W oknie **Wyrażenie czujki** można określić zmienną (lub wyrażenie), którą chcesz śledzić.

    Teraz masz ustawiony zegarek dla zmiennej i możesz zobaczyć, jak jej wartość zmienia się podczas przechodzenia `name` przez debuger. W przeciwieństwie do innych  okien zmiennych, okno Czujka zawsze pokazuje obserwowane zmienne (są one wyszarowane, gdy są poza zakresem).

## <a name="examine-the-call-stack"></a>Badanie stosu wywołań

1. Po wstrzymaniu w pętli kliknij okno Stos wywołań, które jest domyślnie `for` otwarte w prawym dolnym okienku. 

    Jeśli jest zamknięty, otwórz go po wstrzymaniu w debugerze, wybierając polecenie **Debuguj** Windows  >    >  **stos wywołań**.

2. Klikaj **klawisz F11** kilka razy, dopóki debuger nie zostanie wstrzymany w `SendMessage` metodzie . Spójrz na **okno Stos wywołań.**

    ![Badanie stosu wywołań](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Okno **Stos wywołań** pokazuje kolejność wywoływania metod i funkcji. Górny wiersz pokazuje bieżącą funkcję `SendMessage` (metodę w tej aplikacji). Drugi wiersz pokazuje, że `SendMessage` został wywołany z `main` metody i tak dalej.

   > [!NOTE]
   > Okno **stosu wywołań jest** podobne do perspektywy debugowania w niektórych środowiskach PROJEKTOWYCH, takich jak Eclipse.

    Stos wywołań to dobry sposób na zbadanie i zrozumienie przepływu wykonywania aplikacji.

    Możesz kliknąć dwukrotnie wiersz kodu, aby przejść do tego kodu źródłowego i zmienić bieżący zakres sprawdzany przez debuger. Ta akcja nie powoduje postępu debugera.

    Możesz również użyć menu otwieranych prawym przyciskiem myszy w **oknie stosu wywołań,** aby wykonać inne czynności. Możesz na przykład wstawić punkty przerwania do określonych funkcji, przejść do debugera za pomocą polecenia **Uruchom** do kursora i przejść do kodu źródłowego. Aby uzyskać więcej informacji, [zobacz How to: Examine the Call Stack](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Zmienianie przepływu wykonywania

1. Naciśnij dwukrotnie klawisz **F11,** aby uruchomić `std::wcout` funkcję.

1. Po wstrzymaniu debugera w wywołaniu metody użyj myszy, aby chwycić żółtą strzałkę (wskaźnik wykonywania) po lewej stronie i przenieść żółtą strzałkę w górę o jedną linię z powrotem do `SendMessage` `std::wcout` .

1. Naciśnij **klawisz F11**.

    Debuger ponownie uruchomić funkcję `std::wcout` (zobaczysz to w danych wyjściowych okna konsoli).

    Zmieniając przepływ wykonywania, możesz na przykład przetestować różne ścieżki wykonywania kodu lub ponownie uruchomić kod bez ponownego uruchamiania debugera.

    > [!WARNING]
    > Często należy zachować ostrożność podczas pracy z tą funkcją i w etykietce narzędzia jest wyświetlane ostrzeżenie. Mogą pojawić się również inne ostrzeżenia. Przeniesienie wskaźnika nie może przywrócić wcześniejszego stanu aplikacji.

1. Naciśnij **klawisz F5,** aby kontynuować uruchamianie aplikacji.

    Gratulujemy ukończenia tego samouczka!

## <a name="next-steps"></a>Następne kroki

W tym samouczku nauczyliśmy się uruchamiać debuger, przechodzić przez kod i sprawdzać zmienne. Możesz chcieć uzyskać szczegółowe informacje na temat funkcji debugera wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)

