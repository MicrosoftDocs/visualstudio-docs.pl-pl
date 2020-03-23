---
title: Debugowanie ASP.NET rdzenia
description: Debugowanie ASP.NET Core przy użyciu debugera programu Visual Studio
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75847873"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Szybki start: Debugowanie ASP.NET rdzenia za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zawiera wiele zaawansowanych funkcji ułatwiające debugowanie aplikacji. W tym temacie przedstawiono szybki sposób, aby dowiedzieć się niektóre z podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **asp.net**, wybierz **pozycję Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET podstawową aplikację sieci Web**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C#** wybierz pozycję **Sieć Web**, a następnie w środkowym okienku wybierz pozycję ASP.NET Core **Web Application**. Wpisz nazwę taką jak **MyDbgApp** i kliknij **przycisk OK**.

    W wyświetlonym oknie dialogowym wybierz pozycję **Aplikacja sieci Web** w środkowym okienku, a następnie kliknij przycisk **OK**.

    ![Wybieranie aplikacji sieci Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **ASP.NET Core Web Application,** przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

    Visual Studio tworzy projekt.

1. W Eksploratorze rozwiązań otwórz About.cshtml.cs (w obszarze Strony/Informacje.cshtml) i zastąp następujący kod

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    z tym kodem:

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

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

*Punkt przerwania* jest znacznik, który wskazuje, gdzie Visual Studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany. Jest to najbardziej podstawowa funkcja w debugowaniu.

1. Aby ustawić punkt przerwania, kliknij w marginesie `doWork` funkcji (lub wybierz wiersz kodu i naciśnij **klawisz F9**).

    ![Ustawianie punktu przerwania](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Punkt przerwania jest ustawiony po lewej stronie`{`nawiasu klamrowego otwierającego ( ).

1. Teraz naciśnij **klawisz F5** (lub wybierz **debugowanie > rozpocznij debugowanie).**

1. Po załadowaniu strony internetowej kliknij łącze **Informacje** u góry strony sieci Web.

    Debuger wstrzymuje miejsce ustawiania punktu przerwania. Instrukcja, w której debuger i wykonanie aplikacji jest wstrzymana, jest wskazywana przez żółtą strzałkę. Wiersz z nawiasem klamry otwarcia (`{`) po deklaracji `doWork` funkcji nie została jeszcze wykonana.

    ![Trafienie w punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często krok po kroku, należy użyć [warunkowego punktu przerwania,](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że kod jest zawieszony TYLKO po spełnieniu określonych warunków. Pozwala to zaoszczędzić czas i może również ułatwić debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Nawigowanie po kodzie

Istnieją różne polecenia, aby poinstruować debugera, aby kontynuować. Pokazujemy przydatne polecenie nawigacji kodu, które jest dostępne począwszy od programu Visual Studio 2017.

Po wstrzymaniu w punkcie przerwania `return c2` umieść wskaźnik myszy na ![instrukcji,](../debugger/media/dbg-tour-run-to-click.png) aż pojawi się zielony **przycisk Uruchom, aby kliknąć** przycisk Uruchom, aby kliknąć, a następnie naciśnij przycisk **Uruchom, aby kliknąć.**

![Uruchom, aby kliknąć](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikacja kontynuuje wykonywanie i wstrzymuje w wierszu kodu, w którym kliknięno przycisk.

Typowe polecenia klawiatury używane do przechodzenia przez kod obejmują **F10** i **F11**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdzanie zmiennych w etykietce danych

1. W bieżącym wierszu kodu (oznaczone żółtym wskaźnikiem `c2` wykonania) umieść wskaźnik myszy nad obiektem, aby wyświetlić etykietkę danych.

    ![Wyświetlanie etykietki danych](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Porada data zawiera bieżącą `c2` wartość zmiennej i umożliwia sprawdzenie jej właściwości. Podczas debugowania, jeśli widzisz wartość, której się nie spodziewasz, prawdopodobnie masz błąd w poprzednich lub wywołujących wierszy kodu.

2. Rozwiń poradę danych, aby przyjrzeć `c2` się bieżącym wartościom właściwości obiektu.

3. Jeśli chcesz przypiąć etykietkę danych, aby nadal `c2` widzieć wartość podczas wykonywania kodu, kliknij ikonę małego pinezki. (Etykietka przypiętych danych jest ów komfortowa).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Jeśli zidentyfikujesz zmianę, którą chcesz przetestować w kodzie, podczas gdy w środku sesji debugowania, można to zrobić, zbyt.

1. W `OnGet` metodzie kliknij drugie `result.First.Value` wystąpienie `result.First.Value` `result.Last.Value`i zmień na .

1. Naciśnij kilka razy **klawisz F10** (lub **Debug > Step Over),** aby przejść do debugera i wykonać edytowany kod.

    ![Edytowanie i kontynuowanie](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Edytowanie i kontynuowanie")

    **F10** zaliczki debugera jedną instrukcję naraz, ale kroki nad funkcjami zamiast przechodzenia do nich (kod, który pominąć nadal wykonuje).

Aby uzyskać więcej informacji na temat korzystania z funkcji i ograniczeń funkcji, zobacz [Edytowanie i kontynuowanie](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, krok po kroku kodu i sprawdzić zmienne. Możesz chcieć uzyskać spojrzenie wysokiego poziomu na funkcje debugera wraz z łączami do większej ilości informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
