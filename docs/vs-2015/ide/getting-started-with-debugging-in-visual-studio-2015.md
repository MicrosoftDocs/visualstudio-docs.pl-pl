---
title: Wprowadzenie z debugowaniem w programie Visual Studio 2015 | Microsoft Docs
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
ms.openlocfilehash: ca3f3806f9097082d71dd80e74ccf48cd78c951b
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386891"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Wprowadzenie do debugowania w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio 2015 zapewnia zaawansowany zintegrowany zestaw narzędzi do kompilowania i debugowania projektu. W tym temacie dowiesz się, jak zacząć korzystać z najbardziej podstawowego zestawu funkcji interfejsu użytkownika debugowania.

 Uwaga: linki do bardziej zaawansowanych funkcji i tematów dotyczących platformy lub funkcji znajdują się w dolnej części tej strony.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Mój kod nie działa. Pomóż mi, Visual Studio 2015!
 W związku z tym, że znasz Edytor i został utworzony jakiś kod. Teraz chcesz rozpocząć debugowanie tego kodu. W programie Visual Studio 2015, podobnie jak w przypadku większości środowisk IDE, istnieją dwie fazy debugowania: kompilowanie kodu do przechwytywania i rozwiązywanie błędów projektów i kompilatora; i uruchamiając ten kod w środowisku, aby przechwytywać i rozwiązywać problemy w czasie wykonywania i błędy dynamiczne.

