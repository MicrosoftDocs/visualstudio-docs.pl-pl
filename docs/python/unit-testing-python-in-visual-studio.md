---
title: Testy jednostkowe kodu w języku Python
description: Konfigurowanie testów jednostkowych dla kodu w języku Python w programie Visual Studio ma pełne wykorzystanie funkcji Eksploratora testów, aby odkryć, uruchamiania i debugowania testów.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e16612287d1efa76b206de50c6af9f18edab7c8a
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366136"
---
# <a name="set-up-unit-testing-for-python-code"></a>Konfigurowanie testów jednostkowych dla kodu w języku Python

Testy jednostkowe są fragmenty kodu, które testują inne jednostki kodu w aplikacji, zwykle izolowane funkcje, klasy i tak dalej. Gdy aplikacja przekazuje wszystkich testów jednostkowych, mogą co najmniej ufać, że jego niskiego poziomu funkcjonalności jest poprawna.

Python często używa testów jednostkowych do weryfikacji scenariuszy podczas projektowania programu. Obsługa języka Python w programie Visual Studio zawiera odnajdywanie, wykonywanie i debugowanie testów jednostkowych w kontekście swojego procesu programistycznego, bez konieczności uruchomić testy oddzielnie.

Ten artykuł zawiera krótkie konspektu testów jednostkowych funkcji w programie Visual Studio za pomocą języka Python. Aby uzyskać więcej informacji na ogół testów jednostkowych, zobacz [kodu testu jednostkowego](../test/unit-test-your-code.md).

## <a name="discover-and-view-tests"></a>Odnajdywanie i wyświetlić testy

Zgodnie z Konwencją, Visual Studio identyfikuje testów jako metody, których nazwy rozpoczynają się od `test`. Aby wyświetlić ten problem, wykonaj następujące czynności:

1. Otwórz [projektu w języku Python](managing-python-projects-in-visual-studio.md) załadowane w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj** > **nowy element**, a następnie wybierz **Test jednotky Pythonu**  następuje **Dodaj**.

1. Ta akcja powoduje utworzenie *test1.py* pliku z kodem, który importuje standard `unittest` modułu, pochodzi z klasy testowej `unittest.TestCase`i wywołuje `unittest.main()` Jeśli bezpośrednio uruchomić skrypt:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik, jeśli to konieczne, a następnie otwórz **Eksplorator testów** z **testu** > **Windows** > **Eksplorator testów**polecenia menu.

1. **Eksplorator testów** wyszukuje projektu dla testów, a następnie wyświetli je, jak pokazano poniżej. Dwukrotne kliknięcie testu spowoduje otwarcie pliku źródłowego.

    ![Test Explorer przedstawiający domyślną test_A](media/unit-test-A.png)

1. W miarę dodawania więcej testów do projektu, możesz organizować widoku w **Eksplorator testów** przy użyciu **Grupuj według** menu na pasku narzędzi:

    ![Grupy Eksploratora testów przez menu paska narzędzi](media/unit-test-group-menu.png)

1. Możesz też wprowadzić tekst w **wyszukiwania** pola do filtrowania testów według nazwy.

Aby uzyskać więcej informacji na temat `unittest` modułu i pisania testów, zobacz [dokumentacji języka Python 2.7](https://docs.python.org/2/library/unittest.html) lub [dokumentacji języka Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Uruchom testy

W **Eksplorator testów** można uruchomić testy na wiele sposobów:

- **Uruchom wszystkie** wyraźnie uruchamia wszystkie testy pokazano (zależnie od filtry).
- **Uruchom** menu zawiera polecenia, aby uruchomić testy zakończone niepowodzeniem, przekazany lub nie uruchomiono jako grupą.
- Można wybrać jeden lub więcej testów, kliknij prawym przyciskiem myszy, a następnie wybierz **Uruchom wybrane testy**.

Testy uruchamiania w tle i **Eksploratora testów** aktualizuje stan każdego testu w kończeniu:

- Przechodzenie testów przedstawiają zielony znacznik i czas trwania testu:

    ![test_A przekazywane stanu](media/unit-test-A-pass.png)

- Testy zakończone niepowodzeniem Pokaż czerwony krzyżyk z **dane wyjściowe** link, który pokazuje dane wyjściowe konsoli i `unittest` dane wyjściowe z przebiegu testu:

    ![Stan test_A nie powiodło się](media/unit-test-A-fail.png)

    ![nie powiodło się z powodu test_A](media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Debuguj testy

Ponieważ testy jednostkowe są fragmenty kodu, jest zależna od błędów, podobnie jak każdy inny kod, a od czasu do czasu należy uruchomić w debugerze. W debugerze można ustawić punktów przerwania, Sprawdź zmienne i przejść przez kod. Visual Studio udostępnia również narzędzia diagnostyczne dla testów jednostkowych.

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy test (lub zaznaczenie) **Eksploratora testów** i wybierz **Debuguj wybrane testy**. Program Visual Studio uruchamia debugera języka Python, jak dla kodu aplikacji.

![Profilowanie testu](media/unit-test-debugging.png)

Można również użyć **Analizuj pokrycie kodu dla wybrane testy** i **profilu testowego** poleceń.

### <a name="known-issues"></a>Znane problemy

- Podczas uruchamiania, debugowania, Visual Studio pojawia się, aby uruchomić i zatrzymać debugowanie, a następnie uruchom ponownie. To zachowanie jest oczekiwane.
- Podczas debugowania wielu testów, każdej z nich jest wykonywane niezależnie, który przerwania sesji debugowania.
- Program Visual Studio jest sporadycznie nie można uruchomić testu, podczas debugowania. Zwykle próbą debugowania test ponownie kończy się powodzeniem.
- Podczas debugowania, istnieje możliwość kroku poza testu do `unittest` implementacji. Normalnie następnym krokiem jest uruchamiany na końcu program i zatrzymuje debugowanie.
