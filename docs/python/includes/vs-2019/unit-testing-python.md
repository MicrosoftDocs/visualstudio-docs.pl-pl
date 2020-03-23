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
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933494"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Wybierz strukturę testów dla projektu języka Python

Visual Studio obsługuje dwie struktury testowania języka Python, [unittest](https://docs.python.org/3/library/unittest.html) i [pytest](https://pytest.org/en/latest/) (dostępne w programie Visual Studio 2019 począwszy od wersji 16.3). Domyślnie nie jest zaznaczona żadna struktura podczas tworzenia projektu języka Python. Aby określić strukturę, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz opcję **Właściwości.** Spowoduje to otwarcie projektanta projektu, który umożliwia skonfigurowanie testów za pośrednictwem karty **Test.** Na tej karcie można wybrać strukturę testów, która ma być używana dla projektu. 

* W ramach **unittest** katalog główny projektu jest używany do odnajdowania testów. Ta lokalizacja, a także wzorzec tekstu do identyfikowania testów, mogą być modyfikowane na karcie **Test** do określonych przez użytkownika wartości.
* W przypadku struktury **pytest** opcje testowania, takie jak lokalizacja testu i wzorce nazwy pliku, są określane przy użyciu standardowego pliku konfiguracyjnego pytest .ini. Zobacz [dokumentację referencyjną pytest,](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) aby uzyskać więcej informacji.

Po zapisaniu wyboru struktury i ustawienia, odnajdowanie testów jest inicjowane w Eksploratorze testów. Jeśli okno Eksploratora testów nie jest jeszcze otwarte, przejdź do paska narzędzi i wybierz pozycję > **Eksplorator testów**. **Test**

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurowanie testowania języka Python bez projektu
Visual Studio umożliwia uruchamianie i testowanie istniejącego kodu języka Python bez projektu, otwierając folder z [kodem](../../quickstart-05-python-visual-studio-open-folder.md) Pythona. W tych okolicznościach należy użyć pliku **PythonSettings.json** do skonfigurowania testowania. 
1. Otwórz istniejący kod języka Python, korzystając z opcji **Otwórz folder lokalny.** 

   ![Ekran startowy programu Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. W oknie Eksploratora rozwiązań kliknij ikonę **Pokaż wszystkie pliki,** aby wyświetlić wszystkie pliki w bieżącym folderze.

   ![Przycisk Pokaż wszystkie pliki](../../media/unit-test-show-files.png)

1. Przejdź do pliku **PythonSettings.json** w folderze **Ustawienia lokalne.** Jeśli ten plik nie jest widoczny w folderze **Ustawienia lokalne,** utwórz go ręcznie.
   
1. Dodaj pole **TestFramework** do pliku ustawień i ustaw go na **pytest** lub **unittest** w zależności od struktury testowania, której chcesz użyć.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Dla **struktury unittest,** jeśli pola **UnitTestRootDirectory** i **UnitTestPattern** nie są określone w pliku PythonSettings.json, są dodawane i przypisywane wartości domyślne "." i "test*.py" odpowiednio.

1. Jeśli folder zawiera katalog **src,** który jest oddzielony od folderu zawierającego testy, określ ścieżkę do folderu **src** za pomocą pola **SearchPaths** w pliku **PythonSettings.json.**

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Zapisz zmiany w pliku PythonSettings.json, aby zainicjować odnajdowanie testów dla określonej struktury. 
   > [!Note]
   > Jeśli okno Eksploratora testów jest już otwarte **CTRL** + **R,A** również wyzwala odnajdowanie.

## <a name="discover-and-view-tests"></a>Odnajduj i wyświetlaj testy

Domyślnie program Visual Studio identyfikuje testy **unittest i** **pytest** jako metody, których nazwy zaczynają się od `test`. Aby wyświetlić odnajdowanie testów, wykonaj następujące czynności:

1. Otwórz [projekt języka Python](../../managing-python-projects-in-visual-studio.md).

1. Po załadowaniu projektu w programie Visual Studio kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz strukturę **unittest** lub **pytest** z karty **Test** właściwości.
   > [!Note]
   > Jeśli używasz pytest framework, można określić lokalizację testu i wzorce nazwy pliku przy użyciu standardowego pliku konfiguracyjnego pytest .ini. Domyślnie używany jest folder obszaru roboczego/projektu, `test_*py` `*_test.py`ze wzorcem i . Zobacz [dokumentację referencyjną pytest,](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) aby uzyskać więcej informacji.

1. Po wybraniu struktury kliknij ponownie projekt prawym przyciskiem myszy i wybierz polecenie **Dodaj** > **nowy element,** a następnie wybierz pozycję Python Unit **Test,** a następnie **dodaj**.

1. Ta akcja tworzy plik *test_1.py* z kodem, `unittest` który importuje moduł `unittest.TestCase`standardowy, `unittest.main()` wyprowadza klasę testu z i wywołuje po uruchomieniu skryptu bezpośrednio:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie otwórz **Eksploratora testów** za pomocą polecenia menu**Eksploratora** **Test** > testów.

1. **Eksplorator testów** przeszukuje projekt w poszukiwaniu testów i wyświetla je w sposób pokazany poniżej. Dwukrotne kliknięcie testu powoduje otwarcie pliku źródłowego.

    ![Eksplorator testów z domyślną test_A](../../media/unit-test-a-2.png) 

1. Podczas dodawania kolejnych testów do projektu można zorganizować widok w **Eksploratorze testów** za pomocą menu **Grupuj według** na pasku narzędzi:

    ![Menu Grupy eksploratora według paska narzędzi](../../media/unit-test-group-menu-2.png) 

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

> [!Note]
> Domyślnie debugowanie testowe używa debugera ptvsd 4. Jeśli zamiast tego chcesz użyć ptvsd 3, możesz wybrać opcję **Użyj starszego debugera** w**opcjach** >  **narzędzi** > **Python** > **Debugowanie**. 

Aby rozpocząć debugowanie, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy test (lub zaznaczenie) w **Eksploratorze testów** i wybierz opcję **Debugowanie wybranych testów**. Visual Studio uruchamia debuger języka Python, tak jak w przypadku kodu aplikacji.

![Debugowanie testu](../../media/unit-test-debugging.png)

Można również użyć **analizy pokrycia kodu dla wybranych testów**. Aby uzyskać więcej informacji, zobacz [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
