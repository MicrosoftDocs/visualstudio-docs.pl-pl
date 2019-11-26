---
title: Wprowadzenie do debugowania w programie Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe8b158fd870b83b39b9d316e68582f2726d89bb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300204"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Wprowadzenie do debugowania w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio 2015 zapewnia bogaty zestaw zintegrowanych kompilacja projektu i narzędzi do debugowania. W tym temacie Dowiedz się, jak rozpocząć korzystanie z najprostszych zbiór debugowanie funkcji interfejsu użytkownika.

 Uwaga: Łącza do bardziej zaawansowanych funkcji i tematy dotyczące określonych platform lub funkcji są u dołu tej strony.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mój kod nie działa. Pomóż mi, Visual Studio 2015!
 Dlatego zapewnieniu edytorze i został utworzony jakiś kod. Teraz chcesz rozpocząć debugowanie kodu. W programie Visual Studio 2015, podobnie jak w przypadku większości środowisk IDE, są dwie fazy do debugowania: kompilować kod, aby wykrywać i usuń błędy projektu i kompilatora; i uruchamianie kodu w środowisku, aby przechwycić i rozwiązywanie błędów czasu wykonywania i dynamicznych.

### <a name="configuring-a-build"></a>Konfigurowanie kompilacji
 Istnieją dwa podstawowe typy konfiguracji kompilacji: **debugowanie** i **wydanie**. Pierwsza konfiguracja tworzy wolniej, większy plik wykonywalny, który umożliwia bogatszych interaktywne środowisko debugowania środowiska wykonawczego, ale nigdy nie powinny być wysyłane. Drugi opiera się szybciej i bardziej zoptymalizowanego pliku wykonywalnego, który jest odpowiedni do wysłania (co najmniej z punktu widzenia kompilatora).

 Domyślną konfiguracją kompilacji jest **debugowanie**.

 ![Przycisk kompilacji debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Można również określić konkretną platformę kompilacji, która ma być docelowa, na przykład **x86** (32-bitowe procesory Intel), **x64** (64-bitowe procesory Intel) i **ARM** (procesory ARM, obsługiwane tylko dla niektórych typów aplikacji). Wartość domyślna to **x86** dla projektów zarządzanych i natywnych. Aby to zmienić, kliknij listę rozwijaną platforma kompilacji i wybierz inną platformę lub **Configuration Manager...**

 ![Okno Menedżera plików konfiguracji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Możesz określić dodaną konfigurację kompilacji przy użyciu **Configuration Manager**. Uruchom ją, kliknij **konfigurację** lub listę rozwijaną **procesora** , a następnie wybierz pozycję **Nowy...** Aby utworzyć nową kompilację lub platformy.

 ![Okno Configuration Manager programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Począwszy od wersji, należy odpowiednio używać **debugowania** i **architektury x86** jako konfiguracji kompilacji i platformy. Po zakończeniu kodowania i debugowania Zmień konfigurację, aby **zwolnić** i wskazać konkretną platformę. (Starsze wersje programu Visual Studio udostępniają domyślną platformę usługi **AnyCPU** dla projektów kodu platformy .NET).

 Uwaga: Podczas kompilowania projektu wartości Konfiguracja i platforma również służą do określenia, jakie ścieżkę katalogu projektu służy do przechowywania pliku wykonywalnego. Zwykle jest to **\<ścieżka do projektu >\\< Project-name\>\\< Configuration\>\\< platform\>** . Na przykład projekt z konfiguracją `Debug` i platformą `x86` można znaleźć w obszarze `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Może to być przydatne w przypadku własnych narzędzi lub skryptów, które zarządzają tymi skompilowane pliki wykonywalne.

### <a name="building-your-code"></a>Tworzenie kodu
 Za pomocą kompilacji skonfigurowane nadszedł czas na faktyczne utworzenie projektu. Najprostszym sposobem wykonania tej czynności jest naciśnięcie klawisza F7, ale można również uruchomić kompilację, wybierając opcję **Kompiluj-> Kompiluj rozwiązanie** z menu głównego.

 ![Wybór menu projektu kompilacji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Można obserwować proces kompilacji w oknie stanu **danych wyjściowych** w dolnej części interfejsu użytkownika programu Visual Studio. W tym miejscu są wyświetlane błędy, ostrzeżenia i operacji kompilacji. Jeśli masz błędów (lub w przypadku ostrzeżenia wyższym poziomie skonfigurowany) kompilacja nie powiedzie się. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiło. Odbuduj projekt, naciskając ponownie klawisz **F7** (w celu ponownego skompilowania tylko plików z błędami) lub **Ctrl + Alt + F7** (w przypadku czystej i kompletnej odbudowy).

 W oknie wyników znajduje się dwa okna kompilacji z kartami: okno **dane wyjściowe** , które zawiera nieprzetworzone dane wyjściowe kompilatora (w tym komunikaty o błędach); i okno **Lista błędów** , które udostępnia listę wszystkich błędów i ostrzeżeń z możliwością sortowania i filtrowania.

 Po pomyślnym wykonaniu tych operacji w oknie **danych wyjściowych** zostaną wyświetlone wyniki podobne do tego.

 ![Pomyślne Kompilowanie danych wyjściowych programu Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Przeglądanie listy błędów
 O ile nie wprowadzono żadnych modyfikacji kodu, który została wcześniej i pomyślnie skompilowana, prawdopodobnie wystąpił błąd. Jeśli jesteś nowym użytkownikiem kodowania, masz prawdopodobnie wiele z nich. Błędy są czasami oczywiste, na przykład błąd prostą składnię lub nieprawidłowa nazwa zmiennej, dlatego czasami są trudne do zrozumienia, z pozoru kodem przeprowadzenie Cię. Aby zapoznać się z bardziej czytelnym widokiem problemów, przejdź do dolnej części okna **dane wyjściowe** kompilacji i kliknij kartę **Lista błędów** . Spowoduje to przejście do bardziej zorganizowanego widoku błędów i ostrzeżeń dotyczących projektu, a także udostępnia pewne dodatkowe opcje.

 ![Dane wyjściowe i Lista błędów programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Kliknij wiersz błędu w oknie **Lista błędów** i przejdź do wiersza, w którym występuje błąd. (Lub Włącz numery wierszy, klikając pasek **Szybkie uruchamianie** w prawym górnym rogu, wpisując ciąg "numery wierszy" i naciskając klawisz ENTER. Jest to najszybszy sposób, aby przejść do pozycji okna **opcji** , w której można włączyć numery wierszy. Dowiedz się, jak korzystać z paska **szybkiego uruchamiania** i zapisywać wiele kliknięć interfejsu użytkownika!)

 ![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Opcja numerów wierszy programu Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Użyj klawiszy Ctrl + G, aby szybko przechodzić do numer wiersza w którym wystąpił błąd.

 Ten błąd jest identyfikowany przez czerwony znak podkreślenia "Zygzakowata". Umieść kursor nad jej, aby uzyskać więcej informacji. Wprowadzić poprawki i jego znikną, chociaż może powodować nowy błąd z korekty. (Jest to nazywane "regresji").

 ![Aktywowanie błędu programu Visual Studio](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Omówimy listę błędów i naprawić wszystkie błędy w kodzie.

 ![Okno błędów debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Przeglądanie błędy szczegółowe
 Wiele błędów może nie ma sensu dla Ciebie ma inną pisownię, są one w warunkach użytkowania kompilator. W takich przypadkach należy uzyskać dodatkowe informacje. W oknie **Lista błędów** można wykonać automatyczne wyszukiwanie Bing, aby uzyskać więcej informacji na temat błędu (lub ostrzeżenia), klikając prawym przyciskiem myszy odpowiedni wiersz wejścia i wybierając pozycję **Pokaż pomoc dotyczącą błędów** z menu kontekstowego.

 ![Wyszukiwanie Bing na liście błędów programu Visual Studio](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Spowoduje to uruchomienie kartę wewnątrz programu Visual Studio 2015, hosty wyniki Bing Wyszukaj kod błędu i tekst. Wyniki są z różnych źródeł w Internecie, a nie wszystkie dane mogą być pomocne.

 Alternatywnie możesz kliknąć wartość kod błędu z linkiem w kolumnie **kod** **Lista błędów**. Spowoduje to uruchomienie wyszukiwanie Bing tylko kod błędu.

### <a name="performing-static-code-analysis"></a>Wykonywanie analizy kodu statycznego
 "Statycznej analizy kodu" jest ozdobnych sposobem powiedzenia "Automatycznie sprawdzaj mój kod dla typowych problemów, które mogą prowadzić do błędów czasu wykonywania lub problemy w zarządzaniu kodu". W celu przejrzenia ją uruchomić, gdy zostały wyczyszczone oczywiste błędy, co uniemożliwia kompilacji i, co pewien czas do rozwiązania ostrzeżeń, które może ona generować. Będziesz zaoszczędzić kilka problemów występujących, a także Dowiedz się, kilka technik stylu kodu.

 Naciśnij klawisze ALT + F11 (lub wybierz polecenie **Analizuj-> Uruchom analizę kodu w rozwiązaniu** z górnego menu), aby rozpocząć analizę kodu statycznego. Może potrwać trochę czasu, jeśli masz duże ilości kodu.

 ![Element menu analizy kodu dla programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Wszystkie nowe lub zaktualizowane ostrzeżenia pojawią się na karcie **Lista błędów** w dolnej części IDE. Polecenie ostrzeżenia, aby przejść do nich.

 ![Program Visual Studio 2015 Lista błędów z ostrzeżeniami](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Ostrzeżenia zostaną zidentyfikowane przy użyciu wyraziste wężyk żółty zielony zamiast czerwonego. Umieść kursor nad nimi, aby uzyskać więcej szczegółów, a następnie kliknij prawym przyciskiem myszy na ich w celu uzyskania menu kontekstowym, aby pomóc w poprawki lub opcje refaktoryzacji.

 ![Visual Studio Code aktywowania ostrzeżenia analizy](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Za pomocą ikon żarówek Aby naprawić lub refaktoryzacji kodu
 Ikony żarówek są nową funkcją programu Visual Studio 2015, które umożliwiają Refaktoryzuj kod inline. Są one prosty sposób, aby rozwiązać typowe ostrzeżenia szybko i skutecznie. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy na wężyk ostrzeżenie (lub naciśnij klawisze Ctrl +. Po umieszczeniu nad nimi wskaźnika myszy, a następnie wybierz polecenie **szybkie akcje**.

 ![Szybkie opcje dla żarówki programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Zostanie wyświetlona lista możliwych poprawki lub refactors, które można zastosować do tego wiersza kodu.

 ![Visual Studio 2015 Light żarówka — wersja zapoznawcza](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Żarówki może służyć wszędzie tam, gdzie określić analizatorów kodu, jest możliwość rozwiązać problem, Refaktoryzacja, lub poprawić kod. Kliknij dowolny wiersz kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz opcję **szybkie opcje** (lub, jeśli wolisz, naciśnij klawisze CTRL +). Jeśli dostępne są opcje refaktoryzacji obszaru lub ulepszeń, zostaną one wyświetlone. w przeciwnym razie `No quick options available here` zostanie wyświetlony w lewym dolnym rogu IDE.

 ![Tekst "Brak opcji" dla żarówki programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Za pomocą środowiska szybko można użyć klawiszy strzałek oraz klawiszy Ctrl +. Sprawdź, czy opcja szybkie możliwości refaktoryzacji i wyczyścić kod!

 Aby uzyskać więcej informacji o żarówkach, przeczytaj temat [wykonywanie szybkich akcji z żarówkami](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Debugowanie kodu uruchamiania
 Teraz, po pomyślnym skompilowaniu kodu i wykonaniu nieco czyszczenia, uruchom go, naciskając klawisz F5 lub wybierając polecenie **Debuguj-> Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, dzięki czemu możesz obserwować jego zachowanie szczegółowo. Środowisko IDE programu Visual Studio 2015 zmienia się podczas działania aplikacji: okno **dane wyjściowe** jest zastępowane dwoma nowymi (w konfiguracji okna domyślnego), okna elementy **Autostart/lokalne/moduły/Watch** z kartami oraz **stos wywołań/punktów przerwania/ustawienia wyjątku/wyjściowe** okno z kartami. Te okna mają wiele kart, które pozwalają na sprawdzanie i oceny aplikacji zmiennych, wątki, stosy wywołań i różnych innych zachowań podczas jej działania.

 ![PROGRAMU VS2015 i okna stosu wywołań](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Wypróbuj różne akcje ze swoją aplikacją i obserwować zmiany. Jeśli coś występuje nietypowe, Wstrzymaj aplikację, naciskając klawisze CTRL + ALT + BREAK (lub klikając przycisk **pauza** ).

 ![Przycisk Przerwij wszystko w programie Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Naciśnij klawisz F5, aby kontynuować uruchamianie aplikacji (lub kliknij przycisk **Kontynuuj** ).

 ![Przycisk Kontynuuj debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Aby zatrzymać aplikację, naciśnij klawisze Shift + F5 lub klikając przycisk **Zatrzymaj** . Alternatywnie możesz po prostu zamknąć główne okno aplikacji (lub okno wiersza polecenia).

 Jeżeli kod działa bez zarzutu i dokładnie tak jak oczekiwano, Gratulacje! Zmień konfigurację kompilacji, aby **zwolnić** i skompilować ją w celu wdrożenia. (Specjaliści mogą chcieć przeskoczyć do bitu testów jednostkowych na końcu, chociaż). Jeśli jednak zawiesz lub uległ awarii lub wykazałeś pewne dziwne wyniki, musisz znaleźć źródło tych problemów i naprawić błędy.

### <a name="setting-simple-breakpoints"></a>Ustawianie punktów przerwania prosty
 Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu. NIE trzeba ponownie skompiluj projekt po ustawiania i usuwania punktów przerwania.

 Ustaw punkt przerwania, klikając w końcu margines linii, na którym ma przerwanie wystąpią, lub wybierz linii kodu i naciśnij klawisz F9. Kiedy uruchamiasz swój kod, zatrzyma się, zanim wykonywane są instrukcje dotyczące ten wiersz kodu.

 ![Punkt przerwania programu Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Gdy kod zostanie przerwany, oznaczony wiersz kodu nie ma jeszcze wykonane. W tym momencie możesz wykonać instrukcje dotyczące wiersza kodu, oznaczony przez punkt przerwania i sprawdzić zmienionymi wartościami. Jest to nazywane "Przechodzenie do" kodu. Oznaczone kodu w przypadku wywołania metody, można było do niego przejść, naciskając klawisz F11. Użytkownik może również "Przekrocz nad" wiersz kodu, naciskając klawisz F10. Aby uzyskać więcej informacji na temat akcji krok przerwania, przeczytaj temat [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

 Najczęstsze zastosowania dla punktów przerwania obejmują:

1. Aby zawęzić źródło awarię lub zawieszenie, wykres punktowy je w całej i wokół kodu wywołania metody, które Twoim zdaniem jest przyczyną błędu. Jak krok po kroku przez kod, Usuń, a następnie zresetuj punktów przerwania bliżej razem do momentu znalezienia naruszającym wierszem kodu.

2. Po wprowadzeniu nowego kodu, należy ustawić punkt przerwania na początku i Przechodź przez kod, aby upewnić się, że zachowuje się zgodnie z oczekiwaniami.

3. Jeśli zaimplementowano skomplikowane zachowanie, ustaw punktów przerwań dla kodu algorytmicznego, dzięki czemu można sprawdzić wartości zmiennych i danych, kiedy program przerywa.

4. Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać wykonywanie kodu, dzięki czemu można sprawdzić wartości adresów (Zwróć uwagę na wartość NULL) i liczby odwołań podczas debugowania błędów związanych z pamięcią.

   Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj temat [Używanie punktów przerwania](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Ustawienie warunkowe punkty przerwania
 Jeśli masz punkt przerwania w pętli lub rekursji lub masz wiele punktów przerwania, które często krokowo, należy użyć warunkowego punktu przerwania, aby upewnić się, że Twój kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. W przeciwnym razie użytkownik będzie można naciskając klawisz F11 często są bardzo wiele.

 Aby ustawić warunkowego punktu przerwania i zawiesić kodu, gdy zmienna jest równa określonej wartości lub przekazuje określonego progu, kliknij na marginesie, aby ustawić punkt przerwania, a następnie wybierz pozycję "koło zębate" z menu po wskazaniu wskaźnikiem, które pojawia się.

 ![Ustawienia punktu przerwania programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Pojawi się okno dialogowe, które wygląda w następujący sposób gdzie ustawić określone warunki nastąpić przerwanie.

 ![Warunkowy punkt przerwania programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Aby uzyskać szczegółowe informacje na temat sposobu deklarowania wyrażeń używanych do obliczania warunkowych punktów przerwania, zapoznaj się z tematem [Konfiguracja punktu przerwania wideo channel9 w programie Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania
 Kiedy uruchomiony kod uderza w punkt przerwania i zostanie zatrzymana, można sprawdzić zmiennych i Wywołaj stosy, aby ustalić, co się dzieje. Są wartości z zakresów, które powinny być widoczne? Są wykonywane w odpowiedniej kolejności wywołań?

 ![Inspekcja wartości czasu&#45;uruchomienia programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Umieść kursor nad zmienną, aby wyświetlić wartości i odwołania, które obecnie znajdują. Jeśli widzisz wartość, którą Nieoczekiwane wyrażenie, prawdopodobnie masz usterkę w poprzednim lub wywoływania wierszy kodu. Przenieś w górę punktów przerwania lub dodawanie warunków do istniejących punktów przerwania, aby zawęzić wyszukiwanie.

 Ponadto program Visual Studio 2015 Wyświetla okno narzędzia diagnostyczne, w którym możesz obserwować zużycie pamięci i procesora CPU w Twojej aplikacji wraz z upływem czasu. Użyj ich do wyszukania nieprzewidziane duże obciążenie lub pamięć alokacji Procesora. Użyj go w połączeniu z oknem **czujki** i punktem przerwania, aby określić, co powoduje nieoczekiwane użycie lub niewykorzystane zasoby.

 ![Okno narzędzia diagnostyczne programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Uruchamianie testów jednostkowych
 Testy jednostkowe są programy, które wykonuje ścieżek kodu w aplikacji lub usługi. Program Visual Studio 2015 instaluje struktur testowania jednostek pochodzących od firmy Microsoft dla kodu zarządzanego i natywnego. Testowania jednostkowego umożliwia tworzenie testów jednostkowych, uruchamiaj je i raportuje o wynikach tych testów. Jednostka ponownie uruchom testy przy wprowadzaniu zmian do testowania, Twój kod nadal działa poprawnie. Gdy używasz programu Visual Studio 2015 Enterprise, można uruchomić testy automatyczne po każdej kompilacji.

 Aby rozpocząć, przeczytaj artykuł [generowanie testów jednostkowych dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Aby dowiedzieć się więcej o testach jednostkowych w programie Visual Studio 2015 i jak mogą one pomóc w tworzeniu lepszej jakości kodu, Przeczytaj [podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie w ustawieniach debugera programu Visual Studio](../debugger/debugging-in-visual-studio.md) [i debugowanie przygotowania](../debugger/debugger-settings-and-preparation.md) [64-bitowe —](../debugger/debug-64-bit-applications.md) [podstawowe informacje o debugerze](../debugger/debugger-basics.md)
