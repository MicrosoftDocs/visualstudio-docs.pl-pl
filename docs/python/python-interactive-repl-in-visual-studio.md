---
title: Okno interaktywne Pythona (REPL)
description: Użyj okna interaktywnego (REPL) do szybkiego tworzenia kodu języka Python w programie Visual Studio.
ms.date: 02/11/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ceecffec577528484cd67fd13d3e04f368fb916
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302764"
---
# <a name="work-with-the-python-interactive-window"></a>Praca z interakcyjnym oknem Pythona

Visual Studio udostępnia interaktywne okno pętli odczytu i oceny i drukowania (REPL) dla każdego środowiska języka Python, co poprawia po REPL można uzyskać z *python.exe* w wierszu polecenia. **Okno Interaktywne** (otwarte za pomocą poleceń menu **Zobacz** > inne środowisko**Other Windows** > **&lt;&gt; ** systemu Windows interaktywne) umożliwia wprowadzenie dowolnego kodu języka Python i wyświetlenia natychmiastowych wyników. Ten sposób kodowania pomaga uczyć się i eksperymentować z interfejsami API i bibliotekami oraz interaktywnie opracowywać kod roboczy do uwzględnienia w projektach.

![Okno interaktywne języka Python](media/interactive-window.png)

Visual Studio ma wiele trybów REPL języka Python do wyboru:

| Repl | Opis | Edytowanie | Debugging | Obrazy |
| --- | --- | --- | --- | --- |
| Standardowa | Default REPL, rozmawia bezpośrednio z Pythonem | Edycja standardowa (wielowierszowa itp.). | Tak, za pośrednictwem`$attach` | Nie |
| Debugowanie | Domyślne REPL, rozmowy z debugowanym procesem Pythona | Edycja standardowa | Tylko debugowanie | Nie |
| Ipython | REPL rozmawia z zapleczem IPython | Polecenia IPython, wygody Pylab | Nie | Tak, wbudowany w REPL |
| IPython w/o Pylab | REPL rozmawia z zapleczem IPython | Standardowy IPython | Nie | Tak, oddzielne okno |

W tym artykule opisano tryby **Standardowy** i **Debug** REPL. Aby uzyskać szczegółowe informacje na temat trybów IPython, zobacz [Korzystanie z IPython REPL](interactive-repl-ipython.md).

