---
title: Okno interaktywne języka Python (REPL)
description: Użyj okna interaktywnego (REPL) do szybkiego tworzenia kodu w języku Python w programie Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9608f273683865be767a44dd8f1d66106b97b7e0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533552"
---
# <a name="work-with-the-python-interactive-window"></a>Współpraca z oknem interaktywnym języka Python

Program Visual Studio udostępnia interaktywne okno pętle odczytu i wydrukowania (REPL) dla każdego środowiska języka Python, które usprawnia REPL *python.exe* w wierszu polecenia. Okno **interaktywne** (otwierane za pomocą polecenia **Wyświetl**  >  **inne**  >  ** &lt; &gt; interaktywne menu środowisko** Windows) umożliwia wprowadzanie dowolnego kodu w języku Python i wyświetlanie wyników natychmiastowych. Ten sposób kodowania pomaga uczyć się i eksperymentować z interfejsami API i bibliotekami oraz interaktywnie opracowywać kod roboczy do uwzględnienia w projektach.

![Okno interaktywne języka Python](media/interactive-window.png)

Program Visual Studio ma wiele trybów REPL języka Python do wyboru:

| REPL | Opis | Edytowanie | Debugowanie | Obrazy |
| --- | --- | --- | --- | --- |
| Standardowa (Standard) | REPL domyślne, rozmowy bezpośrednio do języka Python | Standardowe edytowanie (wielowierszowe itp.). | Tak, za pomocą`$attach` | Nie |
| Debugowanie | REPL domyślne, rozmowy z debugowanym procesem języka Python | Edycja standardowa | Tylko debugowanie | Nie |
| IPython | REPLe rozmowy z zapleczem IPython | Polecenia IPython, wygody Pylab | Nie | Tak, wbudowane w REPL |
| IPython w/o Pylab | REPLe rozmowy z zapleczem IPython | Standardowa IPython | Nie | Tak, oddziel okno |

W tym artykule opisano tryby REPL **standardowego** i **debugowania** . Szczegółowe informacje na temat trybów IPython można znaleźć w temacie [Use the IPYTHON REPL](interactive-repl-ipython.md).

