---
title: Debugowanie projektów platformy ASP.NET
description: Debugowanie aplikacji ASP.NET przy użyciu debugera programu Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 82288b67916255914d352e4f0f6f2fd75aa9571d
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561960"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Szybki start: Debugowanie projektów platformy ASP.NET za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**.

1. Wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.

1. W oknie dialogowym wybierz **aplikacji sieci Web** w środkowym okienku, a następnie kliknij przycisk **OK**.

     Jeśli nie widzisz **aplikacji sieci Web** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **ASP.NET i tworzenie aplikacji internetowych** obciążenia, wybierz **Modyfikuj**.

    ![Wybierz aplikację sieci Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Program Visual Studio tworzy projekt.

1. W Eksploratorze rozwiązań Otwórz About.cshtml.cs (w obszarze Pages/About.cshtml), a następnie zastąp następujący kod

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

A *punktu przerwania* jest znacznik, który wskazuje, gdzie program Visual Studio należy wstrzymać działającego kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy nie jest wprowadzenie uruchamiane gałęzi kodu. Jest najbardziej podstawowa funkcja podczas debugowania.

1. Aby ustawić punkt przerwania, kliknij na marginesie po lewej stronie `doWork` — funkcja (lub wybierz linii kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Punkt przerwania jest ustawiony do lewego nawiasu otwierającego (`{`).

1. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

1. Podczas ładowania strony sieci web, kliknij przycisk **o** link u góry strony sieci web.

    Wstrzymuje działanie debugera, gdzie ustawić punkt przerwania. Żółta strzałka wskazuje instrukcji, w której zostało wstrzymane wykonanie debugera i aplikacji. Wiersz z otwierający nawias klamrowy (`{`) po `doWork` deklaracji funkcji nie zostało jeszcze wykonane.

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Jeśli punkt przerwania w pętli lub rekursji, lub jeśli masz wiele punktów przerwania, które często krokach, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że Twój kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. To pozwala zaoszczędzić czas i może również ułatwić debugowanie problemów, które są trudne do odtworzenia.

## <a name="navigate-code"></a>Przechodzenie do kodu

Ma innego polecenia, aby wydać polecenie debugera, aby kontynuować. Przedstawiono polecenia nawigacji przydatne kodu, co nowego w programie Visual Studio 2017.

Podczas wstrzymania w punkcie przerwania, umieść kursor nad instrukcji `return c2` aż zielony **Uruchom do kliknięcia** przycisk ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png) pojawia się, a następnie naciśnij klawisz **Uruchom do kliknięcia** przycisk.

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikacja kontynuuje wykonywanie i wstrzymuje w wierszu kodu, gdy kliknięto przycisk.

Typowe polecenia klawiatury używane do obejmują Przechodź przez kod **F10** i **F11**. Aby uzyskać więcej szczegółowych instrukcji, zobacz [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdzanie zmiennych w datatip

1. W bieżącym wierszu kodu (oznaczonych przez wskaźnik wykonania żółty), umieść kursor nad `c2` obiektu myszą, aby pokazać poradzie dotyczącej danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Datatip pokazuje bieżącą wartość `c2` zmiennej i umożliwia inspekcję jego właściwości. Podczas debugowania, jeśli zostanie wyświetlony wartości, który nie powinien, prawdopodobnie masz usterkę w poprzednim lub wywoływania wierszy kodu. 

2. Rozwiń etykietka danych, aby wyświetlić bieżące wartości właściwości `c2` obiektu.

3. Jeśli chcesz przypiąć datatip, dzięki czemu możesz zobaczyć wartość `c2` podczas wykonywania kodu, kliknij ikonę pinezki małe. (W dogodnym miejscu może przechodzić przypiętych etykietki danych).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Po zidentyfikowaniu zmianę, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, zbyt.

1. W `OnGet` metody, kliknij pozycję drugiego wystąpienia `result.First.Value` i zmień `result.First.Value` do `result.Last.Value`.

1. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poszerzyć debugera i wykonywanie edycji kodu.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Edytuj i Kontynuuj")

    **F10** prowadzi instrukcja debugger jeden w danym momencie, ale kroki za pośrednictwem funkcji zamiast przechodzenie krok po kroku do nich (nadal wykonuje kod, który zostanie pominięta).

Aby uzyskać więcej informacji na temat korzystania z edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