Aby uzyskać szczegółowe wskazówki z przykładami, w tym interakcji z edytorem, takich jak **Ctrl**+**Enter**, zobacz [Samouczek Krok 3: Użyj interaktywnego okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otwieranie okna interaktywnego

Istnieje kilka sposobów otwierania okna **Interaktywne** dla środowiska.

Najpierw przełącz się do okna Środowiska Języka Python **(Wyświetl** > inne**środowiska Języka** **Windows** > Python lub **Ctrl**+**K** > **Ctrl)**+**`** i wybierz polecenie lub przycisk **Otwórz okno interaktywne** dla wybranego środowiska.

![Łącze interakcyjne okno w oknie Środowiska języka Python](media/interactive-window-opening.png)

Po drugie, w dolnej części menu **Widok** > **innego systemu Windows** znajduje się polecenie Python Interactive **Window** dla środowiska domyślnego, a także polecenie przełączania się do okna **Środowiska:**

![Elementy menu okno interaktywne w widoku > innych systemach Windows](media/interactive-window-menu.png)

Po trzecie, można otworzyć okno **Interaktywne** w pliku startowym w projekcie lub dla pliku autonomicznego, wybierając **debugowanie** > **projektu \<wykonania |> pliku w** poleceniu menu Python Interactive (**Shift**+**Alt**+**F5**):

![Wykonywanie projektu w interaktywnym menu języka Python](media/interactive-execute-project.png)

Na koniec możesz wybrać kod w pliku i użyć polecenia [ **Wyślij do interaktywnej** ](#send-to-interactive-command) opisanego poniżej.

## <a name="interactive-window-options"></a>Interaktywne opcje okna

Możesz kontrolować różne aspekty okna **interaktywnego** za pomocą**opcji** >  **narzędzi** > **Python** > **Interactive Windows** (zobacz [Opcje):](python-support-options-and-settings-in-visual-studio.md)

![Opcje interaktywnego okna języka Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Korzystanie z okna Interaktywne

Po otwarciu okna **Interaktywne** można rozpocząć wprowadzanie kodu wiersz ** \> \> ** po wierszu w wierszu w wierszu. **Okno Interaktywne** wykonuje każdy wiersz podczas wprowadzania go, który obejmuje importowanie modułów, definiowanie zmiennych itd.:

![Okno interaktywne języka Python](media/interactive-window.png)

Wyjątkiem jest, gdy dodatkowe wiersze kodu są potrzebne do `for` pełnej instrukcji, takich jak gdy instrukcja kończy się dwukropkiem, jak pokazano powyżej. W takich przypadkach wiersz monit zmienia się na **...** wskazując, że należy wprowadzić dodatkowe wiersze dla bloku, jak pokazano w czwartej i piątej linii na powyższej grafice. Po naciśnięciu **klawisza Enter** w pustym wierszu okno **Interaktywne** zamyka blok i uruchamia go w interpreterze.

> [!Tip]
> **Okno Interaktywne** poprawia środowisko wiersza polecenia języka Python, automatycznie wcięcie instrukcji, które należą do otaczającego zakresu. Jego historia (przypomniana strzałką w górę) zawiera również elementy wielowierszowe, podczas gdy wiersz polecenia REPL zapewnia tylko pojedyncze wiersze.

<a name="meta-commands"></a>Okno **Interaktywne** obsługuje również kilka meta-poleceń. Wszystkie meta-polecenia zaczynają `$`się od `$help` , i można wpisać, `$help <command>` aby uzyskać listę meta-poleceń i uzyskać szczegóły użycia dla określonego polecenia.

| Meta-polecenie | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, który jest przydatny do komentowania kodu w całej sesji. |
| `$attach` | Dołącza debuger programu Visual Studio do procesu okna REPL, aby włączyć debugowanie. |
| `$cls`, `$clear` | Czyści zawartość okna edytora, pozostawiając historię i kontekst wykonywania nienaruszone. |
| `$help` | Wyświetl listę poleceń lub pomoc dotyczącą określonego polecenia. |
| `$load` | Ładuje polecenia z pliku i wykonuje do zakończenia. |
| `$mod` | Przełącza bieżący zakres do określonej nazwy modułu. |
| `$reset` | Resetuje środowisko wykonywania do stanu początkowego, ale zachowuje historię. |
| `$wait` | Czeka na co najmniej określoną liczbę milisekund. |

Polecenia są również rozszerzalne przez rozszerzenia programu Visual Studio `IInteractiveWindowCommand` przez implementowanie i eksportowanie[(przykład).](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)

## <a name="switch-scopes"></a>Zakresy przełączników

Domyślnie **okno Interaktywne** dla projektu jest ograniczone do pliku startowego projektu tak, jakby uruchomiono go z wiersza polecenia. W przypadku pliku autonomicznego obejmuje on ten plik. Jednak w dowolnym momencie sesji REPL menu rozwijane w górnej części okna **Interaktywne** umożliwia zmianę zakresu:

![Interaktywne zakresy okien](media/interactive-scopes.png)

Po zaimportowaniu modułu, `import importlib`takiego jak wpisanie, opcje są wyświetlane w menu rozwijanym, aby przełączyć się do dowolnego zakresu w tym module. Komunikat w oknie **Interaktywna** wskazuje również nowy zakres, dzięki czemu można śledzić, jak masz do pewnego stanu podczas sesji.

Wprowadzenie `dir()` w zakresie wyświetla prawidłowe identyfikatory w tym zakresie, w tym nazwy funkcji, klasy i zmienne. Na przykład `import importlib` za `dir()` pomocą następuje pokazuje następujące:

![Okno interaktywne w zakresie importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Polecenie Wyślij do interakcyjne

Oprócz bezpośredniej pracy w oknie **Interaktywna** można wybrać kod w edytorze, kliknąć prawym przyciskiem myszy i wybrać polecenie **Wyślij do interaktywnej** lub nacisnąć **klawisz Ctrl**+**Enter**.

![Polecenie Wyślij do menu interaktywnego](media/interactive-send-to.png)

To polecenie jest przydatne do tworzenia kodu iteracyjną lub ewolucyjnej, w tym testowania kodu podczas jego opracowywania. Na przykład po wysłaniu fragmentu kodu do okna **Interaktywnego** i wyświetleniu jego danych wyjściowych można nacisnąć strzałkę w górę, aby ponownie wyświetlić kod, zmodyfikować go i szybko przetestować, naciskając **klawisze Ctrl**+**Enter**. (Naciśnięcie **klawisza Enter** na końcu wejścia powoduje jego wykonanie, ale naciśnięcie klawisza **Enter** w środku wejścia powoduje wstawienie nowej linii). Po uzyskaniu odpowiedniego kodu można łatwo skopiować go z powrotem do pliku projektu.

> [!Tip]
> Domyślnie visual studio **>>>** usuwa i **...** Funkcja REPL monituje o wklejenie kodu z okna **Interaktywne** do edytora. To zachowanie można zmienić na karcie**Options** > **Edytor** > tekstu **Narzędzia** > **Python** > **Zaawansowane** za pomocą opcji **Wklej usuwa monity REPL.** Zobacz [Opcje — różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Praca z komórkami kodu

Komórki kodu mogą być używane w analizie danych i są obsługiwane przez różne edytory tekstu.

Na przykład podczas korzystania z pliku kodu jako scratchpad, często masz mały blok kodu, który chcesz wysłać wszystkie na raz. Aby zgrupować kod razem, oznacz kod jako *komórkę kodu,* dodając komentarz, zaczynając od `#%%` początku komórki, która kończy poprzednia. Komórki kodu mogą być zwinięte i rozwinięte, a za pomocą **klawisza Ctrl**+**Enter** wewnątrz komórki kodu wysyła całą komórkę do okna **Interaktywne** i przechodzi do następnej.

Program Visual Studio wykrywa również komórki `# In[1]:`kodu, zaczynając od komentarzy, takich jak , który jest formatem, który otrzymujesz podczas eksportowania notesu Jupytera jako pliku Pythona. To wykrywanie ułatwia uruchamianie notesu z [notesów platformy Azure,](https://notebooks.azure.com/) pobierając jako plik języka Python, otwierając w programie Visual Studio i używając **klawisza Ctrl**+**Enter** do uruchamiania każdej komórki.

![Interaktywne komórki kodu](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie IntelliSense

**Okno Interaktywne** zawiera intellisense na podstawie obiektów na żywo, w przeciwieństwie do edytora kodu, w którym IntelliSense opiera się tylko na analizie kodu źródłowego. Te sugestie są bardziej poprawne w oknie **Interaktywne,** szczególnie w przypadku kodu generowanego dynamicznie. Wadą jest to, że funkcje z efektami ubocznymi (takie jak rejestrowanie komunikatów) może mieć wpływ na środowisko rozwoju.

Jeśli to zachowanie jest problemem, zmień ustawienia w obszarze**Opcje** >  **narzędzi** > **Python** > **Interactive Windows** w grupie Tryb **ukończenia,** zgodnie z opisem [opcji — Opcje interakcyjne okna](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
