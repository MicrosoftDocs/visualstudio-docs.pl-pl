---
title: Możliwe jest debugowanie kodu języka Python
description: Program Visual Studio zapewnia zaawansowane funkcje debugowania kodu języka Python, w tym ustawiania punktów przerwania, przechodzenie krok po kroku, sprawdzania wartości, patrząc wyjątków i debugowania w oknie interaktywnym.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409961"
---
# <a name="debug-your-python-code"></a>Debugowanie kodu w języku Python

Program Visual Studio oferuje kompleksowe środowisko debugowania dla języka Python, w tym dołączanie do uruchomionych procesów, ocenianie wyrażeń w oknach **czujka** i **natychmiastowe** , inspekcja lokalnych zmiennych, punktów przerwania, instrukcji krokowych/out/over, **Ustawianie następnej instrukcji**i innych.

Zobacz też następujące artykuły debugowania specyficzne dla scenariusza:

- [Zdalne debugowanie systemu Linux](debugging-python-code-on-remote-linux-machines.md)
- [Środowisko Python/C++ debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Język Python w programie Visual Studio obsługuje debugowanie bez projektu. Gdy jest otwarty autonomiczny plik w języku Python, kliknij prawym przyciskiem myszy w edytorze, wybierz pozycję **Rozpocznij z debugowaniem**, a program Visual Studio uruchamia skrypt z globalnym środowiskiem domyślnym (zobacz [środowiska Python](managing-python-environments-in-visual-studio.md)) i bez argumentów. Ale od tego momentu pełną obsługę debugowania.
>
> Aby kontrolować środowisko i argumenty, należy utworzyć projekt dla kodu, który jest łatwo wykonywany przy użyciu istniejącego szablonu projektu [kodu Python](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) .

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje ustawienia punktów przerwania, krokowe wykonywanie kodu, sprawdzania wartości i obsługa wyjątków, zgodnie z opisem w poniższych sekcjach.

Sesja debugowania rozpoczyna się od polecenia **debuguj** > **Rozpocznij debugowanie** , przycisk **Start** na pasku narzędzi lub klawisz **F5** . Te akcje uruchamiają plik startowy projektu (pogrubienie w **Eksplorator rozwiązań**) z aktywnym środowiskiem projektu i wszystkimi argumentami wiersza polecenia lub ścieżkami wyszukiwania określonymi we **właściwościach projektu** (zobacz [Opcje debugowania projektu](#project-debugging-options)). Program Visual Studio 2017 w wersji 15,6 lub nowszej powiadamia użytkownika, jeśli nie masz zestawu plików startowych; wcześniejsze wersje mogą otworzyć okno danych wyjściowych z uruchomionym interpreterem języka Python, a okno dane wyjściowe pojawia się krótko i znika. W każdym przypadku kliknij prawym przyciskiem myszy odpowiedni plik i wybierz polecenie **Ustaw jako plik startowy**.

> [!Note]
> Debuger zawsze zaczyna się od aktywnego środowiska Python dla projektu. Aby zmienić środowisko, należy wykonać inną aktywną zgodnie z opisem w artykule [Wybieranie środowiska Python dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania zatrzymać wykonywanie kodu w momencie oznaczone, dzięki czemu można sprawdzić stan programu. Ustaw punkty przerwania, klikając na lewym marginesie edytora kodu lub klikając prawym przyciskiem myszy wiersz kodu i wybierając **punkt przerwania** > **Wstawianie punktu przerwania**. Czerwona kropka pojawia się w każdym wierszu za pomocą punktu przerwania.

![Punkty przerwania, pojawiają się w programie Visual Studio](media/debugging-breakpoints.png)

Kliknięcie czerwonej kropki lub kliknięcie prawym przyciskiem myszy linii kodu i wybranie **punktu przerwania** > **Usuń punkt** przerwania spowoduje usunięcie punktu przerwania. Można go również wyłączyć bez usuwania przy użyciu **punktu przerwania** > **wyłączyć polecenie punktu przerwania** .

> [!Note]
> Niektóre punkty przerwania w języku Python może być Zaskakujące dla deweloperów, którzy pracowali z innymi językami programowania. W języku Python cały plik jest kodu wykonywalnego, więc Python jest uruchamiany plik, gdy jest ładowany w celu przetworzenia dowolnej najwyższego poziomu klasy lub definicji funkcji. Jeśli ustawiono punkt przerwania, może się okazać debuger istotnej części — sposób za pomocą deklaracji klasy. To zachowanie jest poprawna, mimo że jest to czasami Zaskakujące.

Można dostosować warunków, w których punkt przerwania zostaje wyzwolona, takie jak przerywanie tylko wtedy, gdy zmienna jest ustawiona na określoną wartość lub wartości zakresu. Aby ustawić warunki, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania, wybierz pozycję **warunek**, a następnie utwórz wyrażenia przy użyciu kodu języka Python. Aby uzyskać pełne szczegóły dotyczące tej funkcji w programie Visual Studio, zobacz [warunki punktu przerwania](../debugger/using-breakpoints.md#breakpoint-conditions).

Podczas ustawiania warunków można także ustawić **akcję** i utworzyć komunikat w celu zarejestrowania się w oknie danych wyjściowych. opcjonalnie kontynuuj wykonywanie automatycznie. Zarejestrowanie komunikatu powoduje utworzenie elementu o nazwie *punkt śledzenia* bez bezpośredniego dodawania kodu rejestrowania do aplikacji:

![Tworzenie punktu śledzenia za pomocą punktu przerwania](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Przejść przez kod

Po zatrzymaniu w punkcie przerwania, możesz mieć różne sposoby, aby przejść przez kod lub uruchomić bloki kodu przed przerwaniem ponownie. Te polecenia są dostępne w wielu miejscach, w tym na górnym pasku narzędzi do debugowania, **w menu** kontekstowym po kliknięciu prawym przyciskiem myszy w edytorze kodu oraz za pomocą skrótów klawiaturowych (chociaż nie wszystkie polecenia znajdują się we wszystkich miejscach):

| Cecha | Keystroke | Opis |
| --- | --- | --- |
| **Continue** | **F5** | Uruchamia kod, aż do osiągnięcia następnego punktu przerwania. |
| **Wkrocz do** | **ALT+F11** | Uruchamia następnej instrukcji i zatrzymuje. Jeśli następna instrukcja jest wywołaniem funkcji, debuger zatrzymuje się w pierwszym wierszu wywoływanej funkcji. |
| **Przekrocz nad** | **F10** | Uruchamia następnej instrukcji, łącznie z wywołania do funkcji (uruchomionego jego kodu) i zastosowanie wszelkich wartości zwracanej. Pominięcie pozwala łatwo pominąć funkcje, które nie trzeba do debugowania. |
| **Wyjdź** | **Shift**+**F11** | Uruchamia kod aż do zakończenia bieżącej funkcji, a następnie kroki do instrukcji wywołujące.  To polecenie jest przydatne, gdy nie jest konieczne do debugowania w pozostałej części bieżącej funkcji. |
| **Uruchom do kursora** | **Ctrl**+**F10** | Uruchamia kod do lokalizacji karetki w edytorze. To polecenie umożliwia łatwe pominąć segment kodu, który nie jest potrzebny do debugowania. |
| **Ustaw następną instrukcję** | **Ctrl**+**SHIFT**+**F10** | Zmienia bieżący przebieg punktów w kodzie do lokalizacji karetki. To polecenie umożliwia pominięcie segmentu kodu są uruchamiane, takie jak, gdy wiesz kod jest uszkodzony lub tworzy niechciane efekt uboczny. |
| **Pokaż następną instrukcję** | **Alt**+**NUM** **&#42;**| Powrót do następnej instrukcji do uruchomienia. To polecenie jest przydatne, jeśli został wyszukiwanie w kodzie, a nie pamiętasz, gdzie debuger został zatrzymany. |

### <a name="inspect-and-modify-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu debugera, można sprawdzić i modyfikować wartości zmiennych. Można również użyć okna **czujki** do monitorowania pojedynczych zmiennych, a także wyrażeń niestandardowych. (Zobacz temat [Sprawdzanie zmiennych](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) , aby uzyskać ogólne szczegóły).

Aby wyświetlić wartość przy użyciu **etykietek**danych, po prostu przesuń wskaźnik myszy nad dowolną zmienną w edytorze. Możesz kliknąć na wartości, aby ją zmienić:

![DataTips wyświetlane w debugerze programu Visual Studio](media/debugging-quick-tips.png)

Okno **Autostarty** (**debugowanie** > **Windows** > Auto) zawiera zmienne i wyrażenia, które znajdują się blisko bieżącej instrukcji. Możesz kliknąć dwukrotnie w kolumnie wartość lub zaznaczyć i nacisnąć klawisz **F2** , aby edytować wartość:

![Okno zmiennych automatycznych w debugerze programu Visual Studio](media/debugging-autos-window.png)

Okno **lokalne** (**debugowanie** > **Windows** > **locale**) wyświetla wszystkie zmienne, które znajdują się w bieżącym zakresie, które mogą być ponownie edytowane:

![Okno zmiennych lokalnych w debugerze programu Visual Studio](media/debugging-locals-window.png)

Aby uzyskać więcej informacji na temat korzystania z funkcji **Autostart** i elementów **lokalnych**, zobacz [Sprawdzanie zmiennych w oknach Autostart i lokalne](../debugger/autos-and-locals-windows.md).

Okna **czujka** (**Debug** > **windows** > **Watch** > **Watch 1-4**) umożliwiają wprowadzanie dowolnych wyrażeń języka Python i wyświetlanie wyników. Wyrażenia są ponownie oceniane dla każdego kroku:

![Okno czujki w debugerze programu Visual Studio](media/debugging-watch-window.png)

Aby uzyskać więcej informacji na temat korzystania z funkcji **Watch**, zobacz [Ustawianie wartości na zmiennych przy użyciu okien czujka i QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Podczas sprawdzania wartości ciągu (`str`, `unicode`, `bytes`i `bytearray` są brane pod uwagę ciągi do tego celu) po prawej stronie wartości zostanie wyświetlona ikona lupy. Klikając ikonę Wyświetla wartość ciągu bez cudzysłowów w oknie dialogowym okna podręcznego, opakowywanie i przewijanie, co jest przydatne dla ciągów długich. Ponadto, wybierając strzałkę listy rozwijanej na ikonie służy do wybierania zwykły tekst, HTML, XML i JSON wizualizacji:

![Ciąg wizualizatorów w debugerze programu Visual Studio](media/debugging-string-visualizers.png)

HTML, XML i JSON wizualizacje są wyświetlane w osobne okno podręczne windows za pomocą widoków wyróżniania i drzewa składni.

### <a name="exceptions"></a>Wyjątki

Jeśli wystąpi błąd w programie podczas debugowania, ale go nie masz obsługi wyjątków, debuger przerywa punkcie wyjątek:

![Wyjątek — menu podręczne w debugerze programu Visual Studio](media/debugging-exception-popup.png)

W tym momencie można sprawdzić stan programu, w tym stos wywołań. Jednak Jeśli spróbujesz przejść przez kod wyjątku będzie nadal jest zgłaszana, dopóki nie jest to obsługiwane lub kończy działanie programu.

Polecenie menu **debuguj** > **Windows** > **Ustawienia wyjątku** powoduje wyświetlenie okna, w którym można rozszerzyć **wyjątki języka Python**:

![Okno wyjątki w debugerze programu Visual Studio](media/debugging-exception-settings.png)

Pole wyboru dla każdego wyjątku kontroluje, czy podczas podniesienia debuger *zawsze* przerywa działanie. Zaznacz to pole wyboru, gdy chcesz przerwać częściej dla określonego wyjątku.

Domyślnie większość wyjątków Przerwij, gdy nie można odnaleźć obsługi wyjątków w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy dowolny wyjątek i zmodyfikuj opcję **Kontynuuj przy nieobsługiwanym kodzie użytkownika** . Wyczyść to pole, gdy chcesz przerwać rzadziej, dla wyjątku.

Aby skonfigurować wyjątek, który nie jest wyświetlany na liście, kliknij przycisk **Dodaj** , aby go dodać. Nazwa musi odpowiadać imię i nazwisko wyjątku.

## <a name="project-debugging-options"></a>Opcje debugowania projektu

Domyślnie debuger zaczyna się od program standardowy uruchamianie języka Python, żadnych argumentów wiersza polecenia z i innych specjalnych ścieżek lub warunki. Opcje uruchamiania są zmieniane za pomocą właściwości debugowania projektu, do których uzyskuje dostęp, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, wybierając **Właściwości**i wybierając kartę **debugowanie** .

![Właściwości debugowania projektu w debugerze programu Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| **Standardowy moduł uruchamiania języka Python** | Zastosowań debugowanie kodu napisanego w języku Python przenośny, zgodny z CPython, IronPython i wariantami, takimi jak Stackless języka Python. Zapewnia najlepsze środowisko do debugowania czystym kodzie języka Python. Po dołączeniu do uruchomionego procesu *Python. exe* jest używany ten program uruchamiający. Ten program uruchamiający udostępnia również [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) dla CPython, co pozwala na bezproblemowe przechodzenieC++ między językiem C/kodem a kodem języka Python. |
| **Uruchamianie w sieci Web** | Uruchamia domyślną przeglądarkę w momencie uruchomienia i powoduje włączenie debugowania szablonów. Aby uzyskać więcej informacji, zobacz sekcję [Debugowanie szablonu sieci Web](python-web-application-project-templates.md#debugging) . |
| **Django internetowy** | Taka sama jak uruchamiającego w sieci Web i wyświetlane tylko w przypadku zapewnienia zgodności. |
| **IronPython (.NET) — uruchamianie** | Używa debugera platformy .NET, które działa tylko w przypadku IronPython, ale umożliwia przechodzenie między każdego projektu języka .NET, w tym C# i VB. Uruchamianie tego programu jest używana, jeśli dołączanie do uruchomionego procesu .NET, który jest hostem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opcje uruchamiania (ścieżki wyszukiwania, argumenty uruchomienia i zmiennych środowiskowych)

| Opcja | Opis |
| --- | --- |
| **Ścieżki wyszukiwania** | Te wartości pasują do elementów wyświetlanych w węźle **ścieżki wyszukiwania** projektu w **Eksplorator rozwiązań**. Tutaj możesz zmodyfikować tę wartość, ale łatwiej jest używać **Eksplorator rozwiązań** , które umożliwiają przeglądanie folderów i automatyczne konwertowanie ścieżek do formy względnej. |
| **Argumenty skryptu** | Te argumenty zostaną dodane do polecenia używane do uruchomienia skryptu, pojawiające się po nazwę pliku skryptu. Pierwszy element w tym miejscu jest dostępny dla skryptu jako `sys.argv[1]`, drugi jako `sys.argv[2]`itd. |
| **Argumenty interpretera** | Te argumenty zostaną dodane do wiersza polecenia uruchamiania przed nazwą skryptu. Typowe argumenty są `-W ...` w celu kontrolowania ostrzeżeń, `-O` do niewielkiej optymalizacji programu, a `-u` do korzystania z niebuforowanej operacji we/wy. IronPython użytkownicy mogą używać tego pola do przekazywania opcji `-X`, takich jak `-X:Frames` lub `-X:MTA`. |
| **Ścieżka interpretera** | Zastępuje ścieżkę skojarzoną z bieżącego środowiska. Wartość może być przydatne w przypadku uruchamiania skryptu za pomocą niestandardowych interpretera. |
| **Zmienne środowiskowe** | W tym wielowierszowym polu tekstowym Dodaj wpisy w formularzu \<NAME > =\<VALUE >. Ponieważ to ustawienie jest stosowane ostatnio, na podstawie wszelkich istniejących globalnych zmiennych środowiskowych, a po `PYTHONPATH` jest ustawiony zgodnie z ustawieniem **ścieżki wyszukiwania** , może służyć do ręcznego przesłonięcia wszelkich innych zmiennych. |

## <a name="immediate-and-interactive-windows"></a>Bezpośrednie i interakcyjne systemu windows

Istnieją dwa **interaktywne okna,** których można użyć podczas sesji debugowania: standardowe okno programu Visual Studio i okno **interaktywne debugowania języka Python** .

**Bezpośrednie** okno (**debugowanie** > **Windows** > **natychmiastowe**) służy do szybkiej oceny wyrażeń języka Python oraz inspekcji lub przypisywania zmiennych w uruchomionym programie. Aby uzyskać szczegółowe informacje, zobacz artykuł ogólne [okna](../ide/reference/immediate-window.md) ogólnego.

Okno **interaktywne debugowania języka Python** (**debugowanie** > **Windows** > **Python Debug Interactive**) jest bogatsze, ponieważ sprawia, że pełne [interaktywne środowisko REPL](python-interactive-repl-in-visual-studio.md) jest dostępne podczas debugowania, w tym pisania i uruchamiania kodu. Automatycznie łączy się z dowolnym procesem uruchomionym w debugerze przy użyciu standardowego uruchamiania języka Python (w tym procesów dołączonych za pośrednictwem **debugowania** > **dołączania do procesu**). Nie, jednak jest dostępne podczas debugowania języka C/C++ w trybie mieszanym.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

Okno **interaktywne debugowania** obsługuje specjalne meta polecenia oprócz [standardowych poleceń REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Zostanie uruchomiony program z bieżącej instrukcji. |
| `$down`, `$d` | Przenieś bieżące ramce jeden poziom w dół w ślad stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | Identyfikator ramki | Przełącza bieżącą ramkę do określonego identyfikatora ramki.
| `$load` | Ładuje poleceń z pliku i uruchamia do czasu ukończenia |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | Identyfikator procesu | Przełącza bieżący proces do określonego identyfikatora procesu. |
| `$procs` | | Wyświetla listę aktualnie debugowanych procesów. |
| `$stepin`, `$step`, `$s` | Kroki opisane w następnym wywołaniu funkcji, jeśli jest to możliwe. |
| `$stepout`, `$return`, `$r` | Kroki poza bieżącą funkcję. |
| `$stepover`, `$until`, `$unt` | Pomija wywołanie funkcji next. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Przełącza bieżący wątek do określonego identyfikatora wątku. |
| `$threads` | | Wyświetla listę wątków obecnie debugowane. |
| `$up`, `$u` | | Przenieś bieżący poziom jednej ramki w górę ślad stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramki dla bieżącego wątku. |

Należy zauważyć, że standardowe okna debugera, takie jak **procesy**, **wątki**i **stos wywołań** nie są zsynchronizowane z oknem **debugowania Interactive** . Zmiana aktywnego procesu, wątku lub ramki w oknie **interaktywnym debugowania** nie ma wpływu na inne okna debugera. Podobnie zmiana aktywnego procesu, wątku lub ramki w innych oknach debugera nie ma wpływu na okno **debugowanie interaktywne** .

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Za pomocą starszej wersji debugera

Visual Studio 2017 w wersji należy zachować 15,8 lub nowszej użyć debugera na podstawie wersji ptvsd 4.1 lub nowszym. Tej wersji ptvsd jest zgodny z języka Python 2.7 i Python 3.5 +. Jeśli używasz języka Python 2,6, 3,1 do 3,4 lub IronPython, program Visual Studio wyświetli błąd, **debuger nie obsługuje tego środowiska Python**:

![Debuger nie obsługuje ten błąd środowiska Python w przypadku używania debugera](media/debugging-experimental-incompatible-error.png)

W takiej sytuacji należy użyć starszy debuger (co jest ustawieniem domyślnym w programie Visual Studio 2017 w wersji 15.7 i starszych). Wybierz polecenie menu **narzędzia** > **Opcje** , przejdź do **debugowania** > języka **Python** , a następnie wybierz opcję **Użyj starszego debugera** .

Jeśli po zainstalowaniu starszej wersji ptvsd w bieżącym środowisku (na przykład z wcześniejszej wersji 4.0.x lub wersji 3.x, wymagane do zdalnego debugowania), program Visual Studio mogą być wyświetlane w błąd lub ostrzeżenie.

Błąd, nie można **załadować pakietu debugera**, pojawia się po zainstalowaniu ptvsd 3. x:

![Pakietu debugera nie można załadować błąd w przypadku używania debugera](media/debugging-experimental-version-error.png)

W takim przypadku wybierz pozycję **Użyj starszego debugera** , aby ustawić opcję **Użyj starszego debugera** , i ponownie uruchom debuger.

Ostrzeżenie, **pakiet debugera jest nieaktualne**, pojawia się, gdy zainstalowano wcześniejszą wersję 4. x ptvsd:

![Pakiet debugera jest nieaktualna, ikona ostrzeżenia, gdy za pomocą debugera](media/debugging-experimental-version-warning.png)

> [!Important]
> Mimo że można zignorować to ostrzeżenie dla niektórych wersji ptvsd, Visual Studio mogą nie działać poprawnie.

Aby zarządzać ptvsd instalacji:

1. Przejdź do karty **pakiety** w oknie **środowiska języka Python** .

1. W polu wyszukiwania wprowadź "ptvsd" i sprawdź zainstalowaną wersję ptvsd:

    ![Sprawdzanie wersji ptvsd w oknie środowiska Python](media/debugging-experimental-check-ptvsd.png)

1. Jeśli wersja jest niższa niż 4.1.1 A9 (wersja z programu Visual Studio), wybierz **znak X** z prawej strony pakietu, aby odinstalować starszą wersję. Visual Studio używa następnie jego wersji. (Można również odinstalować program PowerShell przy użyciu `pip uninstall ptvsd`).

1. Alternatywnie możesz zaktualizować pakiet ptvsd do jego najnowszej wersji, postępując zgodnie z instrukcjami w sekcji [Rozwiązywanie problemów](#troubleshooting) .

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli masz problemy z debugerem najpierw uaktualnić wersję ptvsd w następujący sposób:

1. Przejdź do karty **pakiety** w oknie **środowiska języka Python** .

1. Wprowadź `ptvsd --upgrade` w polu wyszukiwania, a następnie wybierz pozycję **Uruchom polecenie: pip install ptvsd--upgrade**. (Możesz również użyć tego samego polecenia, za pomocą programu PowerShell).

    ![Zapewniając polecenie upgrade ptvsd w oknie środowiska Python](media/debugging-experimental-upgrade-ptvsd.png)

Jeśli problemy będą się powtarzać, należy rozwiązać problem w [repozytorium GitHub PTVS](https://github.com/Microsoft/ptvs/issues).

### <a name="enable-debugger-logging"></a>Włącz rejestrowanie debugera

Badając problem debugera, Microsoft może poprosić o Włącz i zbieranie dzienników debugera, które pomagają w procesie diagnozowania.

Następujące kroki umożliwiają debugowanie w bieżącej sesji programu Visual Studio:

1. Otwórz okno polecenia w programie Visual Studio, korzystając z polecenia **wyświetl** > inne **okna polecenia** **Windows** > menu.

1. Wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Rozpocznij debugowanie i przechodzą przez dowolne kroki są niezbędne do odtworzenia problemu. W tym czasie Dzienniki debugowania są wyświetlane w oknie **dane wyjściowe** w obszarze **Dziennik hosta adaptera debugowania**. Następnie można skopiować dzienników z tego okna i wkleić do problemu w usłudze GitHub, poczty e-mail itd.

    ![Rejestrowanie danych wyjściowych, w oknie danych wyjściowych debugera](media/debugger-logging-output.png)

1. Jeśli program Visual Studio zawiesza się lub w przeciwnym razie nie można uzyskać dostępu do okna **danych wyjściowych** , uruchom ponownie program Visual Studio, Otwórz okno polecenia i wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Uruchamianie debugowania i ponownie odtworzenie problemu. Dzienniki debugera można znaleźć w `%temp%\DebugAdapterHostLog.txt`.

## <a name="see-also"></a>Zobacz też

Aby uzyskać szczegółowe informacje na temat debugera programu Visual Studio, zobacz [debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md).
