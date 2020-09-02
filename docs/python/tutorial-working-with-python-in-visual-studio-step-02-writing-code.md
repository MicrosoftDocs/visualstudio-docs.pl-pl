---
title: Samouczek Python w programie Visual Studio — krok 2, pisanie i uruchamianie kodu
titleSuffix: ''
description: Krok 2 podstawowe Przewodnik po możliwościach języka Python w programie Visual Studio, w tym edytowanie kodu i uruchamianie projektu.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430073"
---
# <a name="step-2-write-and-run-code"></a>Krok 2. Pisanie i uruchamianie kodu

**Poprzedni krok: [Tworzenie nowego projektu w języku Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Mimo że **Eksplorator rozwiązań** jest miejscem zarządzania plikami projektu, okno *edytora* jest zwykle miejscem, w którym pracujesz z *zawartością* plików, takimi jak kod źródłowy. Edytor jest kontekstowy dla typu edytowanego pliku, w tym języka programowania (na podstawie rozszerzenia pliku) i oferuje funkcje odpowiednie dla tego języka, takie jak kolorowanie składni i Autouzupełnianie przy użyciu technologii IntelliSense.

1. Po utworzeniu nowego projektu "aplikacja Python" w edytorze programu Visual Studio jest otwarty domyślny pusty plik o nazwie *PythonApplication1.py* .

1. W edytorze zacznij pisać `print("Hello, Visual Studio")` i Zauważ, jak funkcja IntelliSense programu Visual Studio Wyświetla opcje Autouzupełniania. Opcja z konspektu na liście rozwijanej jest domyślnym uzupełnianiem używanym podczas naciskania klawisza **Tab** . Uzupełniania są najbardziej przydatne, gdy występują dłuższe instrukcje lub identyfikatory.

    ![Menu podręczne uzupełniania funkcji IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. Technologia IntelliSense wyświetla różne informacje w zależności od używanej instrukcji, wywoływanej funkcji i tak dalej. Za pomocą `print` funkcji wpisz polecenie `(` , `print` Aby wskazać, że wywołanie funkcji wyświetla pełne informacje o użyciu dla tej funkcji. Funkcja IntelliSense wyświetla również bieżący argument pogrubiony (**wartość** , jak pokazano poniżej):

    ![Menu podręczne uzupełniania funkcji IntelliSense](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Ukończ instrukcję, aby była zgodna z następującymi:

    ```python
    print("Hello, Visual Studio")
    ```

1. Zwróć uwagę na zabarwienie składni, która odróżnia instrukcję `print` od argumentu `"Hello Visual Studio"` . Ponadto tymczasowo Usuń ostatni `"` ciąg i Zauważ, jak program Visual Studio Wyświetla czerwoną podkreślenie dla kodu, który zawiera błędy składni. Następnie zastąp ciąg, `"` Aby poprawić kod.

    ![Kolorowanie składni IntelliSense i wyróżnianie błędów](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Ponieważ środowisko programistyczne jest bardzo osobiste, program Visual Studio zapewnia pełną kontrolę nad wyglądem i zachowaniem programu Visual Studio. Wybierz **Tools**  >  polecenie menu**Opcje** narzędzia i sprawdź ustawienia w obszarze karty **środowisko** i **Edytor tekstu** . Domyślnie zobaczysz tylko ograniczoną liczbę opcji; Aby wyświetlić każdą opcję dla każdego języka programowania, wybierz pozycję **Pokaż wszystkie ustawienia** u dołu okna dialogowego.

1. Uruchom kod zapisany w tym punkcie, naciskając klawisz **Ctrl** + **F5** lub wybierając pozycję **Debuguj**  >  **Uruchom bez debugowania** elementu menu. Program Visual Studio wyświetli ostrzeżenie, jeśli nadal występują błędy w kodzie.

1. Po uruchomieniu programu zostanie wyświetlone okno konsoli z wynikami, podobnie jak w przypadku uruchamiania interpretera języka Python z *PythonApplication1.py* z wiersza polecenia. Naciśnij klawisz, aby zamknąć okno i powrócić do edytora programu Visual Studio.

    ![Dane wyjściowe pierwszego uruchomienia programu](media/vs-getting-started-python-07-output.png)

1. Oprócz uzupełniania instrukcji i funkcji technologia IntelliSense zapewnia uzupełnianie dla `import` języka Python i `from` instrukcji. Te uzupełniania pomagają w łatwym wykrywaniu modułów dostępnych w danym środowisku i elementach członkowskich tych modułów. W edytorze Usuń `print` wiersz i zacznij pisać `import` . Po wpisaniu miejsca zostanie wyświetlona lista modułów:

    ![IntellSense pokazujący dostępne moduły dla instrukcji import](media/vs-getting-started-python-08-import1.png)

1. Wypełnij wiersz, wpisując lub wybierając `sys` .

1. W następnym wierszu wpisz, `from` Aby ponownie wyświetlić listę modułów:

    ![IntellSense pokazujący dostępne moduły dla instrukcji from](media/vs-getting-started-python-09-import2.png)

1. Wybierz lub wpisz `math` , a następnie kontynuuj wpisywanie spacjami i `import` , które wyświetlają elementy członkowskie modułu:

    ![IntellSense pokazujący elementy członkowskie modułu](media/vs-getting-started-python-10-import3.png)

1. Zakończ, importując `sin` `cos` elementy członkowskie,, i `radians` obserwowanie, które są dostępne dla każdego z nich. Gdy skończysz, kod powinien wyglądać w następujący sposób:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Zakończenia pracy z podciągami podczas wpisywania, dopasowywania części wyrazów, liter na początku wyrazów, a nawet pominiętych znaków. Aby uzyskać szczegółowe informacje, zobacz [Edytowanie kodu — uzupełnianie](editing-python-code-in-visual-studio.md#completions) .

1. Dodaj nieco więcej kodu do drukowania wartości cosinusa dla 360 stopni:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Uruchom program ponownie, **naciskając klawisz Ctrl** + **F5** lub Rozpocznij **debugowanie**  >  **bez debugowania**. Po zakończeniu zamknij okno danych wyjściowych.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Przejdź głębiej

- [Edytuj kod](editing-python-code-in-visual-studio.md)
- [Formatowanie kodu](formatting-python-code.md)
- [Refaktoryzacja kodu](refactoring-python-code.md)
- [Korzystanie z narzędzia PyLint](linting-python-code.md)
