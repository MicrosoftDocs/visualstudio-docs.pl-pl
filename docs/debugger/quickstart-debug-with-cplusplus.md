---
title: Debuguj C++
description: Debugowanie kodu natywnego za pomocą debugera programu Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b619b2b6c93da8be399b2fc35d81ffe226f408ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679414"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Szybki Start: debugowanie przy użyciu języka C++ za pomocą debugera programu Visual Studio

Debuger programu Visual Studio udostępnia wiele zaawansowanych funkcji ułatwiających debugowanie aplikacji. Ten temat zawiera szybki sposób poznania niektórych podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Otwórz program Visual Studio i Utwórz projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz c++**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nowy projekt aplikacji konsolowej**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual C++** wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **Aplikacja konsolowa systemu Windows**. Następnie wpisz nazwę, na przykład **MyDbgApp** , i kliknij przycisk **OK**.
    ::: moniker-end

    Jeśli szablon projektu **aplikacji konsolowej systemu Windows** nie jest widoczny, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje...**, co spowoduje otwarcie Instalator programu Visual Studio. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz pozycję **Programowanie aplikacji klasycznych w języku C++** , a następnie wybierz polecenie **Modyfikuj**.

    Program Visual Studio tworzy projekt.

1. W MyDbgApp. cpp Zastąp następujący kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    za pomocą tego kodu (nie usuwaj `#include "stdafx.h"` ):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

*Punkt przerwania* jest znacznikiem wskazującym, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana. Jest to najbardziej podstawowa funkcja debugowania.

1. Aby ustawić punkt przerwania, kliknij na odstępie po lewej stronie `doWork` wywołania funkcji (lub zaznacz wiersz kodu i naciśnij klawisz **F9**).

    ![Ustawianie punktu przerwania](../debugger/media/dbg-qs-set-breakpoint.png "Ustawianie punktu przerwania")

2. Teraz naciśnij klawisz **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafienie punktu przerwania](../debugger/media/dbg-qs-hit-breakpoint.png "Trafienie punktu przerwania")

    Debuger wstrzymuje miejsce, w którym ustawiono punkt przerwania. Instrukcja, w której debuger i wykonywanie aplikacji jest wstrzymana, jest wskazywana przez żółtą strzałkę. Wiersz z `doWork` wywołaniem funkcji nie został jeszcze wykonany.

    > [!TIP]
    > Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które są często wykonywane, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) , aby upewnić się, że kod jest zawieszony tylko wtedy, gdy spełnione są określone warunki. Warunkowy punkt przerwania oszczędza czas i może ułatwić Debugowanie problemów, które trudno odtworzyć.

    Podczas próby debugowania błędów związanych z pamięcią w języku C++ można także użyć punktów przerwania do sprawdzenia wartości adresu (Wyszukaj wartość NULL) i liczby odwołań.

## <a name="navigate-code"></a>Nawiguj po kodzie

Istnieją różne polecenia, aby polecić debugerowi kontynuowanie. Wyświetlamy przydatne polecenie nawigacji kodu, które jest dostępne w programie Visual Studio 2017.

Gdy punkt przerwania jest wstrzymany, umieść kursor nad instrukcją `c1.push_back(20)` do momentu wyświetlenia zielonego przycisku **Uruchom** ![do](../debugger/media/dbg-tour-run-to-click.png "RunToClick") kliknięcia, a następnie naciśnij przycisk **Uruchom do** kliknięcia.

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click.png "Uruchom do kliknięcia")

Aplikacja kontynuuje wykonywanie, wywoływanie `doWork` i wstrzymuje w wierszu kodu, w którym został kliknięty przycisk.

Typowe polecenia klawiatury używane do przechodzenia przez kod obejmują **F10** i **F11**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Inspekcja zmiennych w etykietki danych

1. W bieżącym wierszu kodu (oznaczonym przez żółty wskaźnik wykonania) Umieść wskaźnik `c1` myszy nad obiektem, aby wyświetlić etykietki danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip.png "Wyświetl etykietki danych")

    Etykietki danych pokazuje bieżącą wartość `c1` zmiennej i pozwala na kontrolowanie jej właściwości. W przypadku debugowania, Jeśli zobaczysz nieoczekiwaną wartość, prawdopodobnie masz usterkę w powyższym lub wywoływanym wierszu kodu.

2. Rozwiń etykietki danych, aby sprawdzić bieżącą wartość właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć etykietki danych, tak aby można było nadal zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę małego numeru PIN. (Można przenieść przypiętą etykietki danych do wygodnej lokalizacji).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Jeśli określisz zmianę, która ma zostać przetestowana w kodzie w trakcie sesji debugowania, możesz to zrobić.

1. Kliknij drugie wystąpienie `c2.front()` i przejdź `c2.front()` do `c2.back()` .

2. Naciśnij klawisz **F10** (lub **Debuguj > krok powyżej**) kilka razy, aby przejść do debugera i wykonać edytowany kod.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue.gif "Edytowanie i kontynuowanie")

    **F10** zastąpi debuger jedną instrukcją w tym samym czasie, ale nie trzeba przechodzić do tych funkcji, zamiast przechodzić do nich (kod, który pominie nadal wykonywany).

Aby uzyskać więcej informacji na temat używania funkcji Edit-and-Continue i on Features, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku dowiesz się, jak uruchomić debuger, przewinąć kod i zbadać zmienne. Możesz chcieć uzyskać ogólne omówienie funkcji debugera oraz linki do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
