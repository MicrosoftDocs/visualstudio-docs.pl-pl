---
title: Debuguj ASP.NET Core
description: Debugowanie ASP.NET Core za pomocą debugera programu Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847873"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Szybki Start: debugowanie ASP.NET Core za pomocą debugera programu Visual Studio

Debuger programu Visual Studio udostępnia wiele zaawansowanych funkcji ułatwiających debugowanie aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz ASP.NET**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET Core aplikacji sieci Web**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Wizualizacja C#** wybierz pozycję **Sieć Web**, a następnie w środkowym okienku wybierz **ASP.NET Core aplikacji sieci Web**. Wpisz nazwę, taką jak **MyDbgApp** , i kliknij przycisk **OK**.

    W oknie dialogowym, które się pojawi, wybierz pozycję **aplikacja sieci Web** w środkowym okienku, a następnie kliknij przycisk **OK**.

    ![Wybierz aplikację sieci Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **ASP.NET Core aplikacji sieci Web** , przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje...** , co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

    Program Visual Studio tworzy projekt.

1. W Eksplorator rozwiązań otwórz About.cshtml.cs (w obszarze Pages/about. cshtml) i Zastąp następujący kod

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    przy użyciu tego kodu:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

*Punkt przerwania* jest znacznikiem wskazującym, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana. Jest to najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij na oprawę po lewej stronie funkcji `doWork` (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Punkt przerwania jest ustawiany z lewej strony otwierającego nawiasu klamrowego (`{`).

1. Teraz naciśnij klawisz **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

1. Po załadowaniu strony sieci Web kliknij link **informacje** w górnej części strony sieci Web.

    Debuger wstrzymuje miejsce, w którym ustawiono punkt przerwania. Instrukcja, w której debuger i wykonywanie aplikacji jest wstrzymana, jest wskazywana przez żółtą strzałkę. Wiersz ze otwierającym nawiasem klamrowym (`{`) po deklaracji funkcji `doWork` nie został jeszcze wykonany.

    ![Trafienie punktu przerwania](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które są często wykonywane, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) , aby upewnić się, że kod jest zawieszony tylko wtedy, gdy spełnione są określone warunki. Pozwala to zaoszczędzić czas i ułatwia debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Nawiguj po kodzie

Istnieją różne polecenia, aby polecić debugerowi kontynuowanie. Wyświetlamy przydatne polecenie nawigacji kodu, które jest dostępne w programie Visual Studio 2017.

Gdy punkt przerwania jest wstrzymany, umieść kursor nad instrukcją `return c2` do momentu, gdy zostanie wyświetlony **![przycisk "** Uruchom](../debugger/media/dbg-tour-run-to-click.png) do" w celu kliknięcia przyciskiem myszy, a następnie naciśnij przycisk **Uruchom do kliknięcia** .

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikacja kontynuuje wykonywanie i zatrzymuje się w wierszu kodu, w którym kliknięto przycisk.

Typowe polecenia klawiatury używane do przechodzenia przez kod obejmują **F10** i **F11**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspekcja zmiennych w etykietki danych

1. W bieżącym wierszu kodu (oznaczonym przez żółty wskaźnik wykonania) Umieść wskaźnik myszy nad obiektem `c2`, aby wyświetlić etykietki danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Etykietki danych pokazuje bieżącą wartość zmiennej `c2` i pozwala na kontrolowanie jej właściwości. W przypadku debugowania, Jeśli zobaczysz nieoczekiwaną wartość, prawdopodobnie masz usterkę w powyższym lub wywoływanym wierszu kodu.

2. Rozwiń etykietki danych, aby sprawdzić bieżącą wartość właściwości obiektu `c2`.

3. Jeśli chcesz przypiąć etykietki danych, tak aby można było nadal zobaczyć wartość `c2` podczas wykonywania kodu, kliknij ikonę małego numeru PIN. (Można przenieść przypiętą etykietki danych do wygodnej lokalizacji).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Jeśli określisz zmianę, która ma zostać przetestowana w kodzie w trakcie sesji debugowania, możesz to zrobić.

1. W metodzie `OnGet` kliknij drugie wystąpienie `result.First.Value` i Zmień `result.First.Value` na `result.Last.Value`.

1. Naciśnij klawisz **F10** (lub **Debuguj > Krok powyżej**) kilka razy, aby przejść do debugera i wykonać edytowany kod.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Edytowanie i kontynuowanie")

    **F10** zastąpi debuger jedną instrukcją w tym samym czasie, ale nie trzeba przechodzić do tych funkcji, zamiast przechodzić do nich (kod, który pominie nadal wykonywany).

Aby uzyskać więcej informacji na temat używania funkcji Edit-and-Continue i on Features, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
