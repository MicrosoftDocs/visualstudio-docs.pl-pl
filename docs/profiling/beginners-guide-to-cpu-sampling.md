---
title: Przewodnik dla początkujących do pobierania próbek procesora
ms.custom: seodec18
ms.date: 02/27/2017
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6a5a0eb84e4f06fd1b4dd248a1bce952b2c7197
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779808"
---
# <a name="beginners-guide-to-cpu-sampling"></a>Przewodnik dla początkujących do pobierania próbek procesora
Narzędzia do profilowania programu Visual Studio umożliwiają analizowanie problemów z wydajnością w aplikacji. W tej procedurze pokazano, jak używać danych **próbkowania.**

> [!NOTE]
> Zaleca się użycie narzędzia [Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md) w oknie Narzędzia diagnostyczne zamiast starszego narzędzia do pobierania próbek procesora CPU, chyba że potrzebne są specjalistyczne funkcje, takie jak obsługa instrumentacji.

 **Próbkowanie** jest statystyczną metodą profilowania, która pokazuje funkcje, które wykonują większość pracy w trybie użytkownika w aplikacji. Próbkowanie jest dobrym miejscem, aby rozpocząć szukać obszarów, aby przyspieszyć aplikację.

 W określonych odstępach czasu **próbkowanie** metoda zbiera informacje o funkcjach, które są wykonywane w aplikacji. Po zakończeniu przebiegu profilowania widok **Podsumowanie** danych profilowania pokazuje najbardziej aktywne drzewo wywołań funkcji, zwane **gorącą ścieżką**, w którym wykonano większość pracy w aplikacji. Widok zawiera również listę funkcji, które wykonywały najbardziej indywidualną pracę i zawiera wykres osi czasu, którego można użyć do skupienia się na określonych segmentach sesji próbkowania.

 Jeśli **próbkowanie** nie daje danych, które są potrzebne, inne metody zbierania narzędzi profilowania zapewniają różne rodzaje informacji, które mogą być pomocne dla Ciebie. Aby uzyskać więcej informacji na temat tych innych metod, zobacz [Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md).

> [!TIP]
> Jeśli kod profilu, który wywołuje funkcje systemu Windows, należy upewnić się, że masz najbardziej aktualne . *plików pdb.* Bez tych plików widoki raportu będą wyświetlać nazwy funkcji systemu Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji o tym, jak upewnić się, że masz potrzebne pliki, zobacz [Jak: Odwoływanie się do informacji o symbolu systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).

## <a name="create-and-run-a-performance-session"></a>Tworzenie i uruchamianie sesji wydajności
 Aby uzyskać dane, które należy analizować, należy najpierw utworzyć sesję wydajności, a następnie uruchomić sesję. **Kreator wydajności** umożliwia wykonanie obu tych ekscesów.

 Jeśli nie profilujesz aplikacji klasycznej systemu Windows lub ASP.NET aplikacji, musisz użyć jednego z innych narzędzi profilowania. Zobacz [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md).

#### <a name="to-create-and-run-a-performance-session"></a>Aby utworzyć i uruchomić sesję wydajności

