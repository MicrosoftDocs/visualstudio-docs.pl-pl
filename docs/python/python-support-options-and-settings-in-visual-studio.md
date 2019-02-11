---
title: Opcje i ustawienia dla języka Python
description: Odwołanie dla różnych ustawień w programie Visual Studio, które odnoszą się do kodu w języku Python i projektów.
ms.date: 02/11/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Experimental
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 3589447cdc9451a52dcffb4653a31f188b33c634
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987395"
---
# <a name="options-for-python-in-visual-studio"></a>Opcje dla języka Python w programie Visual Studio

Aby wyświetlić opcje języka Python, użyj **narzędzia** > **opcje** menu poleceń, upewnij się, że **Pokaż wszystkie ustawienia** jest zaznaczone, a następnie przejdź do  **Narzędzia języka Python**:

![Okno dialogowe z opcjami języka Python, na karcie Ogólne](media/options-general.png)

Dostępne są również dodatkowe opcje specyficzne dla języka Python na **edytora tekstów** > **Python** > **zaawansowane** kartę, a następnie na  **Środowisko** > **czcionki i kolory** kartę w ramach **edytora tekstów** grupy.

> [!Note]
> **Eksperymentalne** grupa zawiera opcje dla funkcji, które są nadal w fazie projektowania i nie są opisane tutaj. Są one często omówione w wpisy na [engineering języka Python w blogu firmy Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="general-options"></a>Opcje ogólne

(**Narzędzia** > **opcje** > **Python** karty.)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Pokaż okno danych wyjściowych, podczas tworzenia środowisk wirtualnych**| On | Usuń zaznaczenie, aby zapobiec **dane wyjściowe** znajdujących się w oknie. |
| **Pokaż okno dane wyjściowe podczas instalowania lub usuwania pakietów** | On | Usuń zaznaczenie, aby zapobiec **dane wyjściowe** znajdujących się w oknie. |
| **Zawsze uruchamiaj pip jako administrator** | Off | Zawsze skutkująca podniesieniem uprawnień `pip install` operacje dla wszystkich środowisk. Podczas instalowania pakietów, Visual Studio monituje o uprawnienia administratora, jeśli środowisko znajduje się w obszarze chronionym systemu plików takich jak *c:\Program Files*. W wierszu polecenia, że użytkownik może zawsze podniesienie poziomu `pip install` danego tylko jednego środowiska. Zobacz [karcie pakiety](python-environments-window-tab-reference.md#packages-tab). |
| **Automatyczne generowanie bazy danych uzupełniania przy pierwszym użyciu** | On | *Podczas korzystania z bazy danych IntelliSense, stosuje się do programu Visual Studio 2017 w wersji 15.5 i starszych i nowszych wersjach.* Priorytet uzupełniania bazy danych biblioteki podczas pisania kodu, który korzysta z niego. Aby uzyskać więcej informacji, zobacz [karta Intellisense](python-environments-window-tab-reference.md#intellisense-tab). |
| **Ignoruj zmienne PYTHONPATH całego systemu** | On | PYTHONPATH jest ignorowana domyślnie, ponieważ program Visual Studio zapewnia bardziej bezpośrednie oznacza, że do określania ścieżek wyszukiwania w środowiskach i projektów. Zobacz [ścieżki wyszukiwania](search-paths.md) Aby uzyskać szczegółowe informacje. |
| **Aktualizowanie ścieżki wyszukiwania podczas dodawania plików połączonych** | On | Gdy ustawiona, dodając [połączonego pliku](managing-python-projects-in-visual-studio.md#linked-files) z projektem aktualizacje [ścieżki wyszukiwania](search-paths.md) tak, aby funkcja IntelliSense może zawierać zawartość folderu plików połączonych ze swojej bazy danych uzupełniania. Usuń zaznaczenie tej opcji, aby wykluczyć takiej zawartości z bazy danych uzupełniania. |
| **Ostrzeżenie podczas importowania, że nie można odnaleźć modułu** | On | Wyczyść tę opcję, aby pominąć ostrzeżenia, gdy wiadomo, zaimportowanego modułu nie jest obecnie dostępna, ale w przeciwnym razie nie ma wpływu na działanie kodu. |
| **Wcięcie niespójne raport jako** | **Ostrzeżenia** | Ponieważ interpreter języka Python silnie zależy właściwe wcięcia, aby określić zakres, Visual Studio domyślnie generuje ostrzeżenia po wykryciu niespójne wcięcia, które mogą wskazywać błędów kodowania. Ustaw **błędy** było jeszcze bardziej rygorystyczne, co powoduje, że program zakończyć działanie w takich przypadkach. Aby całkowicie wyłączyć to zachowanie, zaznacz **nie**. |
| **Wyszukaj ankiety/wiadomości** | **Raz w tygodniu** | Określa częstotliwość, jaką zezwolisz programowi Visual Studio otworzyć okno zawierające strony sieci web z ankiet związane z języka Python i elementy wiadomości, jeśli jest dostępny. Dostępne są opcje **nigdy**, **raz dziennie**, **raz w tygodniu**, i **raz w miesiącu**. |
| **Resetuj wszystkie okna dialogowe trwale ukryty** przycisku | n/d | Różne okna dialogowe udostępniają opcje, takie jak **nie pokazuj mi tego ponownie**. Użyj tego przycisku, aby wyczyścić te opcje i powodować wyświetlanie okien dialogowych się ponownie. |

![Okno dialogowe z opcjami języka Python, na karcie Ogólne](media/options-general.png)

## <a name="debugging-options"></a>Opcje debugowania

(**Narzędzia** > **opcje** > **Python** > **debugowanie** karty.)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Przed uruchomieniem, gdy występują błędy** | On | Gdy opcja, wyświetli monit o potwierdzenie uruchomienia kodu, który zawiera błędy. Usuń zaznaczenie tej opcji, aby wyłączyć ostrzeżenia. |
| **Czeka na dane wejściowe, gdy proces zakończy się nieprawidłowo**<br/><br/>**Czeka na dane wejściowe, gdy proces zakończy się normalnie** | Na (dla obu) | Uruchamia program Python uruchomiony z programu Visual Studio w osobnym oknie konsoli. Domyślnie okno czeka na naciśnięcie klawisza przed jego zamknięciem, niezależnie od tego, w jaki sposób program jest zamykany. Aby usunąć ten monit i zamknąć okno automatycznie, usuń zaznaczenie jednego lub obu tych opcji. |
| **Program Tee dane wyjściowe programu do okna danych wyjściowych debugowania** | On | Wyświetla dane wyjściowe programu zarówno w oknie konsoli oddzielne, jak i programu Visual Studio **dane wyjściowe** okna. Usuń zaznaczenie tej opcji, aby wyświetlić dane wyjściowe tylko w oknie konsoli oddzielne. |
| **Przerwij po wyjątku SystemExit z kodem zakończenia o wartości zero** | Off | Jeśli zestawu, debuger zatrzymuje się na ten wyjątek. Jeśli jest wyczyszczone, debuger kończy działanie bez przerywania. |
| **Włącz debugowanie standardowej biblioteki języka Python** | Off | Umożliwia on kod źródłowy biblioteki standardowej krok po kroku podczas debugowania, ale wydłuża czas potrzebny do debugera rozpocząć.|

![Okno dialogowe języka Python, karta Debugowanie](media/options-debugging.png)

## <a name="diagnostics-options"></a>Opcje diagnostyki

(**Narzędzia** > **opcje** > **Python** > **diagnostyki** karty.)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Obejmują analizy dzienników** | On | Zawiera szczegółowe dzienniki odnoszących się do analizy zainstalowanego środowiska Python, podczas zapisywania pliku diagnostyki lub kopiując je do Schowka, za pomocą przycisków. Ta opcja może znacznie zwiększyć rozmiar wygenerowanego pliku, ale często jest wymagany do diagnozowania problemów z technologii IntelliSense. |
| **Zapisz diagnostyki pliku** przycisku | n/d | Monituje o podanie nazwy pliku, a następnie zapisuje dziennik do pliku tekstowego. |
| **Skopiuj diagnostykę do Schowka** przycisku | n/d | Umieszczenie całego dziennika w Schowku; Ta operacja może potrwać pewien czas w zależności od rozmiaru dziennika. |

![Okno dialogowe z opcjami języka Python, karta Diagnostyka](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Opcje interakcyjne Windows

(**Narzędzia** > **opcje** > **Python** > **interaktywne Windows** karty.)

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Skrypty** | n/d | Określa ogólne folder skrypty uruchamiania zastosować do **Interactive** systemu windows dla wszystkich środowisk. Zobacz [skrypty uruchamiania](python-environments-window-tab-reference.md#startup-scripts). Należy jednak pamiętać, że ta funkcja nie działa obecnie. |
| **Strzałki w górę/w dół przejdź historii** | On | Używa klawiszy strzałek, aby poruszać się po historii w **Interactive** okna. Wyczyść to ustawienie, aby użyć klawiszy strzałek aby przejść w ramach **Interactive** okno danych wyjściowych zamiast tego. |
| **Tryb uzupełniania** | **Tylko ocena wyrażenia bez wywołania funkcji** | Proces określania dostępni członkowie na wyrażeniu w **Interactive** okna może wymagać oceny bieżącego wyrażenia niedokończone może spowodować skutki uboczne lub funkcje wywoływana wiele razy. Ustawieniem domyślnym **tylko obliczać wyrażeń bez wywołania funkcji** wyklucza wyrażeń, które pojawiają się w wywołaniu funkcji, ale ocenia inne wyrażenia. Na przykład, ocenia `a.b` , ale nie `a().b`.  **Nigdy nie obliczać wyrażeń** uniemożliwia wszystkie efekty uboczne, przy użyciu tylko normalne aparatu funkcji IntelliSense dla sugestie. **Oceń wszystkie wyrażenia** ocenia Dokończ wyrażenie, aby uzyskać sugestie, niezależnie od tego, efekty uboczne. |
| **Ukryj podpowiedzi analizy statycznej** | Off | Po ustawieniu wyświetla tylko sugestie, które są uzyskiwane przez obliczenie wyrażenia. Jeśli w połączeniu z **trybem uzupełniania** wartość **nigdy nie obliczać wyrażeń**, nie przydatne uzupełnienia pojawiają się w **Interactive** okna. |

![Python opcji okna dialogowego, karta Windows interaktywne](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Zaawansowane opcje edytora języka Python

(**Narzędzia** > **opcje** > **edytora tekstów** > **Python**  >   **Zaawansowane** karty.)

### <a name="completion-results"></a>Wyniki zakończenia

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Uzupełnianie składowych Wyświetla część wspólną elementów członkowskich** | Off | Po ustawieniu uzupełnienia tylko pokazuje, które są obsługiwane przez wszystkie możliwe typy. |
| **Filtrowanie listy na podstawie ciągu wyszukiwania** | On | Stosuje się filtrowanie sugestie uzupełniania podczas wpisywania (pole jest domyślnie zaznaczone). |
| **Automatycznie pokazuj uzupełnienia dla wszystkich identyfikatorów** | On | Usuń zaznaczenie tej opcji, aby wyłączyć uzupełnianie w edytorze programu i **Interactive** systemu windows. |

### <a name="selection-in-completion-list"></a>Wybór na liście uzupełniania

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Zatwierdzone, wpisując następujące znaki** | **{}\[\]().,:;+-*/%&&#124;^~=<>#@\\** | Te znaki wykonaj zazwyczaj identyfikator, który może wybrać z listy uzupełniania, dzięki czemu jest to wygodne potwierdzić zakończenie po prostu wpisując znak. Możesz usunąć lub dodać określonych znaków do listy zgodnie z potrzebami.  |
| **Wprowadź bieżące ukończenia zatwierdzenia** | On | Po ustawieniu **Enter** klucz wybiera i stosuje ukończenie aktualnie wybranego podobnie jak w powyższym znaków (ale oczywiście nie ma znak dla **Enter** więc nie można go bezpośrednio przejść do tej listy!). |
| **Dodaj nowy wiersz po naciśnięciu klawisza enter na końcu pełnego wpisanego wyrazu** | Off | Domyślnie, jeśli wpiszesz cały wyraz, który pojawia się w menu podręczne ukończenia, a następnie naciśnij klawisz **Enter**, zatwierdzenia tej ukończenia. Przez ustawienie tej opcji, efektywnie zatwierdzić uzupełnienia po zakończeniu wpisywania identyfikatora, tak, aby **Enter** powoduje wstawienie nowego wiersza. |

### <a name="miscellaneous-options"></a>Inne opcje

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| **Przejdź do trybu konspektu po otwarciu plików** | On | Podczas otwierania pliku kodu Python automatycznie należy włączyć funkcję tworzenia konspektów programu Visual Studio w edytorze. |
| **Wklej usunięte monitów REPL** | On | Usuwa **>>>** i **...**  z wklejonego tekstu, umożliwiając łatwy transfer kodu z **Interactive** okna edytora. Usuń zaznaczenie tej opcji, jeśli chcesz zachować te znaki przy wklejaniu z innych źródeł. |
| **Nazw kolorów na podstawie typów** | On | Umożliwia kolorowanie składni w kodzie języka Python. |

![Python edytora okno dialogowe Opcje, karta Zaawansowane](media/options-editor-advanced.png)

## <a name="fonts-and-colors-options"></a>Opcje czcionek i kolorów

(**Środowiska** > **czcionki i kolory** kartę w ramach **edytora tekstów** grupy.)

Nazwy opcji języka Python mają prefiks z **Python** i nie wymaga wyjaśnień. Domyślna czcionka we wszystkich motywów kolorów programu Visual Studio jest 10 pkt Consolas zwykłe (nie pogrubienie). Kolory domyślne zależą od motywu. Zwykle możesz zmienić czcionkę i kolor Jeśli trudne do odczytywania tekstu z ustawieniami domyślnymi.

![Opcje czcionek i kolorów dla języka Python](media/options-fonts-and-colors.png)
