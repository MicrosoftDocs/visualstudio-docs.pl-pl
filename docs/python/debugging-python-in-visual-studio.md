---
title: Możliwe jest debugowanie kodu języka Python
description: Program Visual Studio zapewnia zaawansowane funkcje debugowania kodu języka Python, w tym ustawiania punktów przerwania, przechodzenie krok po kroku, sprawdzania wartości, patrząc wyjątków i debugowania w oknie interaktywnym.
ms.date: 01/07/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fc6c448a80f9517a3bde0333736f4cb83efb09c6
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155880"
---
# <a name="debug-your-python-code"></a>Debugowanie kodu w języku Python

Program Visual Studio udostępnia kompleksowe środowisko debugowania dla języka Python, dołączanie do uruchomionego procesu, w tym oceny wyrażenia w **Obejrzyj** i **bezpośrednie** systemu windows, inspekcja lokalne zmienne, punkty przerwania, krok instrukcji w/out/over **Ustaw następną instrukcję**i nie tylko.

Zobacz też następujące artykuły debugowania specyficzne dla scenariusza:

- [Zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- [Debugowanie w trybie mieszanym języków Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Język Python w programie Visual Studio obsługuje debugowanie bez projektu. Autonomiczny plik w języku Python otwarty, kliknij prawym przyciskiem myszy w edytorze wybierz **rozpocząć debugowanie**, i Visual Studio uruchamia skrypt przy użyciu środowiska domyślnego globalnego (zobacz [środowiska Python](managing-python-environments-in-visual-studio.md)) i bez argumentów. Ale od tego momentu pełną obsługę debugowania.
>
> Aby kontrolować środowiska i argumenty, Utwórz projekt dla kodu, który można łatwo przeprowadzić za pomocą [za pomocą języka Python istniejącego kodu](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) szablonu projektu.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje ustawienia punktów przerwania, krokowe wykonywanie kodu, sprawdzania wartości i obsługa wyjątków, zgodnie z opisem w poniższych sekcjach.

Sesję debugowania, który rozpoczyna się od **debugowania** > **Rozpocznij debugowanie** polecenia **Start** przycisk na pasku narzędzi lub **F5**klucza. Te akcje Uruchom plik startowy projektu (pokazano w pogrubieniem w **Eksploratora rozwiązań**) przy użyciu środowiska active projektu i argumenty wiersza polecenia lub ścieżki wyszukiwania, które zostały określone w **projektu Właściwości** (zobacz [opcje debugowania projektu](#project-debugging-options)). **Visual Studio 2017 w wersji 15.6** i później ostrzega, jeśli nie masz plik startowy, ustaw; wcześniejszych wersji może otworzyć okno danych wyjściowych z interpreter języka Python, uruchamianie lub w oknie danych wyjściowych krótko pojawi się i znika. W każdym przypadku, kliknij prawym przyciskiem myszy odpowiedni plik i wybierz **Ustaw jako plik startowy**.

> [!Note]
> Debuger zawsze zaczyna się od aktywnego środowiska Python dla projektu. Ku zmienianiu środowiska, wprowadzić inną aktywnych jeden, zgodnie z opisem na [wybierz środowisko Python w projekcie](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania zatrzymać wykonywanie kodu w momencie oznaczone, dzięki czemu można sprawdzić stan programu. Ustawianie punktów przerwania, klikając w lewy margines edytora kodu lub klikając prawym przyciskiem myszy linię kodu i wybierając polecenie **punktu przerwania** > **Wstaw punkt przerwania**. Czerwona kropka pojawia się w każdym wierszu za pomocą punktu przerwania.

![Punkty przerwania, pojawiają się w programie Visual Studio](media/debugging-breakpoints.png)

Klikając czerwona kropka, lub kliknij prawym przyciskiem myszy wiersz kodu i wybierając **punktu przerwania** > **Usuń punkt przerwania** Usuwa punkt przerwania. Można również wyłączyć ją bez usuwania go za pomocą **punktu przerwania** > **Wyłącz punkt przerwania** polecenia.

> [!Note]
> Niektóre punkty przerwania w języku Python może być Zaskakujące dla deweloperów, którzy pracowali z innymi językami programowania. W języku Python cały plik jest kodu wykonywalnego, więc Python jest uruchamiany plik, gdy jest ładowany w celu przetworzenia dowolnej najwyższego poziomu klasy lub definicji funkcji. Jeśli ustawiono punkt przerwania, może się okazać debuger istotnej części — sposób za pomocą deklaracji klasy. To zachowanie jest poprawna, mimo że jest to czasami Zaskakujące.

Można dostosować warunków, w których punkt przerwania zostaje wyzwolona, takie jak przerywanie tylko wtedy, gdy zmienna jest ustawiona na określoną wartość lub wartości zakresu. Aby ustawić warunki, kliknij prawym przyciskiem myszy punkt przerwania czerwoną kropkę, wybierz **warunek**, następnie utwórz wyrażeń przy użyciu kodu w języku Python. Aby uzyskać szczegółowe informacje na temat tej funkcji w programie Visual Studio, zobacz [warunków punktu przerwania](../debugger/using-breakpoints.md#breakpoint-conditions).

Podczas ustawiania warunków, można również ustawić **akcji** i utworzyć komunikat do logowania się w oknie danych wyjściowych, opcjonalnie automatycznie kontynuowanie wykonywania. Rejestrowanie komunikatów tworzy tzw *śledzenia* bez dodawania kodu rejestrowania do aplikacji bezpośrednio:

![Tworzenie punktu śledzenia za pomocą punktu przerwania](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Przejść przez kod

Po zatrzymaniu w punkcie przerwania, możesz mieć różne sposoby, aby przejść przez kod lub uruchomić bloki kodu przed przerwaniem ponownie. Te polecenia są dostępne w wielu miejscach, w tym narzędzi debugowania najważniejsze **debugowania** menu w menu kontekstowym kliknij prawym przyciskiem myszy w edytorze kodu, a także za pośrednictwem skróty klawiaturowe (choć nie wszystkie polecenia są we wszystkich miejscach):

| Funkcja | Keystroke | Opis |
| --- | --- | --- |
| **Continue** | **F5** | Uruchamia kod, aż do osiągnięcia następnego punktu przerwania. |
| **Wkrocz** | **F11** | Uruchamia następnej instrukcji i zatrzymuje. Jeśli następna instrukcja jest wywołaniem funkcji, debuger zatrzymuje się w pierwszym wierszu wywoływanej funkcji. |
| **Przekrocz nad** | **F10** | Uruchamia następnej instrukcji, łącznie z wywołania do funkcji (uruchomionego jego kodu) i zastosowanie wszelkich wartości zwracanej. Pominięcie pozwala łatwo pominąć funkcje, które nie trzeba do debugowania. |
| **Wyjdź** | **SHIFT**+**F11** | Uruchamia kod aż do zakończenia bieżącej funkcji, a następnie kroki do instrukcji wywołujące.  To polecenie jest przydatne, gdy nie jest konieczne do debugowania w pozostałej części bieżącej funkcji. |
| **Uruchom do kursora** | **CTRL**+**F10** | Uruchamia kod do lokalizacji karetki w edytorze. To polecenie umożliwia łatwe pominąć segment kodu, który nie jest potrzebny do debugowania. |
| **Ustaw następną instrukcję** | **CTRL**+**Shift**+**F10** | Zmienia bieżący przebieg punktów w kodzie do lokalizacji karetki. To polecenie umożliwia pominięcie segmentu kodu są uruchamiane, takie jak, gdy wiesz kod jest uszkodzony lub tworzy niechciane efekt uboczny. |
| **Pokaż następną instrukcję** | **ALT**+**Num****&#42;**| Powrót do następnej instrukcji do uruchomienia. To polecenie jest przydatne, jeśli został wyszukiwanie w kodzie, a nie pamiętasz, gdzie debuger został zatrzymany. |

### <a name="inspect-and-modify-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu debugera, można sprawdzić i modyfikować wartości zmiennych. Można również użyć **Obejrzyj** okna, aby monitorować poszczególne zmienne, a także wyrażeń niestandardowych. (Zobacz [sprawdzanie zmiennych](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) Aby uzyskać ogólne informacje.)

Aby wyświetlić przy użyciu wartości **DataTips**, po prostu umieść kursor myszy nad dowolnej zmiennej w edytorze. Możesz kliknąć na wartości, aby ją zmienić:

![DataTips wyświetlane w debugerze programu Visual Studio](media/debugging-quick-tips.png)

**Autos** okna (**debugowania** > **Windows** > **Autos**) zawiera zmienne i wyrażenia, znajdują się blisko bieżącej instrukcji. Możesz kliknąć dwukrotnie w kolumnie wartość lub wybierz i naciśnij klawisz **F2** pozwala edytować wartość:

![Okno zmiennych automatycznych w debugerze programu Visual Studio](media/debugging-autos-window.png)

**Lokalne** okna (**debugowania** > **Windows** > **lokalne**) Wyświetla wszystkie zmienne, które znajdują się w bieżącego zakresu, który może być edytowany ponownie:

![Okno zmiennych lokalnych w debugerze programu Visual Studio](media/debugging-locals-window.png)

Więcej używania na **Autos** i **lokalne**, zobacz [sprawdzanie zmiennych w oknach zmiennych automatycznych i zmiennych lokalnych](../debugger/autos-and-locals-windows.md).

**Obejrzyj** systemu windows (**debugowania** > **Windows** > **Obejrzyj**  >   **Obejrzyj 1 – 4**) umożliwiają wprowadź dowolnego wyrażenia języka Python i wyświetlić wyniki. Wyrażenia są ponownie oceniane dla każdego kroku:

![Okno czujki w debugerze programu Visual Studio](media/debugging-watch-window.png)

Więcej używania na **Obejrzyj**, zobacz [Ustawianie wyrażenia kontrolnego na zmiennych przy użyciu oknach wyrażenie kontrolne i QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Podczas sprawdzania wartość ciągu (`str`, `unicode`, `bytes`, i `bytearray` są wszystkie traktowane jako parametry w tym celu), ikonę lupy pojawia się po prawej stronie wartości. Klikając ikonę Wyświetla wartość ciągu bez cudzysłowów w oknie dialogowym okna podręcznego, opakowywanie i przewijanie, co jest przydatne dla ciągów długich. Ponadto, wybierając strzałkę listy rozwijanej na ikonie służy do wybierania zwykły tekst, HTML, XML i JSON wizualizacji:

![Ciąg wizualizatorów w debugerze programu Visual Studio](media/debugging-string-visualizers.png)

HTML, XML i JSON wizualizacje są wyświetlane w osobne okno podręczne windows za pomocą widoków wyróżniania i drzewa składni.

### <a name="exceptions"></a>Wyjątki

Jeśli wystąpi błąd w programie podczas debugowania, ale go nie masz obsługi wyjątków, debuger przerywa punkcie wyjątek:

![Wyjątek — menu podręczne w debugerze programu Visual Studio](media/debugging-exception-popup.png)

W tym momencie można sprawdzić stan programu, w tym stos wywołań. Jednak Jeśli spróbujesz przejść przez kod wyjątku będzie nadal jest zgłaszana, dopóki nie jest to obsługiwane lub kończy działanie programu.

**Debugowania** > **Windows** > **ustawienia wyjątków** polecenia menu wyświetlenie okna, w którym możesz rozwinąć **języka Python Wyjątki**:

![Okno wyjątki w debugerze programu Visual Studio](media/debugging-exception-settings.png)

Pole wyboru dla każdej kontrolki wyjątku czy debugera *zawsze* przerwanie wykonywania przy jest zgłaszany. Zaznacz to pole wyboru, gdy chcesz przerwać częściej dla określonego wyjątku.

Domyślnie większość wyjątków Przerwij, gdy nie można odnaleźć obsługi wyjątków w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy każdy wyjątek i zmodyfikuj **kontynuować po nieobsługiwany w kodzie użytkownika** opcji. Wyczyść to pole, gdy chcesz przerwać rzadziej, dla wyjątku.

Aby skonfigurować wyjątek, który nie ma na tej liście, kliknij **Dodaj** przycisk, aby ją dodać. Nazwa musi odpowiadać imię i nazwisko wyjątku.

## <a name="project-debugging-options"></a>Opcje debugowania projektu

Domyślnie debuger zaczyna się od program standardowy uruchamianie języka Python, żadnych argumentów wiersza polecenia z i innych specjalnych ścieżek lub warunki. Opcje uruchamiania są zmieniane przy użyciu właściwości debugowania projektu dostęp, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierając opcję **właściwości**i wybierając polecenie **debugowania**  kartę.

![Właściwości debugowania projektu w debugerze programu Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| **Standardowa uruchamianie języka Python** | Zastosowań debugowanie kodu napisanego w języku Python przenośny, zgodny z CPython, IronPython i wariantami, takimi jak Stackless języka Python. Zapewnia najlepsze środowisko do debugowania czystym kodzie języka Python. Po dołączeniu do uruchomionej *python.exe* procesu, uruchom ten jest używany. Udostępnia również w tym uruchamianie programu [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) CPython, co umożliwia bezproblemowe krok między kodu C/C++ oraz kodu w języku Python. |
| **Uruchamianie w sieci Web** | Uruchamia domyślną przeglądarkę w momencie uruchomienia i powoduje włączenie debugowania szablonów. Zobacz [debugowania szablonów sieci Web](python-web-application-project-templates.md#debugging) sekcji, aby uzyskać więcej informacji. |
| **Uruchamianie z sieci Django Web** | Taka sama jak uruchamiającego w sieci Web i wyświetlane tylko w przypadku zapewnienia zgodności. |
| **Uruchamianie IronPython (.NET)** | Używa debugera platformy .NET, które działa tylko w przypadku IronPython, ale umożliwia przechodzenie między każdego projektu języka .NET, w tym C# i VB. Uruchamianie tego programu jest używana, jeśli dołączanie do uruchomionego procesu .NET, który jest hostem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opcje uruchamiania (ścieżki wyszukiwania, argumenty uruchomienia i zmiennych środowiskowych)

| Opcja | Opis |
| --- | --- |
| **Ścieżki wyszukiwania** | Te wartości zgodne, co jest wyświetlany w projekcie **ścieżki wyszukiwania** w węźle **Eksploratora rozwiązań**. Można zmodyfikować tę wartość w tym miejscu, ale jest łatwiej można użyć **Eksploratora rozwiązań** który pozwala na przeglądanie folderów i automatycznie konwertuje ścieżki względnej formularza. |
| **Argumenty skryptu** | Te argumenty zostaną dodane do polecenia używane do uruchomienia skryptu, pojawiające się po nazwę pliku skryptu. Pierwszy element w tym miejscu jest dostępne do skryptu jako `sys.argv[1]`, drugi jako `sys.argv[2]`i tak dalej. |
| **Interpreter argumentów** | Te argumenty zostaną dodane do wiersza polecenia uruchamiania przed nazwą skryptu. Są często używanych argumentów tutaj `-W ...` z ostrzeżeniami kontroli, `-O` nieco zoptymalizować program, i `-u` używać Niebuforowane we/wy. Użytkownicy języka IronPython prawdopodobnie to pole służy do przekazywania `-X` opcji, taką jak `-X:Frames` lub `-X:MTA`. |
| **Cesta k Interpretu** | Zastępuje ścieżkę skojarzoną z bieżącego środowiska. Wartość może być przydatne w przypadku uruchamiania skryptu za pomocą niestandardowych interpretera. |
| **Zmienne środowiskowe** | W tym wielowierszowego pola tekstowego, Dodaj wpisy w postaci \<NAME > =\<wartość >. Ponieważ to ustawienie zostanie zastosowane ostatnie, u góry, wszelkie istniejące zmienne środowiskowe globalnego i po `PYTHONPATH` jest ustawiona zgodnie z **ścieżki wyszukiwania** ustawienie, może służyć do ręcznie przezwyciężyć żadnego z tych innych zmiennych. |

## <a name="immediate-and-interactive-windows"></a>Bezpośrednie i interakcyjne systemu windows

Istnieją dwa okna interaktywnego, można użyć podczas sesji debugowania: standardowy programu Visual Studio **bezpośrednie** oknie i **Python debugowanie interakcyjne** okna.

**Bezpośrednie** okna (**debugowania** > **Windows** > **bezpośrednie**) jest używany do szybkiej oceny Wyrażenia języka Python i inspekcji lub przypisania zmiennych w uruchomionego programu. Zobacz ogólne [bezpośrednim](../ide/reference/immediate-window.md) artykuł, aby uzyskać szczegółowe informacje.

**Python debugowanie interakcyjne** okna (**debugowania** > **Windows** > **Python debugowanie interakcyjne**) jest bardziej rozbudowane, ponieważ zapewnia pełną [interaktywna pętla REPL](python-interactive-repl-in-visual-studio.md) środowisko dostępne podczas debugowania, w tym pisanie i uruchamianie kodu. Automatycznie łączy się żaden proces uruchomiony w debugerze, za pomocą uruchamiania standardowego języka Python (w tym procesy dołączonym za pośrednictwem **debugowania** > **dołączyć do procesu**). Nie, jednak jest dostępne podczas debugowania języka C/C++ w trybie mieszanym.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

**Debugowanie interakcyjne** okna obsługuje specjalne meta polecenia oprócz [standardowe polecenia REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Zostanie uruchomiony program z bieżącej instrukcji. |
| `$down`, `$d` | Przenieś bieżące ramce jeden poziom w dół w ślad stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | Identyfikator ramki | Zmienia bieżące ramce do ramki o określonym identyfikatorze.
| `$load` | Ładuje poleceń z pliku i uruchamia do czasu ukończenia |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | Identyfikator procesu | Zmienia bieżący proces na identyfikator określonego procesu. |
| `$procs` | | Wyświetla listę aktualnie debugowanych procesów. |
| `$stepin`, `$step`, `$s` | Kroki opisane w następnym wywołaniu funkcji, jeśli jest to możliwe. |
| `$stepout`, `$return`, `$r` | Kroki poza bieżącą funkcję. |
| `$stepover`, `$until`, `$unt` | Pomija wywołanie funkcji next. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Zmienia bieżący wątek na identyfikator określonego wątku. |
| `$threads` | | Wyświetla listę wątków obecnie debugowane. |
| `$up`, `$u` | | Przenieś bieżący poziom jednej ramki w górę ślad stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramki dla bieżącego wątku. |

Należy pamiętać, że standard debugera, takie jak **procesy**, **wątków**, i **stos wywołań** nie są zsynchronizowane z **debugowanie interakcyjne** okna. Zmiana aktywnego procesu, wątku lub ramki **debugowanie interakcyjne** okno nie ma wpływu na innych oknach debugera. Podobnie, zmianę aktywnego procesu, wątku lub ramki w oknach debugera nie ma wpływu na **debugowanie interakcyjne** okna.

**Debugowanie interakcyjne** okno ma swój własny zestaw opcji, które są dostępne za pośrednictwem **narzędzia** > **opcje**  >   **Narzędzia języka Python** > **debugowanie interakcyjne okno**. W odróżnieniu od zwykłych **Python Interactive** okna, które ma osobnego wystąpienia dla każdego środowiska Python jest tylko jeden **debugowanie interakcyjne** okno i zawsze używa interpretera języka Python dla debugowany proces. Zobacz [opcje - Opcje debugowania](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Okno interaktywne opcje debugowania](media/debugging-interactive-options.png)

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Za pomocą starszej wersji debugera

Visual Studio 2017 w wersji należy zachować 15,8 lub nowszej użyć debugera na podstawie wersji ptvsd 4.1 lub nowszym. Tej wersji ptvsd jest zgodny z języka Python 2.7 i Python 3.5 +. Czy używasz 2.6 języka Python, 3.1 do 3.4, IronPython, Visual Studio pokazuje błąd, **debuger nie obsługuje tego środowiska Python**:

![Debuger nie obsługuje ten błąd środowiska Python w przypadku używania debugera](media/debugging-experimental-incompatible-error.png)

W takiej sytuacji należy użyć starszy debuger (co jest ustawieniem domyślnym w programie Visual Studio 2017 w wersji 15.7 i starszych). Wybierz **narzędzia** > **opcje** menu poleceń, przejdź do **Python** > **debugowanie**i wybierz pozycję **za pomocą starszej wersji debugera** opcji.

Jeśli po zainstalowaniu starszej wersji ptvsd w bieżącym środowisku (na przykład z wcześniejszej wersji 4.0.x lub wersji 3.x, wymagane do zdalnego debugowania), program Visual Studio mogą być wyświetlane w błąd lub ostrzeżenie.

Błąd, **nie można załadować pakietu debugera**, jest wyświetlany, gdy masz zainstalowaną ptvsd 3.x:

![Pakietu debugera nie można załadować błąd w przypadku używania debugera](media/debugging-experimental-version-error.png)

W takim przypadku wybierz **za pomocą starszej wersji debugera** można ustawić **za pomocą starszej wersji debugera** opcji, a następnie ponownie uruchom debuger.

Ostrzeżenie, **pakietu debugera jest nieaktualna**, jest wyświetlany po zainstalowaniu wcześniejszej wersji 4.x ptvsd:

![Pakiet debugera jest nieaktualna, ikona ostrzeżenia, gdy za pomocą debugera](media/debugging-experimental-version-warning.png)

> [!Important]
> Mimo że można zignorować to ostrzeżenie dla niektórych wersji ptvsd, Visual Studio mogą nie działać poprawnie.

Aby zarządzać ptvsd instalacji:

1. Przejdź do **pakietów** karcie **środowiska Python** okna.

1. W polu wyszukiwania wprowadź "ptvsd" i sprawdź zainstalowaną wersję ptvsd:

    ![Sprawdzanie wersji ptvsd w oknie środowiska Python](media/debugging-experimental-check-ptvsd.png)

1. Jeśli wersja jest niższa niż 4.1.1a9 (wersja powiązane z programem Visual Studio), wybierz opcję **X** po prawej stronie pakietu można odinstalować starszej wersji. Visual Studio używa następnie jego wersji. (Można także odinstalować z przy użyciu programu PowerShell `pip uninstall ptvsd`.)

1. Alternatywnie można zaktualizować pakiet ptvsd do jego najnowszej wersji, postępując zgodnie z instrukcjami w [Rozwiązywanie problemów](#troubleshooting) sekcji.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z debugerem najpierw uaktualnić wersję ptvsd w następujący sposób:

1. Przejdź do **pakietów** karcie **środowiska Python** okna.

1. Wprowadź `ptvsd --upgrade` w polu wyszukiwania, a następnie zaznacz **Uruchom polecenie: ptvsd — uaktualnienia instalacji pakietu pip**. (Możesz również użyć tego samego polecenia, za pomocą programu PowerShell).

    ![Zapewniając polecenie upgrade ptvsd w oknie środowiska Python](media/debugging-experimental-upgrade-ptvsd.png)

Jeśli problemy będą się powtarzać, zgłoś problem na [repozytorium PTVS GitHub](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Włącz rejestrowanie debugera

Badając problem debugera, Microsoft może poprosić o Włącz i zbieranie dzienników debugera, które pomagają w procesie diagnozowania.

Następujące kroki umożliwiają debugowanie w bieżącej sesji programu Visual Studio:

1. Otwórz okno poleceń programu Visual Studio przy użyciu **widoku** > **Windows inne** > **okna polecenia** polecenia menu.

1. Wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Rozpocznij debugowanie i przechodzą przez dowolne kroki są niezbędne do odtworzenia problemu. W tym czasie, dzienniki debugowania są wyświetlane w **dane wyjściowe** okna w obszarze **dziennik hosta adaptera debugowania**. Następnie można skopiować dzienników z tego okna i wkleić do problemu w usłudze GitHub, poczty e-mail itd.

    ![Rejestrowanie danych wyjściowych, w oknie danych wyjściowych debugera](media/debugger-logging-output.png)

1. Jeśli program Visual Studio zawiesza się lub których w przeciwnym razie nie można uzyskać dostęp do **dane wyjściowe** okien, uruchom ponownie program Visual Studio, Otwórz okno polecenia i wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Uruchamianie debugowania i ponownie odtworzenie problemu. Następnie można znaleźć w dziennikach debugera w `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Zobacz także

Aby uzyskać szczegółowe informacje dotyczące debugera programu Visual Studio, zobacz [debugowania w programie Visual Studio](../debugger/debugger-feature-tour.md).
