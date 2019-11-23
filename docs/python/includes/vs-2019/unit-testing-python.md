---
title: Testy jednostkowe kodu w języku Python
description: Konfigurowanie testów jednostkowych dla kodu w języku Python w programie Visual Studio ma pełne wykorzystanie funkcji Eksploratora testów, aby odkryć, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933494"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Wybierz platformę testową dla projektu języka Python

Program Visual Studio obsługuje dwie platformy testowania dla języków Python, [testu jednostkowego](https://docs.python.org/3/library/unittest.html) i [pytest](https://pytest.org/en/latest/) (dostępne w programie Visual Studio 2019, począwszy od wersji 16,3). Domyślnie podczas tworzenia projektu w języku Python nie jest wybierana żadna struktura. Aby określić platformę, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz opcję **Właściwości** . Spowoduje to otwarcie projektanta projektu, który umożliwia skonfigurowanie testów za pomocą karty **test** . Na tej karcie można wybrać platformę testową, która ma być używana dla projektu. 

* Dla struktury **testu jednostkowego** , główny katalog projektu służy do odnajdywania testów. Ta lokalizacja, a także wzorzec tekstu służący do identyfikowania testów, można zmodyfikować na karcie **test** do wartości określonych przez użytkownika.
* Dla środowiska **pytest** Framework opcje testowania, takie jak lokalizacja testu i wzorce nazwy pliku, są określane przy użyciu standardowego pliku konfiguracji pytest. ini. Aby uzyskać więcej informacji, zobacz [dokumentację referencyjną pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

Po zapisaniu wyboru platformy i ustawień, odnajdywanie testów jest inicjowane w Eksploratorze testów. Jeśli okno Eksplorator testów nie jest jeszcze otwarte, przejdź do paska narzędzi i wybierz polecenie **testuj** > **Test Explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurowanie testowania dla języka Python bez projektu
Program Visual Studio umożliwia uruchamianie i testowanie istniejącego kodu języka Python bez projektu, [otwierając folder](../../quickstart-05-python-visual-studio-open-folder.md) z kodem języka Python. W tych okolicznościach należy użyć pliku **PythonSettings. JSON** w celu skonfigurowania testowania. 
1. Otwórz istniejący kod w języku Python przy użyciu opcji **Otwórz folder lokalny** . 

   ![Ekran startowy programu Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. W oknie Eksplorator rozwiązań kliknij ikonę **Pokaż wszystkie pliki** , aby wyświetlić wszystkie pliki w bieżącym folderze.

   ![Przycisk Pokaż wszystkie pliki](../../media/unit-test-show-files.png)

1. Przejdź do pliku **PythonSettings. JSON** w folderze **local settings** . Jeśli ten plik nie jest widoczny w folderze **local settings** , utwórz go ręcznie.
   
1. Dodaj pole **TestFramework** do pliku ustawień i ustaw go na **pytest** lub **testu jednostkowego** w zależności od platformy testowania, której chcesz użyć.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > W przypadku platformy **testu jednostkowego** Framework, jeśli pola **UnitTestRootDirectory** i **UnitTestPattern** nie są określone w pliku PythonSettings. JSON, są dodawane odpowiednio wartości domyślne "." i "test *. pr".

1. Jeśli folder zawiera katalog **src** , który jest oddzielony od folderu zawierającego testy, określ ścieżkę do folderu **src** przy użyciu pola **SearchPaths** w pliku **PythonSettings. JSON** .

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Zapisz zmiany w pliku PythonSettings. JSON, aby zainicjować odnajdywanie testów dla określonej struktury. 
   > [!Note]
   > Jeśli okno Eksplorator testów jest już otwarte, **CTRL** + **R, A** także wyzwala odnajdywanie.

## <a name="discover-and-view-tests"></a>Odnajdywanie i wyświetlić testy

Domyślnie program Visual Studio identyfikuje testy **testu jednostkowego** i **pytest** jako metody, których nazwy rozpoczynają się od `test`. Aby wyświetlić odnajdywanie testów, wykonaj następujące czynności:

1. Otwórz projekt w języku [Python](../../managing-python-projects-in-visual-studio.md).

1. Po załadowaniu projektu w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz strukturę **testu jednostkowego** lub **Pytest** z karty **testowanie** właściwości.
   > [!Note]
   > W przypadku korzystania z platformy pytest można określić wzorce lokalizacji i nazw plików przy użyciu standardowego pliku konfiguracji pytest. ini. Domyślnie używany jest folder obszar roboczy/projekt ze wzorcem `test_*py` i `*_test.py`. Aby uzyskać więcej informacji, zobacz [dokumentację referencyjną pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) .

1. Po wybraniu struktury kliknij prawym przyciskiem myszy projekt ponownie i wybierz polecenie **dodaj** > **nowy element**, a następnie wybierz pozycję **test jednostkowy języka Python** , a następnie **Dodaj**.

1. Ta akcja tworzy plik *test_1. PR* z kodem, który importuje standardowy moduł `unittest`, dziedziczy klasę testową z `unittest.TestCase`i wywołuje `unittest.main()`, jeśli skrypt zostanie uruchomiony bezpośrednio:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie otwórz **Eksploratora testów** z poleceniem menu **Testuj** > test **Explorer** .

1. **Eksplorator testów** wyszukuje projektu dla testów, a następnie wyświetli je, jak pokazano poniżej. Dwukrotne kliknięcie testu spowoduje otwarcie pliku źródłowego.

    ![Test Explorer przedstawiający domyślną test_A](../../media/unit-test-a-2.png) 

1. W miarę dodawania kolejnych testów do projektu można organizować widok w **Eksploratorze testów** przy użyciu menu **Grupuj według** na pasku narzędzi:

    ![Grupy Eksploratora testów przez menu paska narzędzi](../../media/unit-test-group-menu-2.png) 

1. Możesz też wprowadzić tekst w **wyszukiwania** pola do filtrowania testów według nazwy.

Aby uzyskać więcej informacji na temat modułu `unittest` i pisania testów, zobacz [dokumentację języka python 2,7](https://docs.python.org/2/library/unittest.html) lub [dokumentację języka python 3,7](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Uruchom testy

W **Eksplorator testów** można uruchomić testy na wiele sposobów:

- **Uruchom wszystkie** wyraźnie uruchamia wszystkie testy pokazano (zależnie od filtry).
- **Uruchom** menu zawiera polecenia, aby uruchomić testy zakończone niepowodzeniem, przekazany lub nie uruchomiono jako grupą.
- Można wybrać jeden lub więcej testów, kliknij prawym przyciskiem myszy, a następnie wybierz **Uruchom wybrane testy**.

Testy uruchamiania w tle i **Eksploratora testów** aktualizuje stan każdego testu w kończeniu:

- Przechodzenie testów przedstawiają zielony znacznik i czas trwania testu:

    ![test_A przekazywane stanu](../../media/unit-test-A-pass.png)

- Testy zakończone niepowodzeniem Pokaż czerwony krzyżyk z **dane wyjściowe** link, który pokazuje dane wyjściowe konsoli i `unittest` dane wyjściowe z przebiegu testu:

    ![Stan test_A nie powiodło się](../../media/unit-test-A-fail.png)

    ![nie powiodło się z powodu test_A](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Debuguj testy

Ponieważ testy jednostkowe są fragmenty kodu, jest zależna od błędów, podobnie jak każdy inny kod, a od czasu do czasu należy uruchomić w debugerze. W debugerze można ustawić punktów przerwania, Sprawdź zmienne i przejść przez kod. Visual Studio udostępnia również narzędzia diagnostyczne dla testów jednostkowych.

> [!Note]
> Domyślnie debugowanie testowe używa debugera ptvsd 4. Jeśli zamiast tego chcesz użyć ptvsd 3, możesz wybrać opcję **Użyj starszego debugera** w obszarze **narzędzia** > **Opcje** > Debuguj >  **debugowanie**. 

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy test (lub zaznaczenie) **Eksploratora testów** i wybierz **Debuguj wybrane testy**. Program Visual Studio uruchamia debugera języka Python, jak dla kodu aplikacji.

![Profilowanie testu](../../media/unit-test-debugging.png)

Można również użyć **Przeanalizuj pokrycie kodu dla wybranych testów**. Aby uzyskać więcej informacji, zobacz [użycie pokrycia kodu, aby ustalić, ile kodu jest testowana](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
