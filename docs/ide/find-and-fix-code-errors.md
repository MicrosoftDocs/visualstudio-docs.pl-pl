---
title: Popraw błędy programu i popraw kod
description: W tym artykule opisano niektóre podstawowe sposoby, w których program Visual Studio może ułatwić znajdowanie i rozwiązywanie problemów w kodzie, w tym błędy kompilacji, analizę kodu, narzędzia debugowania i testy jednostkowe.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d743749ebf1c31c25345c89922fee2434c3284bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386735"
---
# <a name="make-code-work-in-visual-studio"></a>Tworzenie kodu w programie Visual Studio

Program Visual Studio oferuje zaawansowany, zintegrowany zestaw narzędzi do kompilowania i debugowania projektu. W tym artykule dowiesz się, jak program Visual Studio może pomóc w znalezieniu problemów w kodzie przy użyciu danych wyjściowych kompilacji, analizy kodu, narzędzi debugowania i testów jednostkowych.

Poznasz Edytor i utworzono jakiś kod. Teraz chcesz upewnić się, że kod działa prawidłowo. W programie Visual Studio, tak jak w przypadku większości środowisk IDE, istnieją dwie fazy wykonywania kodu: kompilowanie kodu do przechwytywania i rozwiązywanie błędów programu Project i kompilator oraz uruchamianie kodu w celu znalezienia błędów w czasie wykonywania i dynamicznych.

## <a name="build-your-code"></a>Tworzenie kodu

Istnieją dwa podstawowe typy konfiguracji kompilacji: **debugowanie** i **wydanie**. Konfiguracja **debugowania** generuje wolniejszy, większy plik wykonywalny, który umożliwia bogatsze interaktywne środowisko debugowania w czasie wykonywania. Plik wykonywalny **debugowania** nigdy nie powinien być dostarczany. Konfiguracja **wydania** kompiluje szybszy i zoptymalizowany plik wykonywalny, który jest odpowiedni do dostarczenia (co najmniej z perspektywy kompilatora). Domyślną konfiguracją kompilacji jest **debugowanie**.

Najprostszym sposobem kompilowania projektu jest naciśnięcie klawisza **F7**, ale można również uruchomić kompilację, wybierając opcję **Kompiluj**  >  **rozwiązanie** z menu głównego.

