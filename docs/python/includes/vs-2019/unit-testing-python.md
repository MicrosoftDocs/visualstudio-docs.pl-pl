---
title: Kod języka Python testów jednostkowych
description: Skonfigurowanie testów jednostkowych dla kodu Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdywania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bd63d927e41a8b360eb7d934693bb3c83a30ea4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920674"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Wybierz platformę testową dla projektu języka Python

Program Visual Studio obsługuje dwie platformy testowania dla języków Python, [testu jednostkowego](https://docs.python.org/3/library/unittest.html) i [pytest](https://pytest.org/en/latest/) (dostępne w programie Visual Studio 2019, począwszy od wersji 16,3). Domyślnie podczas tworzenia projektu w języku Python nie jest wybierana żadna struktura. Aby określić platformę, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz opcję **Właściwości** . Spowoduje to otwarcie projektanta projektu, który umożliwia skonfigurowanie testów za pomocą karty **test** . Na tej karcie można wybrać platformę testową, która ma być używana dla projektu. 

* Dla struktury **testu jednostkowego** , główny katalog projektu służy do odnajdywania testów. Ta lokalizacja, a także wzorzec tekstu służący do identyfikowania testów, można zmodyfikować na karcie **test** do wartości określonych przez użytkownika.
* Dla środowiska **pytest** Framework opcje testowania, takie jak lokalizacja testu i wzorce nazwy pliku, są określane przy użyciu standardowego pliku konfiguracji pytest. ini. Aby uzyskać więcej informacji, zobacz [dokumentację referencyjną pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Po zapisaniu wyboru platformy i ustawień, odnajdywanie testów jest inicjowane w Eksploratorze testów. Jeśli okno Eksplorator testów nie jest jeszcze otwarte, przejdź do paska narzędzi i wybierz **test**  >  **Eksplorator testów**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurowanie testowania dla języka Python bez projektu
Program Visual Studio umożliwia uruchamianie i testowanie istniejącego kodu języka Python bez projektu, [otwierając folder](../../quickstart-05-python-visual-studio-open-folder.md) z kodem języka Python. W tych okolicznościach należy użyć **PythonSettings.jsw** pliku w celu skonfigurowania testowania. 
1. Otwórz istniejący kod w języku Python przy użyciu opcji **Otwórz folder lokalny** . 

   ![Ekran startowy programu Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. W oknie Eksplorator rozwiązań kliknij ikonę **Pokaż wszystkie pliki** , aby wyświetlić wszystkie pliki w bieżącym folderze.

   ![Przycisk Pokaż wszystkie pliki](../../media/unit-test-show-files.png)

1. Przejdź do **PythonSettings.jsw** pliku w folderze **ustawień lokalnych** . Jeśli ten plik nie jest widoczny w folderze **local settings** , utwórz go ręcznie.
   
1. Dodaj pole **TestFramework** do pliku ustawień i ustaw go na **pytest** lub **testu jednostkowego** w zależności od platformy testowania, której chcesz użyć.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > W przypadku platformy **testu jednostkowego** Framework, jeśli pola **UnitTestRootDirectory** i **UnitTestPattern** nie są określone w PythonSettings.jsw pliku, zostaną dodani odpowiednio do wartości "." i "test *. pr".

1. Jeśli folder zawiera katalog **src** , który jest oddzielony od folderu zawierającego testy, określ ścieżkę do folderu **src** przy użyciu pola **SearchPaths** w **PythonSettings.js** pliku.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Zapisz zmiany w PythonSettings.jspliku, aby zainicjować odnajdywanie testów dla określonej struktury. 
   > [!Note]
   > Jeśli okno Eksplorator testów jest już otwarte **Ctrl**  +  **R, A** także wyzwala odnajdywanie.

## <a name="discover-and-view-tests"></a>Odnajdywanie i wyświetlanie testów

Domyślnie program Visual Studio identyfikuje testy **testu jednostkowego** i **pytest** jako metody, których nazwy zaczynają się od `test` . Aby wyświetlić odnajdywanie testów, wykonaj następujące czynności:

1. Otwórz projekt w języku [Python](../../managing-python-projects-in-visual-studio.md).

1. Po załadowaniu projektu w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz strukturę **testu jednostkowego** lub **Pytest** z karty **testowanie** właściwości.
   > [!Note]
   > W przypadku korzystania z platformy pytest można określić wzorce lokalizacji i nazw plików przy użyciu standardowego pliku konfiguracji pytest. ini. Domyślnie używany jest folder obszar roboczy/projekt z wzorcem `test_*py` i `*_test.py` . Aby uzyskać więcej informacji, zobacz [dokumentację referencyjną pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Po wybraniu struktury kliknij prawym przyciskiem myszy projekt ponownie i wybierz polecenie **Dodaj**  >  **nowy element**, a następnie wybierz polecenie **test jednostkowy Python** , a następnie **Dodaj**.

1. Ta akcja tworzy plik *test_1. PR* z kodem, który importuje `unittest` moduł standardowy, dziedziczy klasę testową z `unittest.TestCase` i wywołuje się, `unittest.main()` gdy skrypt jest uruchamiany bezpośrednio:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie otwórz **Eksploratora testów** z   >  poleceniem menu **Eksplorator testów** testowania.

1. **Eksplorator testów** przeszukuje projekt pod kątem testów i wyświetla je, jak pokazano poniżej. Dwukrotne kliknięcie testu spowoduje otwarcie jego pliku źródłowego.

    ![Eksplorator testów z domyślną test_A](../../media/unit-test-a-2.png) 

1. W miarę dodawania kolejnych testów do projektu można organizować widok w **Eksploratorze testów** przy użyciu menu **Grupuj według** na pasku narzędzi:

    ![Eksplorator testów Grupuj według menu paska narzędzi](../../media/unit-test-group-menu-2.png) 

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

> [!Note]
> Domyślnie debugowanie testów używa debugera ptvsd 4 dla programu Visual Studio 2017 (wersje 15,8 i nowsze) oraz debugpy dla programu Visual Studio 2019 (wersje 16,5 i nowsze). Jeśli zamiast tego chcesz użyć ptvsd 3, możesz wybrać opcję **Użyj starszego debugera** dla opcji **Narzędzia**  >    >    >  **debugowanie** języka Python. 

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy Test (lub zaznaczenie) w **Eksploratorze testów** i wybierz polecenie **Debuguj wybrane testy**. Program Visual Studio uruchamia debuger języka Python, tak jak w przypadku kodu aplikacji.

![Debugowanie testu](../../media/unit-test-debugging.png)

Można również użyć **Przeanalizuj pokrycie kodu dla wybranych testów**. Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
