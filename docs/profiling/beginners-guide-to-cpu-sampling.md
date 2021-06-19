---
title: Przewodnik dla początkujących dotyczący próbkowania procesora CPU
description: Dowiedz się, Visual Studio profilowania ujawniają, ile czasu są używane przez funkcje w aplikacji, prowadząc użytkownika do obszarów przyspieszających aplikację.
ms.custom: SEO-VS-2020
ms.date: 02/27/2017
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07a0593e5139479c1b2d82f7b2f4cd78fde8a884
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387986"
---
# <a name="beginners-guide-to-cpu-sampling"></a>Przewodnik dla początkujących dotyczący próbkowania procesora CPU
Narzędzia profilowania Visual Studio do analizowania problemów z wydajnością w aplikacji. Ta procedura pokazuje, jak używać danych **próbkowania.**

> [!NOTE]
> Zalecamy użycie narzędzia Użycie [procesora CPU](../profiling/beginners-guide-to-performance-profiling.md) w oknie Narzędzia diagnostyczne zamiast starszego narzędzia próbkowania procesora CPU, chyba że potrzebujesz wyspecjalizowanych funkcji, takich jak obsługa instrumentacji.

 **Próbkowanie** to metoda profilowania statystycznego, która pokazuje funkcje, które pełnią większość zadań w trybie użytkownika w aplikacji. Próbkowanie to dobre miejsce, aby zacząć szukać obszarów przyspieszania aplikacji.

 W określonych odstępach czasu metoda **Próbkowanie** zbiera informacje o funkcjach wykonywanych w aplikacji. Po zakończeniu przebiegu profilowania  widok Podsumowanie danych profilowania zawiera najbardziej aktywne drzewo wywołań funkcji o nazwie Ścieżka gorąca, w którym wykonano większość pracy w aplikacji. Widok zawiera również listę funkcji wykonujących najwięcej poszczególnych zadań oraz wykres osi czasu, za pomocą których można skoncentrować się na określonych segmentach sesji próbkowania.

 Jeśli **próbkowanie** nie dostarcza potrzebnych danych, inne metody zbierania narzędzi profilowania zapewniają różne rodzaje informacji, które mogą być przydatne. Aby uzyskać więcej informacji na temat tych innych metod, [zobacz How to: Choose collection methods (Jak wybrać metody kolekcji).](../profiling/how-to-choose-collection-methods.md)

> [!TIP]
> W przypadku profilowania kodu, który wywołuje funkcje systemu Windows, upewnij się, że masz najbardziej aktualny kod . *pliki pdb.* Bez tych plików widoki raportów będą zawierały listę nazw funkcji systemu Windows, które są kryptograficznie i trudne do zrozumienia. Aby uzyskać więcej informacji o tym, jak upewnić się, że masz potrzebne pliki, zobacz Temat Jak odwoływać się do informacji [o symbolach systemu Windows.](../profiling/how-to-reference-windows-symbol-information.md)

## <a name="create-and-run-a-performance-session"></a>Tworzenie i uruchamianie sesji wydajności
 Aby uzyskać dane, które należy przeanalizować, należy najpierw utworzyć sesję wydajności, a następnie uruchomić sesję. Kreator **wydajności umożliwia** wykonanie obu tych funkcji.

 Jeśli nie profilujesz aplikacji klasycznej lub aplikacji klasycznej systemu Windows ASP.NET, musisz użyć jednego z innych narzędzi profilowania. Zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md).

#### <a name="to-create-and-run-a-performance-session"></a>Aby utworzyć i uruchomić sesję wydajności

