---
title: Okno interaktywne języka Python (REPL)
description: Okno interaktywne (REPL) służący do szybkiego opracowywania kodu języka Python w programie Visual Studio.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409946"
---
# <a name="work-with-the-python-interactive-window"></a>Praca z okno interaktywne języka Python

Program Visual Studio udostępnia interaktywne okno pętle Read-Test-Print (REPL) dla każdego środowiska języka Python, które usprawnia REPL uzyskiwany z poziomu języka *Python. exe* w wierszu polecenia. Okno **interaktywne** (otwarte przy użyciu **widoku** > **inne** > **środowiska&lt;środowisko&gt; Interactive** ) umożliwia wprowadzanie dowolnego kodu w języku Python i wyświetlanie wyników natychmiastowych. Ten sposób kodowania pomaga informacje i eksperymentować z interfejsów API i bibliotek oraz interaktywnie tworzyć działającego kodu, aby uwzględnić w swoich projektach.

![Okno interaktywne języka Python](media/interactive-window.png)

Program Visual Studio ma kilka trybów REPL języka Python do wyboru:

| REPL | Opis | Edytowanie | debugowanie | Obrazy |
| --- | --- | --- | --- | --- |
| Standardowy | Domyślne REPL, rozmowy bezpośrednio języka Python. | Standard edycji (wielowierszowe itp.). | Tak, za pomocą `$attach` | Nie |
| Debugowanie | Domyślne REPL, rozmowy do debugowanego procesu języka Python | Edycja standardowa | Debugowania wyłącznie kodu | Nie |
| IPython | Rozmawiają zaplecza IPython REPL | Program IPython poleceń, udogodnienia Pylab | Nie | Tak, bezpośrednio w REPL |
| Program IPython bez Pylab | Rozmawiają zaplecza IPython REPL | Standardowa IPython | Nie | Tak, strona potwierdzenia |

W tym artykule opisano tryby REPL **standardowego** i **debugowania** . Szczegółowe informacje na temat trybów IPython można znaleźć w temacie [Use the IPYTHON REPL](interactive-repl-ipython.md).

