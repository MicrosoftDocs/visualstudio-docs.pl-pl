---
title: Szybki Start — klonowanie repozytorium kodu w języku Python
description: W tym przewodniku szybki start utworzysz projekt w języku Python w programie Visual Studio, klonowanie repozytorium koans języka Python za pomocą programu Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5d0363626748588b6f4058e197f0d6796ece51ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64543142"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Szybki Start: klonowanie repozytorium kodu w języku Python w programie Visual Studio

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)można dodać rozszerzenie GitHub dla programu Visual Studio. Rozszerzenie pozwala łatwo sklonować repozytorium kodu w języku Python i utworzyć projekt z niego z poziomu środowiska IDE. Można zawsze klonować repozytoria również w wierszu polecenia, a następnie korzystać z nich w programie Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Zainstaluj rozszerzenie GitHub dla programu Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Współpraca z usługą GitHub w programie Visual Studio

1. Uruchom program Visual Studio.

1. Wybierz pozycję **Wyświetl**  >  **Team Explorer** , aby otworzyć okno **Team Explorer** , w którym można nawiązać połączenie z usługą GitHub lub Azure Repos lub sklonować repozytorium. (Jeśli nie widzisz poniższej strony **Połącz** , wybierz ikonę wtyczki na górnym pasku narzędzi, która spowoduje przejście do tej strony).

    ![Okno programu Team Explorer zawierające Azure Repos, GitHub i klonowanie repozytorium](media/team-explorer.png)

1. W obszarze **lokalne repozytoria Git**wybierz polecenie **klonowania** , a następnie wprowadź wartość `https://github.com/gregmalcolm/python_koans` w polu adres URL, wprowadź folder dla sklonowanych plików, a następnie wybierz przycisk **klonowania** .

    > [!Tip]
    > Folder określony w **Team Explorer** jest dokładnym folderem, w którym będą odbierane sklonowane pliki. W przeciwieństwie do `git clone` polecenia, utworzenie klonu w **Team Explorer** nie tworzy automatycznie podfolderu o nazwie repozytorium.

1. Po zakończeniu klonowania Nazwa repozytorium pojawia się na liście **lokalnych repozytoriów Git** . Kliknij dwukrotnie tę nazwę, aby przejść do pulpitu nawigacyjnego repozytorium w **Team Explorer**.

1. W obszarze **rozwiązania**wybierz pozycję **Nowy**.

    ![Okno Team Explorer, tworzenie nowego projektu na podstawie klonu](media/team-explorer-new-project.png)

1. W wyświetlonym oknie dialogowym **Nowy projekt** przejdź do języka **Python** (lub wyszukaj ciąg "Python"), wybierz **z istniejącego kodu Python**, określ nazwę projektu, ustaw **lokalizację** na ten sam folder, w którym znajduje się repozytorium, a następnie wybierz przycisk **OK**. W wyświetlonym kreatorze wybierz pozycję **Zakończ**.

1. Wybierz pozycję **Wyświetl**  >  **Eksplorator rozwiązań** z menu.

1. W **Eksplorator rozwiązań**rozwiń węzeł **python3** , kliknij prawym przyciskiem myszy pozycję **contemplate_koans. PR**i wybierz pozycję **Ustaw jako plik startowy**. Ten krok informuje program Visual Studio, który plik powinien być używany podczas uruchamiania projektu.

1. Wybierz pozycję **Project**  >  **koans Properties (właściwości** projektu) z menu, wybierz kartę **Ogólne** i ustaw **katalog roboczy** na "python3". Ten krok jest niezbędny, ponieważ program Visual Studio domyślnie ustawia katalog roboczy na katalog główny projektu, a nie lokalizację pliku startowego (*python3 \ contemplate_koans. PR*, który można także zobaczyć we właściwościach projektu). Kod programu szuka pliku *koans.txt* w folderze roboczym, więc bez zmiany tej wartości zobaczysz błąd w czasie wykonywania.

    ![Ustawianie katalogu roboczego dla projektu języka Python](media/projects-set-working-directory.png)

1. Naciśnij klawisz **Ctrl** + **F5** lub wybierz pozycję **Debuguj**  >  **Uruchom bez debugowania** , aby uruchomić program. Jeśli zobaczysz **FileNotFoundError** dla *koans.txt*, sprawdź ustawienie katalogu roboczego zgodnie z opisem w poprzednim kroku.

1. Po pomyślnym uruchomieniu programu w wierszu 17 z *python3/koans/about_asserts. PR*zostanie wyświetlony błąd potwierdzenia. Jest to zamierzone: program został zaprojektowany z myślą o nauce języka Python, aby poprawić wszystkie zamierzone błędy. (Więcej szczegółów znajduje się w [koans Ruby](https://rubykoans.com/), który inspirowany koans języka Python).

    ![Pierwsze wyjście z programu python koans](media/koans-output.png)

1. Otwórz plik *python3/koans/about_asserts. PR* , przechodząc do niego w **Eksplorator rozwiązań** i klikając go dwukrotnie. Zauważ, że numery wierszy nie są wyświetlane domyślnie w edytorze. Aby to zmienić, wybierz pozycję **Narzędzia**  >  **Opcje**, wybierz pozycję **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego, a następnie przejdź do pozycji **Edytor tekstu**  >  **Python**  >  **Ogólne** i wybierz pozycję **numery wierszy**:

    ![Włączanie numeru wiersza dla plików Python](media/options-general-line-numbers.png)

1. Popraw błąd, zmieniając `False` argument w wierszu od 17 do `True` . Wiersz powinien zostać odczytany w następujący sposób:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Ponownie uruchom program. Jeśli program Visual Studio wyświetli ostrzeżenie o błędach, należy odpowiedzieć na **wartość tak** , aby kontynuować uruchamianie kodu. Zobaczysz, że pierwsze sprawdzanie przebiega i program zatrzyma się na następnej Koan. Kontynuuj poprawianie błędów i programu, tak jak chcesz.

> [!Important]
> W tym przewodniku szybki start utworzono bezpośrednie klonowanie repozytorium *python_koans* w serwisie GitHub. Takie repozytorium jest chronione przez jego autora przed bezpośrednimi zmianami, dlatego próba zatwierdzenia zmian w repozytorium kończy się niepowodzeniem. W związku z tym deweloperzy mogą przetworzyć takie repozytorium na własne konto w usłudze GitHub, wprowadzić w nim zmiany, a następnie utworzyć żądania ściągnięcia, aby przesłać te zmiany do oryginalnego repozytorium. Jeśli masz własne rozwidlenia, użyj swojego adresu URL zamiast oryginalnego adresu URL repozytorium używanego wcześniej.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: współpraca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Ręcznie Zidentyfikuj istniejący interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Jak zainstalować obsługę języka Python w programie Visual Studio w systemie Windows](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)
