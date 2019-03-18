---
title: Okno interaktywne języka Python (REPL)
description: Okno interaktywne (REPL) służący do szybkiego opracowywania kodu języka Python w programie Visual Studio.
ms.date: 02/11/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: f7d4b36003d097fc4750b80f62fc1267908b8c0b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151144"
---
# <a name="work-with-the-python-interactive-window"></a>Praca z okno interaktywne języka Python

Program Visual Studio udostępnia okno interaktywne odczytu oceny — Drukuj pętli (REPL) dla każdego środowiska Python, które poprawia REPL, możesz uzyskać za pomocą *python.exe* w wierszu polecenia. **Interactive** okna (otwartej z **widoku** > **Windows inne** > **&lt;środowiska&gt; Interaktywne** poleceń menu) pozwala wprowadzić dowolny kod Python i zobaczyć wyniki wprowadzenia. Ten sposób kodowania pomaga informacje i eksperymentować z interfejsów API i bibliotek oraz interaktywnie tworzyć działającego kodu, aby uwzględnić w swoich projektach.

![Okno interaktywne języka Python](media/interactive-window.png)

Program Visual Studio ma kilka trybów REPL języka Python do wyboru:

| REPL | Opis | Edytowanie | Debugowanie | Obrazy |
| --- | --- | --- | --- | --- |
| Standardowa | Domyślne REPL, rozmowy bezpośrednio języka Python. | Standard edycji (wielowierszowe itp.). | Tak, za pośrednictwem `$attach` | Nie |
| Debugowanie | Domyślne REPL, rozmowy do debugowanego procesu języka Python | Edycja standardowa | Debugowania wyłącznie kodu | Nie |
| IPython | Rozmawiają zaplecza IPython REPL | Program IPython poleceń, udogodnienia Pylab | Nie | Tak, bezpośrednio w REPL |
| Program IPython bez Pylab | Rozmawiają zaplecza IPython REPL | Standardowa IPython | Nie | Tak, strona potwierdzenia |

W tym artykule opisano **standardowa** i **debugowania** REPL tryby. Szczegółowe informacje na temat trybów IPython, [Użyj środowiska IPython REPL](interactive-repl-ipython.md).

