---
title: Naprawianie błędów programu i ulepszanie kodu
description: W tym artykule opisano kilka podstawowych Visual Studio, które mogą ułatwić znajdowanie i rozwiązywanie problemów w kodzie, takich jak błędy kompilacji, analiza kodu, narzędzia debugowania i testy jednostkowe.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5af76de5dbcc7a70722acf0ee01cfed93dbad761
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308262"
---
# <a name="make-code-work-in-visual-studio"></a>Spraw, aby kod działał w Visual Studio

Visual Studio udostępnia zaawansowany zintegrowany zestaw narzędzi do kompilowania i debugowania projektów. W tym artykule doszukaj się, Visual Studio mogą pomóc w odnalezieniu problemów w kodzie przy użyciu danych wyjściowych kompilacji, analizy kodu, narzędzi debugowania i testów jednostkowych.

Ustaliliśmy edytor i utworzono kod. Teraz chcesz się upewnić, że kod działa prawidłowo. W Visual Studio, podobnie jak w przypadku większości esejów, istnieją dwie fazy, aby kod działał: tworzenie kodu w celu przechwytowania i rozwiązywania błędów projektu i kompilatora oraz uruchamianie kodu w celu znalezienia błędów w czasie działania i błędów dynamicznych.

## <a name="build-your-code"></a>Tworzenie kodu

Istnieją dwa podstawowe typy konfiguracji kompilacji: **debugowanie** i **wydanie**. Konfiguracja **debugowania** generuje wolniejszy, większy plik wykonywalny, który umożliwia bardziej rozbudowane interaktywne środowisko debugowania w czasie wykonywania. Plik **wykonywalny** debugowania nigdy nie powinien być dostarczany. Konfiguracja **wydania** tworzy szybszy, zoptymalizowany plik wykonywalny, który jest odpowiedni do wysłania (przynajmniej z perspektywy kompilatora). Domyślna konfiguracja kompilacji to **Debuguj**.

Najprostszym sposobem skompilowania projektu jest naciśnięcie klawisza **F7,** ale możesz również rozpocząć kompilację, wybierając pozycję **Build** Build Solution (Skompilowanie rozwiązania)  >   z menu głównego.

