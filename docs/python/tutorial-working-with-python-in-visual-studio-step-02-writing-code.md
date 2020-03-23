---
title: Python w programie Visual Studio samouczek krok 2, zapis i uruchamianie kodu
titleSuffix: ''
description: Krok 2 podstawowego przewodnika możliwości języka Python w programie Visual Studio, w tym edytowania kodu i uruchamiania projektu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fda68b9e5bffbd1afab3389a0d8d624312a8de3f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430073"
---
# <a name="step-2-write-and-run-code"></a>Krok 2: Napisz i uruchom kod

**Poprzedni krok: [Tworzenie nowego projektu języka Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Chociaż **Eksplorator rozwiązań** jest, gdzie można zarządzać plikami projektu, okno *edytora* jest zazwyczaj, gdzie pracujesz z *zawartością* plików, takich jak kod źródłowy. Edytor jest kontekstowo świadomy typu edytowanego pliku, w tym języka programowania (opartego na rozszerzeniu pliku) i oferuje funkcje odpowiednie dla tego języka, takie jak kolorowanie składni i automatyczne uzupełnianie za pomocą programu IntelliSense.

1. Po utworzeniu nowego projektu "Aplikacja języka Python" domyślny pusty plik o nazwie *PythonApplication1.py* jest otwarty w edytorze programu Visual Studio.

1. W edytorze zacznij `print("Hello, Visual Studio")` wpisywać i zwróć uwagę, jak program Visual Studio IntelliSense wyświetla opcje automatycznego uzupełniania po drodze. Opisana opcja na liście rozwijanej jest domyślnym zakończeniem, które jest używane po naciśnięciu **klawisza Tab.** Uzupełnienia są najbardziej pomocne, gdy są zaangażowane dłuższe instrukcje lub identyfikatory.

    ![Wyskakujące okienko automatycznego uzupełniania IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense pokazuje różne informacje w zależności od instrukcji, której używasz, funkcji, którą wywołujesz i tak dalej. Za `print` pomocą funkcji `(` wpisując po, `print` aby wskazać wywołanie funkcji wyświetla pełne informacje o użyciu dla tej funkcji. Pop-up IntelliSense pokazuje również bieżący argument pogrubioną czcionką **(wartość,** jak pokazano tutaj):

    ![Wyskakujące okienko intellisense dla funkcji](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Uzupełnij instrukcję tak, aby była zgodna z następującymi zasadami:

    ```python
    print("Hello, Visual Studio")
    ```

1. Zwróć uwagę na zabarwienie składni, które odróżnia instrukcję `print` od argumentu `"Hello Visual Studio"`. Ponadto tymczasowo usunąć ostatni `"` na ciąg i zauważyć, jak Visual Studio pokazuje czerwone podkreślenie dla kodu, który zawiera błędy składni. Następnie wymień, `"` aby poprawić kod.

    ![Kolorowanie składni IntelliSense i wyróżnianie błędów](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Ponieważ środowisko programistyczne jest bardzo osobistą sprawą, visual studio daje pełną kontrolę nad wyglądem i zachowaniem programu Visual Studio. Wybierz polecenie menu **Opcje narzędzi** > **Options** i zapoznaj się z ustawieniami na kartach **Środowisko** i **Edytor tekstu.** Domyślnie widzisz tylko ograniczoną liczbę opcji; aby wyświetlić każdą opcję dla każdego języka programowania, wybierz pozycję **Pokaż wszystkie ustawienia** u dołu okna dialogowego.

1. Uruchom kod, który został zapisany w tym punkcie, naciskając **klawisz Ctrl**+**F5** lub wybierając pozycję menu **Debugowania** > **start bez debugowania.** Visual Studio ostrzega, jeśli nadal masz błędy w kodzie.

1. Po uruchomieniu programu pojawi się okno konsoli wyświetlające wyniki, tak jakby można było uruchomić interpreter języka Python z *PythonApplication1.py* z wiersza polecenia. Naciśnij klawisz, aby zamknąć okno i powrócić do edytora programu Visual Studio.

    ![Dane wyjściowe pierwszego uruchomienia programu](media/vs-getting-started-python-07-output.png)

1. Oprócz uzupełnień dla instrukcji i funkcji IntelliSense zapewniają `import` `from` uzupełnienia dla języka Python i instrukcji. Te uzupełnienia ułatwiają odnajdywanie, jakie moduły są dostępne w twoim środowisku i członków tych modułów. W edytorze usuń `print` wiersz i `import`zacznij wpisywać tekst . Po wpisaniu spacji pojawi się lista modułów:

    ![IntellSense pokazuje dostępne moduły dla instrukcji importu](media/vs-getting-started-python-08-import1.png)

1. Uzupełnij wiersz, wpisując `sys`lub wybierając .

1. W następnym wierszu `from` wpisz ponownie listę modułów:

    ![IntellSense pokazuje dostępne moduły dla a z instrukcji](media/vs-getting-started-python-09-import2.png)

1. Wybierz lub `math`wpisz , a następnie `import`kontynuuj wpisywanie spacji i , która wyświetla elementy modułu:

    ![IntellSense pokazuje elementy modułu](media/vs-getting-started-python-10-import3.png)

1. Zakończ, importując `sin` `cos`program `radians` , i elementy członkowskie, zauważając automatyczne uzupełnianie dostępne dla każdego z nich. Po zakończeniu kod powinien być wyświetlany w następujący sposób:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Uzupełnienia działają z podciągami podczas pisania, dopasowywanie części słów, liter na początku wyrazów, a nawet pomijane znaki. Zobacz [Edytowanie kodu — uzupełnianie, aby](editing-python-code-in-visual-studio.md#completions) uzyskać szczegółowe informacje.

1. Dodaj trochę więcej kodu, aby wydrukować wartości cosine dla 360 stopni:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Uruchom program ponownie za pomocą **Ctrl**+**F5** lub **Debug** > **Start bez debugowania**. Zamknij okno wyjściowe po zakończeniu.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Korzystanie z interaktywnego okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Głębiej

- [Edytuj kod](editing-python-code-in-visual-studio.md)
- [Formatowanie kodu](formatting-python-code.md)
- [Kod refaktoryzatora](refactoring-python-code.md)
- [Korzystanie z narzędzia PyLint](linting-python-code.md)
