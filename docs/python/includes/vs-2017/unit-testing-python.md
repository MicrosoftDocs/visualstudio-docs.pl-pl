---
title: Kod Pythona testu jednostkowego
description: Konfigurowanie testowania jednostkowego dla kodu języka Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdowania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9843b47e38d5d33a25c455efe619dfcc033fb334
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933454"
---
## <a name="discover-and-view-tests"></a>Odnajduj i wyświetlaj testy

Zgodnie z `test`konwencją program Visual Studio identyfikuje testy jako metody, których nazwy zaczynają się od . Aby wyświetlić to zachowanie, wykonaj następujące czynności:

1. Otwórz [projekt języka Python](../../managing-python-projects-in-visual-studio.md) załadowany w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj** > **nowy element,** a następnie wybierz pozycję **Python Unit Test,** a następnie **Dodaj**.

1. Ta akcja tworzy plik *test1.py* z kodem, `unittest` który importuje moduł `unittest.TestCase`standardowy, `unittest.main()` wyprowadza klasę testu z i wywołuje po uruchomieniu skryptu bezpośrednio:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie otwórz **Eksploratora testów** za pomocą polecenia menu **Test** > **Windows** > **Test Explorer.**

1. **Eksplorator testów** przeszukuje projekt w poszukiwaniu testów i wyświetla je w sposób pokazany poniżej. Dwukrotne kliknięcie testu powoduje otwarcie pliku źródłowego.

    ![Eksplorator testów z domyślną test_A](../../media/unit-test-A.png)

1. Podczas dodawania kolejnych testów do projektu można zorganizować widok w **Eksploratorze testów** za pomocą menu **Grupuj według** na pasku narzędzi:

    ![Menu Grupy eksploratora według paska narzędzi](../../media/unit-test-group-menu.png)

1. Tekst można również wprowadzać w polu **Wyszukiwanie,** aby filtrować testy według nazwy.

Aby uzyskać więcej `unittest` informacji na temat modułu i pisania testów, zobacz [dokumentację języka Python 2.7](https://docs.python.org/2/library/unittest.html) lub [dokumentację języka Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Uruchom testy

W **Eksploratorze testów** można uruchamiać testy na różne sposoby:

- **Uruchom wszystkie** wyraźnie uruchamia wszystkie pokazane testy (z zastrzeżeniem filtrów).
- Uruchom **Run** menu daje polecenia do uruchomienia nie powiodło się, przeszedł lub nie uruchomić testy jako grupa.
- Można wybrać jeden lub więcej testów, kliknąć prawym przyciskiem myszy i wybrać **polecenie Uruchom wybrane testy**.

Testy są uruchamiane w tle, a **Eksplorator testów** aktualizuje stan każdego testu po jego zakończeniu:

- Testy zdawające pokazują zielony znacznik i czas, który upływa do uruchomienia testu:

    ![test_A statusu](../../media/unit-test-A-pass.png)

- Testy nie powiodły się pokazują czerwony krzyżyk `unittest` z łączem **Wyjście,** które pokazuje dane wyjściowe i wyjściowe konsoli z przebiegu testu:

    ![test_A stan awarii](../../media/unit-test-A-fail.png)

    ![test_A nie powiodło się z powodu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Testy debugowania

Ponieważ testy jednostkowe są części kodu, podlegają one błędom, podobnie jak każdy inny kod i od czasu do czasu muszą być uruchamiane w debugerze. W debugerze można ustawić punkty przerwania, zbadać zmienne i krok po kroku kodu. Visual Studio udostępnia również narzędzia diagnostyczne dla testów jednostkowych.

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy test (lub zaznaczenie) w **Eksploratorze testów** i wybierz opcję **Debugowanie wybranych testów**. Visual Studio uruchamia debuger języka Python, tak jak w przypadku kodu aplikacji.

![Debugowanie testu](../../media/unit-test-debugging.png)

Można również użyć **analizy pokrycia kodu dla wybranych testów**. Aby uzyskać więcej informacji, zobacz [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Znane problemy

- Podczas uruchamiania debugowania visual studio wydaje się rozpocząć i zatrzymać debugowanie, a następnie uruchomić ponownie. Takie zachowanie jest oczekiwane.
- Podczas debugowania wielu testów, każdy z nich jest uruchamiany niezależnie, co przerywa sesji debugowania.
- Visual Studio sporadycznie nie można uruchomić test podczas debugowania. Zwykle próba debugowania testu powiedzie się.
- Podczas debugowania, jest możliwe, aby wyjść `unittest` z testu do implementacji. Zwykle następny krok jest uruchamiany do końca programu i zatrzymuje debugowanie.
