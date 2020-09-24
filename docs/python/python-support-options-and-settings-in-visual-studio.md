---
title: Opcje i ustawienia dla języka Python
description: Odwołanie do różnych ustawień w programie Visual Studio, które odnoszą się do kodu i projektów języka Python.
ms.date: 03/13/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 99274d3884d002f6dee29a632f8a7c08ac90a56f
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211131"
---
# <a name="options-for-python-in-visual-studio"></a>Opcje języka Python w programie Visual Studio

Aby wyświetlić opcje języka Python, użyj **Tools**  >  menu**Opcje** narzędzi, upewnij się, że wybrano opcję **Pokaż wszystkie ustawienia** , a następnie przejdź do języka **Python**:

::: moniker range="vs-2017"
![Okno dialogowe Opcje środowiska Python, karta Ogólne](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje środowiska Python, karta Ogólne](media/options-general-2019.png)
::: moniker-end

Dostępne są również dodatkowe opcje specyficzne dla języka Python na karcie Zaawansowane **Edytor tekstu**w języku  >  **Python**  >  **Advanced** , a na **Environment**  >  karcie**czcionki i kolory** środowiska w grupie **Edytor tekstu** .

> [!Note]
> Grupa **eksperymentalna** zawiera opcje dla funkcji, które są nadal opracowywane i nie są udokumentowane w tym miejscu. Są one często omówione w wpisach w usłudze [Python inżynierów w blogu firmy Microsoft](https://devblogs.microsoft.com/python/).

## <a name="general-options"></a>Opcje ogólne

(**Narzędzia**  >  **Opcje**  >  Karta **Python** ).

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Pokaż Okno Dane wyjściowe podczas tworzenia środowisk wirtualnych**| Włączone | Wyczyść, aby zapobiec wyświetlaniu okna **danych wyjściowych** . |
| **Pokaż Okno Dane wyjściowe podczas instalowania lub usuwania pakietów** | Włączone | Wyczyść, aby zapobiec wyświetlaniu okna **danych wyjściowych** . |
| **Pokaż pasek powiadomień, aby utworzyć środowiska** | Włączone | *Tylko program Visual Studio 2019.* Gdy ta opcja jest ustawiona, a użytkownik otwiera projekt, który zawiera plik *requirements.txt* lub *Environment. yml* , program Visual Studio Wyświetla pasek informacji z sugestiami dotyczącymi tworzenia środowiska wirtualnego lub środowiska Conda, zamiast korzystać z domyślnego środowiska globalnego. |
| **Pokaż pasek powiadomień, aby zainstalować pakiety** | Włączone | *Tylko program Visual Studio 2019.* Gdy ta opcja jest ustawiona, a użytkownik otwiera projekt, który zawiera plik *requirements.txt* (i nie używa domyślnego środowiska globalnego), program Visual Studio porównuje te wymagania z pakietami zainstalowanymi w bieżącym środowisku. W przypadku braku pakietów program Visual Studio wyświetli monit o zainstalowanie tych zależności. |
| **Zawsze uruchamiaj menedżerów pakietów jako administrator** | Wyłączone | Zawsze Podnieś poziom `pip install` i podobne operacje Menedżera pakietów dla wszystkich środowisk. Podczas instalowania pakietów program Visual Studio poprosi o uprawnienia administratora, jeśli środowisko znajduje się w chronionym obszarze systemu plików, takim jak *C:\Program Files*. W tym monicie można wybrać, aby zawsze podnieść poziom polecenia instalacji tylko w jednym środowisku. Zobacz [kartę pakiety](python-environments-window-tab-reference.md#packages-tab). |
| **Automatycznie Generuj bazę danych uzupełniania przy pierwszym użyciu** | Włączone | *Dotyczy programu Visual Studio 2017 w wersji 15,5 i starszej oraz do nowszych wersji podczas korzystania z bazy danych IntelliSense.* Ustala priorytety uzupełniania bazy danych dla biblioteki podczas pisania kodu, który go używa. Aby uzyskać więcej informacji, zobacz [karta IntelliSense](python-environments-window-tab-reference.md?view=vs-2017&preserve-view=true#intellisense-tab). |
| **Ignoruj zmienne PYTHONPATH całego systemu** | Włączone | PYTHONPATH jest domyślnie ignorowana, ponieważ program Visual Studio zapewnia bardziej bezpośredni sposób określania ścieżek wyszukiwania w środowiskach i projektach. Aby uzyskać szczegółowe informacje, zobacz [ścieżki wyszukiwania](search-paths.md) . |
| **Zaktualizuj ścieżki wyszukiwania podczas dodawania połączonych plików** | Włączone | Po ustawieniu, dodanie [połączonego pliku](managing-python-projects-in-visual-studio.md#linked-files) do projektu aktualizuje [ścieżki wyszukiwania](search-paths.md) , dzięki czemu technologia IntelliSense może uwzględnić zawartość folderu połączonego pliku w jego bazie danych uzupełniania. Usuń zaznaczenie tej opcji, aby wykluczyć taką zawartość z bazy danych uzupełniania. |
| **Ostrzegaj, jeśli nie można znaleźć importowanego modułu** | Włączone | Usuń zaznaczenie tej opcji, aby pominąć ostrzeżenia, gdy wiadomo, że zaimportowany moduł nie jest dostępny, ale w przeciwnym razie nie wpływa na operację kodu. |
| **Zgłoś niespójne wcięcie jako** | **Ostrzeżenia** | Ponieważ interpreter języka Python jest w dużym stopniu zależny od poprawnego wcięcia, aby określić zakres, domyślne błędy programu Visual Studio, gdy wykryje niespójne wcięcia, które mogą wskazywać na błędy kodowania. Ustaw na **Błędy** , aby były jeszcze bardziej rygorystyczne, co spowoduje zakończenie działania programu w takich przypadkach. Aby całkowicie wyłączyć to zachowanie, wybierz pozycję **nie**. |
| **Sprawdź ankiety/wiadomości** | **Raz w tygodniu** | *Program Visual Studio 2017 i jego starsze wersje.* Ustawia częstotliwość, z jaką program Visual Studio ma otwierać okno zawierające stronę sieci Web z ankietami i elementami wiadomości związanymi z językiem Python, jeśli są dostępne. Opcje **nigdy nie**są **, raz dziennie**, raz w **tygodniu**i **raz na miesiąc**. |
| Przycisk **Resetuj wszystkie trwałe ukryte okna dialogowe** | nie dotyczy | Różne okna dialogowe zawierają opcje, takie jak **nie pokazuj mi tego ponownie**. Użyj tego przycisku, aby wyczyścić te opcje i spowodować, że okna dialogowe zostaną wyświetlone ponownie. |

::: moniker range="vs-2017"
![Okno dialogowe Opcje środowiska Python, karta Ogólne](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje środowiska Python, karta Ogólne](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Opcje Conda

(**Narzędzia** > **Opcje** > Język **Python** > Karta **Conda** ).

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Ścieżka pliku wykonywalnego Conda** | puste | Określa dokładną ścieżkę do pliku wykonywalnego *conda.exe* , zamiast polegać na domyślnej instalacji Miniconda dołączonej do obciążenia języka Python. Jeśli w tym miejscu zostanie podana inna ścieżka, ma ona pierwszeństwo przed instalacją domyślną i innymi conda.exe plikami wykonywalnymi określonymi w rejestrze. To ustawienie można zmienić, jeśli ręcznie zainstalujesz nowszą wersję programu Anaconda lub Miniconda lub chcesz użyć 32-bitowego dystrybucji zamiast domyślnego 64-bitowego dystrybucji. |

![Okno dialogowe Opcje środowiska Python, karta serwer języka](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Opcje debugowania

(**Narzędzia**  >  **Opcje**  >  Język **Python**  >  Karta **debugowanie** .)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Monituj przed uruchomieniem, gdy są obecne błędy** | Włączone | Po ustawieniu program prosi o potwierdzenie, że chcesz uruchomić kod zawierający błędy. Usuń zaznaczenie tej opcji, aby wyłączyć ostrzeżenie. |
| **Zaczekaj na dane wejściowe, gdy proces kończy się nienormalnie**<br/><br/>**Zaczekaj na dane wejściowe, gdy proces kończy się normalnie** | On (dla obu) | Program Python uruchomiony z programu Visual Studio jest uruchamiany w osobnym oknie konsoli. Domyślnie okno czeka na naciśnięcie klawisza przed zamknięciem, bez względu na zakończenie działania programu. Aby usunąć ten monit i zamknąć okno automatycznie, usuń zaznaczenie jednej lub obu tych opcji. |
| **Tee dane wyjściowe programu do okna danych wyjściowych debugowania** | Włączone | Wyświetla dane wyjściowe programu w osobnym oknie konsoli i oknie **danych wyjściowych** programu Visual Studio. Usuń zaznaczenie tej opcji, aby wyświetlić dane wyjściowe tylko w osobnym oknie konsoli. |
| **Przerwij w przypadku wyjątku SystemExit z kodem zakończenia równym zero** | Wyłączone | Jeśli ta wartość jest ustawiona, program przerwie debuger tego wyjątku. Po wyczyszczeniu debuger nie przerywa działania. |
| **Włącz debugowanie standardowej biblioteki języka Python** | Wyłączone | Sprawia, że podczas debugowania można przechodzić do standardowego kodu źródłowego biblioteki, ale wydłużyć czas potrzebny na uruchomienie debugera.|
| **Pokaż wartość zwracaną funkcji** | Włączone | *Tylko program Visual Studio 2019.* Wyświetla wartości zwracane przez funkcję w oknie **zmiennych lokalnych** i przechodzenie przez wywołanie funkcji w debugerze (F10) |
| **Użyj starszego debugera** | Wyłączone | *Tylko program Visual Studio 2019.* Powoduje, że program Visual Studio domyślnie używa starszego debugera. Aby uzyskać więcej informacji, zobacz [debugowanie — Użyj starszego debugera](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Okno dialogowe Opcje środowiska Python, karta debugowanie](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje środowiska Python, karta debugowanie](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Opcje diagnostyki

(**Narzędzia**  >  **Opcje**  >  Język **Python**  >  Karta **Diagnostyka** ).

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Uwzględnij dzienniki analizy** | Włączone | Zawiera szczegółowe dzienniki dotyczące analizy zainstalowanych środowisk języka Python podczas zapisywania diagnostyki do pliku lub kopiowania ich do schowka przy użyciu przycisków. Ta opcja może znacząco zwiększyć rozmiar wygenerowanego pliku, ale często jest wymagana do diagnozowania problemów z technologią IntelliSense. |
| Przycisk **zapisywania diagnostyki do pliku** | nie dotyczy | W polu Nazwa pliku zostanie wyświetlony komunikat z pytaniem, a następnie zostanie zapisany dziennik. |
| Przycisk **kopiowania diagnostyki do schowka** | nie dotyczy | Umieszcza pełny dziennik w schowku; Ta operacja może zająć trochę czasu w zależności od rozmiaru dziennika. |

![Okno dialogowe Opcje środowiska Python, karta Diagnostyka](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Interaktywne Opcje systemu Windows

(**Narzędzia**  >  **Opcje**  >  Język **Python**  >  Karta **interaktywne okna** .)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Skrypty** | nie dotyczy | Określa folder ogólny dla skryptów uruchamiania, który ma być stosowany do **interaktywnych** okien dla wszystkich środowisk. Zobacz [skrypty uruchamiania](python-environments-window-tab-reference.md#startup-scripts). Należy jednak pamiętać, że ta funkcja aktualnie nie działa. |
| **Strzałki w górę/w dół — przejdź do historii** | Włączone | Używa klawiszy strzałek, aby nawigować przez historię w oknie **interaktywnym** . Wyczyść to ustawienie, aby użyć klawiszy strzałek do nawigowania w danych wyjściowych okna **interaktywnego** . |
| **Tryb uzupełniania** | **Obliczaj tylko wyrażenia bez wywołań funkcji** | Proces określania dostępnych elementów członkowskich w wyrażeniu w oknie **interaktywnym** może wymagać oceny bieżącego nieukończonego wyrażenia, co może spowodować wielokrotne wywoływanie efektów ubocznych lub funkcji. Ustawienie domyślne **tylko oblicza wyrażenia bez wywołań funkcji** wyklucza wyrażenia, które pojawiają się, aby wywołać funkcję, ale oblicza inne wyrażenia. Na przykład szacuje się, `a.b` ale nie `a().b` .  **Nigdy nie oceniaj wyrażeń** uniemożliwia wszystkie efekty uboczne, używając tylko standardowego aparatu IntelliSense dla sugestii. **Oceń wszystkie wyrażenia** oblicza pełne wyrażenie, aby uzyskać sugestie, niezależnie od efektów ubocznych. |
| **Ukryj sugestie analizy statycznej** | Wyłączone | Po ustawieniu program wyświetla tylko sugestie, które są uzyskiwane przez obliczenie wyrażenia. W połączeniu z wartością **Tryb uzupełniania** **nigdy nie Obliczaj wyrażeń**, w oknie **interaktywnym** nie są wyświetlane żadne użyteczne zakończenia. |

![Okno dialogowe Opcje języka Python, karta interaktywne okna systemu Windows](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Opcje serwera języka

(**Narzędzia** > **Opcje** > Język **Python** > Karta **serwer języka** ).

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Wyłącz uzupełnianie z zbioru typeshed** | Wyłączone | Program Visual Studio IntelliSense zwykle używa powiązanej wersji programu zbioru typeshed (zestawu plików *. Pyi* ), aby znaleźć wskazówki dotyczące typów dla biblioteki standardowej i bibliotek innych firm dla języka Python 2 i Python 3. Ustawienie tej opcji powoduje wyłączenie powiązanego zachowania zbioru typeshed. |
| **Niestandardowa ścieżka zbioru typeshed** | puste | Jeśli ta wartość jest ustawiona, program Visual Studio używa plików zbioru typeshed w tej ścieżce zamiast jej powiązanej wersji. Zignoruj, jeśli ustawiono ustawienie **Wyłącz uzupełniania z zbioru typeshed** . |

![Okno dialogowe Opcje środowiska Python, karta serwer języka](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Zaawansowane opcje edytora języka Python

(**Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  Język **Python**  >  Karta **Zaawansowane** ).

### <a name="completion-results"></a>Wyniki ukończenia

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Uzupełnianie elementu członkowskiego Wyświetla część wspólną elementów członkowskich** | Wyłączone | Gdy ustawiona, pokazuje tylko uzupełniania, które są obsługiwane przez wszystkie możliwe typy. |
| **Lista filtrów oparta na ciągu wyszukiwania** | Włączone | Stosuje filtrowanie sugestii uzupełniania podczas pisania (domyślnie zaznaczone). |
| **Automatycznie pokazuj uzupełniania dla wszystkich identyfikatorów** | Włączone | Usuń zaznaczenie tej opcji, aby wyłączyć uzupełnianie zarówno w edytorze, jak i w **interaktywnych** oknach. |

### <a name="selection-in-completion-list"></a>Wybór na liście uzupełniania

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Zatwierdzone przez wpisanie następujących znaków** | **{}\[\]().,:; +-*/% &&#124;^ ~ =<> #@\\** | Te znaki zwykle są zgodne z identyfikatorem, który może zostać wybrany z listy uzupełniania, dzięki czemu można zatwierdzić zakończenie po prostu wpisując znak. W razie potrzeby można usunąć określone znaki lub dodać je do listy.  |
| **Wprowadź bieżące uzupełnianie zatwierdzeń** | Włączone | Gdy ta opcja jest ustawiona, klawisz **Enter** wybiera i stosuje aktualnie wybrane uzupełnienie, jak w przypadku powyższych znaków (ale oczywiście nie jest znakiem do **wprowadzenia** , więc nie można bezpośrednio przejść do tej listy). |
| **Dodaj nowy wiersz przy klawiszu Enter na końcu w pełni wpisanego wyrazu** | Wyłączone | Domyślnie po wpisaniu całego wyrazu, który pojawia się w podręcznym uzupełnianiu i naciśnięciu klawisza **Enter**, należy zatwierdzić to zakończenie. Ustawiając tę opcję, możesz efektywnie zatwierdzać uzupełnianie po zakończeniu wpisywania identyfikatora, na przykład, który **wprowadza** Wstaw nowy wiersz. |

### <a name="miscellaneous-options"></a>Różne opcje

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Wejdź do trybu konspektu przy otwieraniu plików** | Włączone | Automatycznie Włącz funkcję tworzenia konspektu programu Visual Studio w edytorze podczas otwierania pliku kodu w języku Python. |
| **Wklej usunięte wiersze REPL** | Włączone | Usuwa **>>>** i **...** z wklejonego tekstu, co pozwala na łatwe przenoszenie kodu z okna **interaktywnego** do edytora. Usuń zaznaczenie tej opcji, jeśli chcesz zachować te znaki podczas wklejania z innych źródeł. |
| **Nazwy kolorów oparte na typach** | Włączone | Włącza kolorowanie składni w kodzie języka Python. |

![Okno dialogowe Opcje edytora języka Python, karta Zaawansowane](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opcje czcionek i kolorów

(**Środowisko**  >  Karta **czcionki i kolory** w grupie **Edytor tekstu** .

Nazwy opcji w języku Python są wszystkie poprzedzone językiem **Python** i nie mają wyjaśnień. Domyślną czcionką dla wszystkich motywów kolorów programu Visual Studio jest 10pt Consolas Regular (niepogrubiony). Kolory domyślne różnią się w zależności od motywu. Zazwyczaj można zmienić czcionkę lub kolor, jeśli okaże się trudne odczytanie tekstu z ustawieniami domyślnymi.

![Opcje czcionek i kolorów w języku Python](media/options-fonts-and-colors.png)