Aby uzyskać szczegółowy przewodnik z przykładami, w tym interakcje z edytorem, takie jak **Ctrl**+**Enter**, zobacz [samouczek krok 3: korzystanie z okna interaktywnego REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Otwórz okno interaktywne

Istnieje kilka sposobów otwierania okna **interaktywnego** dla środowiska.

Najpierw przejdź do okna środowiska języka Python (**wyświetl** > **inne środowiska Windows** > **Python** lub **Ctrl**+**K** > **Ctrl**+ **`** ) i wybierz polecenie **Otwórz okno interaktywne** lub przycisk w wybranym środowisku.

![Interaktywne łącza okna w oknie środowiska Python](media/interactive-window-opening.png)

Po drugie, w dolnej części **widoku** > **inne menu systemu Windows** , istnieje polecenie **interaktywnego okna języka Python** dla środowiska domyślnego, a także polecenie przełączenia do okna **środowiska** :

![Menu okna interaktywnego elementy w widoku > inne Windows](media/interactive-window-menu.png)

Po trzecie można otworzyć okno **interaktywne** na pliku startowym w projekcie lub dla pliku autonomicznego, wybierając kolejno opcje **debuguj** > **Wykonaj \<projekt | Plik > w interakcyjnym** menu języka Python — polecenie**SHIFT**+**Alt**+**F5**):

![Wykonaj Project w menu Python Interactive](media/interactive-execute-project.png)

Na koniec możesz wybrać kod w pliku i użyć [polecenia **Wyślij do interaktywnego** ](#send-to-interactive-command) opisanego poniżej.

## <a name="interactive-window-options"></a>Opcje okna interaktywnego

Można kontrolować różne aspekty okna **interaktywnego** za pomocą **narzędzi** > **Opcje** > **Python** > **Interactive Windows** (zobacz [Opcje](python-support-options-and-settings-in-visual-studio.md)):

![Opcje okno interaktywne języka Python](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Za pomocą okna interakcyjnego

Po otwarciu okna **interaktywnego** można zacząć wprowadzać kod wiersz po wierszu w wierszu **\>\>\>** . Okno **interaktywne** wykonuje każdy wiersz w miarę wprowadzania, który obejmuje importowanie modułów, Definiowanie zmiennych i tak dalej:

![Okno interaktywne języka Python](media/interactive-window.png)

Wyjątek polega na tym, że dodatkowe wiersze kodu są konieczne do wykonania kompletnej instrukcji, na przykład gdy instrukcja `for` kończy się dwukropkiem, jak pokazano powyżej. W takich przypadkach wiersz wiersza zmienia się na **...** wskazujący, że musisz wprowadzić dodatkowe linie dla bloku, jak pokazano w czwartym i piątym wierszu grafiki powyżej. Po naciśnięciu klawisza **Enter** w pustym wierszu okno **interaktywne** zamknie blok i uruchomi go w interpreterze.

> [!Tip]
> Okno **interaktywne** ulepsza normalne środowisko wiersza polecenia w języku Python REPL przez automatyczne tworzenie wcięć instrukcji należących do otaczającego zakresu. Jego historię (przypomnieć o strzałkę w górę) zapewnia również wielowierszowy elementów REPL wiersza polecenia stanowi tylko pojedynczych wierszy.

<a name="meta-commands"></a>Okno **interaktywne** obsługuje również kilka meta poleceń. Wszystkie polecenia meta-Commands zaczynają się od `$`i można wpisać `$help`, aby uzyskać listę poleceń meta-Commands i `$help <command>` w celu uzyskania szczegółów użycia dla określonego polecenia.

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

Polecenia są również rozszerzalne przez rozszerzenia programu Visual Studio przez implementację i eksportowanie `IInteractiveWindowCommand` ([przykład](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Przełącz zakresów

Domyślnie okno **interaktywne** dla projektu jest objęte zakresem pliku startowego projektu tak, jakby było uruchamiane z wiersza polecenia. Dla plików autonomicznych zakresów go do tego pliku. Jednak w dowolnym momencie podczas sesji REPL, menu rozwijane w górnej części okna **interaktywnego** umożliwia zmianę zakresu:

![Okno interaktywne zakresów](media/interactive-scopes.png)

Po zaimportowaniu modułu, takiego jak wpisanie `import importlib`, opcje są wyświetlane na liście rozwijanej w celu przełączenia się do dowolnego zakresu w tym module. Komunikat w oknie **interaktywnym** wskazuje również nowy zakres, dzięki czemu można śledzić, w jaki sposób masz do pewnego stanu podczas sesji.

Wprowadzenie `dir()` w zakresie powoduje wyświetlenie prawidłowych identyfikatorów w tym zakresie, w tym nazw funkcji, klas i zmiennych. Na przykład przy użyciu `import importlib`, po których następuje `dir()`, przedstawiono następujące elementy:

![Okno interaktywne w zakresie importlib](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Wysyłać polecenie interaktywne

Oprócz bezpośredniego działania w oknie **interaktywnym** można wybrać kod w edytorze, kliknąć prawym przyciskiem myszy, a następnie wybrać polecenie **Wyślij do interaktywne** lub nacisnąć klawisz **Ctrl**+**Enter**.

![Wyślij do polecenia menu interaktywne](media/interactive-send-to.png)

To polecenie jest przydatne w przypadku tworzenia kodu iteracji lub ewolucyjny, łącznie z testowaniem kodu podczas jego tworzenia. Na przykład po wysłaniu fragmentu kodu do okna **interaktywnego** i zapoznaniu się z jego danymi wyjściowymi możesz nacisnąć strzałkę w górę, aby ponownie wyświetlić kod, zmodyfikować go i przetestować szybko, naciskając klawisz **Ctrl**+**Enter**. (Naciśnięcie klawisza **Enter** na końcu danych wejściowych wykonuje go, ale naciśnięcie klawisza **Enter** w środku danych wejściowych wstawia nowy wiersz.) Gdy masz odpowiedni kod, możesz łatwo skopiować go z powrotem do pliku projektu.

> [!Tip]
> Domyślnie program Visual Studio usuwa **>>>** i **...** REPL pojawia się przy wklejaniu kodu z okna **interaktywnego** do edytora. To zachowanie można zmienić w **opcjach** > **narzędzi** > **Edytor tekstu** > **Python** > **Zaawansowane** karty, korzystając z opcji **Wklej usuwaj polecenia REPL** . Zobacz [Opcje — różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Pracuj z komórkami kodu

Komórki kodu mogą służyć do analizy danych i są obsługiwane przez różne edytory tekstu.

Na przykład w przypadku używania pliku kodu jako ScratchPad często istnieje mały blok kodu, który ma być wysyłany jednocześnie. Aby zgrupować kod razem, Oznacz kod jako *komórkę kodu* , dodając komentarz zaczynający się od `#%%` do początku komórki, co spowoduje zakończenie poprzedniego. Komórki kodu mogą być zwijane i rozszerzane oraz przy użyciu **klawisza Ctrl**+**Enter** wewnątrz komórki kodu wysyła całą komórkę do okna **interaktywnego** i przechodzi do następnego.

Program Visual Studio wykrywa także komórki kodu zaczynające się od komentarzy takich jak `# In[1]:`, czyli formatu, który otrzymujesz podczas eksportowania notesu Jupyter jako pliku języka Python. To wykrywanie ułatwia uruchamianie notesu z [Azure Notebooks](https://notebooks.azure.com/) przez pobranie jako plik w języku Python, otwarcie w programie Visual Studio i użycie **klawisza Ctrl**+**Enter** w celu uruchomienia każdej komórki.

![Komórki kodu interaktywnego](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie funkcji IntelliSense

Okno **interaktywne** zawiera funkcję IntelliSense opartą na obiektach na żywo, w przeciwieństwie do edytora kodu, w którym technologia IntelliSense bazuje wyłącznie na analizie kodu źródłowego. Te sugestie są bardziej prawidłowe w oknie **interaktywnym** , szczególnie z dynamicznie generowanym kodem. Wadą jest to, że funkcje za pomocą efekty uboczne (np. rejestrowanie komunikatów) może mieć wpływ na Twoje środowisko programistyczne.

W przypadku wystąpienia tego problemu zmień ustawienia w obszarze **narzędzia** > **opcje** > **Python** > **Interactive Windows** w grupie **Tryb uzupełniania** , zgodnie z opisem w temacie [Opcje — interaktywne Opcje systemu Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
