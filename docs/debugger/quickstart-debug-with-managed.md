---
title: Debuguj kod zarządzany | Microsoft Docs
description: Debugowanie języka C# lub Visual Basic przy użyciu debugera programu Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f790d30dc97d5549737c3c1cd003086477ce984f
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683013"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Szybki Start: debugowanie za pomocą języka C# lub Visual Basic przy użyciu debugera programu Visual Studio

Debuger programu Visual Studio udostępnia wiele zaawansowanych funkcji ułatwiających debugowanie aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik**  >  **startowy**. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

    W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform.

    Po zastosowaniu filtrów języka i platformy wybierz szablon **aplikacja konsoli** dla platformy .NET Core, a następnie wybierz przycisk **dalej**.

    Wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.

    Jeśli szablon projektu **aplikacji konsolowej** dla platformy .NET Core nie jest widoczny, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz pozycję **Aplikacja konsolowa (.NET Core)**. Następnie wpisz nazwę, na przykład **MyDbgApp** , i kliknij przycisk **OK**.

    Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.
    ::: moniker-end

    Program Visual Studio tworzy projekt.

1. W *program.cs* lub *Module1. vb* Zastąp następujący kod

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    następującym:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > W Visual Basic upewnij się, że obiekt uruchamiania jest ustawiony na `Sub Main` (**Właściwości > aplikacji > obiekt startowy**).

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

*Punkt przerwania* jest znacznikiem wskazującym, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana. Jest to najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij na odstępie po lewej stronie `doWork` wywołania funkcji (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustawianie punktu przerwania](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Ustawianie punktu przerwania")

2. Teraz naciśnij klawisz **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafienie punktu przerwania](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Trafienie punktu przerwania")

    Debuger wstrzymuje miejsce, w którym ustawiono punkt przerwania. Instrukcja, w której debuger i wykonywanie aplikacji jest wstrzymana, jest wskazywana przez żółtą strzałkę. Wiersz z `doWork` wywołaniem funkcji nie został jeszcze wykonany.

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które są często wykonywane, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) , aby upewnić się, że kod jest zawieszony tylko wtedy, gdy spełnione są określone warunki. Warunkowy punkt przerwania może zaoszczędzić czas i może ułatwić Debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Nawiguj po kodzie

Istnieją różne polecenia, aby polecić debugerowi kontynuowanie. Wyświetlamy przydatne polecenie nawigacji kodu, które jest dostępne w programie Visual Studio 2017.

Gdy punkt przerwania jest wstrzymany, umieść kursor nad instrukcją `c1.AddLast(20)` do momentu wyświetlenia zielonego przycisku **Uruchom** ![do](../debugger/media/dbg-tour-run-to-click.png "RunToClick") kliknięcia, a następnie naciśnij przycisk **Uruchom do** kliknięcia.

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click-csharp.png "Uruchom do kliknięcia")

Aplikacja kontynuuje wykonywanie, wywoływanie `doWork` i wstrzymuje w wierszu kodu, w którym został kliknięty przycisk.

Typowe polecenia klawiatury używane do przechodzenia przez kod obejmują **F10** i **F11**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-data-tip"></a>Sprawdzanie zmiennych w etykietce danych

1. W bieżącym wierszu kodu (oznaczonym przez żółty wskaźnik wykonania) Umieść kursor nad `c1` obiektem za pomocą myszy, aby wyświetlić etykietkę danych.

    ![Wyświetlanie etykietki danych](../debugger/media/dbg-qs-data-tip-csharp.png "Wyświetlanie etykietki danych")

    Porada dane przedstawia bieżącą wartość `c1` zmiennej i umożliwia inspekcję jej właściwości. W przypadku debugowania, Jeśli zobaczysz nieoczekiwaną wartość, prawdopodobnie masz usterkę w powyższym lub wywoływanym wierszu kodu.

2. Rozwiń etykietkę danych, aby sprawdzić bieżącą wartość właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć wskazówkę dotyczącą danych, aby można było nadal zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę małego numeru PIN. (Można przenieść przypiętą końcówkę danych do wygodnej lokalizacji).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Jeśli określisz zmianę, która ma zostać przetestowana w kodzie w trakcie sesji debugowania, możesz to zrobić.

1. Kliknij drugie wystąpienie `c2.First.Value` i przejdź `c2.First.Value` do `c2.Last.Value` .

2. Naciśnij klawisz **F10** (lub **Debuguj > krok powyżej**) kilka razy, aby przejść do debugera i wykonać edytowany kod.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edytowanie i kontynuowanie")

    **F10** zastąpi debuger jedną instrukcją w tym samym czasie, ale nie trzeba przechodzić do tych funkcji, zamiast przechodzić do nich (kod, który pominie nadal wykonywany).

Aby uzyskać więcej informacji na temat używania funkcji Edit-and-Continue i on Features, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, przewinąć kod i zbadać zmienne. Możesz chcieć uzyskać ogólne omówienie funkcji debugera oraz linki do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
