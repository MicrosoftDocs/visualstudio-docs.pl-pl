---
title: Debugowanie kodu zarządzanego | Dokumentacja firmy Microsoft
description: Debugowanie języka C# lub Visual Basic przy użyciu debugera programu Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8762d13e1a5981f634b1b13fe08968a6b01c2b94
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58475971"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Szybki start: Debugowanie za pomocą C# lub Visual Basic, za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **konsoli**, wybierz **szablony**, następnie wybierz **Utwórz nowy projekt aplikacji konsoli (.NET Core)**. W oknie dialogowym wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okno dialogowe, w obszarze **Visual C#** , wybierz **platformy .NET Core**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET -Rdzeniowe)**. Następnie wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.
    ::: moniker-end

     Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablon projektu, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych dla platformy .NET** i **platformy .NET Core** obciążenia, wybierz **Modyfikuj**.

    Program Visual Studio tworzy projekt.

1. W *Program.cs* lub *Module1.vb*, Zastąp następujący kod

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

    przy użyciu tego kodu:

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
    > W języku Visual Basic, upewnij się, obiekt startowy jest ustawiony na `Sub Main` (**właściwości > aplikacji > Obiekt początkowy**).

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

A *punktu przerwania* jest znacznik, który wskazuje, gdzie program Visual Studio należy wstrzymać działającego kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy nie jest wprowadzenie uruchamiane gałęzi kodu. Jest najbardziej podstawowa funkcja podczas debugowania.

1. Aby ustawić punkt przerwania, kliknij na marginesie po lewej stronie `doWork` wywołania funkcji (lub wybierz linii kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Ustaw punkt przerwania")

2. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "trafia w punkt przerwania")

    Wstrzymuje działanie debugera, gdzie ustawić punkt przerwania. Żółta strzałka wskazuje instrukcji, w której zostało wstrzymane wykonanie debugera i aplikacji. Wiersz z `doWork` wywołanie funkcji nie zostało jeszcze wykonane.

    > [!TIP]
    > Jeśli punkt przerwania w pętli lub rekursji, lub jeśli masz wiele punktów przerwania, które często krokach, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że Twój kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. Warunkowego punktu przerwania, można zaoszczędzić czas i jego może również ułatwić debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Przechodzenie do kodu

Ma innego polecenia, aby wydać polecenie debugera, aby kontynuować. Przedstawiono polecenia nawigacji przydatne kodu, która jest dostępna, począwszy od programu Visual Studio 2017.

Podczas wstrzymania w punkcie przerwania, umieść kursor nad instrukcji `c1.AddLast(20)` aż zielony **Uruchom do kliknięcia** przycisk ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się, a następnie naciśnij klawisz **Uruchom do kliknięcia** przycisku.

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click-csharp.png "Uruchom do kliknięcia")

Aplikacja kontynuuje wykonywanie, wywołanie `doWork`i zatrzymuje się w wierszu kodu, gdy kliknięto przycisk.

Typowe polecenia klawiatury używane do obejmują Przechodź przez kod **F10** i **F11**. Aby uzyskać więcej szczegółowych instrukcji, zobacz [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdzanie zmiennych w datatip

1. W bieżącym wierszu kodu (oznaczonych przez wskaźnik wykonania żółty), umieść kursor nad `c1` obiektu myszą, aby pokazać poradzie dotyczącej danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip-csharp.png "wyświetlanie etykietki danych")

    Datatip pokazuje bieżącą wartość `c1` zmiennej i umożliwia inspekcję jego właściwości. Podczas debugowania, jeśli zostanie wyświetlony wartości, który nie powinien, prawdopodobnie masz usterkę w poprzednim lub wywoływania wierszy kodu.

2. Rozwiń etykietka danych, aby wyświetlić bieżące wartości właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć datatip, dzięki czemu możesz zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę pinezki małe. (W dogodnym miejscu może przechodzić przypiętych etykietki danych).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Po zidentyfikowaniu zmianę, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, zbyt.

1. Kliknij pozycję drugiego wystąpienia `c2.First.Value` i zmień `c2.First.Value` do `c2.Last.Value`.

2. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poszerzyć debugera i wykonywanie edycji kodu.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edytuj i Kontynuuj")

    **F10** prowadzi instrukcja debugger jeden w danym momencie, ale kroki za pośrednictwem funkcji zamiast przechodzenie krok po kroku do nich (nadal wykonuje kod, który zostanie pominięta).

Aby uzyskać więcej informacji na temat korzystania z edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
