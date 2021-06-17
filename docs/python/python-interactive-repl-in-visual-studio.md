---
title: Okno interaktywne języka Python (REPL)
description: Użyj okna interaktywnego (REPL) do szybkiego tworzenia kodu w języku Python w Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 21115673a41e26b2f1685442d2ed0ad93a147990
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254891"
---
# <a name="work-with-the-python-interactive-window"></a>Praca z programem Python okno Interactive

Visual Studio udostępnia interaktywne okno repl (read-evaluate-print loop) dla każdego środowiska Python, które ulepsza  środowisko REPLpython.exew wierszu polecenia. Okno **Interaktywne** (otwarte za pomocą **poleceń** menu Interaktywne Wyświetlanie innych środowisk systemu Windows) umożliwia wprowadzenie dowolnego kodu w języku  >    >  Python i wyświetlenie natychmiastowych **&lt; &gt;** wyników. Ten sposób kodowania ułatwia naukę i eksperymentowanie z interfejsami API i bibliotekami oraz interaktywne tworzenie kodu roboczego, który ma być uwzględniany w projektach.

![Okno interaktywne języka Python](media/interactive-window.png)

Visual Studio oferuje kilka trybów REPL języka Python do wyboru:

| Repl | Opis | Edytowanie | Debugowanie | Obrazy |
| --- | --- | --- | --- | --- |
| Standardowa (Standard) | Domyślne repl, bezpośrednie rozmowy z językem Python | Edycja standardowa (wieloliniowa itp.). | Tak, za pośrednictwem `$attach` | Nie |
| Debugowanie | Domyślna repl, rozmowy z debugowany proces języka Python | Edytowanie standardowe | Tylko debugowanie | Nie |
| Ipython | RePL rozmawia z zaplecza IPython | Polecenia IPython, wygody Pylab | Nie | Tak, w tekście w REPL |
| IPython w/o Pylab | RePL rozmawia z zaplecza IPython | Standardowa IPython | Nie | Tak, oddzielne okno |

W tym artykule opisano **tryby STANDARD** i **Debug** REPL. Aby uzyskać szczegółowe informacje na temat trybów IPython, [zobacz Use the IPython REPL (Korzystanie z repl IPython).](interactive-repl-ipython.md)

Aby uzyskać szczegółowy przewodnik z przykładami, w tym interakcje z edytorem, takie jak **Ctrl** + **Enter,** zobacz [Samouczek Krok 3. Korzystanie z](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)okna Interactive REPL .

## <a name="open-an-interactive-window"></a>Otwieranie okno Interactive

Istnieje kilka sposobów otwierania **okna** Interaktywne dla środowiska.

