---
title: Debuguj kod w języku Python
description: Program Visual Studio zapewnia zaawansowane Debugowanie kodu języka Python, w tym ustawianie punktów przerwania, krokowe, badanie wartości, przeglądanie wyjątków i debugowanie w oknie interaktywnym.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b5a86f600f9145742f6447af54fccb10dbc302a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931776"
---
# <a name="debug-your-python-code"></a>Debugowanie kodu w języku Python

Program Visual Studio oferuje kompleksowe środowisko debugowania dla języka Python, w tym dołączanie do uruchomionych procesów, ocenianie wyrażeń w oknach **czujka** i **natychmiastowe** , inspekcja lokalnych zmiennych, punktów przerwania, instrukcji krokowych/out/over, **Ustawianie następnej instrukcji** i innych.

Zobacz również następujące artykuły dotyczące debugowania dotyczące scenariusza:

- [Zdalne debugowanie systemu Linux](debugging-python-code-on-remote-linux-machines.md)
- [Debugowanie Python/C++ w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

<a name="debugging-without-a-project"></a>

> [!Tip]
> Język Python w programie Visual Studio obsługuje debugowanie bez projektu. Gdy jest otwarty autonomiczny plik w języku Python, kliknij prawym przyciskiem myszy w edytorze, wybierz pozycję **Rozpocznij z debugowaniem**, a program Visual Studio uruchamia skrypt z globalnym środowiskiem domyślnym (zobacz [środowiska Python](managing-python-environments-in-visual-studio.md)) i bez argumentów. Jednak od tego dnia masz pełną pomoc techniczną dotyczącą debugowania.
>
> Aby kontrolować środowisko i argumenty, należy utworzyć projekt dla kodu, który jest łatwo wykonywany przy użyciu istniejącego szablonu projektu [kodu Python](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) .

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje ustawienia punktów przerwania, przechodzenie przez kod, inspekcję wartości i obsługę wyjątków zgodnie z opisem w poniższych sekcjach.

Sesja debugowania rozpoczyna się od polecenia **Debuguj**  >  **Rozpocznij debugowanie** , przycisku **Start** na pasku narzędzi lub klawisza **F5** . Te akcje uruchamiają plik startowy projektu (pogrubienie w **Eksplorator rozwiązań**) z aktywnym środowiskiem projektu i wszystkimi argumentami wiersza polecenia lub ścieżkami wyszukiwania określonymi we **właściwościach projektu** (zobacz [Opcje debugowania projektu](#project-debugging-options)). Program Visual Studio 2017 w wersji 15,6 lub nowszej powiadamia użytkownika, jeśli nie masz zestawu plików startowych; wcześniejsze wersje mogą otworzyć okno danych wyjściowych z uruchomionym interpreterem języka Python, a okno dane wyjściowe pojawia się krótko i znika. W każdym przypadku kliknij prawym przyciskiem myszy odpowiedni plik i wybierz polecenie **Ustaw jako plik startowy**.

> [!Note]
> Debuger zawsze zaczyna się od aktywnego środowiska języka Python dla projektu. Aby zmienić środowisko, należy wykonać inną aktywną zgodnie z opisem w artykule [Wybieranie środowiska Python dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania zatrzymają wykonywanie kodu w oznaczonym punkcie, aby można było sprawdzić stan programu. Ustaw punkty przerwania, klikając na lewym marginesie edytora kodu lub klikając prawym przyciskiem myszy wiersz kodu i wybierając **punkt** przerwania  >  **Wstaw punkt przerwania**. Czerwona kropka pojawia się w każdym wierszu z punktem przerwania.

![Punkty przerwania pojawiające się w programie Visual Studio](media/debugging-breakpoints.png)

Kliknij czerwoną kropkę lub kliknij prawym przyciskiem myszy wiersz kodu, a **następnie wybierz punkt** przerwania Usuwanie punktu przerwania  >   . Można je również wyłączyć bez usuwania przy użyciu **punktu** przerwania  >  **disable** .

> [!Note]
> Niektóre punkty przerwania w języku Python mogą być zaskakujące dla deweloperów, którzy pracowały w innych językach programowania. W języku Python cały plik to kod wykonywalny, więc w języku Python jest uruchamiany plik, który jest ładowany do przetwarzania każdej klasy najwyższego poziomu lub definicji funkcji. Jeśli punkt przerwania został ustawiony, może się okazać, że debuger przerywa działanie w ramach deklaracji klasy. To zachowanie jest poprawne, mimo że czasami zaskakujące.

Można dostosować warunki, w których jest wyzwalany punkt przerwania, na przykład tylko wtedy, gdy zmienna jest ustawiona na określoną wartość lub zakres wartości. Aby ustawić warunki, kliknij prawym przyciskiem myszy czerwoną kropkę punktu przerwania, wybierz pozycję **warunek**, a następnie utwórz wyrażenia przy użyciu kodu języka Python. Aby uzyskać pełne szczegóły dotyczące tej funkcji w programie Visual Studio, zobacz [warunki punktu przerwania](../debugger/using-breakpoints.md#breakpoint-conditions).

Podczas ustawiania warunków można także ustawić **akcję** i utworzyć komunikat w celu zarejestrowania się w oknie danych wyjściowych. opcjonalnie kontynuuj wykonywanie automatycznie. Zarejestrowanie komunikatu powoduje utworzenie elementu o nazwie *punkt śledzenia* bez bezpośredniego dodawania kodu rejestrowania do aplikacji:

![Tworzenie punkt śledzenia przy użyciu punktu przerwania](media/debugging-tracepoint.png)

### <a name="step-through-code"></a>Przejdź do kodu

Po zatrzymaniu w punkcie przerwania masz różne sposoby przechodzenia przez kod lub uruchamiania bloków kodu przed ponownym rozdzieleniem. Te polecenia są dostępne w wielu miejscach, w tym na górnym pasku narzędzi do debugowania, **w menu** kontekstowym po kliknięciu prawym przyciskiem myszy w edytorze kodu oraz za pomocą skrótów klawiaturowych (chociaż nie wszystkie polecenia znajdują się we wszystkich miejscach):

| Cecha | Klawiszy | Opis |
| --- | --- | --- |
| **Kontynuuj** | **F5** | Uruchamia kod do momentu osiągnięcia następnego punktu przerwania. |
| **Wkrocz do** | **F11** | Uruchamia następną instrukcję i kończy. Jeśli następna instrukcja jest wywołaniem funkcji, debuger zatrzyma się w pierwszym wierszu wywoływanej funkcji. |
| **Przekrocz nad** | **F10** | Uruchamia następną instrukcję, łącznie z wykonywaniem wywołania funkcji (uruchamianie całego kodu) i zastosowaniem dowolnej wartości zwracanej. Przechodzenie w tryb failover pozwala łatwo pominąć funkcje, które nie muszą być debugowane. |
| **Wyjdź** | **SHIFT** + Klawisz **F11** | Uruchamia kod do końca bieżącej funkcji, a następnie kroki do instrukcji wywołującej.  To polecenie jest przydatne, gdy nie trzeba debugować pozostałej części bieżącej funkcji. |
| **Uruchom do kursora** | **Ctrl** + **F10** | Uruchamia kod do lokalizacji karetki w edytorze. To polecenie umożliwia łatwe pominięcie segmentu kodu, który nie musi być debugowany. |
| **Ustaw następną instrukcję** | **Ctrl** + **SHIFT** + **F10** | Zmienia bieżący punkt przebiegu w kodzie do lokalizacji karetki. To polecenie pozwala pominąć segment kodu, który ma być wykonywany w ogóle, na przykład gdy wiadomo, że kod jest uszkodzony lub powoduje niepożądane skutki uboczne. |
| **Pokaż następną instrukcję** | **Alt** + **Liczba** **&#42;**| Zwraca następną instrukcję do uruchomienia. To polecenie jest przydatne, jeśli szukasz w kodzie i nie pamiętasz, gdzie debuger został zatrzymany. |

### <a name="inspect-and-modify-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu w debugerze można sprawdzić i zmodyfikować wartości zmiennych. Można również użyć okna **czujki** do monitorowania pojedynczych zmiennych, a także wyrażeń niestandardowych. (Zobacz temat [Sprawdzanie zmiennych](../debugger/debugger-feature-tour.md#inspect-variables-with-the-autos-and-locals-windows) , aby uzyskać ogólne szczegóły).

Aby wyświetlić wartość przy użyciu **etykietek** danych, po prostu przesuń wskaźnik myszy nad dowolną zmienną w edytorze. Możesz kliknąć wartość, aby ją zmienić:

![Porady dotyczące danych wyświetlane w debugerze programu Visual Studio](media/debugging-quick-tips.png)

Okno **zmiennych** (  >    >  **autostarty** debugowania systemu Windows) zawiera zmienne i wyrażenia, które są blisko bieżącej instrukcji. Możesz kliknąć dwukrotnie w kolumnie wartość lub zaznaczyć i nacisnąć klawisz **F2** , aby edytować wartość:

![Okno Autokorekty w debugerze programu Visual Studio](media/debugging-autos-window.png)

Okno zmiennych **lokalnych** (**debugowanie**  >  ustawień regionalnych **systemu Windows**  >  ) wyświetla wszystkie zmienne, które znajdują się w bieżącym zakresie, które mogą być ponownie edytowane:

![Okno zmiennych lokalnych w debugerze programu Visual Studio](media/debugging-locals-window.png)

Aby uzyskać więcej informacji na temat korzystania z funkcji **Autostart** i elementów **lokalnych**, zobacz [Sprawdzanie zmiennych w oknach Autostart i lokalne](../debugger/autos-and-locals-windows.md).

Okna **czujki** (**debugowanie**  >  czujki w **systemie Windows**:  >    >  **Obserwuj 1-4**) umożliwiają wprowadzanie dowolnych wyrażeń języka Python i wyświetlanie wyników. Wyrażenia są obliczane na potrzeby każdej czynności:

![okno wyrażeń kontrolnych w debugerze programu Visual Studio](media/debugging-watch-window.png)

Aby uzyskać więcej informacji na temat korzystania z funkcji **Watch**, zobacz [Ustawianie wartości na zmiennych przy użyciu okien czujka i QuickWatch](../debugger/watch-and-quickwatch-windows.md).

Podczas sprawdzania wartości ciągu (,, `str` , `unicode` `bytes` i `bytearray` są brane pod uwagę ciągi do tego celu) ikona lupy zostanie wyświetlona po prawej stronie wartości. Kliknięcie ikony powoduje wyświetlenie wartości ciągu bez cudzysłowu w oknie dialogowym podręcznym, z otoką i przewijaniem, która jest przydatna w przypadku długich ciągów. Ponadto wybranie strzałki listy rozwijanej na ikonie umożliwia wybranie wizualizacji w postaci zwykłego tekstu, HTML, XML i JSON:

![Wizualizatory ciągów w debugerze programu Visual Studio](media/debugging-string-visualizers.png)

Wizualizacje HTML, XML i JSON pojawiają się w oddzielnych oknach podręcznych z wyróżnioną składnią i widokami drzewa.

### <a name="exceptions"></a>Wyjątki

Jeśli w programie wystąpi błąd podczas debugowania, ale nie masz obsługi wyjątków dla tego programu, debuger przerwie się w punkcie wyjątku:

![Okno podręczne wyjątku w debugerze programu Visual Studio](media/debugging-exception-popup.png)

W tym momencie można sprawdzić stan programu, w tym stos wywołań. Jeśli jednak próbujesz przejść przez kod, wyjątek będzie nadal zgłaszany, dopóki nie zostanie obsłużony lub że program zakończy pracę.

Polecenie menu **Debuguj**  >    >  **Ustawienia wyjątków** systemu Windows umożliwia wyświetlenie okna, w którym można rozszerzyć **wyjątki języka Python**:

![Okno wyjątków w debugerze programu Visual Studio](media/debugging-exception-settings.png)

Pole wyboru dla każdego wyjątku kontroluje, czy podczas podniesienia debuger *zawsze* przerywa działanie. Zaznacz to pole wyboru, jeśli chcesz wielokrotnie przerwać wyjątek dla określonego wyjątku.

Domyślnie większość wyjątków jest przerywana, gdy program obsługi wyjątków nie może zostać znaleziony w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy dowolny wyjątek i zmodyfikuj opcję **Kontynuuj przy nieobsługiwanym kodzie użytkownika** . Wyczyść to pole, jeśli chcesz, aby w przypadku wyjątku była mniejsza rzadko.

Aby skonfigurować wyjątek, który nie jest wyświetlany na liście, kliknij przycisk **Dodaj** , aby go dodać. Nazwa musi być zgodna z pełną nazwą wyjątku.

## <a name="project-debugging-options"></a>Opcje debugowania projektu

Domyślnie debuger uruchamia program przy użyciu standardowego modułu uruchamiania języka Python, brak argumentów wiersza polecenia i nie ma innych specjalnych ścieżek ani warunków. Opcje uruchamiania są zmieniane za pomocą właściwości debugowania projektu, do których uzyskuje dostęp, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, wybierając **Właściwości** i wybierając kartę **debugowanie** .

![Właściwości debugowania projektu w debugerze programu Visual Studio](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| **Standardowy moduł uruchamiania języka Python** | Używa kodu debugowania pisanego w przenośnym języku Python, który jest zgodny z CPython, IronPython i wariantami, takimi jak środowisko Python bez stosu. Zapewnia najlepsze środowisko debugowania czystego kodu w języku Python. Po dołączeniu do uruchomionego procesu *python.exe* ten program uruchamiający jest używany. Ten program uruchamiający udostępnia również [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) dla CPython, co pozwala na bezproblemowe przechodzenie między kodem C/C++ i kodem w języku Python. |
| **Uruchamianie w sieci Web** | Uruchamia domyślną przeglądarkę przy uruchamianiu i Włącza debugowanie szablonów. Aby uzyskać więcej informacji, zobacz sekcję [Debugowanie szablonu sieci Web](python-web-application-project-templates.md#debugging) . |
| **Django internetowy** | Taka sama jak w przypadku uruchamiania sieci Web i wyświetlana tylko w celu zapewnienia zgodności z poprzednimi wersjami. |
| **IronPython (.NET) — uruchamianie** | Używa debugera platformy .NET, który działa tylko z IronPython, ale umożliwia wykonywanie kroków między dowolnym projektem języka .NET, w tym C# i VB. Ten program uruchamiający jest używany, jeśli dołączysz do działającego procesu .NET, który obsługuje IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opcje uruchamiania (ścieżki wyszukiwania, argumenty uruchamiania i zmienne środowiskowe)

| Opcja | Opis |
| --- | --- |
| **Ścieżki wyszukiwania** | Te wartości pasują do elementów wyświetlanych w węźle **ścieżki wyszukiwania** projektu w **Eksplorator rozwiązań**. Tutaj możesz zmodyfikować tę wartość, ale łatwiej jest używać **Eksplorator rozwiązań** , które umożliwiają przeglądanie folderów i automatyczne konwertowanie ścieżek do formy względnej. |
| **Argumenty skryptu** | Te argumenty są dodawane do polecenia używanego do uruchamiania skryptu, który jest wyświetlany po nazwie pliku skryptu. Pierwszy element w tym miejscu jest dostępny dla skryptu jako `sys.argv[1]` , drugi jako `sys.argv[2]` i tak dalej. |
| **Argumenty interpretera** | Te argumenty są dodawane do wiersza polecenia programu uruchamiającego przed nazwą skryptu. Często używane argumenty służą `-W ...` do kontrolowania ostrzeżeń, `-O` nieznacznie optymalizacji programu i `-u` korzystania z niebuforowanej operacji we/wy. IronPython użytkownicy mogą używać tego pola do przekazywania `-X` opcji, takich jak `-X:Frames` lub `-X:MTA` . |
| **Ścieżka interpretera** | Zastępuje ścieżkę skojarzoną z bieżącym środowiskiem. Ta wartość może być przydatna do uruchamiania skryptu z interpreterem niestandardowym. |
| **Zmienne środowiskowe** | W tym wielowierszowym polu tekstowym Dodaj wpisy w formularzu \<NAME> = \<VALUE> . Ponieważ to ustawienie jest stosowane ostatnio, na podstawie wszelkich istniejących globalnych zmiennych środowiskowych, a po `PYTHONPATH` nim jest ustawiony zgodnie z ustawieniem **ścieżki wyszukiwania** , może służyć do ręcznego przesłonięcia wszelkich innych zmiennych. |

## <a name="immediate-and-interactive-windows"></a>Bezpośrednie i interaktywne okna

Istnieją dwa **interaktywne okna,** których można użyć podczas sesji debugowania: standardowe okno programu Visual Studio i okno **interaktywne debugowania języka Python** .

Okno **bezpośrednie** (bezpośrednie **debugowanie**  >  **systemu Windows**  >  ) służy do szybkiej oceny wyrażeń języka Python oraz inspekcji lub przypisywania zmiennych w uruchomionym programie. Aby uzyskać szczegółowe informacje, zobacz artykuł ogólne [okna](../ide/reference/immediate-window.md) ogólnego.

Okno **interaktywne debugowania języka Python** (**debugowanie**  >    >  **interaktywne debugowania** systemu Windows w języku Python) jest bogatsze, ponieważ udostępnia pełne [interaktywne środowisko REPL](python-interactive-repl-in-visual-studio.md) podczas debugowania, w tym pisania i uruchamiania kodu. Automatycznie łączy się z dowolnym procesem uruchomionym w debugerze przy użyciu standardowego modułu uruchamiania języka Python (w tym procesów dołączonych za pomocą polecenia **Debug**  >  **Attach to Process**). Nie jest to jednak dostępne w przypadku korzystania z debugowania C/C++ w trybie mieszanym.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

Okno **interaktywne debugowania** obsługuje specjalne meta polecenia oprócz [standardowych poleceń REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Uruchamia program z bieżącej instrukcji. |
| `$down`, `$d` | Przenieś bieżącą ramkę o jeden poziom w dół w śladzie stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | Identyfikator ramki | Przełącza bieżącą ramkę do określonego identyfikatora ramki.
| `$load` | Ładuje polecenia z pliku i wykonuje do momentu ukończenia |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | Identyfikator procesu | Przełącza bieżący proces do określonego identyfikatora procesu. |
| `$procs` | | Wyświetla listę aktualnie debugowanych procesów. |
| `$stepin`, `$step`, `$s` | Kroki do następnego wywołania funkcji, jeśli jest to możliwe. |
| `$stepout`, `$return`, `$r` | Kroki z bieżącej funkcji. |
| `$stepover`, `$until`, `$unt` | Kroki w następnym wywołaniu funkcji. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Przełącza bieżący wątek do określonego identyfikatora wątku. |
| `$threads` | | Wyświetla listę aktualnie debugowanych wątków. |
| `$up`, `$u` | | Przenieś bieżącą ramkę o jeden poziom wyżej w ślad stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramek dla bieżącego wątku. |

Należy zauważyć, że standardowe okna debugera, takie jak **procesy**, **wątki** i **stos wywołań** nie są zsynchronizowane z oknem **debugowania Interactive** . Zmiana aktywnego procesu, wątku lub ramki w oknie **interaktywnym debugowania** nie ma wpływu na inne okna debugera. Podobnie zmiana aktywnego procesu, wątku lub ramki w innych oknach debugera nie ma wpływu na okno **debugowanie interaktywne** .

<a name="use-the-experimental-debugger"></a>

## <a name="use-the-legacy-debugger"></a>Użyj starszego debugera

W programie Visual Studio 2017 wersje 15,8 i nowsze używają debugera opartego na ptvsd wersji 4.1 +. W programie Visual Studio 2019 wersje 16,5 i nowsze używają debugera opartego na debugpy. Te wersje debugera są zgodne z językiem Python 2,7 i Python 3.5 +. Jeśli używasz języka Python 2,6, 3,1 do 3,4 lub IronPython, program Visual Studio wyświetli błąd, **debuger nie obsługuje tego środowiska Python**:

![Debuger nie obsługuje tego błędu środowiska języka Python podczas korzystania z debugera](media/debugging-experimental-incompatible-error.png)

W takich przypadkach należy użyć starszego debugera (co jest ustawieniem domyślnym w programie Visual Studio 2017 w wersji 15,7 i starszej). Wybierz   >  polecenie menu **Opcje** narzędzia, przejdź do debugowania **Python**  >  i wybierz opcję **Użyj starszego debugera** .

Jeśli w bieżącym środowisku zainstalowano starszą wersję programu ptvsd (na przykład wcześniejszą wersję 4.0. x lub wersję 3. x wymaganą do debugowania zdalnego), program Visual Studio może wyświetlić błąd lub ostrzeżenie.

Błąd, nie można **załadować pakietu debugera**, pojawia się po zainstalowaniu ptvsd 3. x:

![Nie można załadować pakietu debugera podczas korzystania z debugera](media/debugging-experimental-version-error.png)

W takim przypadku wybierz pozycję **Użyj starszego debugera** , aby ustawić opcję **Użyj starszego debugera** , i ponownie uruchom debuger.

Ostrzeżenie, **pakiet debugera jest nieaktualne**, pojawia się, gdy zainstalowano wcześniejszą wersję 4. x ptvsd:

![W przypadku korzystania z debugera pakiet debugera jest nieaktualny.](media/debugging-experimental-version-warning.png)

> [!Important]
> Chociaż możesz zignorować ostrzeżenie dla niektórych wersji programu ptvsd, program Visual Studio może nie działał poprawnie.

Aby zarządzać instalacją ptvsd:

1. Przejdź do karty **pakiety** w oknie **środowiska języka Python** .

1. Wprowadź ciąg "ptvsd" w polu wyszukiwania i zapoznaj się z zainstalowaną wersją programu ptvsd:

    ![Sprawdzanie wersji ptvsd w oknie środowiska języka Python](media/debugging-experimental-check-ptvsd.png)

1. Jeśli wersja jest niższa niż 4.1.1 A9 (wersja z programu Visual Studio), wybierz **znak X** z prawej strony pakietu, aby odinstalować starszą wersję. Program Visual Studio następnie używa jego powiązanej wersji. (Można również odinstalować program przy użyciu programu PowerShell `pip uninstall ptvsd` ).

1. Alternatywnie możesz zaktualizować pakiet ptvsd do jego najnowszej wersji, postępując zgodnie z instrukcjami w sekcji [Rozwiązywanie problemów](#troubleshooting) .

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="for-visual-studio-2019-version-164-and-earlier-upgrade-ptvsd"></a>Dla programu Visual Studio 2019 (wersja 16,4 i starsze) ptvsd uaktualnienia
Jeśli masz problemy z debugerem, najpierw Uaktualnij wersję debugera w następujący sposób:

1. Przejdź do karty **pakiety** w oknie **środowiska języka Python** .

1. Wprowadź `ptvsd --upgrade` w polu wyszukiwania, a następnie wybierz pozycję **Uruchom polecenie: pip install ptvsd--upgrade**. (Można również użyć tego samego polecenia z programu PowerShell).

    ![Podawanie polecenia upgrade ptvsd w oknie środowiska języka Python](media/debugging-experimental-upgrade-ptvsd.png)

   Jeśli problemy będą się powtarzać, należy rozwiązać problem w [repozytorium GitHub PTVS](https://github.com/Microsoft/ptvs/issues).

   > [!NOTE]
   > W przypadku programu Visual Studio 2019 w wersji 16,5 lub nowszej debugpy jest częścią obciążenia programu Visual Studio Python i jest aktualizowany wraz z programem Visual Studio.

### <a name="enable-debugger-logging"></a>Włącz rejestrowanie debugera

W trakcie badania problemu debugera firma Microsoft może zażądać włączenia i zebrania dzienników debugera, które pomagają w diagnostyce.

Poniższe kroki umożliwiają debugowanie w bieżącej sesji programu Visual Studio:

1. Otwórz okno polecenia w programie Visual Studio, używając polecenia **Wyświetl**  >  **inne**  >  **okna poleceń** systemu Windows.

1. Wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On /OutputWindow
    ```

1. Rozpocznij debugowanie i wykonaj wszelkie kroki niezbędne do odtworzenia problemu. W tym czasie Dzienniki debugowania są wyświetlane w oknie **dane wyjściowe** w obszarze **Dziennik hosta adaptera debugowania**. Następnie możesz skopiować dzienniki z tego okna i wkleić je do problemu w usłudze GitHub, wiadomości e-mail itp.

    ![Dane wyjściowe rejestrowania debugera w oknie danych wyjściowych](media/debugger-logging-output.png)

1. Jeśli program Visual Studio przestanie odpowiadać lub nie można uzyskać dostępu do okna **danych wyjściowych** , uruchom ponownie program Visual Studio, Otwórz okno polecenia i wprowadź następujące polecenie:

    ```ps
    DebugAdapterHost.Logging /On
    ```

1. Rozpocznij debugowanie i ponownie Odtwórz swój problem. Dzienniki debugera można znaleźć w temacie `%temp%\DebugAdapterHostLog.txt` .

## <a name="see-also"></a>Zobacz też

Aby uzyskać szczegółowe informacje na temat debugera programu Visual Studio, zobacz [debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md).
