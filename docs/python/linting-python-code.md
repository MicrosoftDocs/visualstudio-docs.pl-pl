---
title: Korzystanie z PyLint dla kodu w języku Python
description: Uruchom PyLint w programie Visual Studio, aby sprawdzić problemy w kodzie języka Python, łącznie z opcjami wiersza polecenia, aby dostosować Zaznaczanie błędów.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d410fd7575b6f71f272f6924d15249f89aa6ebcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540104"
---
# <a name="use-pylint-to-check-python-code"></a>Sprawdzanie kodu w języku Python za pomocą PyLint

[PyLint](https://www.pylint.org/), powszechnie używane narzędzie sprawdzające błędy w kodzie języka Python i zachęca do używania dobrych wzorców kodowania języka Python, jest zintegrowane z Visual Studio dla projektów Python.

## <a name="run-pylint"></a>Uruchom PyLint

Po prostu kliknij prawym przyciskiem myszy projekt w języku Python w **Eksplorator rozwiązań** i wybierz polecenie **Python**  >  **Run PyLint**:

![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

Za pomocą tego polecenia zostanie wyświetlony komunikat z prośbą o zainstalowanie PyLint w aktywnym środowisku, jeśli jeszcze nie istnieje.

PyLint ostrzeżenia i błędy pojawiają się w oknie **Lista błędów** :

![Lista błędów PyLint](media/code-pylint-error-list.png)

Dwukrotne kliknięcie błędu spowoduje bezpośrednie przejście do kodu źródłowego, który wygenerował problem.

> [!Tip]
> Aby uzyskać szczegółową listę wszystkich komunikatów wyjściowych PyLint, zobacz temat [PyLint Feature Reference](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) .

## <a name="set-pylint-command-line-options"></a>Ustawianie opcji wiersza polecenia PyLint

W sekcji [Opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) w dokumentacji PyLint opisano sposób sterowania zachowaniem PyLint za pomocą pliku konfiguracji *pylintrc* . Taki plik można umieścić w katalogu głównym projektu języka Python w programie Visual Studio lub w innym miejscu, w zależności od tego, jak często mają być stosowane te ustawienia (zobacz [Opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) , aby uzyskać szczegółowe informacje).

Na przykład aby pominąć ostrzeżenia "brakujące docstring" widoczne w poprzednim obrazie z plikiem *. pylintrc* w projekcie, wykonaj następujące czynności:

1. W wierszu polecenia przejdź do katalogu głównego projektu (w którym znajduje się plik *. pyproj* ) i uruchom następujące polecenie, aby wygenerować plik konfiguracji z komentarzem:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. W programie Visual Studio Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**  >  **istniejący element**, przejdź do nowego pliku *. pylintrc* , wybierz go, a następnie wybierz pozycję **Dodaj**.

1. Otwórz plik do edycji, który ma kilka ustawień, z którymi można korzystać. Aby wyłączyć ostrzeżenie, odszukaj `[MESSAGES CONTROL]` sekcję, a następnie Znajdź `disable` ustawienie w tej sekcji. Istnieje długi ciąg konkretnych komunikatów, do których można dołączać wybrane ostrzeżenia. W poniższym przykładzie Dołącz `,missing-docstring` (łącznie z przecinkiem delineating).

1. Zapisz plik *. pylintrc* i ponownie uruchom PyLint, aby zobaczyć, że ostrzeżenia są teraz pomijane.

> [!Tip]
> Aby użyć pliku *. pylintrc* z udziału sieciowego, Utwórz zmienną środowiskową o nazwie `PYLINTRC` z wartością nazwy pliku w udziale sieciowym przy użyciu ścieżki UNC lub zmapowanej litery dysku. Na przykład `PYLINTRC=\\myshare\python\.pylintrc`.
