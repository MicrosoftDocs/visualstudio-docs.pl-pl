---
title: Kod języka Python testów jednostkowych
description: Skonfigurowanie testów jednostkowych dla kodu Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdywania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 032732f19855b9ba5c97c2e5281e8385f9ace3be
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535340"
---
## <a name="discover-and-view-tests"></a>Odnajdywanie i wyświetlanie testów

Zgodnie z Konwencją program Visual Studio identyfikuje testy jako metody, których nazwy zaczynają się od `test` . Aby zobaczyć to zachowanie, wykonaj następujące czynności:

1. Otwórz projekt w języku [Python](../../managing-python-projects-in-visual-studio.md) załadowany w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj**  >  **nowy element**, a następnie wybierz pozycję **test jednostkowy języka Python** , a następnie **Dodaj**.

1. Ta akcja tworzy plik *Test1.py* z kodem, który importuje `unittest` moduł standardowy, dziedziczy klasę testową z `unittest.TestCase` i wywołuje się, `unittest.main()` gdy skrypt jest uruchamiany bezpośrednio:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie otwórz **Eksploratora testów** z **Test**  >  **Windows**  >  poleceniem menu Testuj**Eksplorator** testów systemu Windows.

1. **Eksplorator testów** przeszukuje projekt pod kątem testów i wyświetla je, jak pokazano poniżej. Dwukrotne kliknięcie testu spowoduje otwarcie jego pliku źródłowego.

    ![Eksplorator testów z domyślną test_A](../../media/unit-test-A.png)

1. W miarę dodawania kolejnych testów do projektu można organizować widok w **Eksploratorze testów** przy użyciu menu **Grupuj według** na pasku narzędzi:

    ![Eksplorator testów Grupuj według menu paska narzędzi](../../media/unit-test-group-menu.png)

1. Możesz również wpisać tekst w polu **wyszukiwania** , aby filtrować testy według nazwy.

Aby uzyskać więcej informacji na temat `unittest` modułu i testów pisania, zobacz [dokumentację języka Python 2,7](https://docs.python.org/2/library/unittest.html) lub [dokumentację języka Python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Uruchom testy

W **Eksploratorze testów** można uruchamiać testy na różne sposoby:

- **Uruchom wszystkie** wyraźnie uruchamiane wszystkie pokazywane testy (z uwzględnieniem filtrów).
- Menu **Uruchom** zawiera polecenia, które można uruchomić, nie powiodły się lub nie uruchamiają testów jako grupy.
- Możesz wybrać jeden lub więcej testów, kliknąć prawym przyciskiem myszy i wybrać polecenie **Uruchom wybrane testy**.

Testy są uruchamiane w tle, a **Eksplorator testów** aktualizuje stan każdego testu w miarę jego kończenia:

- Przekazanie testów pokazuje zielony takt i czas potrzebny do uruchomienia testu:

    ![test_A stan przeszedł](../../media/unit-test-A-pass.png)

- Testy zakończone niepowodzeniem pokazują czerwony krzyżyk z linkiem **wyjściowym** wyświetlającym dane wyjściowe konsoli i `unittest` dane wyjściowe z przebiegu testu:

    ![test_A stanu niepowodzenia](../../media/unit-test-A-fail.png)

    ![test_A nie powiodła się z powodu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Debuguj testy

Ponieważ testy jednostkowe są fragmentami kodu, podlegają one błędom, podobnie jak każdy inny kod i sporadycznie muszą być uruchamiane w debugerze. W debugerze można ustawić punkty przerwania, przeanalizować zmienne i krok po kroku. Program Visual Studio udostępnia również narzędzia diagnostyczne do testów jednostkowych.

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy Test (lub zaznaczenie) w **Eksploratorze testów** i wybierz polecenie **Debuguj wybrane testy**. Program Visual Studio uruchamia debuger języka Python, tak jak w przypadku kodu aplikacji.

![Debugowanie testu](../../media/unit-test-debugging.png)

Można również użyć **Przeanalizuj pokrycie kodu dla wybranych testów**. Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Znane problemy

- Podczas uruchamiania debugowania program Visual Studio wydaje się uruchomić i zatrzymać debugowanie, a następnie ponownie uruchomić program. Takie zachowanie jest oczekiwane.
- Podczas debugowania wielu testów każda z nich jest uruchamiana niezależnie, co powoduje przerwanie sesji debugowania.
- Program Visual Studio sporadycznie nie może uruchomić testu podczas debugowania. Zwykle próba debugowania testów powiedzie się.
- Podczas debugowania można wykonać krok po kroku testu do `unittest` implementacji. Zwykle następnym krokiem jest uruchomienie na końcu programu i zatrzymanie debugowania.
