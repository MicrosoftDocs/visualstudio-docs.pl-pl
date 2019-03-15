---
title: Przewodnik Szybki Start — otwórz folder kodu języka Python
description: W tym przewodniku Szybki Start, Otwórz i uruchamianie kodu języka Python z folderu bez korzystania z projektu programu Visual Studio (Visual Studio 2019 tylko).
ms.date: 03/12/2019
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: 6cf4e15ec464b1d438245cd7bfe254d9464ad2a6
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57986954"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Szybki start: Otwórz i uruchamianie kodu języka Python w folderze

Po [zainstalowane obsługi języka Python w programie Visual Studio 2019](installing-python-support-in-visual-studio.md), można łatwo uruchomić istniejący kod języka Python w programie Visual Studio 2019 r bez tworzenia projektu programu Visual Studio.

> [!Note]
> Visual Studio 2017 i wcześniejszych wymagane do tworzenia projektu programu Visual Studio, aby uruchomić kod języka Python, który można łatwo czy przy użyciu szablonu projektu wbudowanych. Zobacz [Szybki Start: Tworzenie projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. W ramach tego przewodnika można użyć dowolnego folderu przy użyciu kodu w języku Python, który chcesz. Aby skorzystać z tym przykładzie, sklonuj repozytorium GitHub gregmalcolm/python_koans do komputera za pomocą polecenia `git clone https://github.com/gregmalcolm/python_koans` w odpowiedni folder.

1. Uruchom program Visual Studio 2019 r, a następnie na ekranie startowym wybierz **Otwórz** w dolnej części **wprowadzenie** kolumny. Alternatywnie Jeśli masz już program Visual Studio działa, wybierz **pliku** > **Otwórz** > **folderu** zamiast tego polecenia.

    ![Ekran startowy programu Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Przejdź do folderu zawierającego kod w języku Python, a następnie wybierz **wybierz Folder**. Jeśli używasz kodu python_koans upewnij się wybrać `python3` folder wewnątrz folderu klonowania.

    ![Okno dialogowe Wybierz Folder z polecenia Otwórz Folder](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio Wyświetla folderu w **Eksploratora rozwiązań** w tak zwany **widok folderu**. Można rozwijać i zwijać folderów za pomocą strzałki przy krawędziach po lewej stronie nazwy folderu:

    ![Określa, aby rozwinąć lub zwinąć folderów w Eksploratorze rozwiązań](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Podczas otwierania folderu języka Python, Visual Studio tworzy kilka folderach ukrytych, aby zarządzać ustawieniami związanych z projektem. Aby wyświetlić te foldery (i innych ukryte pliki i foldery, takie jak *.git* folderu), wybierz opcję **Pokaż wszystkie pliki** przycisku paska narzędzi:

    ![Wyświetlanie ukrytych folderów w Eksploratorze rozwiązań](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Aby uruchomić kod, należy najpierw zidentyfikować uruchamiania lub pliku głównego programu. W tym przykładzie, plik startowy *rozważają koans.py*. Kliknij prawym przyciskiem myszy, plik, a następnie zaznacz **Ustaw jako element startowy**.

    ![Ustawienie elementu startowego w oknie Eksploratora rozwiązań](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Jeśli Twoje element startowy nie znajduje się w katalogu głównym folderu został otwarty, należy również dodać wiersz do pliku JSON konfiguracji uruchamiania, zgodnie z opisem w sekcji [ustawić katalogu roboczego](#set-a-working-directory).

1. Uruchom kod, naciskając klawisz **Ctrl**+**F5** lub wybierając **debugowania** > **Uruchom bez debugowania**. Możesz również wybrać przycisk na pasku narzędzi, który pokazuje element startowy z przycisk odtwarzania, która uruchamia kod w debugerze programu Visual Studio. We wszystkich przypadkach Visual Studio wykryje, że Twoje element startowy plik w języku Python, więc automatycznie uruchamia kod w domyślnym środowisku Python. (Środowisku znajduje się na prawo od elementu startowego na pasku narzędzi).

    ![Uruchom debuger przycisku paska narzędzi](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Dane wyjściowe programu pojawia się w oknie osobne polecenie:

    ![Okno danych wyjściowych do uruchamiania kodu w języku Python](media/quickstart-open-folder/08-result-window.png)

1. Aby uruchomić kod w innym środowisku, wybierz środowisko z listy rozwijanej kontrolki na pasku narzędzi, a następnie ponownie uruchom element startowy.

1. Aby zamknąć folderu w programie Visual Studio, wybierz **pliku** > **Zamknij folder** polecenia menu.

## <a name="set-a-working-directory"></a>Ustaw katalog roboczy

Domyślnie program Visual Studio uruchamia otwarty jako folder w tym samym folderze głównym projektu języka Python. Kod w projekcie, jednak zakładać, że Python jest uruchamiany w podfolderze. Załóżmy na przykład, otwórz folder główny repozytorium python_koans, a następnie ustaw *języku python3/rozważają koans.py* pliku jako element startowy. Jeśli następnie uruchomić kod, zostanie wyświetlony błąd, *koans.txt* nie można odnaleźć pliku. Ten błąd występuje, ponieważ *rozważają koans.py* przyjęto założenie, że Python jest uruchamiany *języku python3* folder, a nie w katalogu głównym repozytorium.

W takich przypadkach można również dodać wiersz do pliku JSON konfiguracji uruchamiania, aby określić katalog roboczy:

1. Kliknij prawym przyciskiem myszy języka Python (*.py*) plik startowy w **Eksploratora rozwiązań** i wybierz **ustawienia debugowania i uruchamiania**.

    ![Ustawienia debugowania i uruchamiania poleceń na plik w języku Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. W **wybierz debuger** zostanie wyświetlone okno dialogowe, wybierz **domyślne** , a następnie wybierz **wybierz**.

    ![Ustawienia debugowania i uruchamiania poleceń na plik w języku Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Jeśli nie widzisz **domyślne** jako opcję, upewnij się, że użytkownik kliknął prawym przyciskiem myszy Python *.py* plików podczas wybierania **ustawienia debugowania i uruchamiania** polecenia. Visual Studio używa typu pliku, można ustalić podczas opcje debugera do wyświetlenia.

1. Visual Studio otwiera plik o nazwie *launch.vs.json*, który znajduje się w ukrytym *.vs* folderu. W tym pliku opisano kontekst debugowania dla projektu. Aby określić katalog roboczy, Dodaj wartość `"workingDirectory"`, jak w `"workingDirectory": "python3"` przykład python koans:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Zapisz plik i ponownie uruchom program, który obecnie działa we wskazanym folderze.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Szybki start: Tworzenie projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Szybki start: Tworzenie projektu języka Python z repozytorium](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Ręcznie Zidentyfikuj istniejące interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