1. Otwórz rozwiązanie w Visual Studio. Ustaw konfigurację na wydanie. (Znajdź pole **Konfiguracje rozwiązań** na pasku narzędzi, który jest domyślnie ustawiony na **debugowanie.** Zmień ją na **Wydanie).**

    > [!IMPORTANT]
    > Jeśli nie jesteś administratorem na komputerze, z których korzystasz, uruchom program Visual Studio jako administrator podczas korzystania z profilera. (Kliknij prawym przyciskiem myszy ikonę Visual Studio aplikacji, a następnie kliknij polecenie **Uruchom jako administrator.**

2. W menu **Debugowanie** wybierz pozycję **Profiler,** a następnie wybierz **pozycję profiler wydajności**.

3. Zaznacz opcję **Kreator wydajności,** a następnie kliknij przycisk **Uruchom.**

4. Zaznacz opcję **Próbkowanie procesora CPU (zalecane)** i kliknij przycisk **Zakończ.**

5. Aplikacja zostanie uruchamiana, a profiler zacznie zbierać dane.

6. Przećwiczyć działanie funkcji, które mogą zawierać problemy z wydajnością.

7. Zamknij aplikację tak, jak zwykle.

     Po zakończeniu uruchamiania aplikacji  widok Podsumowanie danych profilowania zostanie wyświetlony w głównym oknie Visual Studio, a ikona nowej sesji pojawi się w **oknie** Eksplorator wydajności aplikacji.

## <a name="step-2-analyze-sampling-data"></a>Krok 2. Analizowanie danych próbkowania
 Po zakończeniu sesji wydajności widok **Podsumowanie** raportu profilowania zostanie wyświetlony w głównym oknie Visual Studio.

 Zalecamy rozpoczęcie analizowania danych od zbadania ścieżki **gorącej,** a następnie listy funkcji, które działają najlepiej, a na koniec przez skoncentrowanie się na innych funkcjach przy użyciu osi czasu **podsumowania**. Sugestie i ostrzeżenia dotyczące profilowania można również wyświetlić w **oknie Lista** błędów.

 Należy pamiętać, że metoda próbkowania może nie zawierać potrzebnych informacji. Przykłady są zbierane tylko wtedy, gdy aplikacja korzysta z kodu w trybie użytkownika. W związku z tym niektóre funkcje, takie jak operacje wejściowe i wyjściowe, nie są przechwytywane przez próbkowanie. Ten narzędzia profilowania kilka metod zbierania, które pozwalają skupić się na ważnych danych. Aby uzyskać więcej informacji na temat innych metod, zobacz [How to: Choose collection methods (Jak wybrać metody zbierania).](../profiling/how-to-choose-collection-methods.md)

 Każdy numerowany obszar na rysunku odnosi się do kroku procedury.

 ![Widok raportu podsumowania próbkowania](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Aby analizować dane próbkowania

1. W **widoku Podsumowanie** **ścieżka** gorąca pokazuje gałąź drzewa wywołań aplikacji z najwyższymi przykładami włącznie. Jest to ścieżka wykonywania, która była najbardziej aktywna podczas zbierania danych. Wysokie wartości inkluzywne mogą wskazywać, że algorytm generujący drzewo wywołań można zoptymalizować. Znajdź funkcję w kodzie, który jest najniższy w ścieżce. Należy zauważyć, że ścieżka może również zawierać funkcje systemowe lub funkcje w modułach zewnętrznych.

     ![Ścieżka gorąca profilera](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Przykłady** inkluzywne wskazują, ile pracy wykonała funkcja i jakie funkcje ją wywołały. Wysokie liczby inkluzywne wskazują funkcje, które są najdroższe w całości.

    2. **Przykłady** wyłączności wskazują, ile pracy zostało wykonane przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały przez nie wywołane. Wysokie liczby wyłączności mogą wskazywać wąskie gardło wydajności w obrębie samej funkcji.

2. Kliknij nazwę funkcji, aby wyświetlić **widok Szczegóły funkcji** danych profilowania. Widok **Szczegóły** funkcji przedstawia graficzny widok danych profilowania dla wybranej funkcji, pokazujący wszystkie funkcje, które wywołały tę funkcję, oraz wszystkie funkcje, które zostały wywołane przez wybraną funkcję.

    - Rozmiar bloków funkcji wywołującej i wywoływanej reprezentuje względną częstotliwość wywoływanych funkcji lub .

    - Możesz kliknąć nazwę funkcji wywołującej lub wywoływanej, aby ustawić ją jako wybraną funkcję w widoku Szczegóły funkcji.

    - W dolnym okienku okna **Szczegóły funkcji** jest wyświetlany sam kod funkcji. Jeśli przeanalizujesz kod i znajdziesz możliwość zoptymalizowania jego wydajności, kliknij nazwę pliku źródłowego, aby otworzyć plik w Visual Studio edytorze.

3. Aby kontynuować analizę, wróć do widoku **Podsumowanie,** wybierając pozycję **Podsumowanie** **z** listy rozwijanej Widok. Następnie przeanaliż funkcje **funkcji wykonujących najwięcej poszczególnych zadań.** Na tej liście są wyświetlane funkcje z najwyższymi wyłącznościami przykładów. Kod w treści funkcji tych funkcji wykonał znaczącą pracę i może być w stanie go zoptymalizować. Aby dalej analizować określoną funkcję, kliknij nazwę funkcji, aby wyświetlić ją w **widoku Szczegóły** funkcji.

     ![Lista funkcji wykonujących większość pracy](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Aby kontynuować badanie przebiegu profilowania, możesz ponownie zanalizować segment danych profilowania, używając osi czasu  w widoku  Podsumowanie, aby wyświetlić ścieżkę gorącą i funkcje wykonujące większość indywidualnych zadań z wybranego segmentu.  Na przykład skupienie się na mniejszym szczytzie na osi czasu może ujawnić kosztowne drzewa wywołań i funkcje, których nie pokazano w analizie całego przebiegu profilowania.

     Aby ponownie zanalizować segment, wybierz segment w polu **Oś** czasu podsumowania, a następnie kliknij pozycję **Filtruj według wyboru.**

     ![Oś czasu widoku podsumowania wydajności](../profiling/media/performancesummary.png "PerformanceSummary")

4. Profiler używa również zestawu reguł, aby sugerować sposoby ulepszania przebiegu profilowania i identyfikowania możliwych problemów z wydajnością. Jeśli problem zostanie znaleziony, w oknie Lista błędów zostanie **wyświetlone ostrzeżenie.** Aby otworzyć okno **Lista błędów,** w menu **Widok** kliknij pozycję **Lista błędów**.

    - Aby wyświetlić funkcję, która wyedytowała ostrzeżenie w widoku **Szczegóły funkcji,** kliknij dwukrotnie ostrzeżenie.

    - Aby wyświetlić szczegółowe informacje o ostrzeżeniu, kliknij prawym przyciskiem myszy błąd, a następnie kliknij polecenie **Pokaż pomoc o błędzie**

## <a name="step-3-revise-code-and-rerun-a-session"></a>Krok 3. Poprawianie kodu i ponowne uruchomić sesję
 Po odnalezieniu i zoptymalizowaniu co najmniej jednej funkcji możesz powtórzyć przebieg profilowania i porównać dane, aby zobaczyć różnicę w wydajności aplikacji.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Aby poprawić kod i ponownie uruchomić profilera

1. Zmień kod.

2. Aby otworzyć **Eksplorator wydajności**, w menu **Debugowanie** kliknij pozycję **Profiler,** a następnie Eksplorator wydajności **a** następnie kliknij pozycję **Pokaż Eksplorator wydajności.**

3. W **Eksplorator wydajności** kliknij prawym przyciskiem myszy sesję, którą chcesz ponownie uruchomić, a następnie kliknij polecenie **Uruchom z profilowaniem.**

4. Po kolejnym zakończeniu sesji do folderu Raporty zostanie dodany inny plik danych dla sesji w Eksplorator wydajności **.**  Wybierz zarówno oryginalne, jak i nowe dane profilowania, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij polecenie **Porównaj raporty wydajności.**

     Zostanie otwarte nowe okno raportu z wyświetlonymi wynikami porównania. Aby uzyskać więcej informacji na temat sposobu korzystania z widoku porównania, zobacz [How to: Compare performance data files (Jak porównać pliki danych wydajności).](../profiling/how-to-compare-performance-data-files.md)

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
- [Rozpoczęcie pracy](../profiling/getting-started-with-performance-tools.md)
- [Omówienia](../profiling/overviews-performance-tools.md)
- [Profilowanie w Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
