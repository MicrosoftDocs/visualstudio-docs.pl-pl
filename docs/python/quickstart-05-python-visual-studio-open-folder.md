---
title: Szybki Start — Otwieranie folderu kodu w języku Python
description: W tym przewodniku szybki start otwierasz i uruchamiasz kod w języku Python z folderu bez użycia projektu programu Visual Studio (tylko Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: a7bf174191a6a2fb013aa3d25880b01bc2e7f070
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801675"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Szybki Start: otwieranie i uruchamianie kodu w języku Python w folderze

Po [zainstalowaniu obsługi języka Python w programie Visual studio 2019](installing-python-support-in-visual-studio.md)można łatwo uruchomić istniejący kod w języku Python w programie visual Studio 2019 bez tworzenia projektu programu Visual Studio.

> [!Note]
> Program Visual Studio 2017 i jego wcześniejsze wersje wymagają utworzenia projektu programu Visual Studio do uruchamiania kodu w języku Python, który można łatwo użyć w wbudowanym szablonie projektu. Zobacz [Szybki Start: Tworzenie projektu w języku Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. W tym instruktażu można użyć dowolnego folderu z kodem języka Python, który lubisz. Aby postępować zgodnie z poniższym przykładem, Sklonuj repozytorium gregmalcolm/python_koans GitHub na komputerze przy użyciu polecenia `git clone https://github.com/gregmalcolm/python_koans` w odpowiednim folderze.

1. Uruchom program Visual Studio 2019 i w oknie Start wybierz pozycję **Otwórz** w dolnej części kolumny **wprowadzenie** . Alternatywnie, jeśli masz już uruchomiony program Visual Studio, wybierz polecenie **plik**  >  **Otwórz**  >  **folder** zamiast tego.

    ![Ekran startowy programu Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Przejdź do folderu zawierającego kod w języku Python, a następnie wybierz **pozycję Wybierz folder**. Jeśli używasz kodu python_koans, upewnij się, że wybrano `python3` folder w folderze klonowania.

    ![Okno dialogowe Wybieranie folderu z polecenia Otwórz folder](media/quickstart-open-folder/02-select-folder.png)

1. Program Visual Studio wyświetla folder w **Eksplorator rozwiązań** w widoku o nazwie **folder**. Możesz rozwijać i zwijać foldery przy użyciu strzałek na lewej krawędzi nazw folderów:

    ![Kontrolki rozszerzające i zwijające foldery w Eksplorator rozwiązań](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Podczas otwierania folderu języka Python program Visual Studio tworzy kilka ukrytych folderów do zarządzania ustawieniami związanymi z projektem. Aby wyświetlić te foldery (oraz wszystkie inne ukryte pliki i foldery, takie jak folder *. git* ), wybierz przycisk paska narzędzi **Pokaż wszystkie pliki** :

    ![Widok ukrytych folderów w Eksplorator rozwiązań](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Aby uruchomić kod, należy najpierw zidentyfikować plik startowy lub podstawowy programu. W przykładzie przedstawionym tutaj *contemplate-koans.py*plik startowy. Kliknij prawym przyciskiem myszy ten plik i wybierz polecenie **Ustaw jako element startowy**.

    ![Ustawianie elementu startowego w Eksplorator rozwiązań](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Jeśli element startowy nie znajduje się w katalogu głównym otwartego folderu, należy również dodać wiersz do pliku JSON konfiguracji uruchamiania zgodnie z opisem w sekcji, [ustawić katalog roboczy](#set-a-working-directory).

1. Uruchom kod, naciskając klawisz **Ctrl** + **F5** lub wybierając pozycję **Debuguj**  >  **Uruchom bez debugowania**. Możesz również wybrać przycisk paska narzędzi, który pokazuje element startowy z przyciskiem odtwarzania, który uruchamia kod w debugerze programu Visual Studio. We wszystkich przypadkach program Visual Studio wykryje, że element startowy jest plikiem języka Python, więc automatycznie uruchamia kod w domyślnym środowisku języka Python. (To środowisko jest widoczne po prawej stronie elementu startowego na pasku narzędzi).

    ![Przycisk paska narzędzi uruchamiania debugera](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Dane wyjściowe programu są wyświetlane w osobnym oknie poleceń:

    ![Okno danych wyjściowych do uruchamiania kodu w języku Python](media/quickstart-open-folder/08-result-window.png)

1. Aby uruchomić kod w innym środowisku, wybierz to środowisko z kontrolki listy rozwijanej na pasku narzędzi, a następnie ponownie uruchom element startowy.

1. Aby zamknąć folder w programie Visual Studio, wybierz **File**  >  polecenie menu**Zamknij folder** .

## <a name="set-a-working-directory"></a>Ustawianie katalogu roboczego

Domyślnie program Visual Studio uruchamia projekt języka Python otwarty jako folder w katalogu głównym tego samego folderu. Jednak kod w projekcie może założyć, że język Python jest uruchamiany w podfolderze. Załóżmy na przykład, że otworzysz folder główny repozytorium python_koans, a następnie ustawisz plik *python3/koans. PR* jako element startowy. Po uruchomieniu kodu zostanie wyświetlony komunikat o błędzie, że nie można odnaleźć pliku *koans.txt* . Ten błąd występuje, ponieważ *contemplate-koans.py* zakłada, że język Python jest uruchamiany w folderze *python3* , a nie w katalogu głównym repozytorium.

W takich przypadkach należy również dodać wiersz do pliku JSON konfiguracji uruchamiania, aby określić katalog roboczy:

1. Kliknij prawym przyciskiem myszy plik startowy języka Python (*. PR*) w **Eksplorator rozwiązań** i wybierz pozycję **Ustawienia debugowania i uruchamiania**.

    ![Polecenie Ustawienia debugowania i uruchamiania dla pliku języka Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. W wyświetlonym oknie dialogowym **Wybierz debuger** wybierz pozycję **domyślne** , a następnie wybierz **pozycję Wybierz**.

    ![Polecenie Ustawienia debugowania i uruchamiania dla pliku języka Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Jeśli nie widzisz **Domyślnie** jako wyboru, upewnij się, że wybrano plik Python *. PR* podczas wybierania polecenia **Debuguj i Uruchom ustawienia** . Program Visual Studio używa typu pliku, aby określić, które opcje debugera mają być wyświetlane.

1. Program Visual Studio otwiera plik o nazwie *launch.vs.json*, który znajduje się w folderze Hidden *. vs* . Ten plik zawiera opis kontekstu debugowania dla projektu. Aby określić katalog roboczy, należy dodać wartość dla `"workingDirectory"` , jak w  `"workingDirectory": "python3"` przypadku języka Python — koans przykład:

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

1. Zapisz plik i ponownie uruchom program, który jest teraz uruchamiany w określonym folderze.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: współpraca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Szybki Start: Tworzenie projektu w języku Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Szybki Start: Tworzenie projektu w języku Python na podstawie repozytorium](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Ręcznie Zidentyfikuj istniejący interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
