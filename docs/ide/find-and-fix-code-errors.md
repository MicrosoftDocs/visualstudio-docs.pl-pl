---
title: Naprawianie błędów programu i ulepszanie kodu
description: W tym artykule opisano niektóre podstawowe sposoby visual studio może pomóc znaleźć i rozwiązać problemy w kodzie, w tym błędy kompilacji, analizy kodu, narzędzia debugowania i testy jednostkowe.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fa03dec65bcdc1e6c3af94200cfb6c46907e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476871"
---
# <a name="make-code-work-in-visual-studio"></a>Spraw, aby kod działał w programie Visual Studio

Visual Studio zapewnia zaawansowany zintegrowany zestaw narzędzi do tworzenia i debugowania projektu. W tym artykule dowiesz się, jak visual studio może pomóc znaleźć problemy w kodzie przy użyciu danych wyjściowych kompilacji, analizy kodu, narzędzi debugowania i testów jednostkowych.

Wymyśliłeś edytor i utworzyłeś kod. Teraz chcesz upewnić się, że kod działa poprawnie. W programie Visual Studio, podobnie jak w przypadku większości adresów IE, istnieją dwie fazy do tworzenia pracy kodu: tworzenie kodu do połowu i rozwiązywania błędów projektu i kompilatora i uruchamianie kodu, aby znaleźć błędy w czasie wykonywania i dynamiczne.

## <a name="build-your-code"></a>Tworzenie kodu

Istnieją dwa podstawowe typy konfiguracji kompilacji: **Debug** i **Release**. Konfiguracja **debugowania** tworzy wolniejszy, większy plik wykonywalny, który umożliwia bogatsze interaktywne środowisko debugowania w czasie wykonywania. Plik wykonywalny **debugowania** nigdy nie powinien być wysyłany. Konfiguracja **wydania** tworzy szybszy, zoptymalizowany plik wykonywalny, który jest odpowiedni do wysyłki (przynajmniej z perspektywy kompilatora). Domyślną konfiguracją kompilacji jest **Debug**.

Najprostszym sposobem tworzenia projektu jest naciśnięcie **klawisza F7**, ale można również rozpocząć kompilację, wybierając **build** > **build solution** z menu głównego.

