---
title: Użyj kodu PyLint dla języka Python
description: Uruchom PyLint w programie Visual Studio, aby sprawdzić problemy w kodzie języka Python, w tym opcje wiersza polecenia, aby dostosować linting.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf503cff7d8de2c00a93385113de05de00059390
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956819"
---
# <a name="use-pylint-to-check-python-code"></a>Sprawdzanie kodu języka Python za pomocą pylinta

[PyLint](https://www.pylint.org/), powszechnie używane narzędzie, które sprawdza błędy w kodzie Pythona i zachęca do dobrych wzorców kodowania Pythona, jest zintegrowane z Programem Visual Studio dla projektów Pythona.

## <a name="run-pylint"></a>Uruchom PyLint

Wystarczy kliknąć prawym przyciskiem myszy projekt Języka Python w **Eksploratorze rozwiązań** i wybrać **Python** > **Run PyLint:**

![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

Za pomocą tego polecenia monituje o zainstalowanie pylint w aktywnym środowisku, jeśli nie jest jeszcze obecny.

Ostrzeżenia i błędy PyLint są wyświetlane w oknie **Lista błędów:**

![Lista błędów PyLint](media/code-pylint-error-list.png)

Dwukrotne kliknięcie błędu prowadzi bezpośrednio do kodu źródłowego, który wygenerował problem.

> [!Tip]
> Zobacz [odwołanie funkcji PyLint, aby](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) uzyskać szczegółową listę wszystkich komunikatów wyjściowych PyLint.

## <a name="set-pylint-command-line-options"></a>Ustawianie opcji wiersza polecenia PyLint

W sekcji [Opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) w dokumentacji PyLint opisano sposób kontrolowania zachowania PyLinta za pomocą pliku konfiguracyjnego *pylintrc.* Taki plik można umieścić w katalogu głównym projektu języka Python w programie Visual Studio lub w innym miejscu, w zależności od tego, jak szeroko mają być stosowane te ustawienia (szczegółowe informacje można znaleźć w [opcjach wiersza polecenia).](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)

Na przykład, aby pominąć ostrzeżenia "brakujące docstrowanie" wyświetlane na poprzednim obrazie z plikiem *pylintrc* w projekcie, wykonaj następujące czynności:

1. W wierszu polecenia przejdź do katalogu głównego projektu (który zawiera plik *pyproj)* i uruchom następujące polecenie, aby wygenerować skomentowany plik konfiguracyjny:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. W Eksploratorze rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj** > **istniejący element**, przejdź do nowego pliku *pylintrc,* wybierz go i wybierz polecenie **Dodaj**.

1. Otwórz plik do edycji, który ma kilka ustawień, z którymi możesz pracować. Aby wyłączyć ostrzeżenie, `[MESSAGES CONTROL]` zlokalizuj `disable` sekcję, a następnie zlokalizuj ustawienie w tej sekcji. Istnieje długi ciąg określonych wiadomości, do których można dołączyć ostrzeżenia, które chcesz. W tym przykładzie `,missing-docstring` dołącz (w tym przecinek rozkreślający).

1. Zapisz plik *pylintrc* i uruchom pylint ponownie, aby zobaczyć, że ostrzeżenia są teraz pomijane.

> [!Tip]
> Aby użyć pliku *pylintrc* z udziału sieciowego, `PYLINTRC` utwórz zmienną środowiskową o nazwie o wartości nazwy pliku w udziale sieciowym przy użyciu ścieżki UNC lub zamapowanych liter dysku. Na przykład `PYLINTRC=\\myshare\python\.pylintrc`.