Aby uzyskać szczegółowy przewodnik z przykładami, w tym interakcje z edytorem, takie jak **Ctrl** + **Enter**, zobacz [samouczek krok 3: korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otwórz okno interaktywne

Istnieje kilka sposobów otwierania okna **interaktywnego** dla środowiska.

Najpierw przejdź do okna środowiska języka Python (**Wyświetl**  >  **inne**  >  **środowiska Windows Python** lub **Ctrl** + **K**  >  **Ctrl** + **`** ) i wybierz polecenie **Otwórz okno interaktywne** lub przycisk w wybranym środowisku.

![Łącze okna interaktywnego w oknie środowiska języka Python](media/interactive-window-opening.png)

Po drugie, w dolnej części menu **Wyświetl**  >  **inne** okna, istnieje polecenie **interaktywnego okna języka Python** dla środowiska domyślnego, a także polecenie przełączenia do okna **środowiska** :

![Elementy menu okna interaktywnego w widoku > inne okna](media/interactive-window-menu.png)

Po trzecie można otworzyć okno **interaktywne** w pliku startowym w projekcie lub dla autonomicznego pliku, wybierając polecenie **Debuguj**  >  **Wykonaj \<Project | File> w interakcyjnym** menu języka Python (**SHIFT** + **Alt** + **F5**):

![Wykonaj projekt w menu interaktywnym Python](media/interactive-execute-project.png)

Na koniec możesz wybrać kod w pliku i użyć [polecenia **Wyślij do interaktywnego** ](#send-to-interactive-command) opisanego poniżej.

## <a name="interactive-window-options"></a>Opcje okna interaktywnego

Można kontrolować różne aspekty okna **interaktywnego** za pomocą opcji **Narzędzia**  >  **Options**  >  **Python**  >  **Interactive Windows** (zobacz [Opcje](python-support-options-and-settings-in-visual-studio.md)):

![Opcje interaktywnego okna języka Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Korzystanie z okna interaktywnego

Po otwarciu okna **interaktywnego** można zacząć wprowadzać kod wiersz po wierszu w **\>\>\>** wierszu polecenia. Okno **interaktywne** wykonuje każdy wiersz w miarę wprowadzania, który obejmuje importowanie modułów, Definiowanie zmiennych i tak dalej:

![Okno interaktywne języka Python](media/interactive-window.png)

Wyjątek polega na tym, że dodatkowe wiersze kodu są konieczne do wykonania kompletnej instrukcji, na przykład gdy `for` instrukcja kończy się znakiem dwukropka, jak pokazano powyżej. W takich przypadkach wiersz wiersza zmienia się na **...** wskazujący, że musisz wprowadzić dodatkowe linie dla bloku, jak pokazano w czwartym i piątym wierszu grafiki powyżej. Po naciśnięciu klawisza **Enter** w pustym wierszu okno **interaktywne** zamknie blok i uruchomi go w interpreterze.

> [!Tip]
> Okno **interaktywne** ulepsza normalne środowisko wiersza polecenia w języku Python REPL przez automatyczne tworzenie wcięć instrukcji należących do otaczającego zakresu. Jego historia (jest wywoływana z strzałką w górę) zawiera również elementy wielowierszowe, natomiast wiersz polecenia REPL zawiera tylko pojedyncze wiersze.

<a name="meta-commands"></a>Okno **interaktywne** obsługuje również kilka meta poleceń. Wszystkie meta-polecenia zaczynają się od `$` i można wpisać polecenie, `$help` Aby wyświetlić listę meta poleceń i `$help <command>` uzyskać szczegóły użycia określonego polecenia.

| Meta-polecenie | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, który ułatwia dodawanie komentarzy do kodu w całej sesji. |
| `$attach` | Dołącza debuger programu Visual Studio do procesu okna REPL w celu włączenia debugowania. |
| `$cls`, `$clear` | Czyści zawartość okna edytora, pozostawiając historię i kontekst wykonywania bez zmian. |
| `$help` | Wyświetl listę poleceń lub pomoc dotyczącą określonego polecenia. |
| `$load` | Ładuje polecenia z pliku i wykonuje je do momentu ukończenia. |
| `$mod` | Przełącza bieżący zakres do określonej nazwy modułu. |
| `$reset` | Przywraca stan początkowy środowiska wykonawczego, ale zachowuje historię. |
| `$wait` | Czeka przez co najmniej określoną liczbę milisekund. |

Polecenia są również rozszerzalne przez rozszerzenia programu Visual Studio przez implementację i eksportowanie `IInteractiveWindowCommand` ([przykład](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Przełącz zakresy

Domyślnie okno **interaktywne** dla projektu jest objęte zakresem pliku startowego projektu tak, jakby było uruchamiane z wiersza polecenia. W przypadku pliku autonomicznego zakresy IT do tego pliku. Jednak w dowolnym momencie podczas sesji REPL, menu rozwijane w górnej części okna **interaktywnego** umożliwia zmianę zakresu:

![Zakresy okna interaktywnego](media/interactive-scopes.png)

Po zaimportowaniu modułu, takiego jak wpisywanie `import importlib` , opcje są wyświetlane na liście rozwijanej w celu przełączenia się do dowolnego zakresu w tym module. Komunikat w oknie **interaktywnym** wskazuje również nowy zakres, dzięki czemu można śledzić, w jaki sposób masz do pewnego stanu podczas sesji.

Wprowadzenie `dir()` do zakresu wyświetla prawidłowe identyfikatory w tym zakresie, w tym nazwy funkcji, klasy i zmienne. Na przykład przy użyciu, `import importlib` a następnie `dir()` :

![Okno interaktywne w zakresie importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Wyślij do polecenia interaktywnego

Oprócz bezpośredniego działania w oknie **interaktywnym** można wybrać kod w edytorze, kliknąć prawym przyciskiem myszy, a następnie wybrać polecenie **Wyślij do interaktywne** lub nacisnąć klawisz **Ctrl** + **Enter**.

![Polecenie Wyślij do menu interakcyjnego](media/interactive-send-to.png)

To polecenie jest przydatne w przypadku iteracyjnego lub ewolucyjnego tworzenia kodu, w tym testowania kodu podczas jego tworzenia. Na przykład po wysłaniu fragmentu kodu do okna **interaktywnego** i zapoznaniu się z jego danymi wyjściowymi można nacisnąć strzałkę w górę, aby ponownie wyświetlić kod, zmodyfikować go i przetestować szybko, naciskając klawisz **Ctrl** + **Enter**. (Naciśnięcie klawisza **Enter** na końcu danych wejściowych wykonuje go, ale naciśnięcie klawisza **Enter** w środku danych wejściowych wstawia nowy wiersz.) Gdy masz odpowiedni kod, możesz łatwo skopiować go z powrotem do pliku projektu.

> [!Tip]
> Domyślnie program Visual Studio usuwa **>>>** i **...** REPL pojawia się przy wklejaniu kodu z okna **interaktywnego** do edytora. To zachowanie można zmienić na karcie Opcje **narzędzi**  >  **Options**  >  **Edytor tekstu**  >  **Python**  >  w języku Python**Zaawansowane** przy użyciu opcji **Wklej Usuń REPL** . Zobacz [Opcje — różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Pracuj z komórkami kodu

Komórki kodu mogą służyć do analizy danych i są obsługiwane przez różne edytory tekstu.

Na przykład w przypadku używania pliku kodu jako ScratchPad często istnieje mały blok kodu, który ma być wysyłany jednocześnie. Aby zgrupować kod razem, Oznacz kod jako *komórkę kodu* , dodając komentarz, zaczynając od `#%%` początku komórki, który zostanie zakończony poprzednią. Komórki kodu mogą być zwijane i rozszerzane, a przy użyciu **klawisza Ctrl** + **Enter** wewnątrz komórki kodu jest wysyłana cała komórka do okna **interaktywnego** i przechodzi do następnego.

Program Visual Studio wykrywa także komórki kodu zaczynające się od komentarzy, takich jak format, który otrzymujesz `# In[1]:` podczas eksportowania notesu Jupyter jako pliku języka Python. To wykrywanie ułatwia uruchamianie notesu z [Azure Notebooks](https://notebooks.azure.com/) przez pobranie go jako pliku języka Python, otwarcie w programie Visual Studio i użycie **klawisza Ctrl** + **Enter** w celu uruchomienia każdej komórki.

![Interaktywne komórki kodu](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie funkcji IntelliSense

Okno **interaktywne** zawiera funkcję IntelliSense opartą na obiektach na żywo, w przeciwieństwie do edytora kodu, w którym technologia IntelliSense bazuje wyłącznie na analizie kodu źródłowego. Te sugestie są bardziej prawidłowe w oknie **interaktywnym** , szczególnie z dynamicznie generowanym kodem. Wadą jest to, że funkcje z efektami ubocznymi (takie jak komunikaty rejestrowania) mogą mieć wpływ na środowisko programistyczne.

W przypadku wystąpienia tego problemu zmień ustawienia w obszarze Opcje **Narzędzia**  >  **Options**  >  **Python**  >  **Interactive Windows** w grupie **Tryb uzupełniania** , zgodnie z opisem w temacie [Opcje — interaktywne Opcje systemu Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