1. Otwórz rozwiązanie w programie Visual Studio. Ustaw konfigurację na Zwolnij. (Znajdź pole **Konfiguracje rozwiązań** na pasku narzędzi, które jest domyślnie ustawione na **Debugowanie.** Zmień go na **Release**.)

    > [!IMPORTANT]
    > Jeśli nie jesteś administratorem na używanym komputerze, należy uruchomić program Visual Studio jako administrator podczas korzystania z profilera. (Kliknij prawym przyciskiem myszy ikonę aplikacji programu Visual Studio, a następnie kliknij polecenie **Uruchom jako administrator**.

2. W menu **Debugowanie** wybierz pozycję **Profiler**, a następnie wybierz polecenie **Profiler wydajności**.

3. Sprawdź opcję **Kreator wydajności** i kliknij przycisk **Start**.

4. Sprawdź opcję **Próbkowanie procesora (zalecane)** i kliknij przycisk **Zakończ**.

5. Aplikacja zostanie uruchomiony i profiler rozpoczyna zbieranie danych.

6. Korzystaj z funkcji, które mogą zawierać problemy z wydajnością.

7. Zamknij aplikację w sposób zwykle.

     Po zakończeniu uruchamiania aplikacji w głównym oknie programu Visual Studio pojawi się widok **podsumowania** danych profilowania, a w oknie **Eksploratora wydajności** pojawi się ikona nowej sesji.

## <a name="step-2-analyze-sampling-data"></a>Krok 2: Analizowanie danych próbkowania
 Po zakończeniu uruchamiania sesji wydajności, **widok podsumowanie** raportu profilowania pojawia się w oknie głównym w programie Visual Studio.

 Zalecamy rozpoczęcie analizy danych, badając **gorącą ścieżkę,** następnie listę funkcji, które wykonują najwięcej pracy, a na koniec koncentrując się na innych funkcjach za pomocą **osi czasu podsumowania**. Sugestie profilowania i ostrzeżenia można również wyświetlać w oknie **Lista błędów.**

 Należy pamiętać, że metoda próbkowania może nie dać ci potrzebnych informacji. Na przykład przykład próbki są zbierane tylko wtedy, gdy aplikacja wykonuje kod trybu użytkownika. W związku z tym niektóre funkcje, takie jak operacje wejściowe i wyjściowe, nie jest przechwytywany przez próbkowanie. Narzędzia profilowania zapewniają kilka metod zbierania danych, które umożliwiają skupienie się na ważnych danych. Aby uzyskać więcej informacji na temat innych metod, zobacz [Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md).

 Każdy ponumerowany obszar na rysunku odnosi się do kroku w procedurze.

 ![Widok raportu podsumowującego do pobierania próbek](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Aby przeanalizować dane próbkowania

1. W widoku **Podsumowanie** **ścieżka gorąca** pokazuje gałąź drzewa wywołań aplikacji z najwyższymi przykładami włącznie. Jest to ścieżka wykonywania, która była najbardziej aktywna podczas zbierania danych. Wysokie wartości włącznie może wskazywać, że algorytm, który generuje drzewa wywołań można zoptymalizować. Znajdź funkcję w kodzie, która jest najniższa w ścieżce. Należy zauważyć, że ścieżka może również zawierać funkcje systemowe lub funkcje w modułach zewnętrznych.

     ![Ścieżka gorąca profilera](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Przykłady włącznie** wskazują, ile pracy zostało wykonane przez funkcję i wszystkie funkcje wywoływane przez nią. Wysoka liczba włącznie wskazują na funkcje, które są najdroższe ogólnej.

    2. **Próbki wyłączności** wskazują, ile pracy zostało wykonane przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały wywołane przez niego. Wysokie liczby wyłączności może wskazywać wąskie gardło wydajności w ramach samej funkcji.

2. Kliknij nazwę funkcji, aby wyświetlić widok **Szczegóły funkcji** danych profilowania. Widok **Szczegóły funkcji** przedstawia graficzny widok danych profilowania dla wybranej funkcji, przedstawiający wszystkie funkcje, które wywoływały tę funkcję i wszystkie funkcje, które zostały wywołane przez wybraną funkcję.

    - Rozmiar bloków wywoływania i wywoływanych funkcji reprezentują względną częstotliwość, że funkcje wywoływane lub były wywoływane.

    - Można kliknąć nazwę wywołania lub wywołanej funkcji, aby uczynić ją wybraną funkcją widoku Szczegóły funkcji.

    - W dolnym okienku okien **Szczegóły funkcji** jest wyświetlany sam kod funkcji. Jeśli zbadasz kod i znajdziesz możliwość optymalizacji jego wydajności, kliknij nazwę pliku źródłowego, aby otworzyć plik w edytorze Visual Studio.

3. Aby kontynuować analizę, wróć do widoku **Podsumowanie,** wybierając **pozycję Podsumowanie** z listy rozwijanej **Widok.** Następnie sprawdź funkcje w **funkcji wykonując najbardziej indywidualnej pracy**. Ta lista wyświetla funkcje z najwyższymi próbkami wyłączności. Kod w treści funkcji tych funkcji wykonywane znaczną pracę i może być w stanie zoptymalizować go. Aby dokładniej przeanalizować określoną funkcję, kliknij nazwę funkcji, aby wyświetlić ją w widoku **Szczegóły funkcji.**

     ![Lista funkcji wykonujących najwięcej pracy](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Aby kontynuować badanie przebiegu profilowania, można ponownie przeanalizować segment danych profilowania, korzystając z osi czasu w widoku **Podsumowanie,** aby wyświetlić **gorącą ścieżkę** i **funkcje wykonujące większość pracy indywidualnej** z wybranego segmentu. Na przykład skupienie się na mniejszym szczycie na osi czasu może ujawnić kosztowne drzewa wywołań i funkcje, które nie zostały pokazane w analizie całego przebiegu profilowania.

     Aby ponownie przeanalizować segment, zaznacz segment wewnątrz pola **Podsumowanie osi czasu,** a następnie kliknij pozycję **Filtruj według zaznaczenia**.

     ![Oś czasu widoku Podsumowanie skuteczności](../profiling/media/performancesummary.png "PerformanceSummary (WYD.")

4. Profilera używa również zestaw reguł, aby zaproponować sposoby poprawy przebiegu profilowania i zidentyfikować możliwe problemy z wydajnością. Jeśli problem zostanie znaleziony, ostrzeżenie jest wyświetlane w oknie **Lista błędów.** Aby otworzyć okno **Lista błędów,** w menu **Widok** kliknij polecenie **Lista błędów**.

    - Aby wyświetlić funkcję, która wywołała ostrzeżenie w widoku **Szczegóły funkcji,** kliknij dwukrotnie ostrzeżenie.

    - Aby wyświetlić szczegółowe informacje o ostrzeżeniu, kliknij prawym przyciskiem myszy błąd, a następnie kliknij polecenie **Pokaż Pomoc dotyczącą błędów**

## <a name="step-3-revise-code-and-rerun-a-session"></a>Krok 3: Poprawianie kodu i ponowne uruchomienie sesji
 Po znalezieniu i optymalizacji jednej lub więcej funkcji, można powtórzyć przebieg profilowania i porównać dane, aby zobaczyć różnicę, że zmiany zostały wprowadzone do wydajności aplikacji.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Aby poprawić kod i ponownie uruchomić profiler

1. Zmień swój kod.

2. Aby otworzyć **Eksplorator wydajności,** w menu **Debugowania** kliknij pozycję **Profiler**, a następnie **Eksplorator wydajności,** a następnie kliknij pozycję **Pokaż Eksploratora wydajności**.

3. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję, którą chcesz ponownie uruchomić, a następnie kliknij polecenie **Uruchom z profilowania.**

4. Po ponownym podaniu sesji do folderu *Raporty* dla sesji w **Eksploratorze wydajności**zostanie dodany inny plik danych . Zaznacz zarówno oryginalne, jak i nowe dane profilowania, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij polecenie **Porównaj raporty wydajności**.

     Zostanie otwarte nowe okno raportu z wynikami porównania. Aby uzyskać więcej informacji na temat korzystania z widoku porównania, zobacz [Jak: Porównywanie plików danych o wydajności](../profiling/how-to-compare-performance-data-files.md).

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
- [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)
- [Omówienia](../profiling/overviews-performance-tools.md)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
