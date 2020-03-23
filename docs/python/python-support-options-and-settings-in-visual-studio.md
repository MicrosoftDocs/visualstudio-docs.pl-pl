---
title: Opcje i ustawienia języka Python
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
ms.openlocfilehash: 08501d71400a0df139022f04e68573d0dd1449d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302750"
---
# <a name="options-for-python-in-visual-studio"></a>Opcje języka Python w programie Visual Studio

Aby wyświetlić opcje języka Python, użyj polecenia menu**Opcje** **narzędzi,** > upewnij się, że jest zaznaczone pokaż **wszystkie ustawienia,** a następnie przejdź do **języka Python:**

::: moniker range="vs-2017"
![Okno dialogowe Opcje języka Python, karta Ogólne](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje języka Python, karta Ogólne](media/options-general-2019.png)
::: moniker-end

Istnieją również dodatkowe opcje specyficzne dla języka Python na karcie **Environment** > **Zaawansowana** **edytor** > tekstu**Python** > oraz na karcie**Czcionki środowiska i kolory** w grupie Edytor **tekstu.**

> [!Note]
> Grupa **Eksperymentalna** zawiera opcje dla funkcji, które są nadal opracowywały i nie są tutaj udokumentowane. Są one często omawiane w postach na [temat inżynierii Pythona na blogu Microsoft](https://devblogs.microsoft.com/python/).

## <a name="general-options"></a>Opcje ogólne

(Karta**Opcje** > **narzędzi** > **Pythona).**

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Pokazywanie okna wyjściowego podczas tworzenia środowisk wirtualnych**| Włączone | Wyczyść, aby zapobiec pojawianiu się okna **Dane wyjściowe.** |
| **Pokaż okno wyjściowe podczas instalowania lub usuwania pakietów** | Włączone | Wyczyść, aby zapobiec pojawianiu się okna **Dane wyjściowe.** |
| **Pokaż pasek powiadomień, aby tworzyć środowiska** | Włączone | *Tylko visual studio 2019.* Gdy ta opcja jest ustawiona, a użytkownik otwiera projekt, który zawiera plik *requirements.txt* lub *environment.yml,* program Visual Studio wyświetla pasek informacji z sugestiami, aby utworzyć środowisko wirtualne lub środowisko conda, odpowiednio, zamiast używać domyślnego środowiska globalnego. |
| **Pokaż pasek powiadomień, aby zainstalować pakiety** | Włączone | *Tylko visual studio 2019.* Gdy ta opcja jest ustawiona i użytkownik otwiera projekt, który zawiera plik *requirements.txt* (i nie używa domyślnego środowiska globalnego) Program Visual Studio porównuje te wymagania z pakietami zainstalowanymi w bieżącym środowisku. Jeśli brakuje pakietów, program Visual Studio wyświetla monit o zainstalowanie tych zależności. |
| **Zawsze uruchamiaj menedżerów pakietów jako administrator** | Wyłączone | Zawsze podnosi `pip install` i podobne operacje menedżera pakietów dla wszystkich środowisk. Podczas instalowania pakietów program Visual Studio monituje o uprawnienia administratora, jeśli środowisko znajduje się w chronionym obszarze systemu plików, takim jak *c:\Program Files*. W tym wierszu można wybrać, aby zawsze podnieść poziom polecenia install tylko dla tego jednego środowiska. Zobacz [kartę Pakiety](python-environments-window-tab-reference.md#packages-tab). |
| **Automatyczne generowanie bazy danych ukończenia przy pierwszym użyciu** | Włączone | *Dotyczy programu Visual Studio 2017 w wersji 15.5 i wcześniejszych oraz nowszych wersjach podczas korzystania z bazy danych IntelliSense.* Nadaje priorytet ukończeniu bazy danych dla biblioteki podczas pisania kodu, który jej używa. Aby uzyskać więcej informacji, zobacz [kartę Intellisense](python-environments-window-tab-reference.md?view=vs-2017#intellisense-tab). |
| **Ignoruj zmienne PYTHONPATH dla całego systemu** | Włączone | PYTHONPATH jest domyślnie ignorowane, ponieważ visual studio zapewnia bardziej bezpośrednie środki do określenia ścieżek wyszukiwania w środowiskach i projektach. Zobacz [Wyszukiwanie ścieżek, aby](search-paths.md) uzyskać szczegółowe informacje. |
| **Aktualizowanie ścieżek wyszukiwania podczas dodawania połączonych plików** | Włączone | Po ustawieniu dodanie [połączonego pliku](managing-python-projects-in-visual-studio.md#linked-files) do projektu [aktualizuje ścieżki wyszukiwania,](search-paths.md) dzięki czemu intellisense może zawierać zawartość folderu połączonego pliku w bazie danych ukończenia. Wyczyść tę opcję, aby wykluczyć taką zawartość z bazy danych ukończenia. |
| **Nie można znaleźć ostrzeżenia, gdy importowany moduł** | Włączone | Wyczyść tę opcję, aby pominąć ostrzeżenia, gdy wiesz, że importowany moduł nie jest obecnie dostępny, ale w przeciwnym razie nie wpływa na działanie kodu. |
| **Zgłaszanie niespójnego wcięciem jako** | **Ostrzeżenia** | Ponieważ interpreter języka Python zależy w dużej mierze od prawidłowego wcięcia w celu określenia zakresu, program Visual Studio domyślnie wydaje ostrzeżenia, gdy wykryje niespójne wcięcia, które mogą wskazywać na błędy kodowania. Ustaw **błędy,** aby być jeszcze bardziej rygorystyczne, co powoduje, że program do zakończenia w takich przypadkach. Aby całkowicie wyłączyć to zachowanie, wybierz opcję **Nie.** |
| **Sprawdź ankietę/wiadomości** | **Raz w tygodniu** | *Visual Studio 2017 i wcześniej.* Ustawia częstotliwość, z jaką program Visual Studio może otwierać okno zawierające stronę sieci web z ankietami i wiadomościami związanymi z językiem Python, jeśli są dostępne. Opcje są **nigdy**, **Raz dziennie,** **Raz w tygodniu**i **Raz w miesiącu.** |
| **Przycisk Resetowanie wszystkich trwale ukrytych okien dialogowych** | Nie dotyczy | Różne okna dialogowe zawierają opcje, takie jak **Nie pokazuj mi tego ponownie.** Użyj tego przycisku, aby wyczyścić te opcje i spowodować ponowne pojawienie się okien dialogowych. |

::: moniker range="vs-2017"
![Okno dialogowe Opcje języka Python, karta Ogólne](media/options-general.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje języka Python, karta Ogólne](media/options-general-2019.png)
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="conda-options"></a>Opcje Conda

(Opcje**narzędzi** > **Options** > **Python** > **Conda** kartę.)

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Ścieżka wykonywalna Conda** | (puste) | Określa dokładną ścieżkę do pliku wykonywalnego *conda.exe,* zamiast polegać na domyślnej instalacji Miniconda, która jest dołączona do obciążenia języka Python. Jeśli w tym miejscu zostanie podana inna ścieżka, ma pierwszeństwo przed instalacją domyślną i innymi plikami wykonywalnymi conda.exe określonymi w rejestrze. To ustawienie można zmienić, jeśli ręcznie zainstalujesz nowszą wersję anakondy lub minikondy lub chcesz użyć dystrybucji 32-bitowej zamiast domyślnej dystrybucji 64-bitowej. |

![Okno dialogowe Opcje języka Python, karta Serwer języka](media/options-conda.png)

::: moniker-end

## <a name="debugging-options"></a>Opcje debugowania

(Opcje**narzędzi** > **Options** > **Python** > **Debugowanie** kartę.)

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Monituj przed uruchomieniem, gdy występują błędy** | Włączone | Po ustawieniu monituje o potwierdzenie, że chcesz uruchomić kod zawierający błędy. Wyczyść tę opcję, aby wyłączyć ostrzeżenie. |
| **Poczekaj na wejście, gdy proces zakończy się nieprawidłowo**<br/><br/>**Poczekaj na wejście, gdy proces zakończy się normalnie** | Wł./WE (dla obu) | Program Python uruchomiony z programu Visual Studio jest uruchamiany we własnym oknie konsoli. Domyślnie okno czeka na naciśnięcie klawisza przed zamknięciem, niezależnie od tego, jak program kończy działanie. Aby usunąć ten monit i automatycznie zamknąć okno, wyczyść jedną lub obie te opcje. |
| **Dane wyjściowe programu trójnikowego do okna Dane wyjściowe debugowania** | Włączone | Wyświetla dane wyjściowe programu zarówno w osobnym oknie konsoli, jak i w oknie **Dane wyjściowe** programu Visual Studio. Wyczyść tę opcję, aby wyświetlić dane wyjściowe tylko w osobnym oknie konsoli. |
| **Przerwa na Wyjątek SystemExit z kodem zakończenia zero** | Wyłączone | Jeśli jest ustawiona, zatrzymuje debugera na ten wyjątek. Gdy jest jasne, debuger kończy pracę bez przerywania. |
| **Włączanie debugowania biblioteki standardowej języka Python** | Wyłączone | Umożliwia krok do standardowego kodu źródłowego biblioteki podczas debugowania, ale zwiększa czas potrzebny do uruchomienia debugera.|
| **Pokaż wartość zwracaną funkcji** | Włączone | *Tylko visual studio 2019.* Wyświetla wartości zwracane funkcji w oknie **Zmiennoprawicy,** a następnie przechodzenie przez wywołanie funkcji w debugerze (F10) |
| **Używanie starszego debugera** | Wyłączone | *Tylko visual studio 2019.* Nakazuje visual studio, aby domyślnie używać starszego debugera. Aby uzyskać więcej informacji, zobacz [Debugowanie — używanie starszego debugera](debugging-python-in-visual-studio.md#use-the-legacy-debugger). |

::: moniker range="vs-2017"
![Okno dialogowe Opcje języka Python, karta Debugowanie](media/options-debugging.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno dialogowe Opcje języka Python, karta Debugowanie](media/options-debugging-2019.png)
::: moniker-end

## <a name="diagnostics-options"></a>Opcje diagnostyki

(Opcje**narzędzi** > **Options** > **python** > **diagnostyki** kartę.)

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Dołącz dzienniki analizy** | Włączone | Zawiera szczegółowe dzienniki dotyczące analizy zainstalowanych środowisk Języka Python podczas zapisywania diagnostyki w pliku lub kopiowania ich do schowka za pomocą przycisków. Ta opcja może znacznie zwiększyć rozmiar wygenerowanego pliku, ale jest często wymagana do diagnozowania problemów z programem IntelliSense. |
| **Zapisz przycisk diagnostyki w pliku** | Nie dotyczy | Monituje o nazwę pliku, a następnie zapisuje dziennik w pliku tekstowym. |
| **Przycisk Kopiowania diagnostyki do schowka** | Nie dotyczy | Umieszcza całość dziennika w schowku; ta operacja może zająć trochę czasu w zależności od rozmiaru dziennika. |

![Okno dialogowe Opcje języka Python, karta Diagnostyka](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Interaktywne opcje systemu Windows

 > (Opcje**narzędzi** > **Options****Python** > **Interactive Windows** kartę.)

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Scripts** | Nie dotyczy | Określa ogólny folder skryptów startowych, który ma być stosowany do okien **interaktywnych** dla wszystkich środowisk. Zobacz [Skrypty startowe](python-environments-window-tab-reference.md#startup-scripts). Należy jednak pamiętać, że ta funkcja nie działa obecnie. |
| **Historia nawigacji w górę/w dół** | Włączone | Używa klawiszy strzałek do poruszania się po historii w oknie **Interaktywna.** Wyczyść to ustawienie, aby zamiast tego za pomocą klawiszy strzałek poruszać się w oknie **interaktywnym.** |
| **Tryb ukończenia** | **Oceniaj tylko wyrażenia bez wywołań funkcji** | Proces określania dostępnych elementów członkowskich wyrażenia w oknie **Interaktywna** może wymagać oceny bieżącego niedokończonego wyrażenia, co może spowodować, że skutki uboczne lub funkcje będą wywoływane wiele razy. Ustawienie domyślne **Tylko oceniać wyrażenia bez wywołań funkcji** wyklucza wyrażenia, które wydają się wywoływać funkcję, ale ocenia inne wyrażenia. Na przykład ocenia, `a.b` ale `a().b`nie .  **Nigdy nie oceniaj wyrażeń** zapobiega wszystkie skutki uboczne, przy użyciu tylko normalny aparat IntelliSense sugestie. **Oceń wszystkie wyrażenia** ocenia pełne wyrażenie, aby uzyskać sugestie, niezależnie od skutków ubocznych. |
| **Ukrywanie sugestii analizy statycznej** | Wyłączone | Po ustawieniu wyświetla tylko sugestie, które są uzyskiwane przez ocenę wyrażenia. W połączeniu z wartością **trybu ukończenia** Nigdy **nie oceniaj wyrażeń,** w oknie **Interaktywna** nie są wyświetlane przydatne uzupełnienia. |

![Okno dialogowe Opcje języka Python, karta Interaktywne systemy Windows](media/options-interactive-windows.png)

::: moniker range=">=vs-2019"
## <a name="language-server-options"></a>Opcje serwera językowego

**Options** > (Opcje**narzędzi** > na **serwerze języka** **Python).** >

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Wyłączanie uzupełnień z typeshed** | Wyłączone | Visual Studio IntelliSense zwykle używa dołączonej wersji Typeshed (zestaw plików *pyi)* do znajdowania wskazówek dotyczących typu dla biblioteki standardowej i bibliotek innych firm dla pythona 2 i Pythona 3. Ustawienie tej opcji powoduje wyłączenie powiązanego zachowania TypeShed. |
| **Ścieżka typowa niestandardowa** | (puste) | Jeśli jest ustawiona, program Visual Studio używa typeshed plików w tej ścieżce zamiast jego wersji dołączonej. Ignoruj, jeśli **wyłącz uzupełnienia z Typeshed** jest ustawiona. |

![Okno dialogowe Opcje języka Python, karta Serwer języka](media/options-language-server.png)

::: moniker-end

## <a name="advanced-python-editor-options"></a>Zaawansowane opcje edytora Języka Python

(Opcje**narzędzi** > **Options** > **Edytor** > tekstu**Python** > **Zaawansowane** karty.)

### <a name="completion-results"></a>Wyniki ukończenia

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Zakończenie elementu członkowskiego wyświetla przecięcie elementów członkowskich** | Wyłączone | Po ustawieniu pokazuje tylko uzupełnienia, które są obsługiwane przez wszystkie możliwe typy. |
| **Lista filtrów na podstawie ciągu wyszukiwania** | Włączone | Stosuje filtrowanie sugestii ukończenia podczas pisania (domyślnie jest zaznaczone). |
| **Automatyczne wyświetlanie uzupełnień dla wszystkich identyfikatorów** | Włączone | Wyczyść tę opcję, aby wyłączyć uzupełnienia zarówno w edytorze, jak i w oknach **interaktywnych.** |

### <a name="selection-in-completion-list"></a>Wybór na liście uzupełnień

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Zatwierdzone przez wpisanie następujących znaków** | **{}\[\]().,:;+-*/%&&#124;^~=<> #@\\** | Te znaki zazwyczaj są zgodne z identyfikatorem, który można wybrać z listy uzupełnień, więc wygodnie jest zatwierdzić ukończenie po prostu wpisując znak. W razie potrzeby można usunąć lub dodać określone znaki do listy.  |
| **Wprowadzanie bieżącego zakończenia zatwierdzania** | Włączone | Po ustawieniu klawisz **Enter** wybiera i stosuje aktualnie wybrane uzupełnianie, tak jak w przypadku powyższych znaków (ale oczywiście nie ma znaku **enter,** więc nie może przejść bezpośrednio do tej listy!). |
| **Dodawanie nowego wiersza na końcu w pełni wpisanego wyrazu** | Wyłączone | Domyślnie, jeśli wpiszesz cały wyraz, który pojawi się w wyskakującym okienku zakończenia i naciśnij **klawisz Enter,** zatwierdzisz to zakończenie. Ustawiając tę opcję, skutecznie zatwierdzasz uzupełnienia po zakończeniu wpisywania identyfikatora, w taki sposób, **że enter** wstawia nowy wiersz. |

### <a name="miscellaneous-options"></a>Różne opcje

| Opcja | Domyślne | Opis |
| --- | --- | --- |
| **Wprowadzanie trybu tworzenia po otwarciu plików** | Włączone | Automatycznie włącz funkcję obliczania programu Visual Studio w edytorze podczas otwierania pliku kodu języka Python. |
| **Wklej usunięte monity REPL** | Włączone | Usuwa **>>>** i **...** z wklejony tekst, co pozwala na łatwe przeniesienie kodu z okna **Interaktywne** do edytora. Wyczyść tę opcję, jeśli chcesz zachować te znaki podczas wklejania z innych źródeł. |
| **Nazwy kolorów na podstawie typów** | Włączone | Włącza kolorowanie składni w kodzie języka Python. |

![Okno dialogowe opcje edytora Języka Python, karta zaawansowane](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opcje czcionek i kolorów

**(Czcionki środowiska** > **i kolory** w grupie Edytor **tekstu).**

Nazwy opcji Pythona są poprzedzone **Pythonem** i są oczywiste. Domyślna czcionka dla wszystkich motywów kolorów programu Visual Studio jest 10pt Consolas regularne (nie pogrubienie). Kolory domyślne różnią się w zależności od motywu. Zazwyczaj czcionka lub kolor jest zmieniany, jeśli trudno jest odczytać tekst z ustawieniami domyślnymi.

![Opcje czcionek i kolorów języka Python](media/options-fonts-and-colors.png)
