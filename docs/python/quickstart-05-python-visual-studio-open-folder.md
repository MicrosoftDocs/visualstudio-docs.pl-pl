---
title: Szybki start — otwieranie folderu kodu języka Python
description: W tym przewodniku Szybki start można otworzyć i uruchomić kod języka Python z folderu bez użycia projektu programu Visual Studio (tylko visual studio 2019).
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
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431159"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Szybki start: otwieranie i uruchamianie kodu języka Python w folderze

Po [zainstalowaniu obsługi języka Python w programie Visual Studio 2019](installing-python-support-in-visual-studio.md)można łatwo uruchomić istniejący kod języka Python w programie Visual Studio 2019 bez tworzenia projektu programu Visual Studio.

> [!Note]
> Visual Studio 2017 i wcześniej wymagają utworzenia projektu programu Visual Studio do uruchamiania kodu języka Python, co można łatwo zrobić przy użyciu wbudowanego szablonu projektu. Zobacz [Szybki start: tworzenie projektu języka Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. W tym instruktażu możesz użyć dowolnego folderu z kodem Języka Python, który Ci się podoba. Aby wykonać wraz z przykładem pokazanym tutaj, sklonować gregmalcolm/python_koans repozytorium `git clone https://github.com/gregmalcolm/python_koans` GitHub do komputera za pomocą polecenia w odpowiednim folderze.

1. Uruchom program Visual Studio 2019 i w oknie startowym wybierz pozycję **Otwórz** u dołu kolumny **Wprowadzenie.** Alternatywnie, jeśli program Visual Studio jest już uruchomiony, wybierz polecenie **Folder** > **otwierania** > **Folder** pliku.

    ![Ekran startowy programu Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Przejdź do folderu zawierającego kod języka Python, a następnie wybierz pozycję **Wybierz folder**. Jeśli używasz kodu python_koans, zaznacz `python3` folder w folderze klonowania.

    ![Okno dialogowe Wybieranie folderu z polecenia Otwórz folder](media/quickstart-open-folder/02-select-folder.png)

1. Program Visual Studio wyświetla folder w **Eksploratorze rozwiązań** w **widoku folderów.** Foldery można rozwijać i zwijać za pomocą strzałek na lewej krawędziach nazw folderów:

    ![Formanty do rozwijania i zwijania folderów w Eksploratorze rozwiązań](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Podczas otwierania folderu Języka Python program Visual Studio tworzy kilka ukrytych folderów do zarządzania ustawieniami związanymi z projektem. Aby wyświetlić te foldery (i wszystkie inne ukryte pliki i foldery, takie jak folder *.git),* wybierz przycisk **Pokaż wszystkie pliki** na pasku narzędzi:

    ![Widok ukrytych folderów w Eksploratorze rozwiązań](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Aby uruchomić kod, należy najpierw zidentyfikować plik startowy lub podstawowy plik programu. W przykładzie pokazanym w tym miejscu plik startowy *contemplate-koans.py*. Kliknij prawym przyciskiem myszy ten plik i wybierz pozycję **Ustaw jako element startowy**.

    ![Ustawianie elementu startowego w Eksploratorze rozwiązań](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Jeśli element startowy nie znajduje się w katalogu głównym otwartego folderu, należy również dodać wiersz do pliku JSON konfiguracji uruchamiania, jak opisano w [sekcji, Ustaw katalog roboczy](#set-a-working-directory).

1. Uruchom kod, naciskając klawisz **Ctrl**+**F5** lub wybierając **debugowanie** > **start bez debugowania**. Można również wybrać przycisk paska narzędzi, który pokazuje element startowy z przyciskiem odtwarzania, który uruchamia kod w debugerze programu Visual Studio. We wszystkich przypadkach visual studio wykrywa, że element startowy jest plik python, więc automatycznie uruchamia kod w domyślnym środowisku Pythona. (To środowisko jest wyświetlane po prawej stronie elementu startowego na pasku narzędzi).

    ![Przycisk Uruchamianie paska narzędzi debugera](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Dane wyjściowe programu są wyświetlane w osobnym oknie polecenia:

    ![Okno danych wyjściowych do uruchamiania kodu języka Python](media/quickstart-open-folder/08-result-window.png)

1. Aby uruchomić kod w innym środowisku, wybierz to środowisko z formantu rozwijanego na pasku narzędzi, a następnie uruchom element startowy ponownie.

1. Aby zamknąć folder w programie Visual Studio, wybierz polecenie menu**folderu Zamknij** **plik.** > 

## <a name="set-a-working-directory"></a>Ustawianie katalogu roboczego

Domyślnie program Visual Studio uruchamia projekt języka Python otwarty jako folder w katalogu głównym tego samego folderu. Kod w projekcie, jednak może zakładać, że Python jest uruchamiany w podfolderze. Załóżmy na przykład, że otworzysz folder główny repozytorium python_koans, a następnie ustaw *plik python3/contemplate-koans.py* jako element startowy. Jeśli następnie uruchomisz kod, zostanie wyświetlony błąd, którego nie można odnaleźć pliku *koans.txt.* Ten błąd *występuje,* ponieważ contemplate-koans.py zakłada, że Python jest uruchamiany w *folderze python3,* a nie w katalogu głównym repozytorium.

W takich przypadkach należy również dodać wiersz do pliku JSON konfiguracji uruchamiania, aby określić katalog roboczy:

1. Kliknij prawym przyciskiem myszy plik startowy Języka Python (*py*) w **Eksploratorze rozwiązań** i wybierz polecenie **Debugowanie i uruchom ustawienia**.

    ![Polecenie Debugowanie i uruchamianie ustawień dla pliku języka Python](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. W wyświetlonym oknie dialogowym **Wybieranie debugera** wybierz pozycję **Domyślne,** a następnie wybierz pozycję **Wybierz**.

    ![Polecenie Debugowanie i uruchamianie ustawień dla pliku języka Python](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Jeśli nie widzisz **opcji Domyślne** jako wybór, upewnij się, że kliknięno plik *py* pythona prawym przyciskiem myszy podczas wybierania polecenia **Debugowanie i Uruchamianie ustawień.** Visual Studio używa typu pliku do określenia podczas debugera opcje do wyświetlenia.

1. Program Visual Studio otwiera plik o nazwie *launch.vs.json*, który znajduje się w ukrytym folderze *.vs.* Ten plik opisuje kontekst debugowania dla projektu. Aby określić katalog roboczy, `"workingDirectory"`dodaj wartość `"workingDirectory": "python3"` dla , jak w przypadku python-koans przykład:

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

1. Zapisz plik i uruchom program ponownie, który teraz działa w określonym folderze.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z Pythonem w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Szybki start: tworzenie projektu języka Python na podstawie istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Szybki start: tworzenie projektu języka Python z repozytorium](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Ręczne identyfikowanie istniejącego interpretera języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