Najpierw przejdź do okna Środowiska Języka Python **(Wyświetl** inne środowiska Windows Python lub naciśnij klawisze  >    >   **Ctrl** + **K**  >  **Ctrl)** i wybierz polecenie + lub **`**  przycisk Otwórz okno interaktywne dla wybranego środowiska.

![Link okna interakcyjnego w oknie środowiska Python](media/interactive-window-opening.png)

Po drugie w dolnej części menu Wyświetl inne okna znajduje się polecenie Interaktywne okno języka Python dla środowiska domyślnego, a także polecenie przełączania się do  >   **okna** Środowiska: 

![Elementy menu okna interakcyjnego w widoku > inne okna](media/interactive-window-menu.png)

Po trzecie możesz  otworzyć okno Interaktywne w pliku startowym w projekcie lub w przypadku pliku autonomicznego, wybierając polecenie Debuguj wykonywanie w menu Interaktywny język  >  **\<Project | File> Python** **(Shift** + **Alt** + **F5):**

![Menu Execute Project in Python Interactive (Wykonywanie projektu w interaktywnym menu języka Python)](media/interactive-execute-project.png)

Na koniec możesz wybrać kod w pliku i użyć polecenia Wyślij do [  interaktywnego opisanego](#send-to-interactive-command) poniżej.

## <a name="interactive-window-options"></a>okno Interactive opcji

Możesz kontrolować różne aspekty  okna interaktywnego za pomocą opcji narzędzi Okna interaktywne  >    >  **języka Python**  >   (zobacz [Opcje](python-support-options-and-settings-in-visual-studio.md)):

![Opcje okna interaktywnego języka Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Korzystanie z okno Interactive

Po **otwarciu** okna Interaktywne możesz rozpocząć wprowadzanie kodu wiersz po wierszu **\>\>\>** polecenia. Okno **Interaktywne** wykonuje każdy wiersz podczas jego wprowadzania, co obejmuje importowanie modułów, definiowanie zmiennych i tak dalej:

![Okno interaktywne języka Python](media/interactive-window.png)

Wyjątek występuje, gdy do wykonania pełnej instrukcji potrzebne są dodatkowe wiersze kodu, na przykład gdy instrukcja kończy się `for` dwukropkiem, jak pokazano powyżej. W takich przypadkach wiersz monitu zmienia się na **...,** co oznacza, że musisz wprowadzić dodatkowe wiersze dla bloku, jak pokazano w czwartym i piątym wierszu na powyższej ilustracji. Po naciśnięciu **klawisza Enter**  w pustym wierszu okno Interaktywne zamyka blok i uruchamia go w interpreterze.

> [!Tip]
> Okno **Interakcyjne** ulepsza środowisko REPL w języku Python przez automatyczne wcięcie instrukcji należących do otaczającego zakresu. Jego historia (przywoływana strzałką w górę) udostępnia również elementy wieloliniowe, natomiast wiersz polecenia REPL udostępnia tylko pojedyncze wiersze.

<a name="meta-commands"></a> Okno **Interaktywne** obsługuje również kilka meta poleceń. Wszystkie meta polecenia rozpoczynają się od . Można wpisać polecenie , aby uzyskać listę meta poleceń i uzyskać szczegółowe informacje o użyciu `$` `$help` określonego `$help <command>` polecenia.

:::moniker range="<=vs-2017"

| Meta-polecenie | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, który przydaje się do komentowania kodu w całej sesji. |
| `$attach` | Dołącza Visual Studio do procesu okna REPL, aby włączyć debugowanie. |
| `$cls`, `$clear` | Czyszczy zawartość okna edytora, pozostawiając historię i kontekst wykonywania bez zmian. |
| `$help` | Wyświetlanie listy poleceń lub pomocy dotyczącej określonego polecenia. |
| `$load` | Ładuje polecenia z pliku i wykonuje do momentu ukończenia. |
| `$mod` | Przełącza bieżący zakres do określonej nazwy modułu. |
| `$reset` | Resetuje środowisko wykonawcze do stanu początkowego, ale zachowuje historię. |
| `$wait` | Oczekuje na co najmniej określoną liczbę milisekund. |

:::moniker-end

:::moniker range=">=vs-2019"

| Meta-polecenie | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, który przydaje się do komentowania kodu w całej sesji. |
| `$cls`, `$clear` | Czyszczy zawartość okna edytora, pozostawiając historię i kontekst wykonywania bez zmian. |
| `$help` | Wyświetlanie listy poleceń lub pomocy dotyczącej określonego polecenia. |
| `$load` | Ładuje polecenia z pliku i wykonuje do momentu ukończenia. |
| `$mod` | Przełącza bieżący zakres do określonej nazwy modułu. |
| `$reset` | Resetuje środowisko wykonawcze do stanu początkowego, ale zachowuje historię. |
| `$wait` | Oczekuje na co najmniej określoną liczbę milisekund. |

:::moniker-end

Polecenia można również rozszerzać przez Visual Studio przez implementację i eksportowanie `IInteractiveWindowCommand` [(na przykład](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Przełączanie zakresów

Domyślnie okno **Interakcyjne** dla projektu jest w zakresie pliku startowego projektu, tak jakby było ono otwierane z wiersza polecenia. W przypadku pliku autonomicznego zakres obejmuje ten plik. Jednak w dowolnym momencie podczas sesji REPL menu rozwijane w  górnej części okna Interaktywne umożliwia zmianę zakresu:

![okno Interactive zakresów](media/interactive-scopes.png)

Po zaimportowaniu modułu, takiego jak wpisanie , opcje są wyświetlane na liście rozwijanej, aby przełączyć się do `import importlib` dowolnego zakresu w tym module. Komunikat w oknie **Interaktywny** wskazuje również nowy zakres, dzięki czemu można śledzić, jak dotarliśmy do określonego stanu podczas sesji.

Wprowadzanie `dir()` w zakresie powoduje wyświetlenie prawidłowych identyfikatorów w tym zakresie, w tym nazw funkcji, klas i zmiennych. Na przykład przy `import importlib` użyciu następuje pokazuje następujące `dir()` czynności:

![okno Interactive w zakresie importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Wyślij do polecenia interaktywnego

Oprócz bezpośredniego działania  w oknie Interaktywny można wybrać kod w edytorze,  kliknąć prawym przyciskiem myszy i wybrać polecenie Wyślij do środowiska interakcyjnego lub nacisnąć **klawisz Ctrl,** + **naciskając klawisz .**

![Polecenie Wyślij do menu interaktywnego](media/interactive-send-to.png)

To polecenie jest przydatne do iteracyjnych lub ewolucyjnych opracowywania kodu, w tym testowania kodu podczas jego tworzenia. Na przykład po wysłaniu fragmentu kodu  do okna Interaktywne i wyświetlniu jego danych wyjściowych możesz nacisnąć strzałkę w górę, aby ponownie wyświetlić kod, zmodyfikować go i szybko go przetestować, naciskając klawisz **Ctrl** + **Enter**. (Naciśnięcie **klawisza Enter** na końcu danych wejściowych powoduje jego wykonanie, ale naciśnięcie klawisza **Enter** w środku danych wejściowych powoduje wstawienie nowego linii). Gdy już masz kod, możesz łatwo skopiować go z powrotem do pliku projektu.

> [!Tip]
> Domyślnie program Visual Studio i **>>>** **...** Podczas wklejania kodu z okna  interaktywnego do edytora jest wyświetlany monit REPL. To zachowanie można zmienić na karcie Narzędzia Opcje Edytor tekstu Python Zaawansowane przy użyciu opcji  >    >    >    >   Wklej **usuwa monity REPL.** Zobacz [Opcje — różne opcje.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Praca z komórkami kodu

Komórki kodu mogą być używane w analizie danych i są obsługiwane przez różne edytory tekstu.

Na przykład w przypadku korzystania z pliku kodu jako notatnika często masz mały blok kodu, który chcesz wysłać wszystko jednocześnie. Aby zgrupować kod, oznacz  kod jako komórkę kodu, dodając komentarz rozpoczynający się od początku `#%%` komórki, która kończy poprzednią komórkę. Komórki kodu można zwinąć i rozwinąć, a użycie klawisza **Ctrl** Enter wewnątrz komórki kodu powoduje wysłanie całej komórki do okna Interaktywne i przejście +  do  następnego.

