---
title: Szybki start — klonowanie repozytorium kodu języka Python
description: W tym przewodniku Szybki start utworzysz projekt języka Python w programie Visual Studio, klonując repozytorium koans języka Python przy użyciu Eksploratora zespołu programu Visual Studio.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "64543142"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Szybki start: klonowanie repozytorium kodu języka Python w programie Visual Studio

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)można dodać rozszerzenie GitHub dla programu Visual Studio. Rozszerzenie umożliwia łatwe klonowanie repozytorium kodu języka Python i tworzenie projektu z niego z poziomu IDE. Zawsze można sklonować repozytoria w wierszu polecenia, a następnie pracować z nimi w programie Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Instalowanie rozszerzenia GitHub dla programu Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Praca z githubem w programie Visual Studio

1. Uruchom program Visual Studio.

1. Wybierz **pozycję Wyświetl** > **Eksploratora zespołu,** aby otworzyć okno **Eksploratora zespołu,** w którym można połączyć się z witryną GitHub lub repozytorium platformy Azure lub sklonować repozytorium. (Jeśli nie widzisz strony **Połącz** pokazano poniżej, wybierz ikonę wtyczki na górnym pasku narzędzi, która przeniesie Cię do tej strony).

    ![Okno Eksploratora zespołu z programem Azure Reposo, GitHub i klonowaniem repozytorium](media/team-explorer.png)

1. W **obszarze Lokalne repozytoria Git**wybierz polecenie `https://github.com/gregmalcolm/python_koans` **Klonuj,** a następnie wprowadź pole ADRESU URL, wprowadź folder sklonowanych plików i wybierz przycisk **Klonuj.**

    > [!Tip]
    > Folder określony w **Eksploratorze zespołu** jest dokładnym folderem do odbierania sklonowanych plików. W `git clone` przeciwieństwie do polecenia, utworzenie klona w **Eksploratorze zespołu** nie powoduje automatycznego utworzenia podfolderu o nazwie repozytorium.

1. Po zakończeniu klonowania nazwa repozytorium pojawia się na liście **Lokalne repozytoria Git.** Kliknij dwukrotnie tę nazwę, aby przejść do pulpitu nawigacyjnego repozytorium w **Eksploratorze zespołu**.

1. W obszarze **Rozwiązania**wybierz pozycję **Nowy**.

    ![Okno eksploratora zespołu, tworzenie nowego projektu z klonu](media/team-explorer-new-project.png)

1. W wyświetlonym oknie dialogowym **Nowy projekt** przejdź do języka **Pythona** (lub wyszukaj w "Pythonie"), wybierz **pozycję Z istniejącego kodu języka Pythona**, określ nazwę projektu, ustaw **lokalizację** na ten sam folder co repozytorium i wybierz **przycisk OK**. W wyświetlonym kreatorze wybierz pozycję **Zakończ**.

1. Z menu **wybierz polecenie Wyświetl** > **Eksploratora rozwiązań.**

1. W **Eksploratorze rozwiązań**rozwiń węzeł **python3,** kliknij prawym przyciskiem **myszy contemplate_koans.py**i wybierz polecenie **Ustaw jako plik startowy**. Ten krok informuje visual studio, który plik należy użyć podczas uruchamiania projektu.

1. Wybierz polecenie **Właściwości projektu** > **Koans** z menu, wybierz kartę **Ogólne** i ustaw **katalog roboczy** na "python3". Ten krok jest konieczny, ponieważ domyślnie program Visual Studio ustawia katalog roboczy na katalog główny projektu, a nie lokalizację pliku startowego (*python3\contemplate_koans.py*, który można zobaczyć również we właściwościach projektu). Kod programu wyszukuje plik *koans.txt* w folderze roboczym, więc bez zmiany tej wartości pojawia się błąd środowiska uruchomieniowego.

    ![Ustawianie katalogu roboczego dla projektu języka Python](media/projects-set-working-directory.png)

1. Naciśnij **klawisz Ctrl**+**F5** lub wybierz **opcję Debugowanie** > **start bez debugowania,** aby uruchomić program. Jeśli widzisz **FileNotFoundError** dla *koans.txt,* sprawdź ustawienie katalogu roboczego zgodnie z opisem w poprzednim kroku.

1. Gdy program działa pomyślnie, wyświetla błąd potwierdzenia w wierszu 17 *python3/koans/about_asserts.py*. Jest to celowe: program jest przeznaczony do nauczania Pythona poprzez poprawienie wszystkich zamierzonych błędów. (Więcej szczegółów można znaleźć na [Ruby Koans](https://rubykoans.com/), co zainspirowało Pythona Koansa.

    ![Pierwsze wyjście z programu Python koans](media/koans-output.png)

1. Otwórz *python3/koans/about_asserts.py,* przechodząc do niego w **Eksploratorze rozwiązań** i klikając dwukrotnie plik. Należy zauważyć, że numery wierszy nie są wyświetlane domyślnie w edytorze. Aby to zmienić, wybierz pozycję**Opcje** **narzędzi** > , wybierz pozycję **Pokaż wszystkie ustawienia** u dołu okna dialogowego, a następnie przejdź do pozycji Edytor >  **tekstu****Python** > **Ogólne** i wybierz pozycję **Numery wierszy:**

    ![Włączanie numeru wiersza dla plików Języka Python](media/options-general-line-numbers.png)

1. Popraw błąd, zmieniając `False` argument w wierszu `True`17 na . Wiersz powinien brzmieć następująco:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Uruchom program ponownie. Jeśli program Visual Studio ostrzega o błędach, **odpowiedz** tak, aby kontynuować uruchamianie kodu. Następnie widać, że pierwszy czek przechodzi i program zatrzymuje się na następnym koan. Kontynuuj poprawianie błędów i program ponownie, jak chcesz.

> [!Important]
> W tym przewodniku Szybki start utworzono bezpośredni klon repozytorium *python_koans* w usłudze GitHub. Takie repozytorium jest chronione przez jego autora przed bezpośrednimi zmianami, więc próba zatwierdzenia zmian w repozytorium kończy się niepowodzeniem. W praktyce deweloperzy zamiast rozwidlić takie repozytorium do własnego konta GitHub, wprowadzić zmiany tam, a następnie utworzyć żądania ściągnięcia, aby przesłać te zmiany do oryginalnego repozytorium. Jeśli masz własny widelec, użyj jego adresu URL zamiast oryginalnego adresu URL repozytorium używanego wcześniej.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z Pythonem w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Ręczne identyfikowanie istniejącego interpretera języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Jak zainstalować pomoc techniczną języka Python w programie Visual Studio w systemie Windows](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)
