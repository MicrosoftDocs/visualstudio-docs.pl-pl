---
title: Debugowanie C++
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
ms.openlocfilehash: 7bcf2c97e26e61b72a1279a11e8c95474099c3d6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918567"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Szybki start: Debugowanie przy użyciu języka C++, za pomocą debugera programu Visual Studio

Debuger programu Visual Studio zapewnia wiele zaawansowanych funkcji, aby pomóc w debugowaniu aplikacji. Ten temat zapewnia szybki sposób, aby dowiedzieć się, niektóre z podstawowych funkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

2. W obszarze **Visual C++**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **aplikacji konsoli Windows**.

    Jeśli nie widzisz **aplikacji konsoli Windows** szablonu projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie aplikacji klasycznych w języku C++** obciążenia, wybierz **Modyfikuj**.

3. Wpisz nazwę, takich jak **MyDbgApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

4. W MyDbgApp.cpp Zastąp poniższy kod

    ```c++
    int main()
    {
        return 0;
    }
    ```

    przy użyciu tego kodu (nie należy usuwać `#include "stdafx.h"`):

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

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

A *punktu przerwania* jest znacznik, który wskazuje, gdzie program Visual Studio należy wstrzymać działającego kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy nie jest wprowadzenie uruchamiane gałęzi kodu. Jest najbardziej podstawowa funkcja podczas debugowania.

1. Aby ustawić punkt przerwania, kliknij na marginesie po lewej stronie `doWork` wywołania funkcji (lub wybierz linii kodu i naciśnij klawisz **F9**).

    ![Ustaw punkt przerwania](../debugger/media/dbg-qs-set-breakpoint.png "Ustaw punkt przerwania")

2. Teraz naciśnij **F5** (lub wybierz **Debuguj > Rozpocznij debugowanie**).

    ![Trafiony punkt przerwania](../debugger/media/dbg-qs-hit-breakpoint.png "trafia w punkt przerwania")

    Wstrzymuje działanie debugera, gdzie ustawić punkt przerwania. Żółta strzałka wskazuje instrukcji, w której zostało wstrzymane wykonanie debugera i aplikacji. Wiersz z `doWork` wywołanie funkcji nie zostało jeszcze wykonane.

    > [!TIP]
    > Jeśli punkt przerwania w pętli lub rekursji, lub jeśli masz wiele punktów przerwania, które często krokach, użyj [warunkowego punktu przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) aby upewnić się, że Twój kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. Warunkowego punktu przerwania pozwala zaoszczędzić czas i może również ułatwić debugowanie problemów, które są trudne do odtworzenia.

    Podczas próby debugowania błędy związane z pamięcią w języku C++, umożliwia także punktów przerwania można sprawdzić wartości adresów (Zwróć uwagę na wartość NULL) i odwoływać się do liczby. 

## <a name="navigate-code"></a>Przechodzenie do kodu

Ma innego polecenia, aby wydać polecenie debugera, aby kontynuować. Przedstawiono polecenia nawigacji przydatne kodu, co nowego w programie Visual Studio 2017.

Podczas wstrzymania w punkcie przerwania, umieść kursor nad instrukcji `c1.push_back(20)` aż zielony **Uruchom do kliknięcia** przycisk ![uruchamianie do kliknięcia](../debugger/media/dbg-tour-run-to-click.png "RunToClick") pojawia się, a następnie naciśnij klawisz **Uruchom do kliknięcia** przycisku.

![Uruchom do kliknięcia](../debugger/media/dbg-qs-run-to-click.png "Uruchom do kliknięcia")

Aplikacja kontynuuje wykonywanie, wywołanie `doWork`i zatrzymuje się w wierszu kodu, gdy kliknięto przycisk.

Typowe polecenia klawiatury używane do obejmują Przechodź przez kod **F10** i **F11**. Aby uzyskać więcej szczegółowych instrukcji, zobacz [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Sprawdzanie zmiennych w datatip

1. W bieżącym wierszu kodu (oznaczonych przez wskaźnik wykonania żółty), umieść kursor nad `c1` obiektu myszą, aby pokazać poradzie dotyczącej danych.

    ![Wyświetl etykietki danych](../debugger/media/dbg-qs-data-tip.png "wyświetlanie etykietki danych")

    Datatip pokazuje bieżącą wartość `c1` zmiennej i umożliwia inspekcję jego właściwości. Podczas debugowania, jeśli zostanie wyświetlony wartości, który nie powinien, prawdopodobnie masz usterkę w poprzednim lub wywoływania wierszy kodu. 

2. Rozwiń etykietka danych, aby wyświetlić bieżące wartości właściwości `c1` obiektu.

3. Jeśli chcesz przypiąć datatip, dzięki czemu możesz zobaczyć wartość `c1` podczas wykonywania kodu, kliknij ikonę pinezki małe. (W dogodnym miejscu może przechodzić przypiętych etykietki danych).

## <a name="edit-code-and-continue-debugging"></a>Edytowanie kodu i kontynuowanie debugowania

Po zidentyfikowaniu zmianę, która ma zostać przetestowana w kodzie, gdy w trakcie sesji debugowania, możesz to zrobić, zbyt.

1. Kliknij pozycję drugiego wystąpienia `c2.front()` i zmień `c2.front()` do `c2.back()`.

2. Naciśnij klawisz **F10** (lub **Debuguj > Step Over**) kilka razy, aby poszerzyć debugera i wykonywanie edycji kodu.

    ![Edytuj i Kontynuuj](../debugger/media/dbg-qs-edit-and-continue.gif "Edytuj i Kontynuuj")

    **F10** prowadzi instrukcja debugger jeden w danym momencie, ale kroki za pośrednictwem funkcji zamiast przechodzenie krok po kroku do nich (nadal wykonuje kod, który zostanie pominięta).

Aby uzyskać więcej informacji na temat korzystania z edit-and-continue i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób uruchamiania debugera, Przechodź przez kod i Sprawdź zmienne. Możesz chcieć wysokiego poziomu poznać funkcje debugera, wraz z linkami do dodatkowych informacji.

> [!div class="nextstepaction"]
> [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