Visual Studio wykrywa również komórki kodu rozpoczynające się od komentarzy, takich jak , czyli format, który można uzyskać podczas eksportowania `# In[1]:` notesu Jupyter jako pliku języka Python. To wykrywanie ułatwia uruchamianie notesu z usługi [Azure Notebooks](https://notebooks.azure.com/) przez pobranie go jako pliku języka Python, otwarcie w Visual Studio i uruchomienie każdej komórki za pomocą klawisza **Ctrl** + **Enter.**

![Komórki kodu interaktywnego](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie funkcji IntelliSense

Okno **Interaktywne** zawiera mechanizm IntelliSense oparty na obiektach na żywo, w przeciwieństwie do edytora kodu, w którym funkcja IntelliSense jest oparta tylko na analizie kodu źródłowego. Te sugestie są bardziej poprawne w **oknie** Interaktywny, szczególnie w przypadku dynamicznie generowanego kodu. Wadą jest to, że funkcje z efektami ubocznymi (takimi jak rejestrowanie komunikatów) mogą mieć wpływ na środowisko programowe.

Jeśli to zachowanie jest problemem, zmień ustawienia w obszarze Opcje narzędzi Okna interakcyjne języka Python w grupie Tryb ukończenia, zgodnie z opisem w te  >    >    >    [tematu Opcje — opcje okna interaktywnego.](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)
