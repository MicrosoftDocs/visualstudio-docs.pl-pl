---
title: Kod zarządzany debugowania | Dokumenty firmy Microsoft
description: Debugowanie języka C# lub visual basic przy użyciu debugera programu Visual Studio
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
ms.openlocfilehash: e5495bb1f531db00d43e04cce9f5f771c88cc1a7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679206"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Szybki start: debugowanie za pomocą języka C# lub Visual Basic przy użyciu debugera programu Visual Studio

Debuger programu Visual Studio zawiera wiele zaawansowanych funkcji ułatwiające debugowanie aplikacji. W tym temacie przedstawiono szybki sposób, aby dowiedzieć się niektóre z podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio i utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **konsolę**, wybierz **pozycję Szablony**, a następnie wybierz pozycję **Utwórz nowy projekt aplikacji konsoli (.NET Core).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **.NET Core**, a następnie w środkowym okienku wybierz pozycję Aplikacja konsoli **(.NET Core).** Następnie wpisz nazwę, taką jak **MyDbgApp** i kliknij **przycisk OK**.
    ::: moniker-end

     Jeśli nie widzisz szablonu projektu **aplikacji konsoli (.NET Core),** przejdź do **pozycji Narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz program **.NET rozwoju pulpitu** i **.NET Core** obciążenia, a następnie wybierz pozycję **Modyfikuj**.

    Visual Studio tworzy projekt.

1. W *Program.cs* lub *Module1.vb*należy wymienić następujący kod

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

    z tym kodem:

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
    > W języku Visual Basic upewnij się, `Sub Main` że obiekt startowy jest ustawiony na (**Właściwości > Obiekt uruchamiania aplikacji > ).**

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

*Punkt przerwania* jest znacznik, który wskazuje, gdzie Visual Studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany. Jest to najbardziej podstawowa funkcja w debugowaniu.

1. Aby ustawić punkt przerwania, kliknij w marginesie `doWork` na marginesie wywołania funkcji (lub wybierz wiersz kodu i naciśnij **klawisz F9**).

    ![Ustawianie punktu przerwania](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Ustawianie punktu przerwania")

2. Teraz naciśnij **klawisz F5** (lub wybierz **debugowanie > rozpocznij debugowanie).**

    ![Trafienie w punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Trafienie w punkt przerwania")

    Debuger wstrzymuje miejsce ustawiania punktu przerwania. Instrukcja, w której debuger i wykonanie aplikacji jest wstrzymana, jest wskazywana przez żółtą strzałkę. Wiersz z `doWork` wywołaniem funkcji nie został jeszcze wykonany.

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często krok po kroku, należy użyć [warunkowego punktu przerwania,](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że kod jest zawieszony TYLKO po spełnieniu określonych warunków. Warunkowy punkt przerwania może zaoszczędzić czas i może również ułatwić debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Nawigowanie po kodzie

Istnieją różne polecenia, aby poinstruować debugera, aby kontynuować. Pokazujemy przydatne polecenie nawigacji kodu, które jest dostępne począwszy od programu Visual Studio 2017.

Po wstrzymaniu w punkcie przerwania `c1.AddLast(20)` umieść wskaźnik myszy na instrukcji, aż pojawi się zielony **przycisk Uruchom, aby kliknąć** przycisk ![Uruchom, aby kliknąć,](../debugger/media/dbg-tour-run-to-click.png "RunToClick (RunToClick)") a następnie naciśnij przycisk **Uruchom, aby kliknąć.**

![Uruchom, aby kliknąć](../debugger/media/dbg-qs-run-to-click-csharp.png "Uruchom, aby kliknąć")

Aplikacja kontynuuje wykonywanie, `doWork`wywoływanie i wstrzymuje wiersz kodu, w którym kliknięno przycisk.

Typowe polecenia klawiatury używane do przechodzenia przez kod obejmują **F10** i **F11**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdzanie zmiennych w etykietce danych

1. W bieżącym wierszu kodu (oznaczone żółtym wskaźnikiem `c1` wykonania) umieść wskaźnik myszy nad obiektem, aby wyświetlić etykietkę danych.

    ![Wyświetlanie etykietki danych](../debugger/media/dbg-qs-data-tip-csharp.png "Wyświetlanie etykietki danych")

    Porada data zawiera bieżącą `c1` wartość zmiennej i umożliwia sprawdzenie jej właściwości. Podczas debugowania, jeśli widzisz wartość, której się nie spodziewasz, prawdopodobnie masz błąd w poprzednich lub wywołujących wierszy kodu.

2. Rozwiń poradę danych, aby przyjrzeć `c1` się bieżącym wartościom właściwości obiektu.

3. Jeśli chcesz przypiąć etykietkę danych, aby nadal `c1` widzieć wartość podczas wykonywania kodu, kliknij ikonę małego pinezki. (Etykietka przypiętych danych jest ów komfortowa).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Jeśli zidentyfikujesz zmianę, którą chcesz przetestować w kodzie, podczas gdy w środku sesji debugowania, można to zrobić, zbyt.

1. Kliknij drugie wystąpienie `c2.First.Value` `c2.First.Value` i `c2.Last.Value`zmień na .

2. Naciśnij kilka razy **klawisz F10** (lub **Debug > Step Over),** aby przejść do debugera i wykonać edytowany kod.

    ![Edytowanie i kontynuowanie](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edytowanie i kontynuowanie")

    **F10** zaliczki debugera jedną instrukcję naraz, ale kroki nad funkcjami zamiast przechodzenia do nich (kod, który pominąć nadal wykonuje).

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytowanie i kontynuowanie](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, krok po kroku kodu i sprawdzić zmienne. Możesz chcieć uzyskać spojrzenie wysokiego poziomu na funkcje debugera wraz z łączami do większej ilości informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
