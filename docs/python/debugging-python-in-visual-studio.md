---
title: Kod języka Python debugowania
description: Visual Studio zapewniają bogate debugowanie dla kodu języka Python, w tym ustawianie punktów przerwania, przechodzenie krok po kroku, sprawdzanie wartości, przeglądanie wyjątków i debugowanie w oknie interaktywnym.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4678e3508c16b38fec2a10cdeb79bc499eaf15fd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302890"
---
# <a name="debug-your-python-code"></a>Debugowanie kodu języka Python

Visual Studio zapewnia kompleksowe środowisko debugowania dla języka Python, w tym dołączanie do uruchomionych procesów, oceny wyrażeń w **oknach Czujka** i **Natychmiastowe,** sprawdzanie zmiennych lokalnych, punktów przerwania, instrukcji step in/out/over, **Ustaw następną instrukcję**i inne.

Zobacz także następujące artykuły debugowania specyficzne dla scenariusza:

- [Debugowanie zdalne linuksa](debugging-python-code-on-remote-linux-machines.md)
- [Debugowanie języka Python/C++ w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python w programie Visual Studio obsługuje debugowanie bez projektu. Po otwarciu autonomicznego pliku języka Python, kliknij prawym przyciskiem myszy w edytorze, wybierz start **z debugowaniem,** a program Visual Studio uruchamia skrypt z globalnym środowiskiem domyślnym (zobacz [środowiska Python)](managing-python-environments-in-visual-studio.md)i bez argumentów. Ale od tego czasu masz pełną obsługę debugowania.
>
> Aby kontrolować środowisko i argumenty, utwórz projekt dla kodu, który można łatwo wykonać za pomocą szablonu projektu [kodu Pythona Z istniejącego języka Python.](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files)

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje punkty przerwania ustawień, przechodzenie przez kod, sprawdzanie wartości i obsługę wyjątków, jak opisano w poniższych sekcjach.

Sesja debugowania rozpoczyna się od polecenia **Debugowanie start debugowania,** > **Start Debugging** **przycisku Start** na pasku narzędzi lub klawisza **F5.** Te akcje uruchamiają plik startowy projektu (pokazany pogrubioną czcionką w **Eksploratorze rozwiązań)** z aktywnym środowiskiem projektu i wszelkimi argumentami wiersza polecenia lub ścieżkami wyszukiwania określonymi we **właściwościach projektu** (zobacz [opcje debugowania projektu).](#project-debugging-options) Visual Studio 2017 w wersji 15.6 i nowszych alerty, jeśli nie masz zestawu plików startowych; starsze wersje mogą otworzyć okno wyjściowe z uruchomionym interpreterem języka Python lub okno wyjściowe na krótko pojawia się i znika. W każdym przypadku kliknij prawym przyciskiem myszy odpowiedni plik i wybierz polecenie **Ustaw jako plik startowy**.

> [!Note]
> Debuger zawsze rozpoczyna się od aktywnego środowiska Języka Python dla projektu. Aby zmienić środowisko, należy uaktywnić inny, zgodnie z [opisem](selecting-a-python-environment-for-a-project.md)w języku Wybierz środowisko języka Python dla projektu .

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania zatrzymać wykonywanie kodu w oznaczonym punkcie, dzięki czemu można sprawdzić stan programu. Ustawiaj punkty przerwania, klikając lewy margines edytora kodu lub klikając prawym przyciskiem myszy wiersz kodu i wybierając opcję **Breakpoint** > **Insert Breakpoint Breakpoint .** Na każdym wierszu z punktem przerwania pojawia się czerwona kropka.

![Punkty przerwania wyświetlane w programie Visual Studio](media/debugging-breakpoints.png)

Kliknięcie czerwonej kropki lub kliknięcie prawym przyciskiem myszy wiersza kodu i wybranie opcji **Punkt** > **przerwania usuń punkt** przerwania powoduje usunięcie punktu przerwania. Można go również wyłączyć bez usuwania go za pomocą polecenia **Breakpoint** > **Disable Breakpoint.**

> [!Note]
> Niektóre punkty przerwania w Pythonie mogą być zaskakujące dla deweloperów, którzy pracowali z innymi językami programowania. W Pythonie cały plik jest kodem wykonywalnym, więc Python uruchamia plik po załadowaniu do przetwarzania dowolnej klasy najwyższego poziomu lub definicji funkcji. Jeśli punkt przerwania został ustawiony, może się okazać debugera podziału części sposób za pośrednictwem deklaracji klasy. To zachowanie jest poprawne, nawet jeśli czasami jest zaskakujące.

Można dostosować warunki, w których punkt przerwania jest wyzwalany, takie jak podział tylko wtedy, gdy zmienna jest ustawiona na określoną wartość lub zakres wartości. Aby ustawić warunki, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania, wybierz **warunek**, a następnie utwórz wyrażenia przy użyciu kodu Języka Python. Aby uzyskać szczegółowe informacje na temat tej funkcji w programie Visual Studio, zobacz [Warunki punktu przerwania.](../debugger/using-breakpoints.md#breakpoint-conditions)

Podczas ustawiania warunków można również ustawić **akcję** i utworzyć komunikat, aby zalogować się do okna danych wyjściowych, opcjonalnie kontynuując wykonywanie automatycznie. Rejestrowanie wiadomości tworzy to, co nazywa się *punktem śledzenia* bez dodawania kodu rejestrowania bezpośrednio do aplikacji:

![Tworzenie punktu śledzenia z punktem przerwania](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Krok po kroku przez kod

Po zatrzymaniu w punkcie przerwania, masz różne sposoby, aby przejść przez kod lub uruchomić bloki kodu przed zerwaniem ponownie. Polecenia te są dostępne w wielu miejscach, w tym w górnym pasku narzędzi debugowania, menu **debugowania,** w menu kontekstowym prawym przyciskiem myszy w edytorze kodu i za pomocą skrótów klawiaturowych (choć nie wszystkie polecenia znajdują się we wszystkich miejscach):

| Funkcja | Klawiszy | Opis |
| --- | --- | --- |
| **Continue** | **F5** | Uruchamia kod do momentu osiągnięcia następnego punktu przerwania. |
| **Wejdź do** | **F11** | Uruchamia następną instrukcję i zatrzymuje. Jeśli następna instrukcja jest wywołaniem funkcji, debuger zatrzymuje się w pierwszym wierszu wywoływanej funkcji. |
| **Krok nad** | **F10** | Uruchamia następną instrukcję, w tym wykonywanie wywołania funkcji (uruchamianie całego kodu) i stosowanie dowolnej wartości zwracanej. Przechodzenie przez pozwala łatwo pominąć funkcje, które nie trzeba debugować. |
| **Wyjdź** | **Zmiana**+**F11** | Uruchamia kod do końca bieżącej funkcji, a następnie kroki do instrukcji wywołującej.  To polecenie jest przydatne, gdy nie trzeba debugować pozostałą część bieżącej funkcji. |
| **Uruchom do kursora** | **Ctrl**+**F10** | Uruchamia kod do lokalizacji cieczy w edytorze. To polecenie umożliwia łatwe pomijanie segmentu kodu, który nie jest potrzebny do debugowania. |
| **Ustaw następną instrukcję** | **Ctrl**+**Shift**Przesunięcie+ctrl**F10** | Zmienia bieżący punkt uruchomienia w kodzie na lokalizację cieczy. To polecenie umożliwia pominięcie segmentu kodu z uruchamiania w ogóle, na przykład gdy wiesz, że kod jest uszkodzony lub daje niepożądany efekt uboczny. |
| **Pokaż następną instrukcję** | **Alt**+**Num** **&#42;**| Zwraca do następnej instrukcji do uruchomienia. To polecenie jest przydatne, jeśli rozglądasz się w kodzie i nie pamiętasz, gdzie debuger jest zatrzymany. |

### <a name="inspect-and-modify-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu w debugerze można sprawdzić i zmodyfikować wartości zmiennych. **Można** również użyć watch okna do monitorowania poszczególnych zmiennych, jak również wyrażeń niestandardowych. (Aby uzyskać ogólne [informacje, zobacz Inspekcja zmiennych).](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows)

Aby wyświetlić wartość za pomocą **etykietek danych,** wystarczy najechać kursorem myszy na dowolną zmienną w edytorze. Możesz kliknąć na wartość, aby ją zmienić:

![Liczba etykietek danych wyświetlanych w debugerze programu Visual Studio](media/debugging-quick-tips.png)

Okno **Autos** (**Debugowanie** > **autos****systemu Windows** > ) zawiera zmienne i wyrażenia, które znajdują się w pobliżu bieżącej instrukcji. Możesz kliknąć dwukrotnie w kolumnie wartości lub wybrać i nacisnąć **klawisz F2,** aby edytować wartość:

![Okno Autos w debugerze programu Visual Studio](media/debugging-autos-window.png)

W oknie **Zmiennych** lokalnych **(Debug** > **Windows** > **Locals)** są wyświetlane wszystkie zmienne, które znajdują się w bieżącym zakresie, które można ponownie edytować:

![Okna dla mieszkańców w debugerze programu Visual Studio](media/debugging-locals-window.png)

Aby uzyskać więcej informacji na temat **używania autos** i **lokalnych mieszkańców**, zobacz [Inspekcja zmiennych w oknach Autos i Locals](../debugger/autos-and-locals-windows.md).

Okna **czujki** **(Debug** > **Windows** > **Watch** > Watch**1-4**) umożliwiają wprowadzanie dowolnych wyrażeń języka Python i wyświetlanie wyników. Wyrażenia są ponownie dokonywalne dla każdego kroku:

![Okno obserwowanie w debugerze programu Visual Studio](media/debugging-watch-window.png)

Aby uzyskać więcej informacji na temat korzystania z **programu Watch**, zobacz [Ustawianie zegarka na zmiennych przy użyciu okien Zegarka i zegarka QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Podczas sprawdzania wartości`str`ciągu( `unicode` `bytes`, `bytearray` , i są uważane za ciągi znaków w tym celu), ikona lupy pojawia się po prawej stronie wartości. Kliknięcie ikony powoduje wyświetlenie wartości niecytowanego ciągu w oknie dialogowym wyskakującego okienka z zawijaniem i przewijaniem, co jest przydatne w przypadku długich ciągów. Ponadto wybranie strzałki rozwijanej na ikonie umożliwia zaznaczenie wizualizacji w postaci zwykłego tekstu, HTML, XML i JSON:

![Wizualizatory ciągów w debugerze programu Visual Studio](media/debugging-string-visualizers.png)

Wizualizacje HTML, XML i JSON są wyświetlane w oddzielnych oknach podręcznych z wyróżnianiem składni i widokami drzewa.

### <a name="exceptions"></a>Wyjątki

Jeśli wystąpi błąd w programie podczas debugowania, ale nie masz dla niego obsługi wyjątków, debuger przerywa w punkcie wyjątku:

![Wyskakujące okienko wyjątków w debugerze programu Visual Studio](media/debugging-exception-popup.png)

W tym momencie można sprawdzić stan programu, w tym stos wywołań. Jednak jeśli spróbujesz przejść przez kod, wyjątek będzie nadal zgłaszany, dopóki nie zostanie obsłużona lub program zakończy działanie.

Polecenie menu **Debugowanie** > **ustawień wyjątków** **systemu Windows** > powoduje wyświetlenie okna, w którym można rozwinąć **wyjątki języka Python:**

![Okna Wyjątki w debugerze programu Visual Studio](media/debugging-exception-settings.png)

Pole wyboru dla każdego wyjątku określa, czy debuger *zawsze* dzieli się, gdy jest wywoływany. Zaznacz to pole, gdy chcesz przerwać częściej dla określonego wyjątku.

Domyślnie większość wyjątków przerwy, gdy nie można znaleźć obsługi wyjątków w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy dowolny wyjątek i zmodyfikuj opcję **Kontynuuj, gdy nie obsłużony w kodzie użytkownika.** Wyczyść to pole, jeśli chcesz złamać rzadziej dla wyjątku.

Aby skonfigurować wyjątek, który nie jest wyświetlany na tej liście, kliknij przycisk **Dodaj,** aby go dodać. Nazwa musi być zgodna z pełną nazwą wyjątku.

## <a name="project-debugging-options"></a>Opcje debugowania projektu

Domyślnie debuger uruchamia program ze standardowym programem uruchamianym języka Python, bez argumentów wiersza polecenia i bez innych specjalnych ścieżek ani warunków. Opcje uruchamiania są zmieniane za pomocą właściwości debugowania projektu, do których uzyskuje się dostęp, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań,** wybierając **polecenie właściwości**i wybierając kartę **Debugowanie.**

![Właściwości debugowania projektu w debugerze programu Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| **Standardowy wyrzutnia Pythona** | Używa kodu debugowania napisanego w przenośnym pythonie, który jest zgodny z CPython, IronPython i wariantów, takich jak Stackless Python. Zapewnia najlepsze środowisko do debugowania czystego kodu Języka Python. Po dołączeniu do uruchomionego procesu *python.exe,* ten launcher jest używany. Ten program uruchamiający zapewnia również [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) dla CPython, co pozwala na bezproblemowe krok między kodem C/C++ i kodem Pythona. |
| **Uruchamianie sieci Web** | Uruchamia domyślną przeglądarkę po uruchomieniu i umożliwia debugowanie szablonów. Aby uzyskać więcej informacji, zobacz sekcję [debugowania szablonu sieci Web.](python-web-application-project-templates.md#debugging) |
| **Django Web launcher** | Identyczne z programem Web Launcher i wyświetlane tylko w celu zapewnienia zgodności z powrotem. |
| **Wyrzutnia IronPython (.NET)** | Używa debugera .NET, który działa tylko z IronPython, ale pozwala na przechodzenie między dowolnym projektem języka .NET, w tym C# i VB. Ten program uruchamiający jest używany, jeśli dołączysz do uruchomionego procesu .NET, który jest gospodarzem IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Uruchamianie opcji (ścieżki wyszukiwania, argumenty uruchamiania i zmienne środowiskowe)

| Opcja | Opis |
| --- | --- |
| **Ścieżki wyszukiwania** | Wartości te są zgodne z tym, co jest wyświetlane w węźle **Ścieżki wyszukiwania** projektu w **Eksploratorze rozwiązań**. Tę wartość można zmodyfikować w tym miejscu, ale łatwiej jest używać **Eksploratora rozwiązań,** który umożliwia przeglądanie folderów i automatyczne konwertowanie ścieżek na formularz względny. |
| **Argumenty skryptu** | Argumenty te są dodawane do polecenia używanego do uruchamiania skryptu, pojawiającego się po nazwach pliku skryptu. Pierwszy element tutaj jest dostępny `sys.argv[1]`dla skryptu `sys.argv[2]`jako , drugi jako , i tak dalej. |
| **Argumenty interpretera** | Argumenty te są dodawane do wiersza polecenia launchera przed nazwą skryptu. Typowe argumenty `-W ...` w tym `-O` miejscu są do kontrolowania `-u` ostrzeżeń, aby nieznacznie zoptymalizować program i używać niebuforowane we/wy. Użytkownicy IronPython mogą używać tego `-X` pola do `-X:Frames` `-X:MTA`przekazywania opcji, takich jak lub . |
| **Ścieżka interpretera** | Zastępuje ścieżkę skojarzoną z bieżącym środowiskiem. Wartość może być przydatna do uruchamiania skryptu z niestandardowym interpreterem. |
| **Zmienne środowiskowe** | W tym wielowierszowym polu tekstowym \<dodaj wpisy formularza\<NAZWA>= WARTOŚĆ>. Ponieważ to ustawienie jest stosowane jako ostatnie, na podstawie istniejących `PYTHONPATH` globalnych zmiennych środowiskowych i po jest ustawiane zgodnie z **ustawieniem Ścieżki wyszukiwania,** można użyć do ręcznego zastąpienia dowolnej z tych innych zmiennych. |

## <a name="immediate-and-interactive-windows"></a>Okna natychmiastowe i interaktywne

Istnieją dwa interaktywne okna, których można użyć podczas sesji debugowania: standardowe okno **natychmiastowe** programu Visual Studio i okno **Interaktywne debugowanie języka Python.**

**Natychmiastowe** okno **(Debug** > **Windows** > **Immediate)** służy do szybkiej oceny wyrażeń języka Python i inspekcji lub przypisywania zmiennych w uruchomionym programie. Szczegółowe informacje można znaleźć w ogólnym artykule [natychmiastowego okna.](../ide/reference/immediate-window.md)

**Okno Interaktywne debugowanie języka Python** **(Debug** > **Windows** > **Python Debug Interactive)** jest bogatsze, ponieważ udostępnia pełne środowisko [interactive REPL](python-interactive-repl-in-visual-studio.md) podczas debugowania, w tym pisanie i uruchamianie kodu. Automatycznie łączy się z dowolnym procesem uruchomionym w debugerze za pomocą standardowego programu uruchamiający Python (w tym procesów dołączonych za pośrednictwem **debugowania** > **dołączania do procesu).** Nie jest jednak dostępna podczas korzystania z debugowania c/c++ w trybie mieszanym.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

Okno **Debug Interactive** obsługuje specjalne polecenia meta oprócz [standardowych poleceń REPL:](python-interactive-repl-in-visual-studio.md#meta-commands)

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Rozpoczyna uruchamianie programu z bieżącej instrukcji. |
| `$down`, `$d` | Przenieś bieżącą ramkę o jeden poziom w dół w śladzie stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | identyfikator ramki | Przełącza bieżącą klatkę na określony identyfikator ramki.
| `$load` | Ładuje polecenia z pliku i wykonuje do końca |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | identyfikator procesu | Przełącza bieżący proces na określony identyfikator procesu. |
| `$procs` | | Wyświetla listę procesów aktualnie debugowanych. |
| `$stepin`, `$step`, `$s` | Kroki do następnego wywołania funkcji, jeśli to możliwe. |
| `$stepout`, `$return`, `$r` | Wychodzi z bieżącej funkcji. |
| `$stepover`, `$until`, `$unt` | Kroki w ciągu następnego wywołania funkcji. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Przełącza bieżący wątek do określonego identyfikatora wątku. |
| `$threads` | | Wyświetla listę wątków aktualnie debugowanych. |
| `$up`, `$u` | | Przenieś bieżącą ramkę o jeden poziom w górę w śladzie stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramek dla bieżącego wątku. |

Należy zauważyć, że standardowe okna debugera, takie jak **Procesy,** **Wątki**i **Stos wywołań,** nie są synchronizowane z interakcyjnym oknem **Debug.** Zmiana aktywnego procesu, wątku lub ramki w oknie **Debug Interactive** nie wpływa na inne okna debugera. Podobnie zmiana aktywnego procesu, wątku lub ramki w innych oknach debugera nie wpływa na okno **Debug Interactive.**

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Używanie starszego debugera

Visual Studio 2017 w wersjach 15.8 i nowszych używać debugera na podstawie ptvsd wersji 4.1+. Ta wersja ptvsd jest kompatybilna z Python 2.7 i Python 3.5 +. Jeśli używasz Języka Python 2.6, 3.1 do 3.4 lub IronPython, Visual Studio pokazuje błąd, **Debuger nie obsługuje tego środowiska Python:**

![Debuger nie obsługuje tego błędu środowiska języka Python podczas korzystania z debugera](media/debugging-experimental-incompatible-error.png)

W takich przypadkach należy użyć starszego debugera (który jest domyślny w programie Visual Studio 2017 w wersjach 15.7 i wcześniejszych). Wybierz polecenie menu**Opcje** **narzędzi,** > przejdź do**debugowania** **języka Python** > i wybierz opcję **Użyj starszego debugera.**

Jeśli zainstalowano starszą wersję ptvsd w bieżącym środowisku (na przykład wcześniejszą wersję 4.0.x lub wersję 3.x wymaganą do zdalnego debugowania), program Visual Studio może wyświetlić błąd lub ostrzeżenie.

Nie **można załadować błędu, którego nie można załadować pakietu debugera,** pojawia się po zainstalowaniu ptvsd 3.x:

![Nie można załadować błędu pakietu debugera podczas korzystania z debugera](media/debugging-experimental-version-error.png)

W takim przypadku wybierz opcję **Użyj starszego debugera,** aby ustawić opcję **Użyj starszego debugera** i uruchom ponownie debuger.

Ostrzeżenie, **pakiet debugera jest nieaktualny**, pojawia się po zainstalowaniu wcześniejszej wersji 4.x ptvsd:

![Pakiet debugera jest nieaktualne ostrzeżenie podczas korzystania z debugera](media/debugging-experimental-version-warning.png)

> [!Important]
> Chociaż można zignorować ostrzeżenie dla niektórych wersji ptvsd, Visual Studio może nie działać poprawnie.

Aby zarządzać instalacją ptvsd:

1. Przejdź do karty **Pakiety** w oknie **Środowiska języka Python.**

1. Wpisz "ptvsd" w polu wyszukiwania i sprawdź zainstalowaną wersję ptvsd:

    ![Sprawdzanie wersji ptvsd w oknie Środowiska Pythona](media/debugging-experimental-check-ptvsd.png)

1. Jeśli wersja jest niższa niż 4.1.1a9 (wersja w pakiecie z programem Visual Studio), wybierz **X** po prawej stronie pakietu, aby odinstalować starszą wersję. Visual Studio następnie używa jego wersji dołączonej. (Można również odinstalować z `pip uninstall ptvsd`programu PowerShell przy użyciu .)

1. Alternatywnie można zaktualizować pakiet ptvsd do jego najnowszej wersji, postępując zgodnie z instrukcjami w sekcji [Rozwiązywanie problemów.](#troubleshooting)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z debugerem, najpierw uaktualnij wersję ptvsd w następujący sposób:

1. Przejdź do karty **Pakiety** w oknie **Środowiska języka Python.**

1. Wprowadź `ptvsd --upgrade` w polu wyszukiwania, a następnie wybierz polecenie **Uruchom: pip install ptvsd --upgrade**. (Można również użyć tego samego polecenia z programu PowerShell).

    ![Nadanie polecenia aktualizacji ptvsd w oknie Środowiska Pythona](media/debugging-experimental-upgrade-ptvsd.png)

Jeśli problemy będą się powtarzać, zgłać problem w [repozytorium PTVS GitHub](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Włączanie rejestrowania debugera

W trakcie badania problemu debugera firma Microsoft może poprosić o włączenie i zbieranie dzienników debugera, które pomagają w diagnostyce.

Następujące kroki umożliwiają debugowanie w bieżącej sesji programu Visual Studio:

1. Otwórz okno polecenia w programie Visual Studio przy użyciu polecenia menu **Wyświetl** > inne**okno polecenia** **systemu Windows.** > 

1. Wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Rozpocznij debugowanie i przejdź przez wszelkie kroki są niezbędne do odtworzenia problemu. W tym czasie dzienniki debugowania są wyświetlane w oknie **Dane wyjściowe** w obszarze **Dziennik hosta karty debugowania**. Następnie można skopiować dzienniki z tego okna i wkleić do problemu GitHub, e-mail, itp.

    ![Dane wyjściowe rejestrowania debugera w oknie Dane wyjściowe](media/debugger-logging-output.png)

1. Jeśli program Visual Studio zawiesza się lub w inny sposób nie możesz uzyskać dostępu do okna **Dane wyjściowe,** uruchom ponownie program Visual Studio, otwórz okno polecenia i wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Rozpocznij debugowanie i ponownie odtwórz problem. Dzienniki debugera można następnie `%temp%\DebugAdapterHostLog.txt`znaleźć w pliku .

## <a name="see-also"></a>Zobacz też

Aby uzyskać pełne informacje na temat debugera programu Visual Studio, zobacz [Debugowanie w programie Visual Studio.](../debugger/debugger-feature-tour.md)