![Visual Studio menu projektu kompilacji](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Proces kompilacji można obserwować w oknie **Dane** wyjściowe w dolnej części Visual Studio użytkownika. Błędy, ostrzeżenia i operacje kompilacji są wyświetlane tutaj. Jeśli występują błędy (lub jeśli masz ostrzeżenia powyżej skonfigurowanego poziomu), kompilacja kończy się niepowodzeniem. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiły. Ponownie skompiluj projekt, naciskając klawisz **F7** (aby ponownie skompilować tylko pliki z błędami) lub naciskając klawisze **Ctrl** + **Alt** F7 (w celu oczyszczenia i ukończenia +  ponownej kompilacji).

W oknie wyników poniżej edytora istnieją dwa  okna z kartami: okno Dane wyjściowe, które zawiera nieprzetworzone dane wyjściowe kompilatora (w tym komunikaty o błędach); i okno **Lista błędów,** które udostępnia sortowalna i filtrowalna lista wszystkich błędów i ostrzeżeń.

Gdy kompilacja zakończy się powodzeniem, w oknie Dane wyjściowe zobaczysz **wyniki podobne** do tych:

![Visual Studio danych wyjściowych kompilacji](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Przejrzyj listę błędów

Jeśli nie w kodzie, który został wcześniej i pomyślnie skompilowany, prawdopodobnie wystąpił błąd. Jeśli programowanie jest dla Ciebie nowe, prawdopodobnie masz ich wiele. Błędy są czasami oczywiste, takie jak prosty błąd składniowy lub nieprawidłowa nazwa zmiennej, i czasami są trudne do zrozumienia, z jedynie kodem kryptograficznym, który Cię poprowadzi. Aby uzyskać bardziej przejrzysty widok problemów, przejdź  do dolnej części okna Dane wyjściowe kompilacji i kliknij **kartę Lista błędów.** Dzięki temu można uzyskać bardziej zorganizowany widok błędów i ostrzeżeń dotyczących projektu, a także uzyskać dodatkowe opcje.

![Visual Studio dane wyjściowe i lista błędów](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknij wiersz błędu w **oknie Lista błędów,** aby przejść do wiersza, w których występuje błąd. (Lub włącz numery wiersza, naciskając **klawisze Ctrl)** + **Q**, wpisując **numery wiersza**, a następnie wybierając pozycję Włącz lub **wyłącz** numery wiersza w wynikach. Jest to najszybszy sposób na dostęp do okna dialogowego **Opcje,** w którym można włączyć numery wiersza).

![Visual Studio z numerami wiersza](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio numerów wiersza](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Naciśnij **klawisze Ctrl** + **G,** aby szybko przejść do numeru wiersza, w którym wystąpił błąd.

Błąd jest identyfikowany za pomocą czerwonego podkreślenia "zygzyka&quot;. Umieść na nim wskaźnik myszy, aby uzyskać dodatkowe szczegóły. Wprowadź poprawkę i zostanie ona wymysła, chociaż możesz wprowadzić nowy błąd z poprawką. (Jest to nazywane &quot;regresją").

![Visual Studio myszy na błędzie](../ide/media/vs_ide_gs_debug_error_hover1.png)

Należy przejść przez listę błędów i rozwiązać wszystkie błędy w kodzie.

![Visual Studio debugowania błędów](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Szczegółowe informacje o błędach

Wiele błędów może nie mieć sensu — są one sformułowane w terminach kompilatora. W takich przypadkach będą potrzebne dodatkowe informacje. W **oknie Lista** błędów możesz automatycznie wyszukać usługę Bing, aby uzyskać więcej informacji na temat błędu lub ostrzeżenia. Kliknij prawym przyciskiem myszy odpowiedni  wiersz wejścia i wybierz polecenie Pokaż pomoc o błędach  z menu kontekstowego lub kliknij wartość kodu błędu hiperlinku w kolumnie Kod listy **błędów**.

![Visual Studio wyszukiwania Bing na liście błędów](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

W zależności od ustawień przeglądarka internetowa wyświetla wyniki wyszukiwania dla kodu błędu i tekstu albo otwiera kartę Visual Studio i wyświetla wyniki wyszukiwania Bing. Wyniki są z wielu różnych źródeł w Internecie i nie wszystkie mogą być przydatne.

## <a name="use-code-analysis"></a>Korzystanie z analizy kodu

Analizatory kodu poszukaj typowych problemów z kodem, które mogą prowadzić do błędów w czasie działania lub problemów z zarządzaniem kodem.

### <a name="c-and-visual-basic-code-analysis"></a>Analiza kodu w języku C# Visual Basic analizy kodu

Visual Studio zawiera wbudowany zestaw analizatorów [.NET Compiler Platform,](../code-quality/roslyn-analyzers-overview.md) które badają język C# i Visual Basic kodu podczas wpisywania. Dodatkowe analizatory można zainstalować jako rozszerzenie Visual Studio lub jako pakiet NuGet. Jeśli zostaną znalezione naruszenia reguł, będą one zgłaszane zarówno na liście błędów, jak i w edytorze kodu jako zygmki pod kodem naruszającym zasady.

### <a name="c-code-analysis"></a>Analiza kodu C++

Aby przeanalizować kod C++, uruchom [statyczną analizę kodu](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Po wyczyszczeniu oczywistych błędów, które uniemożliwiają pomyślną kompilację, poświęć trochę czasu na działanie tych ostrzeżeń. Zaoszczędzisz sobie kilka kroków w drodze i poznasz kilka technik stylu kodu.

Naciśnij **klawisz Alt** + **F11** (lub wybierz pozycję Analizuj wyniki Code Analysis w rozwiązaniu z górnego menu), aby rozpocząć   >   statyczną analizę kodu.

![Visual Studio Code menu Analiza](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Wszystkie nowe lub zaktualizowane ostrzeżenia są wyświetlane na karcie **Lista błędów** w dolnej części środowiska IDE. Kliknij ostrzeżenia, aby przejść do nich w kodzie.

![Visual Studio listy błędów z ostrzeżeniami](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Używanie szybkich akcji do naprawiania lub refaktoryzacji kodu

[Szybkie akcje](../ide/quick-actions.md), dostępne z ikony żarówki lub śrubokręta, umożliwiają refaktoryzę kodu w tekście. Są one łatwym sposobem szybkiego i skutecznego naprawiania typowych ostrzeżeń w języku C#, C++ i Visual Basic kodu. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy zygieł ostrzeżenie i wybierz pozycję Szybkie **akcje i refaktoryzowanie.** Lub, gdy kursor znajduje się na linii z kolorowym zygieł, naciśnij **klawisze Ctrl** + **.** lub wybierz ikonę żarówki, żarówki błędu lub śrubokręta na marginesie. Zostanie wyświetlona lista możliwych poprawek lub refaktoryzacji, które można zastosować do tego wiersza kodu.

![Visual Studio żarówki (wersja zapoznawcza)](../ide/media/quick-actions-options.png)

Szybkich akcji można używać wszędzie tam, gdzie analizatory kodu określają możliwość naprawy, refaktoryzacji lub ulepszenia kodu. Kliknij dowolny wiersz kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz pozycję Szybkie **akcje i refaktoryzowanie.** Jeśli są dostępne opcje refaktoryzacji lub ulepszeń, są one wyświetlane. W przeciwnym razie **w** lewym dolnym rogu środowiska IDE zostanie wyświetlony komunikat Brak dostępnych szybkich akcji.

![Brak dostępnego tekstu szybkich akcji](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Z doświadczeniem możesz szybko używać klawiszy strzałek i **klawiszy Ctrl.** +  w celu sprawdzenia możliwości łatwej refaktoryzacji i oczyszczenia kodu!

::: moniker range=">=vs-2019"

## <a name="run-code-cleanup"></a>Uruchamianie oczyszczania kodu

Visual Studio formatuje plik kodu [języka C#](code-styles-and-code-cleanup.md#apply-code-styles)na żądanie, w tym preferencje stylu kodu, za pomocą przycisku **Oczyszczanie** kodu w dolnej części edytora.

![Przycisk Oczyszczanie kodu w Visual Studio 2019 r.](media/execute-code-cleanup.png)

Oprócz formatowania pliku dla spacji, wcięć, et **cetera,** oczyszczanie kodu stosuje również zestaw określonych konwencji stylu kodu. Preferencje dla każdego stylu kodu są odczytywane z pliku [EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) jeśli istnieje dla projektu lub z ustawień stylu kodu w **oknie dialogowym** Opcje.

::: moniker-end

## <a name="debug-your-running-code"></a>Debugowanie uruchomionego kodu

Teraz, po pomyślnym s zbudowaniu kodu i wykonaniu niewielkiego czyszczenia, uruchom go, naciskając **klawisz F5** lub wybierając pozycję **Debuguj**  >  **rozpocznij debugowanie.** To uruchamia aplikację w środowisku debugowania, dzięki czemu można dokładnie obserwować jej zachowanie. W Visual Studio IDE zmienia się, gdy aplikacja  jest uruchomiona: okno Danych wyjściowych jest zastępowane dwoma nowymi (w domyślnej konfiguracji okna), oknem z kartami **Autos/Locals/Watch** i oknem z kartami Stos **wywołań/Punkty przerwania/Ustawienia wyjątków/Dane** wyjściowe. Te okna mają wiele kart, które umożliwiają sprawdzanie i ocenianie zmiennych, wątków, stosów wywołań i różnych innych zachowań aplikacji podczas jej działania.

![Visual Studio automatyczne i okna stosu wywołań](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zatrzymaj aplikację, naciskając **klawisz** + **Shift F5** lub klikając **przycisk** Zatrzymaj. Możesz też po prostu zamknąć główne okno aplikacji (lub okno dialogowe wiersza polecenia).

Jeśli twój kod działa idealnie i dokładnie zgodnie z oczekiwaniami, gratulacje! Jeśli jednak przestanie odpowiadać, ulegać awarii lub da Ci dziwne wyniki, musisz znaleźć źródło tych problemów i naprawić błędy.

### <a name="set-simple-breakpoints"></a>Ustawianie prostych punktów przerwania

[Punkty przerwania to](../debugger/using-breakpoints.md) najbardziej podstawowa i najważniejsza funkcja niezawodnego debugowania. Punkt przerwania wskazuje, gdzie Visual Studio powinien wstrzymać uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych, zachowaniu pamięci lub temu, czy gałąź kodu jest uruchamiana. Po ustawieniu i usunięciu punktów przerwania nie trzeba ponownie kompilować projektu.

Ustaw punkt przerwania, klikając na marginesie daleko wiersza, w którym ma wystąpić przerwa, lub naciśnij **klawisz F9,** aby ustawić punkt przerwania w bieżącym wierszu kodu. Po uruchomieniu kodu zostanie on wstrzymany *(lub* przerwany) przed wykonaniem instrukcji dla tego wiersza kodu.

![Visual Studio punkt przerwania](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Typowe zastosowania punktów przerwania obejmują:

- Aby zawęzić źródło awarii lub nieosiągalnego programu, należy rozproszyć punkty przerwania w całym kodzie wywołania metody, które według Ciebie powoduje awarię. Podczas uruchamiania kodu w debugerze usuń, a następnie zresetuj punkty przerwania bliżej siebie, aż znajdziesz wiersz kodu, który jest zaniedresowany. Zobacz następną sekcję, aby dowiedzieć się, jak uruchamiać kod w debugerze.

- Po wprowadzeniu nowego kodu ustaw punkt przerwania na jego początku i uruchom go, aby upewnić się, że działa zgodnie z oczekiwaniami.

- Jeśli zaimplementowano skomplikowane zachowanie, ustaw punkty przerwania dla kodu algorytmu, aby można było sprawdzić wartości zmiennych i danych, gdy program przerwie działanie.

- Jeśli piszesz kod w języku C lub C++, użyj punktów przerwania, aby zatrzymać kod, aby sprawdzić wartości adresów (poszukaj wartości NULL) i liczby odwoływać się podczas debugowania w przypadku błędów związanych z pamięcią.

Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj [używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Inspekcja kodu w czasie uruchamiania

Gdy uruchomiony kod trafi do punktu przerwania i zostanie wstrzymany, wiersz kodu oznaczony kolorem żółtym (bieżąca instrukcja) nie został jeszcze wykonany. W tym momencie można wykonać bieżącą instrukcje, a następnie sprawdzić zmienione wartości. Do wykonania kodu w *debugerze* można użyć kilku poleceń krokowych. Jeśli oznaczony kod jest wywołaniem metody, możesz przejść do niego, naciskając **klawisz F11**. Możesz również *przejść przez wiersz* kodu, naciskając klawisz **F10**. Aby uzyskać dodatkowe polecenia i szczegółowe informacje na temat przechodzenia przez kod, przeczytaj [navigate code with the debugger (Nawigowanie po kodzie za pomocą debugera).](../debugger/navigating-through-code-with-the-debugger.md)

![Zrzut ekranu przedstawiający Visual Studio kodu. Czerwona kropka w lewym śmietku wskazuje punkt przerwania w wierszu kodu oznaczonym kolorem żółtym.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na powyższej ilustracji można przejść do poprzednich instrukcji debugera, naciskając klawisz **F10** lub **F11** (ponieważ nie ma tutaj wywołania metody, oba polecenia mają taki sam wynik).

Gdy debuger jest wstrzymany, można sprawdzić zmienne i stosy wywołań, aby określić, co się dzieje. Czy wartości znajdują się w spodziewanych zakresach? Czy wywołania są podejmowane w odpowiedniej kolejności?

![Zrzut ekranu przedstawiający Visual Studio kodu. W wierszu kodu oznaczonym kolorem żółtym jest zaznaczona zmienna, a na liście rozwijanej jest widać jej bieżącą wartość i odwołania.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Umieść kursor na zmiennej, aby wyświetlić jej bieżącą wartość i odwołania. Jeśli zobaczysz oczekiwaną wartość, prawdopodobnie masz usterkę w poprzednim lub wywołującym kodzie. Aby uzyskać więcej szczegółowych informacji na temat debugowania, [dowiedz się więcej](../debugger/debugger-feature-tour.md) na temat korzystania z debugera.

Ponadto Visual Studio zostanie wyświetlone narzędzia diagnostyczne, w którym można obserwować użycie procesora CPU i pamięci aplikacji w czasie.  W dalszej części opracowywania aplikacji możesz użyć tych narzędzi, aby znaleźć nieoczekiwane wysokie użycie procesora CPU lub alokację pamięci. Użyj go w połączeniu z oknem **Czujka** i punktami przerwania, aby określić, co powoduje nieoczekiwane duże użycie lub niewydajne zasoby. Aby uzyskać więcej informacji, zobacz [Profiling feature tour (Przewodnik po funkcji profilowania).](../profiling/profiling-feature-tour.md)

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Testy jednostkowe są twoją pierwszą linią obrony przed błędami kodu, ponieważ jeśli zostaną wykonane prawidłowo, testują pojedynczą "jednostkę" kodu, zwykle jedną funkcję, i są łatwiejsze do debugowania niż pełny program. Visual Studio instaluje struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Użyj struktury testowania jednostkowego, aby tworzyć testy jednostkowe, uruchamiać je i raportować wyniki tych testów. Ponownie przetrunuj testy jednostkowe po wymuszeniu zmian, aby sprawdzić, czy kod nadal działa prawidłowo. W Visual Studio Enterprise można uruchamiać testy automatycznie po każdej kompilacji.

Aby rozpocząć pracę, przeczytaj [temat Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest.](../test/generate-unit-tests-for-your-code-with-intellitest.md)

Aby dowiedzieć się więcej o testach jednostkowych w programie Visual Studio i o tym, jak mogą one pomóc w tworzeniu kodu o lepszej jakości, zapoznaj się z [tematem Podstawowe informacje dotyczące testów jednostkowych.](../test/unit-test-basics.md)

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Dowiedz się więcej na temat korzystania z debugera](../debugger/index.yml)
- [Generowanie i naprawianie kodu](../ide/code-generation-in-visual-studio.md)
