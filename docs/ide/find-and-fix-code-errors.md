---
title: Napraw błędy programu i poprawienia kodu
description: W tym artykule opisano niektóre podstawowe sposoby programu Visual Studio może pomóc znajdowania i rozwiązywania problemów w kodzie, w tym błędy kompilacji analizy kodu, narzędzi i testy jednostkowe debugowania.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43be698fd908737c96f9de3cf346b48e84f27fc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59504461"
---
# <a name="make-code-work-in-visual-studio"></a>Kodu, pracy w programie Visual Studio

Program Visual Studio zapewnia bogaty zestaw zintegrowanych kompilacja projektu i narzędzi do debugowania. W tym artykule Dowiedz się, jak Visual Studio może pomóc problemów możesz znaleźć w kodzie przy użyciu danych wyjściowych kompilacji analizy kodu, narzędzi do debugowania i testów jednostkowych.

Po zapewnieniu edytora i utworzony jakiś kod. Teraz chcesz upewnij się, że kod działa poprawnie. W programie Visual Studio, podobnie jak w przypadku większości środowisk IDE, są dwie fazy znaczenie kodu: kod, aby przechwycić i usuń błędy projektu i kompilatora kompilowania i uruchamiania kodu, aby znaleźć błędy czasu wykonywania i dynamicznych.

## <a name="build-your-code"></a>Tworzenie kodu

Istnieją dwa podstawowe rodzaje konfiguracji kompilacji: **Debugowanie** i **wersji**. **Debugowania** konfiguracja daje wolniej, większy plik wykonywalny, który umożliwia bogatszych interaktywne środowisko debugowania środowiska wykonawczego. **Debugowania** plik wykonywalny nigdy nie powinny być wysyłane. **Wersji** konfiguracji kompilacji szybciej i zoptymalizowany plik wykonywalny, który jest odpowiedni do wysłania (co najmniej z punktu widzenia kompilatora). W domyślnej konfiguracji kompilacji **debugowania**.

Najprostszym sposobem utworzenia projektu jest naciśnięcie **F7**, ale można również uruchomić kompilację, wybierając **kompilacji** > **Kompiluj rozwiązanie** z menu głównego.