Szczegółowy przewodnik dotyczący wraz z przykładami, w tym interakcji z edytorem takich jak **Ctrl**+**Enter**, zobacz [samouczek krok 3: Korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otwórz okno interaktywne

Istnieje kilka sposobów, aby otworzyć **Interactive** okna dla środowiska.

Po pierwsze, przejdź do okna środowiska Python (**widoku** > **Windows inne** > **środowiska Python** lub **Ctrl** + **K** > **Ctrl**+**`**) i wybierz **interakcyjnego otwarte Okno** polecenia lub przycisku dla wybranego środowiska.

![Interaktywne łącza okna w oknie środowiska Python](media/interactive-window-opening.png)

Po drugie w dolnej części **widoku** > **Windows inne** menu jest **oknie interakcyjnym środowiska Python** polecenie, aby uzyskać środowisko domyślne, a także jako polecenie, aby przełączyć się do **środowisk** okna:

![Menu okna interaktywnego elementy w widoku > inne Windows](media/interactive-window-menu.png)

Po trzecie, możesz otworzyć **Interactive** okno na plik startowy w projekcie lub autonomicznego pliku, wybierając **debugowania** > **Execute \<projektu | Plik > w języku Python w trybie interaktywnym** polecenia menu (**Shift**+**Alt**+**F5**):

![Wykonaj Project w menu Python Interactive](media/interactive-execute-project.png)

Na koniec wybierz kod w pliku i użyć [ **Wyślij do środowiska interaktywnego** polecenia](#send-to-interactive-command) opisane poniżej.

## <a name="interactive-window-options"></a>Opcje okna interaktywnego

Można kontrolować różne aspekty **Interactive** okna za pośrednictwem **narzędzia** > **opcje** > **Python**  >  **Interaktywne Windows** (zobacz [opcje](python-support-options-and-settings-in-visual-studio.md)):

![Opcje okno interaktywne języka Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Za pomocą okna interakcyjnego

Raz **Interactive** jest otwarte okno, możesz rozpocząć wprowadzanie kodu wiersz po wierszu na **\> \> \>** wiersza. **Interactive** okna wykonuje każdy wiersz, wprowadź go, który obejmuje importowanie modułów, definiowanie zmiennych i tak dalej:

![Okno interaktywne języka Python](media/interactive-window.png)

Wyjątkiem jest, kiedy są potrzebne dodatkowe wiersze kodu, aby pełną instrukcję, takie jak czas `for` instrukcja kończy się średnikiem, jak pokazano powyżej. W takich przypadkach wiersz zmieni się na **...**  wskazująca, że należy wprowadzić dodatkowe wiersze do bloku, jak pokazano w wierszach czwarty i piąty na rysunku powyżej. Po naciśnięciu klawisza **Enter** w pustym wierszu **Interactive** okno zamyka blok i uruchamia je w interpretera.

> [!Tip]
> **Interactive** okna poprawia zwykle REPL wiersza polecenia środowiska, automatycznie wcięcia instrukcji, które należą do zakresu otaczającego języka Python. Jego historię (przypomnieć o strzałkę w górę) zapewnia również wielowierszowy elementów REPL wiersza polecenia stanowi tylko pojedynczych wierszy.

<a name="meta-commands"></a> **Interactive** okna obsługuje również kilka poleceń meta. Wszystkie polecenia meta rozpoczynać `$`, i możesz wpisać `$help` w celu uzyskania listy poleceń meta i `$help <command>` można pobrać szczegółów użycia dla określonego polecenia.

| Meta-polecenia | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, co jest przydatne w komentarz kod w całej sesji. |
| `$attach` | Dołącza debuger programu Visual Studio do procesów okien REPL, by włączyć debugowanie. |
| `$cls`, `$clear` | Czyści zawartość okna edytora, pozostawiając bez zmian historii i wykonywania kontekstu. |
| `$help` | Wyświetlanie listy poleceń lub pomoc dotyczącą określonego polecenia. |
| `$load` | Ładuje poleceń z pliku i uruchamia do czasu ukończenia. |
| `$mod` | Zmienia bieżący zakres na nazwę określonego modułu. |
| `$reset` | Resetuje środowisko wykonawcze do stanu początkowego, ale przechowuje historię. |
| `$wait` | Czeka na co najmniej określoną liczbę milisekund. |

Polecenia są również extensible przez rozszerzenia programu Visual Studio przez implementację i eksportowanie `IInteractiveWindowCommand` ([przykład](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Przełącz zakresów

Domyślnie **Interactive** okna dla projektu jest ograniczone do projektu plik startowy, tak, jakby uruchomieniu z wiersza polecenia. Dla plików autonomicznych zakresów go do tego pliku. W dowolnym momencie podczas sesji REPL, jednak menu rozwijane u góry **Interactive** okno pozwala na zmianę zakresu:

![Okno interaktywne zakresów](media/interactive-scopes.png)

Po zaimportowaniu modułu, na przykład wpisanie `import importlib`, opcje są wyświetlane w liście rozwijanej, aby przełączyć się do dowolnego zakresu, w tym module. Wiadomości w **Interactive** okno wskazuje także nowego zakresu, dzięki czemu można śledzić, jak stało się do pewnego stanu podczas sesji.

Wprowadzanie `dir()` w zakresie Wyświetla prawidłowych identyfikatorów, w tym zakresie, w tym nazwy funkcji, klasy i zmienne. Na przykład za pomocą `import importlib` następuje `dir()` zawiera następujące czynności:

![Okno interaktywne w zakresie importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Wysyłać polecenie interaktywne

Oprócz pracy w ramach **Interactive** okna bezpośrednio, można wybrać kod w edytorze, kliknij prawym przyciskiem myszy i wybierz polecenie **Wyślij do środowiska interaktywnego** lub naciśnij **Ctrl** + **Wprowadź**.

![Wyślij do polecenia menu interaktywne](media/interactive-send-to.png)

To polecenie jest przydatne w przypadku tworzenia kodu iteracji lub ewolucyjny, łącznie z testowaniem kodu podczas jego tworzenia. Na przykład raz wysłanych do fragment kodu do **Interactive** okna i widoczne dane wyjściowe, możesz nacisnąć klawisze strzałki w górę pokazuj kod, zmodyfikuj go i szybko przetestować, naciskając klawisz **Ctrl** + **Wprowadź**. (Naciskając klawisz **Enter** na końcu danych wejściowych go uruchomi, ale naciśnięcie **Enter** trakcie wprowadzania wstawia nowy wiersz.) Gdy masz kod, który ma, można go łatwo skopiować do pliku projektu.

> [!Tip]
> Domyślnie program Visual Studio usuwa **>>>** i **...** REPL monity podczas wklejania kodu z **Interactive** okna do edytora. To zachowanie można zmienić na **narzędzia** > **opcje** > **edytora tekstów** > **Python**  >  **Zaawansowane** kartę za pomocą **Wklej usuwa monitów REPL** opcji. Zobacz [opcje - różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

Korzystając z pliku z kodem jak Notatnik, często mają małych blokach kodu, nad którym chcesz wysłać wszystkie na raz. Aby zgrupować kod, należy oznaczyć kod jako *komórkę kodu* , dodając komentarz, począwszy od `#%%` na początku komórka, która kończy się poprzedniego. Komórki kodu może być zwiniętego i rozwinięte i korzystać z funkcji **Ctrl**+**Enter** wewnątrz kodu komórka wysyła cały komórce **Interactive** okna i przenosi do kolejny.

Program Visual Studio wykrywa także komórki kodu, począwszy od komentarze, takich jak `# In[1]:`, czyli formatu podczas eksportowania notesu programu Jupyter jako plik w języku Python. Wykrywanie ułatwia uruchamianie notesu z [notesów usługi Azure](https://notebooks.azure.com/) , pobierając jako plik w języku Python, otwierając w programie Visual Studio i za pomocą **Ctrl**+**Enter**do uruchomienia każdej komórki.

![Komórki kodu interaktywnego](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie funkcji IntelliSense

**Interactive** okno zawiera funkcję IntelliSense, na podstawie obiektów na żywo, w przeciwieństwie do edytora kodu, w którym IntelliSense opiera się na tylko analizę kodu źródłowego. Te sugestie dotyczą bardziej poprawny w **Interactive** okna, szczególnie w przypadku dynamicznie generowanego kodu. Wadą jest to, że funkcje za pomocą efekty uboczne (np. rejestrowanie komunikatów) może mieć wpływ na Twoje środowisko programistyczne.

Jeśli to zachowanie jest to problem, Zmień ustawienia w obszarze **narzędzia** > **opcje** > **Python**  >   **Interaktywne Windows** w **trybem uzupełniania** grupy, zgodnie z opisem na [opcje — Opcje interaktywnych okien](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
