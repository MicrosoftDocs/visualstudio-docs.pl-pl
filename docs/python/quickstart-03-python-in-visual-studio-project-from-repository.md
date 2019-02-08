---
title: Przewodnik Szybki Start — klonować repozytorium kodu w języku Python
description: W tym przewodniku Szybki Start utworzysz projektu języka Python w programie Visual Studio przez Sklonowanie repozytorium koans języka Python za pomocą programu Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e80c09978aa313aa3392ef8221d0e58bda26e385
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928455"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Szybki start: Klonowanie repozytorium kodu w języku Python w programie Visual Studio

Po [zainstalowane obsługi języka Python w programie Visual Studio 2017](installing-python-support-in-visual-studio.md), można dodać rozszerzenie GitHub dla programu Visual Studio. Rozszerzenie pozwala łatwo sklonować repozytorium kodu w języku Python i Utwórz projekt z niego z poziomu środowiska IDE. Można zawsze klonowanie repozytoriów z wiersza polecenia i pracować z nimi w programie Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Zainstaluj rozszerzenie GitHub dla programu Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Praca z usługi GitHub w programie Visual Studio

1. Uruchom program Visual Studio.

1. Wybierz **widoku** > **Team Explorer** otworzyć **Team Explorer** okna, w którym można nawiązać połączenie z usługi GitHub i repozytoriów platformy Azure lub klonowanie repozytorium. (Jeśli nie widzisz **Connect** pokazanej poniżej wybierz ikonę wtyczki na górnym pasku narzędzi, który spowoduje przejście do tej strony.)

    ![Okno Eksploratora zespołu, wyświetlanie repozytoriów platformy Azure, usługi GitHub i klonowanie repozytorium](media/team-explorer.png)

1. W obszarze **lokalne repozytoria Git**, wybierz opcję **klonowania** polecenia, a następnie wprowadź `https://github.com/gregmalcolm/python_koans` w polu adres URL wprowadź folderu na sklonowane pliki, a następnie wybierz pozycję **klonowania** przycisk.

    > [!Tip]
    > Folder w **Team Explorer** jest dokładnie folder do odbierania sklonowane pliki. W odróżnieniu od `git clone` polecenia, tworzenie własnego klonu w **Team Explorer** nie tworzy automatycznie podfolder o nazwie repozytorium.

1. Po ukończeniu klonowania Nazwa repozytorium jest wyświetlana w **lokalne repozytoria Git** listy. Kliknij dwukrotnie tej nazwy, aby przejść do pulpitu nawigacyjnego repozytorium w **Team Explorer**.

1. W obszarze **rozwiązania**, wybierz opcję **New**.

    ![Okno Eksploratora zespołu, tworząc nowy projekt z klonu](media/team-explorer-new-project.png)

1. W **nowy projekt** wyświetlonym oknie dialogowym Przejdź do **Python** języka (lub wyszukiwania "Python"), wybierz **z istniejącego kodu języka Python**, określ nazwę dla projektu, Ustaw **lokalizacji** w tym samym folderze, jako repozytorium, a następnie wybierz **OK**. W oknie kreatora wybierz **Zakończ**.

1. Wybierz **widoku** > **Eksploratora rozwiązań** z menu.

1. W **Eksploratora rozwiązań**, rozwiń węzeł **języku python3** węzła, kliknij prawym przyciskiem myszy **contemplate_koans.py**i wybierz **Ustaw jako plik startowy**. W tym kroku opisano programu Visual Studio, plik, który należy używać, podczas uruchamiania projektu.

1. Wybierz **projektu** > **właściwości Koans** menu, wybierz polecenie **ogólne** , a następnie ustaw **katalog roboczy** do " środowiska python3 jako ". Ten krok jest niezbędny, ponieważ domyślnie program Visual Studio Ustawia katalog roboczy katalogu głównego projektu, a nie lokalizację pliku uruchamiania (*python3\contemplate_koans.py*, którą można zobaczyć w oknie właściwości projektu). Kod programu szuka pliku *koans.txt* w folderze roboczym, dlatego bez zmiany tej wartości zostanie wyświetlony błąd w czasie wykonywania.

    ![Ustawianie katalogu roboczego dla projektu w języku Python](media/projects-set-working-directory.png)

1. Naciśnij klawisz **Ctrl**+**F5** lub wybierz **debugowania** > **Uruchom bez debugowania** do uruchomienia programu. Jeśli widzisz **FileNotFoundError** dla *koans.txt*, Sprawdź katalog roboczy ustawienia, zgodnie z opisem w poprzednim kroku.

1. Gdy program zostanie uruchomiony pomyślnie, wyświetla błąd asercji w wierszu 17 *python3/koans/about_asserts.py*. Jest to zamierzone: program jest przeznaczony do nauki, Python, konfigurując możesz Popraw wszystkie błędy zamierzone. (Szczegółowe informacje znajdują się na [Ruby Koans](https://rubykoans.com/), który inspirację Koans języka Python.)

    ![Pierwsze dane wyjściowe programu koans języka Python](media/koans-output.png)

1. Otwórz *python3/koans/about_asserts.py* , przechodząc do niego w **Eksploratora rozwiązań** i dwukrotne kliknięcie pliku. Zauważ, że numery wierszy nie są wyświetlane domyślnie w edytorze. Aby zmienić to ustawienie, wybierz pozycję **narzędzia** > **opcje**, wybierz opcję **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego, a następnie przejdź do **Edytor tekstu**   >  **Python** > **ogólne** i wybierz **numery wierszy**:

    ![Włączenie numeru wiersza dla plików języka Python](media/options-general-line-numbers.png)

1. Popraw błąd, zmieniając `False` argument w wierszu 17 do `True`. Wiersz powinien wyglądać następująco:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Ponownie uruchom program. Jeśli program Visual Studio wyświetli ostrzeżenie o błędach, elastyczniejsze **tak** ma kontynuować wykonywanie kodu. Następnie zobaczysz, że pierwsze sprawdzanie to kończy i program zatrzymuje działanie przy następnym koan. Kontynuuj poprawianie błędów, a program ponownie, jak chcesz.

> [!Important]
> W tym przewodniku Szybki Start utworzono bezpośrednie klon *python_koans* repozytorium w witrynie GitHub. Takie repozytorium jest chroniony przez jego autora od zmian bezpośrednio, więc próby zatwierdzenia zmian w repozytorium nie powiedzie się. W praktyce deweloperów zamiast rozwidlenie repozytorium do własnego konta usługi GitHub, wprowadzać w nim zmian, a następnie utwórz żądania ściągnięcia do przesyłania tych zmian do oryginalnego repozytorium. Jeśli masz własne rozwidlenie, należy użyć adresu URL zamiast oryginalny adres URL repozytorium wcześniej używane.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Ręcznie Zidentyfikuj istniejące interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)