![Wybór menu projektu kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Możesz obserwować proces kompilacji w **dane wyjściowe** okna w dolnej części interfejsie użytkownika programu Visual Studio. W tym miejscu są wyświetlane błędy, ostrzeżenia i operacji kompilacji. Jeśli masz błędów (lub w przypadku ostrzeżenia wyższym poziomie skonfigurowany) kompilacja kończy się niepowodzeniem. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiło. Ponownie skompiluj projekt, albo naciskając **F7** ponownie (, aby ponownie skompilować tylko te pliki z błędami) lub **Ctrl**+**Alt**+**F7**  (dla przejrzystości oraz pełną ponowną kompilację).

Istnieją dwa okien z zakładkami w oknie wyników poniżej edytora: **dane wyjściowe** okno, które zawiera kompilator nieprzetworzonych danych wyjściowych (w tym komunikaty o błędach); i **lista błędów** okno, które zawiera Sortowanie i filtrowanie listę wszystkich błędów i ostrzeżeń.

Jeśli kompilacja zakończy się pomyślnie, zobaczysz wyniki, tak jak poniżej w **dane wyjściowe** okna:

![Wyjścia udanej kompilacji usługi Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Przejrzyj listę błędów

O ile nie wprowadzono żadnych modyfikacji kodu, który została wcześniej i pomyślnie skompilowana, prawdopodobnie wystąpił błąd. Jeśli jesteś nowym użytkownikiem kodowania, masz prawdopodobnie wiele z nich. Błędy są czasami oczywiste, takie jak błąd prostą składnię lub nieprawidłowa nazwa zmiennej, a czasami są trudne do zrozumienia, z pozoru kodem przeprowadzenie Cię. Widok oczyszczarki problemów, przejdź do dolnej części kompilacji **dane wyjściowe** okna, a następnie kliknij przycisk **lista błędów** kartę. Przejście do bardziej zorganizowane widoku błędów i ostrzeżeń dotyczących projektu i zapewnia pewne dodatkowe opcje.

![Dane wyjściowe programu Visual Studio i lista błędów](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknij wiersz błędu w **lista błędów** odbywa się w oknie, aby przejść do wiersza błędu. (Lub włączyć numery wierszy, naciskając klawisz **Ctrl**+**pytania**, wpisz **numery wierszy**, a następnie wybierając **włączyć numery wierszy, lub wyłączyć**z wyników. Jest to najszybszy sposób, aby przejść do **opcje** okna dialogowego, w którym można włączyć numery wierszy.)

![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opcja numery wiersza w usłudze Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Naciśnij klawisz **Ctrl**+**G** można szybko przechodzić do numer wiersza w którym wystąpił błąd.

Ten błąd jest identyfikowany przez czerwony znak podkreślenia "Zygzakowata". Umieść kursor nad jej, aby uzyskać więcej informacji. Wprowadzić poprawki i jego znikną, chociaż może powodować nowy błąd z korekty. (Jest to nazywane "regresji").

![Visual Studio error hover](../ide/media/vs_ide_gs_debug_error_hover1.png)

Omówimy listę błędów i naprawić wszystkie błędy w kodzie.

![Visual Studio debugować błędy okna](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Przejrzyj błędy szczegółowe

Wiele błędów może nie ma sensu dla Ciebie ma inną pisownię, są one w warunkach użytkowania kompilator. W takich przypadkach należy uzyskać dodatkowe informacje. Z **lista błędów** okna, możecie automatyczne wyszukiwanie Bing, aby uzyskać więcej informacji na temat błędu lub ostrzeżenia. Kliknij prawym przyciskiem myszy w odpowiednim wierszu wpis, a następnie wybierz pozycję **Pokaż Pomoc błędu** z menu kontekstowego lub kliknij wartość kodu błędu hiperłącza w **kodu** kolumny **lista błędów**.

![Lista błędów w usłudze Visual Studio wyszukiwanie Bing](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

W zależności od ustawień przeglądarki sieci web wyświetla wyniki wyszukiwania dla kodu błędu i tekstu albo karcie zostanie otwarta w programie Visual Studio i przedstawiono wyniki wyszukiwania Bing. Wyniki są z różnych źródeł w Internecie, a nie wszystkie dane mogą być pomocne.

## <a name="use-code-analysis"></a>Użyj analizy kodu

Analizatorów kodu szukać typowych problemów z kodu, które mogą prowadzić do błędów czasu wykonywania lub problemy z zarządzania kodem.

### <a name="c-and-visual-basic-code-analysis"></a>C#i analiza kodu języka Visual Basic

Program Visual Studio zawiera zestaw wbudowanych [analizatory platformie kompilatora .NET](../code-quality/roslyn-analyzers-overview.md) , sprawdź C# i kodu języka Visual Basic podczas typu. Można zainstalować dodatkowe analizatorów, jako rozszerzenie programu Visual Studio lub jako pakiet NuGet. Jeśli zostaną znalezione naruszeń zasady, są zgłaszane zarówno w edytorze kodu jako falista pod kodem powodujący problemy, a w **lista błędów**.

### <a name="c-code-analysis"></a>Analiza kodu C++

Do analizowania kodu w języku C++, należy uruchomić [statycznej analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md). Pobierz w celu przejrzenia ją uruchomić, gdy zostały wyczyszczone oczywiste błędów, które zapobiegania pomyślnej kompilacji i zająć trochę czasu, aby rozwiązać ostrzeżeń, które może ona generować. Zaoszczędzisz samodzielnie niektórych problemów występujących i mogą dowiedzieć się kilka technik stylu kodu.

Naciśnij klawisz **Alt**+**F11** (lub wybierz **analizy** > **Uruchom analizę kodu dla rozwiązania** z górnego menu) do Rozpocznij statycznej analizy kodu.

![Element menu w usłudze Visual Studio Code Analysis](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Wszelkie nowe lub zaktualizowane ostrzeżenia są wyświetlane w **lista błędów** karta w dolnej części IDE. Polecenie ostrzeżenia, aby przejść do nich w kodzie.

![Lista błędów programu Visual Studio z ostrzeżeniami](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Użyj szybkie akcje, aby naprawić lub refaktoryzacji kodu

[Szybkie akcje](../ide/quick-actions.md), która jest dostępna z żarówkę lub ikonę śrubokręt Pozwól, Refaktoryzuj kod inline. Są one prosty sposób, aby rozwiązać typowe ostrzeżenia szybko i skutecznie w C#, C++ i Visual Basic code. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy na wężyk ostrzeżenie, a następnie wybierz **szybkie akcje i refaktoryzacje**. Lub, jeśli kursor znajduje się na wiersz z kolorowym wężyk, naciśnij klawisze **Ctrl**+**.** lub wybierz żarówki, błąd żarówki lub śrubokręt ikonę na marginesie. Zobaczysz listę możliwych poprawki lub refaktoryzacji, które można zastosować do tego wiersza kodu.

![Visual Studio żarówka — Podgląd](../ide/media/quick-actions-options.png)

Szybkie akcje może służyć wszędzie tam, gdzie określić analizatorów kodu, jest możliwość rozwiązać problem, Refaktoryzacja, lub poprawić kod. Kliknij pozycję w każdym wierszu kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **szybkie akcje i refaktoryzacje**. Jeśli opcje refaktoryzacji i poprawy jakości obsługi są dostępne, zostaną one wyświetlone. W przeciwnym razie komunikat **nie tutaj dostępne szybkie akcje** wyświetlane w lewym dolnym rogu IDE.

![Brak tekstu dostępne szybkie akcje](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Za pomocą środowiska, możesz za pomocą klawiszy strzałek oraz **Ctrl**+**.** Aby sprawdzić, czy są dostępne możliwości refaktoryzacji łatwe i wyczyścić kod!

## <a name="debug-your-running-code"></a>Debugowanie kodu uruchomionego

Teraz, po pomyślnym utworzeniu kodu i wykonać nieco czyszczenia, uruchom ją, naciskając klawisz **F5** lub wybierając **debugowania** > **Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, dzięki czemu możesz obserwować jego zachowanie szczegółowo. Środowiska IDE programu Visual Studio zmienia się po uruchomieniu aplikacji: **dane wyjściowe** okna zastępuje dwóch nowych komentarzy (w oknie Konfiguracja domyślna), **Autos/zmienne lokalne/Obejrzyj** z zakładkami, okna i **Wywołanie wyjątku-stosu/punktów przerwania ustawienia/Output** okien z kartami. Te okna mają wiele kart, które pozwalają na sprawdzanie i ocenić zmienne Twojej aplikacji, wątki, stosy wywołań i różnych innych zachowań, ponieważ działa.

![Automatyczne programu Visual Studio i Windows stosu wywołań](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zatrzymaj aplikację, naciskając klawisz **Shift**+**F5** lub przez kliknięcie przycisku **zatrzymać** przycisku. Alternatywnie możesz po prostu zamknąć główne okno aplikacji (lub okno wiersza polecenia).

Jeżeli kod działa bez zarzutu i dokładnie tak jak oczekiwano, Gratulacje! Jednak jeśli nieuruchamianie lub uległ awarii lub udostępniła Ci niektóre dziwne wyniki, należy znaleźć źródło tych problemów i naprawiania błędów.

### <a name="set-simple-breakpoints"></a>Ustawianie punktów przerwania prosty

[Punkty przerwania](../debugger/using-breakpoints.md) są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu. Nie trzeba ponownie skompiluj projekt po ustawiania i usuwania punktów przerwania.

Ustaw punkt przerwania, klikając w końcu margines linii, na którym ma podziału wystąpienia lub naciśnij **F9** ustawiany jest punkt przerwania w bieżącym wierszu kodu. Podczas uruchamiania kodu spowoduje wstrzymanie (lub *podziału*) przed wykonywane są instrukcje dotyczące ten wiersz kodu.

![Visual Studio punktu przerwania](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Najczęstsze zastosowania dla punktów przerwania obejmują:

- Aby zawęzić źródło awarię lub zawieszenie, wykres punktowy punktów przerwania w całej i wokół kodu wywołania metody, które Twoim zdaniem jest przyczyną błędu. Podczas wykonywania kodu w debugerze Usuń, a następnie zresetować punktów przerwania bliżej razem do momentu znalezienia naruszającym wierszem kodu. Zobacz następną sekcję, aby dowiedzieć się, jak uruchamiać kod w debugerze.

- Po wprowadzeniu nowego kodu, ustaw punkt przerwania na początku, a następnie uruchom kod, aby upewnić się, że zachowuje się zgodnie z oczekiwaniami.

- Jeśli zastało zaimplementowane skomplikowane zachowanie, ustaw punkty przerwania w konsolidatorze kodu, dzięki czemu można sprawdzić wartości zmiennych i danych, kiedy program przerywa.

- Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać wykonywanie kodu, dzięki czemu można sprawdzić wartości adresów (Zwróć uwagę na wartość NULL) i liczby odwołań podczas debugowania błędów związanych z pamięcią.

Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj [używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania

Kiedy uruchomiony kod uderza w punkt przerwania i wstrzymuje, wiersz kodu oznaczone kolorem żółtym (bieżąca instrukcja) nie ma jeszcze wykonane. W tym momencie można wykonać bieżącej instrukcji, a następnie sprawdź zmienionymi wartościami. Można użyć kilku *kroku* poleceń do wykonania kodu w debugerze. Oznaczone kodu w przypadku wywołania metody, można było do niego przejść, naciskając klawisz **F11**. Możesz również *Przekrocz nad* wiersza kodu, naciskając klawisz **F10**. Aby uzyskać dodatkowe polecenia i szczegółowe informacje na temat przejść przez kod, przeczytaj [Przechodzenie do kodu z debugerem](../debugger/navigating-through-code-with-the-debugger.md).

![Inspekcja wartości czasu wykonywania w usłudze Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na poprzedniej ilustracji, można odtwarzać instrukcja debugera jeden, naciskając klawisz albo **F10** lub **F11** (ponieważ brak wywołania metody, oba polecenia mają ten sam wynik).

Gdy debuger jest wstrzymany, można sprawdzić zmiennych i Wywołaj stosy, aby ustalić, co się dzieje. Są wartości z zakresów, które powinny być widoczne? Są wykonywane w odpowiedniej kolejności wywołań?

![Inspekcja wartości czasu wykonywania w usłudze Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Umieść kursor nad zmiennej, aby zobaczyć jego bieżąca wartość i odwołania. Jeśli widzisz wartość, którą Nieoczekiwane wyrażenie, prawdopodobnie masz usterki na poprzednim lub wywoływania w kodzie. Aby uzyskać więcej szczegółowych informacji debugowania [więcej](../debugger/debugger-feature-tour.md) o korzystaniu z debugera.

Ponadto, Visual Studio Wyświetla **narzędzia diagnostyczne** okna, w którym można obserwować wykorzystanie Procesora i pamięci aplikacji wraz z upływem czasu. W dalszej części Tworzenie aplikacji można użyć tych narzędzi do wyszukania nieprzewidziane duże obciążenie lub pamięć alokacji Procesora. Używane w połączeniu z **Obejrzyj** okien i punkty przerwania, aby sprawdzić, co powoduje nieoczekiwany duże obciążenie lub niewydany zasobów. Aby uzyskać więcej informacji, zobacz [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Testy jednostkowe są Twoje pierwszą linią obrony przed usterki kodu, ponieważ, jeśli zostaną prawidłowo wykonane, test pojedynczego "jednostka" kodu, zazwyczaj jednej funkcji i są łatwiejsze do debugowania niż pełny program. Program Visual Studio instaluje struktur testowania jednostek pochodzących od firmy Microsoft dla kodu zarządzanego i natywnego. Testowania jednostkowego umożliwia tworzenie testów jednostkowych, uruchamiaj je i raportuje o wynikach tych testów. Jednostka ponownie uruchom testy po wprowadzeniu zmian, aby sprawdzić, czy kod nadal działa poprawnie. Za pomocą programu Visual Studio Enterprise edition można uruchomić testy automatyczne po każdej kompilacji.

Aby rozpocząć pracę, przeczytaj [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Aby dowiedzieć się więcej na temat testów jednostkowych w programie Visual Studio i jak mogą one pomóc tworzyć lepszy kod jakości, przeczytaj [podstawy testów jednostkowych](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Dowiedz się więcej na temat używania debugera](../debugger/index.md)
- [Generowanie i naprawianie kodu](../ide/code-generation-in-visual-studio.md)