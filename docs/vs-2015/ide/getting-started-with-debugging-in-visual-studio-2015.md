---
title: Wprowadzenie do debugowania w programie Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7fecc637a62e96381362d79f66eb5a3cd4d8fa1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764851"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Wprowadzenie do debugowania w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio 2015 zapewnia bogaty zestaw zintegrowanych kompilacja projektu i narzędzi do debugowania. W tym temacie Dowiedz się, jak rozpocząć korzystanie z najprostszych zbiór debugowanie funkcji interfejsu użytkownika.

 Uwaga: Zawiera łącza do bardziej zaawansowanych funkcji i tematy dotyczące określonych platform lub funkcji są u dołu tej strony.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mój kod nie działa. Pomóż mi, Visual Studio 2015!
 Dlatego zapewnieniu edytorze i został utworzony jakiś kod. Teraz chcesz rozpocząć debugowanie kodu. W programie Visual Studio 2015, podobnie jak w przypadku większości środowisk IDE, są dwie fazy do debugowania: kompilować kod, aby wykrywać i usuń błędy projektu i kompilatora; i uruchamianie kodu w środowisku, aby przechwycić i rozwiązywanie błędów czasu wykonywania i dynamicznych.

### <a name="configuring-a-build"></a>Konfigurowanie kompilacji
 Istnieją dwa podstawowe rodzaje konfiguracji kompilacji: **Debugowanie** i **wersji**. Pierwsza konfiguracja tworzy wolniej, większy plik wykonywalny, który umożliwia bogatszych interaktywne środowisko debugowania środowiska wykonawczego, ale nigdy nie powinny być wysyłane. Drugi opiera się szybciej i bardziej zoptymalizowanego pliku wykonywalnego, który jest odpowiedni do wysłania (co najmniej z punktu widzenia kompilatora).

 W domyślnej konfiguracji kompilacji **debugowania**.

 ![Visual Studio Debug Build przycisk](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Można również określić platformę kompilacji określonego obiektu docelowego, takie jak **x86** (32-bitowe procesory Intel), **x64** (procesorów Intel 64-bitowy), a **ARM** (procesory ARM, obsługiwane tylko w przypadku niektórych aplikacji typy). Wartość domyślna to **x86** dla projektów zarządzanego i natywnego. Aby je zmienić, kliknij listę rozwijaną platformy kompilacji i wybierz pozycję innej platformy lub **programu Configuration Manager...**

 ![Okno Menedżera plik konfiguracji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Można określić konfiguracji docelowej kompilacji przy użyciu **programu Configuration Manager**. Uruchom go, kliknij przycisk **konfiguracji** lub **Procesora** listy rozwijanej i wybierz **nowy...** Aby utworzyć nową kompilację lub platformy.

 ![Okno Menedżera konfiguracji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Po prostu zaczynasz pracę, użyj **debugowania** i **x86** jako konfigurację kompilacji i platformy, odpowiednio. Gdy wszystko będzie gotowe do kodowania i debugowania, zmień konfigurację, aby **wersji** i określania elementów docelowych określonej platformy. (Starsze wersje programu Visual Studio, pod warunkiem **AnyCPU** domyślna platforma dla projektów kodu .net.)

 Uwaga: Podczas kompilowania projektu wartości Konfiguracja i platforma również służą do określenia, jakie ścieżkę katalogu projektu służy do przechowywania pliku wykonywalnego. Zazwyczaj jest to  **\<ścieżkę do projektu >\\< Nazwa projektu >\\< configuration\>\\< platforma\>**. Na przykład projektu z konfiguracją `Debug` i platformie `x86` będzie można znaleźć w obszarze `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Może to być przydatne w przypadku własnych narzędzi lub skryptów, które zarządzają tymi skompilowane pliki wykonywalne.

### <a name="building-your-code"></a>Tworzenie kodu
 Za pomocą kompilacji skonfigurowane nadszedł czas na faktyczne utworzenie projektu. Najprostszym sposobem, aby to zrobić, można nacisnąć klawisz F7, ale można również uruchomić kompilację, wybierając **kompilacji -> Kompiluj rozwiązanie** z menu głównego.

 ![Program Visual Studio kompilacji projektu menu wyboru](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Możesz obserwować proces kompilacji w **dane wyjściowe** okno stanu w dolnej części interfejsie użytkownika programu Visual Studio. W tym miejscu są wyświetlane błędy, ostrzeżenia i operacji kompilacji. Jeśli masz błędów (lub w przypadku ostrzeżenia wyższym poziomie skonfigurowany) kompilacja nie powiedzie się. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiło. Ponownie skompiluj projekt, naciskając klawisz albo **F7** ponownie (, aby ponownie skompilować tylko te pliki z błędami) lub **Ctrl + Alt + F7** (dla przejrzystości oraz pełną ponowną kompilację).

 Istnieją dwa tworzenie okien z zakładkami w oknie wyników poniżej edytora: **dane wyjściowe** okno, które zawiera kompilator nieprzetworzonych danych wyjściowych (w tym komunikaty o błędach); i **lista błędów** okna, które zawiera listę sortowanie i filtrowanie wszystkich błędów i ostrzeżeń.

 Jeśli operacja się powiedzie, będzie możliwe zobaczenie wyników tak jak poniżej w **dane wyjściowe** okna.

 ![Dane wyjściowe kompilacji programu Visual Studio pomyślnie](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Przeglądanie listy błędów
 O ile nie wprowadzono żadnych modyfikacji kodu, który została wcześniej i pomyślnie skompilowana, prawdopodobnie wystąpił błąd. Jeśli jesteś nowym użytkownikiem kodowania, masz prawdopodobnie wiele z nich. Błędy są czasami oczywiste, na przykład błąd prostą składnię lub nieprawidłowa nazwa zmiennej, dlatego czasami są trudne do zrozumienia, z pozoru kodem przeprowadzenie Cię. Widok oczyszczarki problemów, przejdź do dolnej części kompilacji **dane wyjściowe** okna, a następnie kliknij przycisk **lista błędów** kartę. Przejście do bardziej zorganizowane widoku błędów i ostrzeżeń dotyczących projektu i zapewnia pewne dodatkowe opcje.

 ![Visual Studio 2015 w danych wyjściowych i lista błędów](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Kliknij wiersz błędu w **lista błędów** okna i przechodzenie do wiersza błędu w. (Lub włączyć numery wierszy, klikając w **Szybkie uruchamianie** paska w prawym górnym rogu, wpisując "numery wierszy" do niego i naciskając klawisz Enter. Jest to najszybszy sposób, aby przejść do **opcje** wpis okna, gdzie można włączyć numery wierszy. Dowiedz się, jak używać **Szybkie uruchamianie** paska i zaoszczędzić mnóstwo kliknięć interfejsu użytkownika!)

 ![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Visual Studio liczbami opcji](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Użyj klawiszy Ctrl + G, aby szybko przechodzić do numer wiersza w którym wystąpił błąd.

 Ten błąd jest identyfikowany przez czerwony znak podkreślenia "Zygzakowata". Umieść kursor nad jej, aby uzyskać więcej informacji. Wprowadzić poprawki i jego znikną, chociaż może powodować nowy błąd z korekty. (Jest to nazywane "regresji").

 ![Visual Studio błąd po wskazaniu wskaźnikiem](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Omówimy listę błędów i naprawić wszystkie błędy w kodzie.

 ![Visual Studio debugować błędy okna](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Przeglądanie błędy szczegółowe
 Wiele błędów może nie ma sensu dla Ciebie ma inną pisownię, są one w warunkach użytkowania kompilator. W takich przypadkach należy uzyskać dodatkowe informacje. Z **lista błędów** okna, możesz zrobić automatyczne wyszukiwanie Bing, aby uzyskać więcej informacji na temat błędu (lub ostrzeżenia), kliknij prawym przyciskiem myszy w odpowiednim wierszu wejścia i wybierając polecenie **Pokaż Pomoc błędu** z menu kontekstowe.

 ![Lista błędów w usłudze Visual Studio wyszukiwania Bing](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Spowoduje to uruchomienie kartę wewnątrz programu Visual Studio 2015, hosty wyniki Bing Wyszukaj kod błędu i tekst. Wyniki są z różnych źródeł w Internecie, a nie wszystkie dane mogą być pomocne.

 Alternatywnie możesz kliknąć wartość kodu błędu hiperłącza w **kodu** kolumny **lista błędów**. Spowoduje to uruchomienie wyszukiwanie Bing tylko kod błędu.

### <a name="performing-static-code-analysis"></a>Wykonywanie analizy kodu statycznego
 "Statycznej analizy kodu" jest ozdobnych sposobem powiedzenia "Automatycznie sprawdzaj mój kod dla typowych problemów, które mogą prowadzić do błędów czasu wykonywania lub problemy w zarządzaniu kodu". W celu przejrzenia ją uruchomić, gdy zostały wyczyszczone oczywiste błędy, co uniemożliwia kompilacji i, co pewien czas do rozwiązania ostrzeżeń, które może ona generować. Będziesz zaoszczędzić kilka problemów występujących, a także Dowiedz się, kilka technik stylu kodu.

 Naciśnij klawisze Alt + F11 (lub wybierz **Analiza -> Uruchom analizę kodu dla rozwiązania** z górnego menu) można rozpocząć analizy kodu statycznego. Może potrwać trochę czasu, jeśli masz duże ilości kodu.

 ![Element menu w usłudze Visual Studio 2015 Code Analysis](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Wszelkie ostrzeżenia nowych lub zaktualizowanych pojawi się w **lista błędów** karta w dolnej części IDE. Polecenie ostrzeżenia, aby przejść do nich.

 ![Visual Studio 2015 listy błędów z ostrzeżeniami](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Ostrzeżenia zostaną zidentyfikowane przy użyciu wyraziste wężyk żółty zielony zamiast czerwonego. Umieść kursor nad nimi, aby uzyskać więcej szczegółów, a następnie kliknij prawym przyciskiem myszy na ich w celu uzyskania menu kontekstowym, aby pomóc w poprawki lub opcje refaktoryzacji.

 ![Wizualne umieść ostrzeżenie analizy kodu Studio](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Za pomocą ikon żarówek Aby naprawić lub refaktoryzacji kodu
 Ikony żarówek są nową funkcją programu Visual Studio 2015, które umożliwiają Refaktoryzuj kod inline. Są one prosty sposób, aby rozwiązać typowe ostrzeżenia szybko i skutecznie. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy na wężyk ostrzeżenie (lub naciśnij klawisze Ctrl +. Podczas przesuwania wskaźnika w obrębie wężyk), a następnie wybierz pozycję **szybkie akcje**.

 ![Visual Studio 2015 żarówki Kreatora szybkich](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Zostanie wyświetlona lista możliwych poprawki lub refactors, które można zastosować do tego wiersza kodu.

 ![Visual Studio 2015, okno żarówka — Podgląd](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Żarówki może służyć wszędzie tam, gdzie określić analizatorów kodu, jest możliwość rozwiązać problem, Refaktoryzacja, lub poprawić kod. Kliknij pozycję w każdym wierszu kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **szybkich** (ewentualnie ponownie, jeśli wolisz wydajność, naciśnij klawisze Ctrl +.). Jeśli obszar dostępne opcje refaktoryzacji lub ulepszenia, będą one wyświetlane; w przeciwnym razie komunikat `No quick options available here` będą wyświetlane w ramką lewego dolnego rogu IDE.

 ![Visual Studio 2015 pomysłów żadnej opcji tekst](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Za pomocą środowiska szybko można użyć klawiszy strzałek oraz klawiszy Ctrl +. Sprawdź, czy opcja szybkie możliwości refaktoryzacji i wyczyścić kod!

 Aby uzyskać więcej informacji na temat żarówki, przeczytaj [szybkie wykonywanie akcji dzięki żarówkom](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Debugowanie kodu uruchamiania
 Teraz, po pomyślnym utworzeniu kodu i wykonać nieco czyszczenia, uruchom ją, naciskając klawisz F5 lub wybierając **Debuguj -> Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, dzięki czemu możesz obserwować jego zachowanie szczegółowo. Visual Studio 2015 IDE zmienia się po uruchomieniu aplikacji: **dane wyjściowe** okna zastępuje dwóch nowych komentarzy (w oknie Konfiguracja domyślna), **Autos/zmienne lokalne/modułów/Obejrzyj** okien z kartami i **Wywołanie wyjątku-stosu/punktów przerwania ustawienia/Output** okien z kartami. Te okna mają wiele kart, które pozwalają na sprawdzanie i oceny aplikacji zmiennych, wątki, stosy wywołań i różnych innych zachowań podczas jej działania.

 ![VS2015 Zmiennych automatycznych i wywołanie stosu Windows](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Wypróbuj różne akcje ze swoją aplikacją i obserwować zmiany. Jeśli pojawi się coś nietypowe, wstrzymać aplikacji, naciskając klawisze Ctrl + Alt + Break (lub kliknąć **wstrzymać** przycisk).

 ![Visual Studio Przerwij wszystko przycisk](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Naciśnij klawisz F5, aby kontynuować, uruchamiając aplikację (lub kliknij przycisk **Kontynuuj** przycisk).

 ![Visual Studio debugowanie nadal przycisk](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Możesz zatrzymać aplikację, naciskając klawisz Shift + F5 lub klikając **zatrzymać** przycisku. Alternatywnie możesz po prostu zamknąć główne okno aplikacji (lub okno wiersza polecenia).

 Jeżeli kod działa bez zarzutu i dokładnie tak jak oczekiwano, Gratulacje! Zmień konfigurację kompilacji, aby **wersji** i odbuduj go do wdrożenia! (Może chcieć szybkiego dostępu do bitu na testy jednostkowe na końcu, mimo że specjalistów). Jednak jeśli nieuruchamianie lub uległ awarii lub udostępniła Ci niektóre dziwne wyniki, należy znaleźć źródło tych problemów i naprawiania błędów.

### <a name="setting-simple-breakpoints"></a>Ustawianie punktów przerwania prosty
 Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu. NIE trzeba ponownie skompiluj projekt po ustawiania i usuwania punktów przerwania.

 Ustaw punkt przerwania, klikając w końcu margines linii, na którym ma przerwanie wystąpią, lub wybierz linii kodu i naciśnij klawisz F9. Kiedy uruchamiasz swój kod, zatrzyma się, zanim wykonywane są instrukcje dotyczące ten wiersz kodu.

 ![Visual Studio breakpoint](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Gdy kod zostanie przerwany, oznaczony wiersz kodu nie ma jeszcze wykonane. W tym momencie możesz wykonać instrukcje dotyczące wiersza kodu, oznaczony przez punkt przerwania i sprawdzić zmienionymi wartościami. Jest to nazywane "Przechodzenie do" kodu. Oznaczone kodu w przypadku wywołania metody, można było do niego przejść, naciskając klawisz F11. Użytkownik może również "Przekrocz nad" wiersz kodu, naciskając klawisz F10. Aby uzyskać szczegółowe informacje na temat akcje kroku punktu przerwania, przeczytaj [nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md).

 Najczęstsze zastosowania dla punktów przerwania obejmują:

1. Aby zawęzić źródło awarię lub zawieszenie, wykres punktowy je w całej i wokół kodu wywołania metody, które Twoim zdaniem jest przyczyną błędu. Jak krok po kroku przez kod, Usuń, a następnie zresetuj punktów przerwania bliżej razem do momentu znalezienia naruszającym wierszem kodu.

2. Po wprowadzeniu nowego kodu, należy ustawić punkt przerwania na początku i Przechodź przez kod, aby upewnić się, że zachowuje się zgodnie z oczekiwaniami.

3. Jeśli zaimplementowano skomplikowane zachowanie, ustaw punktów przerwań dla kodu algorytmicznego, dzięki czemu można sprawdzić wartości zmiennych i danych, kiedy program przerywa.

4. Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać wykonywanie kodu, dzięki czemu można sprawdzić wartości adresów (Zwróć uwagę na wartość NULL) i liczby odwołań podczas debugowania błędów związanych z pamięcią.

   Aby uzyskać więcej informacji na temat korzystania z punktów przerwania, przeczytaj [przy użyciu punktów przerwania](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Ustawienie warunkowe punkty przerwania
 Jeśli masz punkt przerwania w pętli lub rekursji lub masz wiele punktów przerwania, które często krokowo, należy użyć warunkowego punktu przerwania, aby upewnić się, że Twój kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki. W przeciwnym razie użytkownik będzie można naciskając klawisz F11 często są bardzo wiele.

 Aby ustawić warunkowego punktu przerwania i zawiesić kodu, gdy zmienna jest równa określonej wartości lub przekazuje określonego progu, kliknij na marginesie, aby ustawić punkt przerwania, a następnie wybierz pozycję "koło zębate" z menu po wskazaniu wskaźnikiem, które pojawia się.

 ![Ustawienia punktu przerwania w usłudze Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Pojawi się okno dialogowe, które wygląda w następujący sposób gdzie ustawić określone warunki nastąpić przerwanie.

 ![Visual Studio 2015, warunkowe przerwania](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Aby uzyskać więcej informacji na temat sposobu deklarowania wyrażenia używane do oceny, warunkowe punkty przerwania, zapoznaj się z wideo w witrynie Channel9 [środowisko konfiguracji punktów przerwania w programie Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania
 Kiedy uruchomiony kod uderza w punkt przerwania i zostanie zatrzymana, można sprawdzić zmiennych i Wywołaj stosy, aby ustalić, co się dzieje. Są wartości z zakresów, które powinny być widoczne? Są wykonywane w odpowiedniej kolejności wywołań?

 ![Uruchom program Visual Studio 2015&#45;czasu inspekcja wartości](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Umieść kursor nad zmienną, aby wyświetlić wartości i odwołania, które obecnie znajdują. Jeśli widzisz wartość, którą Nieoczekiwane wyrażenie, prawdopodobnie masz usterkę w poprzednim lub wywoływania wierszy kodu. Przenieś w górę punktów przerwania lub dodawanie warunków do istniejących punktów przerwania, aby zawęzić wyszukiwanie.

 Ponadto program Visual Studio 2015 Wyświetla okno narzędzia diagnostyczne, w którym możesz obserwować zużycie pamięci i procesora CPU w Twojej aplikacji wraz z upływem czasu. Użyj ich do wyszukania nieprzewidziane duże obciążenie lub pamięć alokacji Procesora. Używane w połączeniu z **Obejrzyj** okien i punkty przerwania, aby sprawdzić, co powoduje nieoczekiwany duże obciążenie lub niewydany zasobów.

 ![Visual Studio 2015 Diagnostic Tools okna](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Uruchamianie testów jednostkowych
 Testy jednostkowe są programy, które wykonuje ścieżek kodu w aplikacji lub usługi. Program Visual Studio 2015 instaluje struktur testowania jednostek pochodzących od firmy Microsoft dla kodu zarządzanego i natywnego. Testowania jednostkowego umożliwia tworzenie testów jednostkowych, uruchamiaj je i raportuje o wynikach tych testów. Jednostka ponownie uruchom testy przy wprowadzaniu zmian do testowania, Twój kod nadal działa poprawnie. Gdy używasz programu Visual Studio 2015 Enterprise, można uruchomić testy automatyczne po każdej kompilacji.

 Aby rozpocząć pracę, przeczytaj [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Aby dowiedzieć się więcej na temat testów jednostkowych w Visual Studio 2015 i jak mogą one pomóc tworzyć lepszy kod jakości, przeczytaj [o teście jednostkowym](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md) [debugera, ustawienia i przygotowania](../debugger/debugger-settings-and-preparation.md) [debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md) [podstawowe informacje o debugerze](../debugger/debugger-basics.md)
