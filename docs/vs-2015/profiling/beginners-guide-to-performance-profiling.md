---
title: Początkujący Przewodnik dotyczący profilowania wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecfd329e0e5c096e6e0c2011b60cd97dcd1c2937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64838045"
---
# <a name="beginners-guide-to-performance-profiling"></a>Profilowanie wydajności — Przewodnik dla początkujących
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby analizować problemy z wydajnością w aplikacji, można użyć programu Visual Studio narzędzia profilowania. Ta procedura pokazuje, jak używać danych **próbkowania** .  
  
 **Próbkowanie** to statystyczna Metoda profilowania, która pokazuje funkcje, które wykonuje większość pracy w trybie użytkownika w aplikacji. Pobieranie próbek jest dobrym miejscem do rozpoczęcia wyszukiwania obszarów w celu przyspieszenia działania aplikacji.  
  
 W określonych odstępach czasu Metoda **próbkowania** zbiera informacje o funkcjach, które są wykonywane w aplikacji. Po zakończeniu przebiegu profilowania widok **Podsumowanie** danych profilowania pokazuje najbardziej aktywne drzewo wywołań funkcji, nazywane **ścieżką gorącą**, gdzie większość pracy w aplikacji została wykonana. Widok zawiera również listę funkcji, które były wykonywane z największą ilością pracy, i zawiera wykres osi czasu, którego można użyć do skoncentrowania się na określonych segmentach sesji próbkowania.  
  
 Jeśli **próbkowanie** nie daje potrzebnych danych, inne metody zbierania narzędzi profilowania zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. Aby uzyskać więcej informacji o tych innych metodach, zobacz [How to: Choose Method Collections](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
> Jeśli utworzysz kod, który wywołuje funkcje systemu Windows, upewnij się, że masz najbardziej aktualne pliki. pdb. Bez tych plików widoki raportów wyświetlają nazwy funkcji systemu Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji o tym, jak upewnić się, że masz potrzebne pliki, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="create-and-run-a-performance-session"></a><a name="Step1"></a> Tworzenie i uruchamianie sesji wydajności  
 Aby uzyskać dane, które należy analizować, należy najpierw utworzyć sesję wydajności, a następnie uruchomić sesję. **Kreator wydajności** pozwala wykonać obie czynności.  
  
 Jeśli nie masz profilowania aplikacji klasycznych systemu Windows lub aplikacji ASP.NET, musisz użyć jednego z innych narzędzi profilowania. Zobacz [narzędzia profilowania](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Aby utworzyć i uruchomić sesję wydajności  
  
1. Otwórz rozwiązanie w programie Visual Studio. Skonfiguruj konfigurację do wydania. (Znajdź pozycję **konfiguracje rozwiązania** na pasku narzędzi, która domyślnie jest ustawiona na wartość **Debuguj** . Zmień go na **Release**.)  
  
    > [!IMPORTANT]
    > Jeśli nie jesteś administratorem na komputerze, którego używasz, musisz uruchomić program Visual Studio jako administrator, gdy korzystasz z profilera. (Kliknij prawym przyciskiem myszy ikonę aplikacji Visual Studio, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
2. W menu **debugowanie** kliknij pozycję **Profiler wydajności**.  
  
3. Sprawdź opcję **Kreatora wydajności** , a następnie kliknij przycisk **Uruchom**.  
  
4. Sprawdź opcję **próbkowania procesora (zalecane)** , a następnie kliknij przycisk **Zakończ**.  
  
5. Aplikacja zostanie uruchomiona, a Profiler zacznie zbierać dane.  
  
6. Korzystanie z funkcji, które mogą zawierać problemy z wydajnością.  
  
7. Zamknij aplikację jak zwykle.  
  
     Po zakończeniu działania aplikacji widok **podsumowania** danych profilowania pojawia się w głównym oknie programu Visual Studio, a ikona nowej sesji zostanie wyświetlona w oknie **Eksplorator wydajności** .  
  
## <a name="step-2-analyze-sampling-data"></a><a name="Step2"></a> Krok 2. analizowanie danych próbkowania  
 Po zakończeniu wykonywania sesji wydajności widok **Podsumowanie** raportu profilowania jest wyświetlany w oknie głównym w programie Visual Studio.  
  
 Zalecamy, aby rozpocząć analizowanie danych **, sprawdzając ścieżkę gorącą,** a następnie listę funkcji, które są w największym działaniu, a wreszcie przez skoncentrowanie się na innych funkcjach przy użyciu **podsumowania osi czasu**. Możesz również wyświetlić sugestie dotyczące profilowania i ostrzeżenia w oknie **Lista błędów** .  
  
 Należy pamiętać, że metoda próbkowania może nie podawać potrzebnych informacji. Przykładowo przykłady są zbierane tylko wtedy, gdy aplikacja wykonuje kod trybu użytkownika. W związku z tym niektóre funkcje, takie jak operacje wejścia i wyjścia, nie są przechwytywane przez próbkowanie. Narzędzia profilowania zapewnić kilka metod zbierania danych, które umożliwiają skoncentrowanie się na ważnych informacjach. Aby uzyskać więcej informacji o innych metodach, zobacz [How to: Choose Method Collections](../profiling/how-to-choose-collection-methods.md).  
  
 Każdy numerowany obszar na rysunku odnosi się do kroku procedury.  
  
 ![Widok raportu podsumowania do próbkowania](../profiling/media/summary-sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Aby analizować dane próbkowania  
  
1. W widoku **podsumowania** **ścieżka gorąca** pokazuje gałąź drzewa wywołań aplikacji z najwyższymi próbkami włącznie. Jest to ścieżka wykonywania, która była najbardziej aktywna podczas zbierania danych. Wysokie wartości łączne mogą wskazywać, że algorytm generujący drzewo wywołań może zostać zoptymalizowany. Znajdź funkcję w kodzie, który jest najniższy w ścieżce. Należy zauważyć, że ścieżka może również zawierać funkcje systemowe lub funkcje w modułach zewnętrznych.  
  
     ![Gorąca ścieżka profilera](../profiling/media/profiler-hotpath.png "Profiler_HotPath")  
  
    1. **Próbki włączne** wskazują, ile pracy zostało wykonane przez funkcję i wszystkich funkcji wywoływanych przez nią. Duże liczby łączne wskazują funkcje, które są najbardziej kosztowne.  
  
    2. **Próbki wyłączne** wskazują, ile pracy zostało wykonane przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały przez nią wywołane. Duże liczby wyłączne mogą wskazywać wąskie gardła wydajności w samej funkcji.  
  
2. Kliknij nazwę funkcji, aby wyświetlić widok **Szczegóły funkcji** dla danych profilowania. Widok **Szczegóły funkcji** przedstawia widok graficzny danych profilowania dla wybranej funkcji, pokazując wszystkie funkcje, które wywołały tę funkcję i wszystkie funkcje, które zostały wywołane przez wybraną funkcję.  
  
    - Rozmiar bloków wywoływanych i wywoływanych funkcji reprezentuje względną częstotliwość, z jaką funkcje wywołane lub zostały wywołane.  
  
    - Możesz kliknąć nazwę funkcji wywołującej lub wywoływanej, aby ją wybrać w widoku Szczegóły funkcji.  
  
    - W dolnym okienku okna **Szczegóły funkcji** jest wyświetlany sam kod funkcji. Jeśli przebadasz kod i znajdziesz szansę optymalizacji jej wydajności, kliknij nazwę pliku źródłowego, aby otworzyć plik w edytorze programu Visual Studio.  
  
3. Aby kontynuować analizę, Wróć do widoku **Podsumowanie** , wybierając pozycję **Podsumowanie** na liście rozwijanej widok. Następnie należy przeanalizować funkcje w **funkcjach wykonujących najwięcej zadań**. Ta lista zawiera funkcje z najwyższymi wyłącznymi próbkami. Kod w treści funkcji tych funkcji wykonuje znaczną ilość pracy i można go zoptymalizować. Aby dodatkowo analizować konkretną funkcję, kliknij nazwę funkcji, aby wyświetlić ją w widoku **Szczegóły funkcji** .  
  
     ![Lista funkcji, które działają najlepiej](../profiling/media/functions-mostwork.png "Functions_MostWork")  
  
     Aby kontynuować badanie przebiegu profilowania, można ponownie przeanalizować segment danych profilowania przy użyciu osi czasu w widoku **Podsumowanie** , aby wyświetlić **gorącą ścieżkę** i **funkcje wykonujące najwięcej pracy** z wybranego segmentu. Na przykład skoncentrowanie się na mniejszym szczycie na osi czasu może ujawnić kosztowne drzewa wywołań i funkcje, które nie były widoczne w analizie całego przebiegu profilowania.  
  
     Aby ponownie przeanalizować segment, zaznacz segment w polu Podsumowanie osi czasu, a następnie kliknij przycisk **Filtruj według wyboru**.  
  
     ![Oś czasu widoku podsumowania wydajności](../profiling/media/performancesummary.png "PerformanceSummary")  
  
4. Profiler używa również zestawu reguł, aby zasugerować sposoby ulepszania przebiegu profilowania i identyfikowania możliwych problemów z wydajnością. W przypadku znalezienia problemu w oknie **Lista błędów** zostanie wyświetlone ostrzeżenie. Aby otworzyć okno **Lista błędów** , w menu **widok** kliknij pozycję **Lista błędów**.  
  
    - Aby wyświetlić funkcję, która wywołała ostrzeżenie widoku **Szczegóły funkcji** , kliknij dwukrotnie ostrzeżenie.  
  
    - Aby wyświetlić szczegółowe informacje na temat ostrzeżenia, kliknij błąd prawym przyciskiem myszy, a następnie kliknij polecenie **Pokaż pomoc błędu** .  
  
## <a name="step-3-revise-code-and-rerun-a-session"></a><a name="Step3"></a> Krok 3. Popraw kod i ponownie uruchom sesję  
 Po znalezieniu i optymalizacji co najmniej jednej funkcji można powtórzyć przebieg profilowania i porównać dane, aby zobaczyć różnicę zmiany wydajności aplikacji.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Aby poprawić kod i ponownie uruchomić Profiler  
  
1. Zmień swój kod.  
  
2. Aby otworzyć **Eksplorator wydajności**, w menu **debugowanie** kliknij pozycję **Profiler**, a następnie **Eksplorator wydajności** a następnie kliknij pozycję **Pokaż Eksplorator wydajności**.  
  
3. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję, którą chcesz ponownie uruchomić, a następnie kliknij polecenie **Uruchom z profilem.**  
  
4. Po ponownym uruchomieniu sesji do folderu **Reports** zostanie dodany inny plik danych dla sesji w **Eksplorator wydajności**. Wybierz zarówno oryginalne, jak i nowe dane profilowania, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij **PORÓWNAJ raporty wydajności**.  
  
     Zostanie otwarte nowe okno raportu, w którym wyświetlane są wyniki porównania. Aby uzyskać więcej informacji o sposobach korzystania z widoku porównania, zobacz [How to: Compare Data Performance Files](../profiling/how-to-compare-performance-data-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Omówienia](../profiling/overviews-performance-tools.md)