### <a name="configuring-a-build"></a>Konfigurowanie kompilacji
 Istnieją dwa podstawowe typy konfiguracji kompilacji: **debugowanie** i **wydanie**. Pierwsza konfiguracja tworzy wolniejszy, większy plik wykonywalny, który umożliwia bogatsze interaktywne środowisko debugowania w czasie wykonywania, ale nigdy nie powinno być wysyłane. Drugi kompiluje szybszy i bardziej zoptymalizowany plik wykonywalny, który jest odpowiedni do dostarczenia (co najmniej z perspektywy kompilatora).

 Domyślną konfiguracją kompilacji jest **debugowanie**.

 ![Przycisk kompilacji debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Można również określić konkretną platformę kompilacji, która ma być docelowa, na przykład **x86** (32-bitowe procesory Intel), **x64** (64-bitowe procesory Intel) i **ARM** (procesory ARM, obsługiwane tylko dla niektórych typów aplikacji). Wartość domyślna to **x86** dla projektów zarządzanych i natywnych. Aby to zmienić, kliknij listę rozwijaną platforma kompilacji i wybierz inną platformę lub **Configuration Manager...**

 ![Okno Menedżera plików konfiguracji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Możesz określić dodaną konfigurację kompilacji przy użyciu **Configuration Manager**. Uruchom ją, kliknij **konfigurację** lub listę rozwijaną **procesora** , a następnie wybierz pozycję **Nowy...** Aby utworzyć nową kompilację lub platformę.

 ![Okno Configuration Manager programu Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Począwszy od wersji, należy odpowiednio używać **debugowania** i **architektury x86** jako konfiguracji kompilacji i platformy. Po zakończeniu kodowania i debugowania Zmień konfigurację, aby **zwolnić** i wskazać konkretną platformę. (Starsze wersje programu Visual Studio udostępniają domyślną platformę usługi **AnyCPU** dla projektów kodu platformy .NET).

 Uwaga: podczas kompilowania projektu wartości konfiguracji i platformy są również używane do określania, jaka ścieżka katalogu projektu została utworzona w celu przechowywania pliku wykonywalnego. Typowo, jest to ** \<path-to-project> \\<\> \\<konfiguracji \> \\<platformy \> **. Na przykład projekt z konfiguracją `Debug` i platformą `x86` można znaleźć w sekcji `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86` . Może to być przydatne, jeśli masz własne narzędzia lub skrypty zarządzające tymi skompilowanymi plikami wykonywalnymi.

### <a name="building-your-code"></a>Kompilowanie kodu
 Gdy Twoja kompilacja została skonfigurowana, czas na faktyczne skompilowanie projektu. Najprostszym sposobem wykonania tej czynności jest naciśnięcie klawisza F7, ale można również uruchomić kompilację, wybierając opcję **Kompiluj->Kompiluj rozwiązanie** z menu głównego.

 ![Wybór menu projektu kompilacji programu Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Można obserwować proces kompilacji w oknie stanu **danych wyjściowych** w dolnej części interfejsu użytkownika programu Visual Studio. Błędy, ostrzeżenia i operacje kompilacji są wyświetlane w tym miejscu. Jeśli występują błędy (lub jeśli masz ostrzeżenia powyżej skonfigurowanego poziomu), kompilacja zakończy się niepowodzeniem. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiły. Odbuduj projekt, naciskając ponownie klawisz **F7** (w celu ponownego skompilowania tylko plików z błędami) lub **Ctrl + Alt + F7** (w przypadku czystej i kompletnej odbudowy).

 W oknie wyników znajduje się dwa okna kompilacji z kartami: okno **dane wyjściowe** , które zawiera nieprzetworzone dane wyjściowe kompilatora (w tym komunikaty o błędach); i okno **Lista błędów** , które udostępnia listę wszystkich błędów i ostrzeżeń z możliwością sortowania i filtrowania.

 Po pomyślnym wykonaniu tych operacji w oknie **danych wyjściowych** zostaną wyświetlone wyniki podobne do tego.

 ![Pomyślne Kompilowanie danych wyjściowych programu Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Przeglądanie Lista błędów
 Jeśli nie wprowadzono żadnych modyfikacji kodu, który został wcześniej utworzony i pomyślnie skompilowany, prawdopodobnie wystąpił błąd. Jeśli dopiero zaczynasz kodowanie, prawdopodobnie masz wiele z nich. Błędy są czasami oczywiste, takie jak prosty błąd składniowy lub niepoprawna nazwa zmiennej, a czasami są trudne do zrozumienia, tylko kod tajemnicze, który poprowadzi Cię przez Ciebie. Aby zapoznać się z bardziej czytelnym widokiem problemów, przejdź do dolnej części okna **dane wyjściowe** kompilacji i kliknij kartę **Lista błędów** . Spowoduje to przejście do bardziej zorganizowanego widoku błędów i ostrzeżeń dotyczących projektu, a także udostępnia pewne dodatkowe opcje.

 ![Dane wyjściowe i Lista błędów programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 Kliknij wiersz błędu w oknie **Lista błędów** i przejdź do wiersza, w którym występuje błąd. (Lub Włącz numery wierszy, klikając pasek **Szybkie uruchamianie** w prawym górnym rogu, wpisując ciąg "numery wierszy" i naciskając klawisz ENTER. Jest to najszybszy sposób, aby przejść do pozycji okna **opcji** , w której można włączyć numery wierszy. Dowiedz się, jak korzystać z paska **szybkiego uruchamiania** i zapisywać wiele kliknięć interfejsu użytkownika!)

 ![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Opcja numerów wierszy programu Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Użyj klawiszy CTRL + G, aby szybko przejść do numeru wiersza, w którym wystąpił błąd.

 Błąd jest identyfikowany przez czerwoną podkreślenie "zygzaka". Umieść kursor nad nim, aby uzyskać dodatkowe informacje. Wprowadź poprawkę i przejdziemy do niej, chociaż możesz wprowadzić nowy błąd przy korekcie. (Jest to nazywane "regresją").

 ![Aktywowanie błędu programu Visual Studio](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Zapoznaj się z listą błędów i zapoznaj się ze wszystkimi błędami w kodzie.

 ![Okno błędów debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Szczegółowe przeglądanie błędów
 Wiele błędów może nie mieć sensu, ponieważ są one w warunkach kompilatora. W takich przypadkach konieczne będzie dodanie dodatkowych informacji. W oknie **Lista błędów** można wykonać automatyczne wyszukiwanie Bing, aby uzyskać więcej informacji na temat błędu (lub ostrzeżenia), klikając prawym przyciskiem myszy odpowiedni wiersz wejścia i wybierając pozycję **Pokaż pomoc dotyczącą błędów** z menu kontekstowego.

 ![Wyszukiwanie Bing na liście błędów programu Visual Studio](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Spowoduje to uruchomienie karty w programie Visual Studio 2015, która obsługuje wyniki wyszukiwania w usłudze Bing dla kodu błędu i tekstu. Wyniki pochodzą z wielu różnych źródeł w Internecie, a nie wszystkie mogą być pomocne.

 Alternatywnie możesz kliknąć wartość kod błędu z linkiem w kolumnie **kod** **Lista błędów**. Spowoduje to uruchomienie wyszukiwania Bing tylko dla kodu błędu.

### <a name="performing-static-code-analysis"></a>Wykonywanie statycznej analizy kodu
 "Analiza kodu statycznego" to ozdobny sposób wymawiania "automatycznie sprawdzaj mój kod pod kątem typowych problemów, które mogą prowadzić do błędów lub problemów w czasie wykonywania w usłudze Code Management". Zapoznaj się z wykonywaćem, aby uruchomić go po wyczyszczeniu oczywistych błędów, które uniemożliwiają kompilację, i Poświęć trochę czasu na wygenerowanie ostrzeżeń. Zarządzaniem mu towarzyszą się z nim, a także poznasz kilka technik stylu kodu.

 Naciśnij klawisze ALT + F11 (lub wybierz polecenie **Analizuj->Uruchom analizę kodu w rozwiązaniu** z górnego menu), aby rozpocząć analizę kodu statycznego. Może to potrwać trochę czasu, jeśli masz wiele kodu.

 ![Element menu analizy kodu dla programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Wszystkie nowe lub zaktualizowane ostrzeżenia pojawią się na karcie **Lista błędów** w dolnej części IDE. Kliknij ostrzeżenia, aby przejść do nich.

 ![Program Visual Studio 2015 Lista błędów z ostrzeżeniami](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Ostrzeżenia będą identyfikowane przy użyciu jasnego żółtego, zielonego, a nie czerwonego. Umieść kursor nad nimi, aby uzyskać więcej szczegółów, a następnie kliknij prawym przyciskiem myszy, aby uzyskać menu kontekstowe pomocne w poprawkach lub opcjach refaktoryzacji.

 ![Visual Studio Code aktywowania ostrzeżenia analizy](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Korzystanie z żarówki do naprawy lub refaktoryzacji kodu
 Żarówki są nową funkcją dla programu Visual Studio 2015, która umożliwia refaktoryzację kodu w tekście. Są one łatwym sposobem szybkiego i efektywnego rozwiązywania typowych ostrzeżeń. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy ostrzeżenie Zygzak (lub naciśnij klawisze CTRL +). Po umieszczeniu nad nimi wskaźnika myszy, a następnie wybierz polecenie **szybkie akcje**.

 ![Szybkie opcje dla żarówki programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Zostanie wyświetlona lista możliwych poprawek lub refaktoryzacji, które można zastosować do tego wiersza kodu.

 ![Visual Studio 2015 Light żarówka — wersja zapoznawcza](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Żarówki można używać wszędzie tam, gdzie analizatory kodu decydują o sposobach naprawy, refaktoryzacji lub ulepszania kodu. Kliknij dowolny wiersz kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz opcję **szybkie opcje** (lub, jeśli wolisz, naciśnij klawisze CTRL +). Jeśli dostępne są opcje refaktoryzacji obszaru lub ulepszeń, zostaną one wyświetlone. w przeciwnym razie wiadomość `No quick options available here` zostanie wyświetlona w lewym dolnym rogu IDE.

 ![Tekst "Brak opcji" dla żarówki programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Korzystając z funkcji, możesz szybko użyć klawiszy strzałek i klawiszy CTRL +. Aby sprawdzić możliwości szybkiego refaktoryzacji opcji i oczyścić kod!

 Aby uzyskać więcej informacji o żarówkach, przeczytaj temat [wykonywanie szybkich akcji z żarówkami](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Debugowanie uruchomionego kodu
 Teraz, po pomyślnym skompilowaniu kodu i wykonaniu nieco czyszczenia, uruchom go, naciskając klawisz F5 lub wybierając polecenie **Debuguj->Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, aby można było obserwować jej zachowanie szczegółowo. Środowisko IDE programu Visual Studio 2015 zmienia się podczas działania aplikacji: okno **dane wyjściowe** jest zastępowane dwoma nowymi (w konfiguracji okna domyślnego), okna elementy **Autostart/lokalne/moduły/Watch** z kartami oraz **stos wywołań/punktów przerwania/ustawienia wyjątku/wyjściowe** okno z kartami. Te okna mają wiele kart, które umożliwiają sprawdzanie i ocenianie zmiennych aplikacji, wątków, stosów wywołań i różnych innych zachowań w miarę ich działania.

 ![PROGRAMU VS2015 i okna stosu wywołań](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Wypróbuj różne działania z aplikacją i obserwuj zmiany. Jeśli coś występuje nietypowe, Wstrzymaj aplikację, naciskając klawisze CTRL + ALT + BREAK (lub klikając przycisk **pauza** ).

 ![Przycisk Przerwij wszystko w programie Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Naciśnij klawisz F5, aby kontynuować uruchamianie aplikacji (lub kliknij przycisk **Kontynuuj** ).

 ![Przycisk Kontynuuj debugowania programu Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Aby zatrzymać aplikację, naciśnij klawisze Shift + F5 lub klikając przycisk **Zatrzymaj** . Możesz też po prostu zamknąć okno główne aplikacji (lub okno dialogowe wiersza polecenia).

 Jeśli kod działa doskonale i dokładnie zgodnie z oczekiwaniami, gratulacje! Zmień konfigurację kompilacji, aby **zwolnić** i skompilować ją w celu wdrożenia. (Specjaliści mogą chcieć przeskoczyć do bitu testów jednostkowych na końcu, chociaż). Jeśli jednak przestanie ona odpowiadać lub uległa awarii lub podała pewne dziwne wyniki, należy znaleźć źródło tych problemów i naprawić błędy.

### <a name="setting-simple-breakpoints"></a>Ustawianie prostych punktów przerwania
 Punkty przerwania są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana. NIE jest konieczne ponowne kompilowanie projektu po ustawieniu i usunięciu punktów przerwania.

 Ustaw punkt przerwania, klikając górny margines linii, w której ma nastąpić przerwanie, lub zaznacz wiersz kodu, a następnie naciśnij klawisz F9. Po uruchomieniu kodu zostanie on zatrzymany przed wykonaniem instrukcji dla tego wiersza kodu.

 ![Punkt przerwania programu Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Gdy kod jest podzielony, oznaczony wiersz kodu nie został jeszcze wykonany. W tym momencie możesz chcieć wykonać instrukcje dotyczące wiersza kodu oznaczonego przez punkt przerwania i sprawdzić zmienione wartości. Jest to tzw. "krok po kroku". Jeśli oznaczony kod jest wywołaniem metody, możesz przejść do niego, naciskając klawisz F11. Możesz również "przekroczyć" linię kodu, naciskając klawisz F10. Aby uzyskać więcej informacji na temat akcji krok przerwania, przeczytaj temat [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

 Typowe zastosowania punktów przerwania to:

1. Aby zawęzić Źródło awarii lub programu, który nie odpowiada, należy przetworzyć je w całym i dookoła kodzie wywołania metody, które Twoim zdaniem jest przyczyną błędu. Po przekroczeniu kodu, Usuń, a następnie zresetuj punkty przerwania bliżej siebie do momentu znalezienia niezgodnego wiersza kodu.

2. Gdy wprowadzasz nowy kod, ustaw punkt przerwania na początku go i przechodzenie przez kod, aby upewnić się, że działa zgodnie z oczekiwaniami.

3. Jeśli zaimplementowano skomplikowane zachowanie, ustaw punkty przerwania dla kodu algorytmu, aby można było sprawdzić wartości zmiennych i danych w przypadku przerwania działania programu.

4. Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać kod, tak aby można było sprawdzać wartości adresu (poszukiwania wartości NULL) i liczby odwołań podczas debugowania błędów związanych z pamięcią.

   Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj temat [Używanie punktów przerwania](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Ustawianie warunkowych punktów przerwania
 Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które są często wykonywane, użyj warunkowego punktu przerwania, aby upewnić się, że kod jest zawieszony tylko wtedy, gdy spełnione są określone warunki. W przeciwnym razie nastąpi naciśnięcie klawisza F11 a Awful.

 Aby ustawić warunkowy punkt przerwania i zawiesić swój kod, gdy zmienna jest ustawiona na określoną wartość lub przekazuje określony próg, kliknij na marginesie, aby ustawić punkt przerwania, a następnie wybierz pozycję "koło zębate" w wyświetlonym menu aktywowanym.

 ![Ustawienia punktu przerwania programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Zobaczysz okno dialogowe, które wygląda jak w tym miejscu, w którym można ustawić określone warunki dla przerwy.

 ![Warunkowy punkt przerwania programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Aby uzyskać szczegółowe informacje na temat sposobu deklarowania wyrażeń używanych do obliczania warunkowych punktów przerwania, zapoznaj się z tematem [Konfiguracja punktu przerwania wideo channel9 w programie Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania
 Gdy uruchomiony kod trafi punkt przerwania i zatrzymuje, można sprawdzić zmienne i wywoływać stosy, aby określić, co się dzieje. Czy wartości w zakresach powinny być widoczne? Czy wywołania są wykonywane w odpowiedniej kolejności?

 ![Inspekcja wartości czasu w programie Visual Studio 2015&#45;](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Umieść kursor nad zmienną, aby wyświetlić wartości i odwołania, które aktualnie zawiera. Jeśli zobaczysz nieoczekiwaną wartość, prawdopodobnie masz usterkę w powyższym lub wywoływanym wierszu kodu. Przenieś punkty przerwania w górę lub Dodaj warunki do istniejących punktów przerwania, aby jeszcze bardziej zawęzić wyszukiwanie.

 Ponadto program Visual Studio 2015 wyświetla okno narzędzia diagnostyczne, w którym można obserwować użycie procesora i pamięci przez aplikację w czasie. Skorzystaj z nich, aby wyszukać nieprzewidziane duże użycie procesora CPU lub alokację pamięci. Użyj go w połączeniu z oknem **czujki** i punktem przerwania, aby określić, co powoduje nieoczekiwane użycie lub niewykorzystane zasoby.

 ![Okno narzędzia diagnostyczne programu Visual Studio 2015](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Uruchamianie testów jednostkowych
 Testy jednostkowe są programami, które wykonują ścieżki kodu w aplikacji lub usłudze. Program Visual Studio 2015 instaluje platformy testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Użyj struktury testów jednostkowych, aby utworzyć testy jednostkowe, uruchomić je i zgłosić wyniki tych testów. Ponownie uruchom testy jednostkowe, gdy wprowadzisz zmiany w celu przetestowania, że kod nadal działa poprawnie. W przypadku korzystania z programu Visual Studio 2015 Enterprise można uruchomić testy automatycznie po każdej kompilacji.

 Aby rozpocząć, przeczytaj artykuł [generowanie testów jednostkowych dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Aby dowiedzieć się więcej o testach jednostkowych w programie Visual Studio 2015 i jak mogą one pomóc w tworzeniu lepszej jakości kodu, Przeczytaj [podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie w ustawieniach debugera programu Visual Studio](../debugger/debugging-in-visual-studio.md) [i debugowanie przygotowania](../debugger/debugger-settings-and-preparation.md) [64-bitowe —](../debugger/debug-64-bit-applications.md) [podstawowe informacje o debugerze](../debugger/debugger-basics.md)
