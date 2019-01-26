---
title: Język Python w programie Visual Studio — samouczek krok 2, pisania i uruchamiania kodu
titleSuffix: ''
description: Krok 2 przewodnika podstawowe funkcje języka Python w programie Visual Studio, w tym edytowanie kodu i uruchamianie projektu.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a378efd38a4ccd415276cb1a10f24ff39600894f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988678"
---
# <a name="step-2-write-and-run-code"></a>Krok 2. Pisanie i uruchamianie kodu

**Poprzedniego kroku: [Utwórz nowy projekt języka Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Mimo że **Eksploratora rozwiązań** zarządzają pliki projektu *edytora* okna zazwyczaj jest miejscem służącym do pracy z *zawartość* plików, takich jak kod źródłowy. Edytor jest kontekstowych typu pliku edycji, w tym języku (na podstawie rozszerzenia pliku) i oferuje funkcje odpowiednie dla danego języka, takich jak kolorowanie składni i automatycznego uzupełniania za pomocą funkcji IntelliSense.

1. Po utworzeniu nowego projektu "Aplikacja języka Python" domyślny pusty plik o nazwie *PythonApplication1.py* jest otwarty w edytorze programu Visual Studio.

1. W edytorze, zacznij pisać `print("Hello, Visual Studio")` i zwróć uwagę, jak Visual Studio technologia IntelliSense wyświetla opcje automatycznego uzupełniania po drodze. Schemat opcję na liście rozwijanej jest ukończenie domyślne, używany, gdy użytkownik naciśnie klawisz **kartę** klucza. Uzupełnianie są najbardziej przydatne w przypadku dłużej instrukcji lub identyfikatorów.

    ![Okno podręczne z automatycznego uzupełniania IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. Funkcja IntelliSense wyświetla różne informacje w zależności od tego, czy oświadczenie, którego używasz, funkcji, które w przypadku wywoływania i tak dalej. Za pomocą `print` funkcji, wpisując `(` po `print` do wskazania funkcję wywołania Wyświetla informacje o użyciu pełnego dla tej funkcji. Wyskakujące okienko IntelliSense pokazuje również bieżącego argument pogrubioną czcionką (**wartość** jak pokazano poniżej):

    ![Okno podręczne z automatycznego uzupełniania IntelliSense dla funkcji](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Wykonaj instrukcję tak, aby odpowiadała następujące czynności:

    ```python
    print("Hello, Visual Studio")
    ```

1. Zwróć uwagę, barwienia składni, która odróżnia instrukcji `print` w argumencie `"Hello Visual Studio"`. Ponadto tymczasowo usunąć ostatni `"` na ciąg i zwróć uwagę, jak Visual Studio Wyświetla czerwoną linią dla kodu, zawiera błędy składni. Następnie zastąp `"` aby poprawić kod.

    ![Kolorowanie składni IntelliSense i funkcji wyróżniania błędów](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Ponieważ w jednym środowisku programistycznym jest bardzo osobistych kwestią, Visual Studio zapewnia pełną kontrolę nad wygląd i zachowanie programu Visual Studio. Wybierz **narzędzia** > **opcje** menu poleceń i zapoznaj się z ustawieniami w obszarze **środowiska** i **edytora tekstów** karty. Domyślnie zostanie wyświetlony tylko ograniczoną liczbę opcji; Aby wyświetlić każdej opcji dla każdego języka programowania, wybierz **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego.

1. Uruchamianie kodu napisanych do tego punktu, naciskając klawisz **Ctrl**+**F5** lub wybierając **debugowania** > **Uruchom bez debugowania**  elementu menu. Program Visual Studio wyświetli ostrzeżenie, jeśli nadal występują błędy w kodzie.

1. Po uruchomieniu programu, zostanie wyświetlone okno konsoli, za pomocą wyświetlania wyników, tak, jakby należy uruchomić następujące polecenie interpreter języka Python za pomocą *PythonApplication1.py* z wiersza polecenia. Naciśnij dowolny klawisz, aby zamknąć okno i powrócić do edytora programu Visual Studio.

    ![Dane wyjściowe dla pierwszego uruchomienia programu](media/vs-getting-started-python-07-output.png)

1. Oprócz uzupełniania instrukcji i funkcji, funkcji IntelliSense zapewniają uzupełnienia dla języka Python `import` i `from` instrukcji. Te uzupełnienia pomóc łatwo wykryć, które moduły są dostępne w Twoim środowisku oraz elementów członkowskich tych modułów. W edytorze, Usuń `print` wiersza, a następnie zacznij pisać `import `. Podczas wpisywania tekstu miejsca, zostanie wyświetlona lista modułów:

    ![Wyświetlanie dostępnych modułów dla instrukcji importowania IntellSense](media/vs-getting-started-python-08-import1.png)

1. Zakończ wiersz, wpisując lub wybierając `sys`.

1. W następnym wierszu, wpisz `from` Aby ponownie wyświetlić listę modułów:

    ![IntellSense przedstawiający dostępnych modułów dla instrukcji](media/vs-getting-started-python-09-import2.png)

1. Wybierz lub wpisz `math`, pracując ze spacją i `import`, który zawiera elementy członkowskie modułu:

    ![Elementy członkowskie modułu przedstawiający IntellSense](media/vs-getting-started-python-10-import3.png)

1. Zakończ importując `sin`, `cos`, i `radians` członków, obserwowanie automatyczne uzupełnianie dostępne dla każdego. Gdy skończysz, Twój kod powinien wyglądać następująco:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Uzupełnianie pracować podciągów pisania, dopasowanie części wyrazów, litery na początku słowa, a nawet pominięte znaków. Zobacz [edytowania kodu - uzupełnienia](editing-python-code-in-visual-studio.md#completions) Aby uzyskać szczegółowe informacje.

1. Dodaj nieco więcej kodu, aby wydrukować wartości funkcji cosinus dla 360 stopni:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Uruchom program ponownie, używając **Ctrl**+**F5** lub **debugowania** > **Uruchom bez debugowania**. Zamknij okno danych wyjściowych, gdy wszystko będzie gotowe.

## <a name="next-step"></a>Następny krok

> [!div class="nextstepaction"]
> [Użycie okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Przejdź dalej

- [Edytowanie kodu](editing-python-code-in-visual-studio.md)
- [Formatowanie kodu](formatting-python-code.md)
- [Refaktoryzacja kodu](refactoring-python-code.md)
- [Użyj PyLint](linting-python-code.md)