![Wybór menu projektu kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Można zaobserwować proces kompilacji w oknie **dane wyjściowe** w dolnej części interfejsu użytkownika programu Visual Studio. Błędy, ostrzeżenia i operacje kompilacji są wyświetlane w tym miejscu. Jeśli masz błędy (lub jeśli masz ostrzeżenia powyżej skonfigurowanego poziomu), kompilacja nie powiedzie się. Możesz kliknąć na błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiły. Odbuduj swój projekt, naciskając ponownie **klawisz F7** (aby ponownie skompilować tylko pliki z błędami) lub **Ctrl**+**Alt**+**F7** (aby uzyskać czystą i kompletną przebudowę).

Istnieją dwa okna z kartami w oknie wyników poniżej edytora: **okno Dane wyjściowe,** które zawiera nieprzetworzone dane wyjściowe kompilatora (w tym komunikaty o błędach); oraz okno **Lista błędów,** które zawiera sortowalne i filtrowalne listy wszystkich błędów i ostrzeżeń.

Gdy kompilacja powiedzie się, zobaczysz wyniki takie jak ten w oknie **Dane wyjściowe:**

![Pomyślne wyniki kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Przejrzyj listę błędów

Jeśli nie wprowadzono żadnych modyfikacji kodu, który został wcześniej i pomyślnie skompilowany, prawdopodobnie wystąpił błąd. Jeśli jesteś nowy w kodowaniu, prawdopodobnie masz ich wiele. Błędy są czasami oczywiste, takie jak prosty błąd składni lub niepoprawna nazwa zmiennej, a czasami są trudne do zrozumienia, z tylko tajemniczy kod, aby cię poprowadzić. Aby uzyskać czystszy widok problemów, przejdź do dołu okna **dane wyjściowe** kompilacji i kliknij kartę **Lista błędów.** Spowoduje to przejście do bardziej zorganizowanego widoku błędów i ostrzeżeń dla projektu, a także daje kilka dodatkowych opcji.

![Lista danych wyjściowych i błędów programu Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknij wiersz błędu w oknie **Lista błędów,** aby przejść do wiersza, w który występuje błąd. (Możesz też włączyć numery wierszy, naciskając klawisz **Ctrl**+**Q**, wpisując **numery wierszy,** a następnie wybierając **pozycję Włącz lub wyłącz z** wyników opcję Włącz lub wyłącz z wyników. Jest to najszybszy sposób, aby przejść do okna dialogowego **Opcje,** w którym można włączyć numery wierszy.)

![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opcja numery wierszy programu Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Naciśnij **klawisz Ctrl**+**G,** aby szybko przejść do numeru wiersza, w którym wystąpił błąd.

Błąd jest identyfikowany przez czerwony znak podkreślenia "squiggle". Umieść nad nim wskaźnik myszy, aby uzyskać dodatkowe informacje. Zrób poprawkę i zniknie, chociaż możesz wprowadzić nowy błąd z korektą. (Jest to nazywane "regresją".)

![Numer alarmowy błędu programu Visual Studio](../ide/media/vs_ide_gs_debug_error_hover1.png)

Przejdź przez listę błędów i zamień wszystkie błędy w kodzie.

![Okno błędy debugowania programu Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Szczegółowe przeglądanie błędów

Wiele błędów może mieć sens dla Ciebie, sformułowane, ponieważ są one w warunkach kompilatora. W takich przypadkach potrzebne są dodatkowe informacje. W oknie **Lista błędów** można wykonać automatyczne wyszukiwanie bing, aby uzyskać więcej informacji na temat błędu lub ostrzeżenia. Kliknij prawym przyciskiem myszy odpowiedni wiersz wpisu i wybierz polecenie **Pokaż Pomoc błędu** z menu kontekstowego lub kliknij na wartość kodu błędu hiperłącza w kolumnie **Kod** **listy błędów**.

![Wyszukiwanie listy błędów programu Visual Studio bing](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

W zależności od ustawień przeglądarka sieci Web wyświetla wyniki wyszukiwania kodu błędu i tekstu lub otwiera się karta wewnątrz programu Visual Studio i pokazuje wyniki wyszukiwania Bing. Wyniki pochodzą z wielu różnych źródeł w Internecie i nie wszystkie mogą być pomocne.

## <a name="use-code-analysis"></a>Użyj analizy kodu

Analizatory kodu szukać typowych problemów z kodem, które mogą prowadzić do błędów w czasie wykonywania lub problemów w zarządzaniu kodem.

### <a name="c-and-visual-basic-code-analysis"></a>Analiza kodu języka C# i Visual Basic

Visual Studio zawiera wbudowany zestaw [analizatorów platformy kompilatora .NET,](../code-quality/roslyn-analyzers-overview.md) które badają kod Języka C# i języka Visual Basic podczas pisania. Można zainstalować dodatkowe analizatory jako rozszerzenie programu Visual Studio lub jako pakiet NuGet. Jeśli zostaną znalezione naruszenia reguły, są one zgłaszane zarówno na liście błędów, jak i w edytorze kodu jako falista pod kodem naruszającym.

### <a name="c-code-analysis"></a>Analiza kodu języka C++

Aby przeanalizować kod C++, uruchom [analizę kodu statycznego](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Wczyść się w nawyk uruchamiania go po oczyszczeniu oczywistych błędów, które uniemożliwiają pomyślną kompilację i poświęć trochę czasu na rozwiązanie ostrzeżeń, które może spowodować. Zaoszczędzisz sobie kilka bólów głowy w dół drogi, i może nauczyć się kilku technik stylu kodu.

Naciśnij **klawisz Alt**+**F11** (lub wybierz **opcję Analizuj** > analizę**kodu przebiegu w rozwiązaniu** z górnego menu), aby rozpocząć analizę kodu statycznego.

![Element menu Analizy kodu programu Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Wszelkie nowe lub zaktualizowane ostrzeżenia są wyświetlane na karcie **Lista błędów** u dołu IDE. Kliknij ostrzeżenia, aby przejść do nich w kodzie.

![Lista błędów programu Visual Studio z ostrzeżeniami](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Naprawianie lub refaktoryzowanie kodu za pomocą szybkich akcji

[Szybkie akcje,](../ide/quick-actions.md)dostępne z żarówki lub ikony śrubokręta, pozwalają refaktoryfikować kod wbudowany. Są one łatwym sposobem, aby szybko i skutecznie naprawić typowe ostrzeżenia w kodzie C#, C++ i Visual Basic. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy ostrzeżenie i wybierz **szybkie akcje i refaktoryzowania**. Lub, gdy kursor jest na linii z kolorowym squiggle, naciśnij klawisz **Ctrl**+**.** lub wybierz żarówkę, żarówkę błędu lub ikonę śrubokręta na marginesie. Zostanie wyświetlona lista możliwych poprawek lub refaktoryzacji, które można zastosować do tego wiersza kodu.

![Podgląd żarówki programu Visual Studio](../ide/media/quick-actions-options.png)

Szybkie akcje mogą być używane wszędzie tam, gdzie analizatory kodu określają, że istnieje możliwość naprawienia, refaktoryzacji lub ulepszenia kodu. Kliknij dowolny wiersz kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz **pozycję Szybkie akcje i refaktoryzowania**. Jeśli dostępne są opcje refaktoryzacji lub poprawy, są one wyświetlane. W przeciwnym razie komunikat **Brak szybkich akcji dostępnych w tym miejscu** jest wyświetlany w lewym dolnym rogu IDE.

![Brak dostępnych szybkich akcji](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Dzięki doświadczeniu można szybko korzystać z klawiszy strzałek i **ctrl**+**.** aby sprawdzić, czy możliwości refaktoryzacji i oczyścić kod!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Uruchamianie oczyszczania kodu

Visual Studio zapewnia [formatowanie na żądanie pliku kodu języka C#](code-styles-and-code-cleanup.md#apply-code-styles), w tym preferencje stylu kodu, za pomocą przycisku **Oczyszczanie kodu** u dołu edytora.

![Przycisk Oczyszczanie kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

Oprócz formatowania pliku dla spacji, wcjętów, et cetera, **Oczyszczanie kodu** stosuje również zestaw konwencji stylu kodu, które definiujesz. Preferencje dla każdego stylu kodu są odczytywane z [pliku EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), jeśli masz go dla projektu lub z [ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) w oknie dialogowym **Opcje.**

::: moniker-end

## <a name="debug-your-running-code"></a>Debugowanie uruchomionego kodu

Teraz, gdy pomyślnie skonkrzyzujesz kod i wykonano trochę czyszczenia, uruchom go, naciskając **klawisz F5** lub wybierając **debugowanie** > **start debugowania.** Spowoduje to uruchomienie aplikacji w środowisku debugowania, dzięki czemu można obserwować jego zachowanie w szczegółach. Visual Studio IDE zmienia się, gdy aplikacja jest uruchomiona: okno **Dane wyjściowe** jest zastępowany przez dwa nowe (w domyślnej konfiguracji okna), **Autos/Locals/Watch** okna karty i **stos wywołań/punkty przerwania/ustawienia wyjątków/dane wyjściowe** okna karty. Te okna mają wiele kart, które umożliwiają sprawdzanie i ocenę zmiennych aplikacji, wątki, stosy wywołań i różne inne zachowania, jak działa.

![Autos programu Visual Studio i stos wywołań w systemie Windows](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zatrzymaj aplikację, naciskając **klawisz Shift**+**F5** lub klikając przycisk **Zatrzymaj.** Możesz też po prostu zamknąć okno główne aplikacji (lub okno dialogowe wiersza polecenia).

Jeśli kod działał idealnie i dokładnie tak, jak oczekiwano, gratulacje! Jeśli jednak wisiał, rozbił się lub dał ci jakieś dziwne wyniki, musisz znaleźć źródło tych problemów i naprawić błędy.

### <a name="set-simple-breakpoints"></a>Ustawianie prostych punktów przerwania

[Punkty przerwania](../debugger/using-breakpoints.md) są najbardziej podstawową i istotną cechą niezawodnego debugowania. Punkt przerwania wskazuje, gdzie visual studio należy zawiesić uruchomiony kod, dzięki czemu można spojrzeć na wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu jest coraz uruchamiany. Nie trzeba odbudować projekt po ustawieniu i usunięciu punktów przerwania.

Ustaw punkt przerwania, klikając na daleki margines wiersza, w którym ma wystąpić przerwa, lub naciśnij **klawisz F9,** aby ustawić punkt przerwania w bieżącym wierszu kodu. Po uruchomieniu kodu, zostanie wstrzymany (lub *przerwać)* przed wykonaniem instrukcji dla tego wiersza kodu.

![Punkt przerwania programu Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Typowe zastosowania punktów przerwania obejmują:

- Aby zawęzić źródło awarii lub zawieszenia, punkty przerwania scatter w całym i wokół kodu wywołania metody, które uważasz, że powoduje błąd. Po uruchomieniu kodu w debugerze, usuń, a następnie zresetować punkty przerwania bliżej siebie, aż znajdziesz obraźliwe wiersz kodu. Zobacz następną sekcję, aby dowiedzieć się, jak uruchomić kod w debugerze.

- Po wprowadzeniu nowego kodu, ustawić punkt przerwania na początku i uruchom kod, aby upewnić się, że działa zgodnie z oczekiwaniami.

- Jeśli zaimplementowano skomplikowane zachowanie, ustaw punkty przerwania dla kodu algorytmicznego, dzięki czemu można sprawdzić wartości zmiennych i danych, gdy program zostanie przerwany.

- Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać kod, dzięki czemu można sprawdzić wartości adresów (szukać NULL) i liczby odwołań podczas debugowania dla błędów związanych z pamięcią.

Aby uzyskać więcej informacji na temat korzystania z punktów przerwania, zobacz [Korzystanie z punktów przerwania](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania

Gdy uruchomiony kod trafi punkt przerwania i wstrzymuje, wiersz kodu oznaczony na żółto (bieżąca instrukcja) nie został jeszcze wykonany. W tym momencie można wykonać bieżącą instrukcję, a następnie sprawdzić zmienione wartości. Do wykonania kodu w debugerze można użyć kilku poleceń *kroku.* Jeśli oznaczony kod jest wywołaniem metody, można wkroczyć do niego, naciskając **klawisz F11**. Można również *przejść przez* linię kodu, naciskając klawisz **F10**. Aby uzyskać dodatkowe polecenia i szczegółowe informacje na temat przechodzenia przez kod, przeczytaj [navigate code z debugerem](../debugger/navigating-through-code-with-the-debugger.md).

![Kontrola wartości w czasie wykonywania programu Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na powyższej ilustracji można przejść debuger jedną instrukcję, naciskając **F10** lub **F11** (ponieważ nie ma wywołania metody w tym miejscu, oba polecenia mają ten sam wynik).

Podczas debugera jest wstrzymany, można sprawdzić zmienne i stosy wywołań, aby ustalić, co się dzieje. Czy wartości w zakresach, których oczekujesz, są widoczne? Czy połączenia są nawiązywane w odpowiedniej kolejności?

![Kontrola wartości w czasie wykonywania programu Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Umieść wskaźnik myszy na zmiennej, aby wyświetlić jej bieżącą wartość i odwołania. Jeśli widzisz wartość, której się nie spodziewałeś, prawdopodobnie masz błąd w poprzednim lub wywołującym kod. Aby uzyskać bardziej szczegółowe informacje debugowania, [dowiedz się więcej](../debugger/debugger-feature-tour.md) na temat korzystania z debugera.

Ponadto program Visual Studio wyświetla okno **Narzędzia diagnostyczne,** w którym można obserwować użycie procesora CPU i pamięci aplikacji w czasie. W dalszej części tworzenia aplikacji można użyć tych narzędzi, aby wyszukać nieoczekiwane użycie procesora CPU lub alokacji pamięci. Użyj go w połączeniu z **watch** okna i punktów przerwania, aby określić, co jest przyczyną nieoczekiwanego użycia ciężkich lub niepublikowanych zasobów. Aby uzyskać więcej informacji, zobacz [Przewodnik funkcji profilowania](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Testy jednostkowe są pierwszą linią obrony przed błędami kodu, ponieważ po wykonaniu poprawnie testują pojedynczą "jednostkę" kodu, zazwyczaj pojedynczą funkcję i są łatwiejsze do debugowania niż pełny program. Visual Studio instaluje struktury testowania jednostkowego firmy Microsoft dla kodu zarządzanego i macierzystego. Użyj struktury testowania jednostkowego do tworzenia testów jednostkowych, uruchamiania ich i raportowania wyników tych testów. Uruchom ponownie testy jednostkowe po wprowadzeniu zmian, aby sprawdzić, czy kod nadal działa poprawnie. W programie Visual Studio Enterprise edition można automatycznie uruchamiać testy po każdej kompilacji.

Aby rozpocząć, przeczytaj artykuł [Generowanie testów jednostkowych dla kodu za pomocą intellitestu](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Aby dowiedzieć się więcej o testach jednostkowych w programie Visual Studio i o tym, jak mogą one pomóc w tworzeniu kodu lepszej jakości, zapoznaj [się z podstawami testów jednostkowych](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Dowiedz się więcej o używaniu debugera](../debugger/index.yml)
- [Generowanie i naprawianie kodu](../ide/code-generation-in-visual-studio.md)