![Wybór menu projektu kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Można obserwować proces kompilacji w oknie **danych wyjściowych** w dolnej części interfejsu użytkownika programu Visual Studio. Błędy, ostrzeżenia i operacje kompilacji są wyświetlane w tym miejscu. Jeśli występują błędy (lub jeśli masz ostrzeżenia powyżej skonfigurowanego poziomu), kompilacja zakończy się niepowodzeniem. Możesz kliknąć błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpiły. Odbuduj projekt, ponownie naciskając klawisz **F7** (w celu ponownego skompilowania tylko plików z błędami) lub **Ctrl** + **Alt** + **F7** (w przypadku czystej i kompletnej odbudowy).

W oknie wyniki są dwa okna z kartami, poniżej edytora: okno **dane wyjściowe** zawierające nieprzetworzone dane wyjściowe kompilatora (w tym komunikaty o błędach); i okno **Lista błędów** , które udostępnia listę wszystkich błędów i ostrzeżeń z możliwością sortowania i filtrowania.

Gdy kompilacja zakończy się pomyślnie, zobaczysz wyniki podobne do tego w oknie **danych wyjściowych** :

![Pomyślne Kompilowanie danych wyjściowych programu Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Przejrzyj Lista błędów

Jeśli nie wprowadzono żadnych modyfikacji kodu, który został wcześniej utworzony i pomyślnie skompilowany, prawdopodobnie wystąpił błąd. Jeśli dopiero zaczynasz kodowanie, prawdopodobnie masz wiele z nich. Błędy są czasami oczywiste, takie jak prosty błąd składniowy lub nieprawidłowa nazwa zmiennej, a czasami są trudne do zrozumienia, tylko kod tajemnicze, który poprowadzi Cię przez Ciebie. Aby zapoznać się z bardziej czytelnym widokiem problemów, przejdź do dolnej części okna **dane wyjściowe** kompilacji i kliknij kartę **Lista błędów** . Spowoduje to przejście do bardziej zorganizowanego widoku błędów i ostrzeżeń dotyczących projektu, a także udostępnia pewne dodatkowe opcje.

![Dane wyjściowe i Lista błędów programu Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknij wiersz błędu w oknie **Lista błędów** , aby przejść do wiersza, w którym występuje błąd. (Lub Włącz numery wierszy, naciskając klawisz **Ctrl** + **Q**, wpisując **numery wierszy**, a następnie wybierając **opcję Włącz lub Wyłącz numery wierszy na** podstawie wyników. Jest to najszybszy sposób uzyskania okna dialogowego **Opcje** , w którym można włączyć numery wierszy.)

![Edytor programu Visual Studio z numerami wierszy](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opcja numerów wierszy programu Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Naciśnij klawisz **Ctrl** + **G** , aby szybko przejść do numeru wiersza, w którym wystąpił błąd.

Błąd jest identyfikowany przez czerwoną podkreślenie "zygzaka". Umieść kursor nad nim, aby uzyskać dodatkowe informacje. Wprowadź poprawkę i przejdziemy do niej, chociaż możesz wprowadzić nowy błąd przy korekcie. (Jest to nazywane "regresją").

![Aktywowanie błędu programu Visual Studio](../ide/media/vs_ide_gs_debug_error_hover1.png)

Zapoznaj się z listą błędów i zapoznaj się ze wszystkimi błędami w kodzie.

![Okno błędów debugowania programu Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Przejrzyj błędy szczegółowo

Wiele błędów może nie mieć sensu, ponieważ są one w warunkach kompilatora. W takich przypadkach konieczne będzie dodanie dodatkowych informacji. W oknie **Lista błędów** można wykonać automatyczne wyszukiwanie w usłudze Bing, aby uzyskać więcej informacji na temat błędu lub ostrzeżenia. Kliknij prawym przyciskiem myszy odpowiedni wiersz wejścia i wybierz polecenie **Pokaż pomoc dotyczącą błędów** z menu kontekstowego lub kliknij hiperłącze wartość kod błędu w kolumnie **kod** **Lista błędów**.

![Wyszukiwanie Bing na liście błędów programu Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

W zależności od ustawień przeglądarka sieci Web Wyświetla wyniki wyszukiwania dla kodu błędu i tekstu lub kartę otwiera się w programie Visual Studio i pokazuje wyniki wyszukiwania Bing. Wyniki pochodzą z wielu różnych źródeł w Internecie, a nie wszystkie mogą być pomocne.

## <a name="use-code-analysis"></a>Użyj analizy kodu

Analizatory kodu szukają typowych problemów z kodem, które mogą prowadzić do błędów lub problemów w czasie wykonywania w celu zarządzania kodem.

### <a name="c-and-visual-basic-code-analysis"></a>Analiza kodu w języku C# i Visual Basic

Program Visual Studio zawiera wbudowany zestaw [.NET compiler platform analizatorów](../code-quality/roslyn-analyzers-overview.md) , które sprawdzają kod C# i Visual Basic podczas pisania. Dodatkowe analizatory można zainstalować jako rozszerzenie programu Visual Studio lub jako pakiet NuGet. Jeśli zostaną znalezione naruszenia zasad, są one raportowane zarówno w Lista błędów, jak i w edytorze kodu jako zygzak w kodzie nieprawidłowym.

### <a name="c-code-analysis"></a>Analiza kodu w języku C++

Aby analizować kod języka C++, uruchom [analizę kodu statycznego](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Zapoznaj się z wykonywać, aby uruchomić go po usunięciu oczywistych błędów, które uniemożliwiają pomyślne skompilowanie, i Poświęć trochę czasu na wygenerowanie ostrzeżeń. Zarządzaniem mu towarzyszą się na siebie i możesz poznać kilka technik stylu kodu.

Naciśnij klawisz **Alt** + **F11** (lub wybierz polecenie **Analizuj**  >  **analizę kodu w rozwiązaniu** z górnego menu), aby rozpocząć analizę kodu statycznego.

![Element menu analizy Visual Studio Code](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Wszystkie nowe lub zaktualizowane ostrzeżenia są wyświetlane na karcie **Lista błędów** w dolnej części IDE. Kliknij ostrzeżenia, aby przeskoczyć do nich w kodzie.

![Program Visual Studio Lista błędów z ostrzeżeniami](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Używanie szybkich akcji do naprawy lub refaktoryzacji kodu

[Szybkie akcje](../ide/quick-actions.md), dostępne na ikonie żarówki lub śrubokrętu, umożliwiają refaktoryzację kodu w tekście. Są one łatwym sposobem na szybkie i efektywne Rozwiązywanie typowych ostrzeżeń w języku C#, C++ i Visual Basic. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy ikonę ostrzeżenia i wybierz polecenie **szybkie akcje i refaktoryzacje**. Lub, gdy kursor znajduje się w wierszu z kolorem zygzakowym, naciśnij klawisz **Ctrl** + **.** lub wybierz ikonę żarówki, żarówki błędów lub śrubokręt na marginesie. Zobaczysz listę możliwych poprawek lub refaktoryzacji, które można zastosować do tego wiersza kodu.

![Visual Studio Light — wersja zapoznawcza](../ide/media/quick-actions-options.png)

Szybkie akcje mogą być używane wszędzie, gdzie analizator kodu decyduje o możliwości naprawy, refaktoryzacji lub ulepszania kodu. Kliknij dowolny wiersz kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe, a następnie wybierz polecenie **szybkie akcje i refaktoryzacje**. Jeśli są dostępne opcje refaktoryzacji lub poprawy jakości obsługi, są wyświetlane. W przeciwnym razie w lewym dolnym rogu IDE **nie są dostępne żadne szybkie akcje** .

![Brak dostępnego tekstu szybkich akcji](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Korzystając z funkcji, możesz szybko użyć klawiszy strzałek i **Ctrl** + **.** Aby sprawdzić, czy masz możliwość szybkiego refaktoryzacji i wyczyścić swój kod!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Uruchom oczyszczanie kodu

Program Visual Studio zapewnia [Formatowanie na żądanie pliku kodu w języku C#](code-styles-and-code-cleanup.md#apply-code-styles), w tym preferencje stylu kodu, za pomocą przycisku **Wyczyść kod** w dolnej części edytora.

![Przycisk oczyszczania kodu w programie Visual Studio 2019](media/execute-code-cleanup.png)

Oprócz formatowania pliku dla spacji, wcięcia, et zadanie, **czyszczenie kodu** stosuje również zestaw zdefiniowanych Konwencji stylu kodu. Preferencje dla każdego stylu kodu są odczytywane z [pliku EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), jeśli istnieje dla projektu lub z [ustawień stylu kodu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) w oknie dialogowym **Opcje** .

::: moniker-end

## <a name="debug-your-running-code"></a>Debugowanie uruchomionego kodu

Teraz, po pomyślnym skompilowaniu kodu i wykonaniu małego czyszczenia, uruchom go, naciskając klawisz **F5** lub wybierając **Debuguj**  >  **Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, aby można było obserwować jej zachowanie szczegółowo. Środowisko IDE programu Visual Studio zmienia się podczas działania aplikacji: okno **dane wyjściowe** jest zastępowane dwoma nowymi (w konfiguracji okna domyślnego), oknem **autostarts/locale/Watch** z kartami oraz **stos wywołań/punktów przerwania/ustawienia wyjątku/** wychodzące okno z kartami. Te okna mają wiele kart, które umożliwiają sprawdzanie i ocenianie zmiennych aplikacji, wątków, stosów wywołań i różnych innych zachowań w miarę ich działania.

![Program Visual Studio — autouzupełniania i stosy wywołań okien](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zatrzymaj aplikację, naciskając klawisz **SHIFT** + **F5** lub klikając przycisk **Zatrzymaj** . Lub po prostu możesz zamknąć okno główne aplikacji (lub okno dialogowe wiersza polecenia).

Jeśli kod działa doskonale i dokładnie zgodnie z oczekiwaniami, gratulacje! Jeśli jednak przestanie ona odpowiadać lub uległa awarii lub podała pewne dziwne wyniki, należy znaleźć źródło tych problemów i naprawić błędy.

### <a name="set-simple-breakpoints"></a>Ustaw proste punkty przerwania

[Punkty przerwania](../debugger/using-breakpoints.md) są najbardziej podstawową i istotną funkcją niezawodnego debugowania. Punkt przerwania wskazuje, gdzie program Visual Studio powinien zawiesić uruchomiony kod, aby można było przyjrzeć się wartościom zmiennych lub działaniu pamięci lub niezależnie od tego, czy gałąź kodu jest uruchamiana. Nie musisz odbudować projektu po ustawieniu i usunięciu punktów przerwania.

Ustaw punkt przerwania, klikając górny margines linii, w której ma nastąpić przerwanie, lub naciśnij klawisz **F9** , aby ustawić punkt przerwania w bieżącym wierszu kodu. Po uruchomieniu kodu zostanie ono wstrzymane (lub *przerwane*) przed wykonaniem instrukcji dla tego wiersza kodu.

![Punkt przerwania programu Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Typowe zastosowania punktów przerwania to:

- Aby zawęzić Źródło awarii lub nieodpowiadającego programu, punkty przerwania punktów kontrolnych w całym i dookoła kodu wywoływanego wywołania metody są przyczyną błędu. Podczas uruchamiania kodu w debugerze Usuń, a następnie zresetuj punkty przerwania bliżej siebie do momentu znalezienia niezgodnego wiersza kodu. Zapoznaj się z następną sekcją, aby dowiedzieć się, jak uruchomić kod w debugerze.

- Gdy wprowadzasz nowy kod, ustaw punkt przerwania na początku go i uruchom kod, aby upewnić się, że działa zgodnie z oczekiwaniami.

- Jeśli zaimplementowano skomplikowane zachowanie, ustaw punkty przerwania dla kodu algorytmu, aby można było sprawdzić wartości zmiennych i danych w przypadku przerwania działania programu.

- Jeśli piszesz kod C lub C++, użyj punktów przerwania, aby zatrzymać kod, tak aby można było sprawdzać wartości adresu (poszukiwania wartości NULL) i liczby odwołań podczas debugowania błędów związanych z pamięcią.

Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj temat [Używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania

Gdy uruchomiony kod trafi punkt przerwania i zatrzymuje, wiersz kodu oznaczony kolorem żółtym (Bieżąca instrukcja) nie został jeszcze wykonany. W tym momencie możesz chcieć wykonać bieżącą instrukcję, a następnie sprawdzić zmienione wartości. Aby wykonać kod w debugerze, można użyć kilku poleceń *kroków* . Jeśli oznaczony kod jest wywołaniem metody, możesz przejść do niego, naciskając klawisz **F11**. Możesz również *przekroczyć* linię kodu, naciskając klawisz **F10**. Aby uzyskać dodatkowe polecenia i szczegółowe informacje na temat sposobu przechodzenia przez kod, Przeczytaj [Przechodzenie do kodu za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

![Inspekcja wartości w czasie wykonywania programu Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na powyższej ilustracji możesz przejść do jednej instrukcji debugera, naciskając klawisz **F10** lub **F11** (ponieważ w tym miejscu nie ma żadnego wywołania metody, oba polecenia mają ten sam wynik).

Gdy debuger jest wstrzymany, można sprawdzić zmienne i wywoływać stosy, aby określić, co się dzieje. Czy wartości w zakresach powinny być widoczne? Czy wywołania są wykonywane w odpowiedniej kolejności?

![Inspekcja wartości w czasie wykonywania programu Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Umieść kursor nad zmienną, aby zobaczyć jej bieżącą wartość i odwołania. Jeśli zobaczysz nieoczekiwaną wartość, prawdopodobnie masz usterkę w powyższym lub wywoływanym kodzie. Aby uzyskać bardziej szczegółowe informacje dotyczące debugowania, [Dowiedz się więcej](../debugger/debugger-feature-tour.md) o korzystaniu z debugera.

Ponadto program Visual Studio Wyświetla okno **Narzędzia diagnostyczne** , w którym można obserwować użycie procesora i pamięci przez aplikację w czasie. W dalszej części opracowywania aplikacji można używać tych narzędzi do wyszukiwania nieoczekiwanego użycia procesora CPU lub alokacji pamięci. Użyj go w połączeniu z oknem **czujki** i punktem przerwania, aby określić, co powoduje nieoczekiwane użycie lub niewykorzystane zasoby. Aby uzyskać więcej informacji, zobacz temat [profilowanie funkcji](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

Testy jednostkowe są pierwszym wierszem obrony przed usterkami kodu, ponieważ po prawidłowym przetestowaniu pojedynczej "jednostki" kodu, zazwyczaj pojedynczej funkcji i są łatwiejsze do debugowania niż w przypadku pełnego programu. Program Visual Studio instaluje platformy testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Użyj struktury testów jednostkowych, aby utworzyć testy jednostkowe, uruchomić je i zgłosić wyniki tych testów. Uruchom ponownie testy jednostkowe po wprowadzeniu zmian, aby sprawdzić, czy kod nadal działa poprawnie. W wersji Visual Studio Enterprise można uruchomić testy automatycznie po każdej kompilacji.

Aby rozpocząć, przeczytaj artykuł [generowanie testów jednostkowych dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Aby dowiedzieć się więcej o testach jednostkowych w programie Visual Studio i sposobach tworzenia lepszych kodów jakości, Przeczytaj [podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Dowiedz się więcej o korzystaniu z debugera](../debugger/index.yml)
- [Generowanie i naprawianie kodu](../ide/code-generation-in-visual-studio.md)
