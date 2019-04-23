---
title: Początkujących przewodnik dotyczący profilowanie wydajności | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3b2421a8c1002e8fed1830a9de51383c35c01393
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059230"
---
# <a name="beginners-guide-to-performance-profiling"></a>Profilowanie wydajności — Przewodnik dla początkujących
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą programu Visual Studio Profiling Tools do analizowania problemów z wydajnością w aplikacji. Poniższa procedura przedstawia sposób użycia **próbkowania** danych.  
  
 **Próbkowanie** jest statystyczną metodą profilowania, która pokazuje funkcje, które wykonują większość trybu użytkownika działają w aplikacji. Pobieranie próbek jest dobrym miejscem do rozpoczęcia wyszukiwania obszarów przyspieszania działania aplikacji.  
  
 W określonych odstępach czasu **próbkowania** metoda zbiera informacje o funkcjach, które są wykonywane w aplikacji. Po zakończeniu przebiegu profilowania **Podsumowanie** widok profilowania danych zawiera drzewo wywołań najbardziej aktywnych funkcji o nazwie **ścieżka aktywna**, gdzie większość pracy w aplikacji zostało wykonane. Widok również Wyświetla listę funkcji, które wykonywały najbardziej indywidualną pracę i zawiera wykres osi czasu, w którym można skupić się na poszczególnych segmentach sesji pobierania próbek.  
  
 Jeśli **próbkowania** nie oferują danych, których potrzebują, innych metod profilowania kolekcji tools zapewniają różne rodzaje informacji, które mogą być pomocne dla użytkownika. Aby uzyskać więcej informacji o tych innych metodach, zobacz [jak: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md).  
  
> [!TIP]
>  Jeśli profilowany kod wywołuje funkcje Windows, należy upewnić się, że najbardziej aktualne pliki PDB. Bez tych plików widok raportu wyświetli listę nazw funkcji Windows, które są tajemnicze i trudne do zrozumienia. Aby uzyskać więcej informacji na temat upewnij się, że pliki potrzebne Ci zobacz [jak: Informacje o symbolach Windows odwołanie](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="Step1"></a> Tworzenie i uruchamianie sesji wydajności  
 Aby uzyskać dane potrzebne do analizowania, należy najpierw utworzyć sesję wydajności, a następnie uruchom sesji. **Kreatora wydajności** pozwala wykonać obie czynności.  
  
 Jeśli nie profilowany aplikację Windows lub aplikacji platformy ASP.NET, należy użyć jednego z innych narzędzi do profilowania. Zobacz [narzędzia profilowania](../profiling/profiling-tools.md).  
  
#### <a name="to-create-and-run-a-performance-session"></a>Aby utworzyć i uruchomić sesję wydajności  
  
1. Otwórz rozwiązanie w programie Visual Studio. Ustaw konfigurację do wydania. (Znajdź **konfiguracje rozwiązania** na pasku narzędzi, który jest ustawiony na **debugowania** domyślnie. Zmień ją na **wersji**.)  
  
    > [!IMPORTANT]
    >  Jeśli nie jesteś administratorem na komputerze, którego używasz, należy uruchamiać Visual Studio jako administrator, podczas korzystania z programu profilującego. (Kliknij prawym przyciskiem myszy ikonę aplikacji Visual Studio, a następnie kliknij przycisk **Uruchom jako administrator**.  
  
2. Na **debugowania** menu, kliknij przycisk **Profiler wydajności**.  
  
3. Sprawdź **kreatora wydajności** opcji, a następnie kliknij przycisk **Start**.  
  
4. Sprawdź **próbkowania Procesora (zalecane)** opcji, a następnie kliknij przycisk **Zakończ**.  
  
5. Aplikacja uruchamia się i program profiler uruchamia zbieranie danych.  
  
6. Przetestuj funkcjonalność, która może zawierać problemy z wydajnością.  
  
7. Zamknij aplikację, tak jak zwykle.  
  
     Po zakończeniu działania aplikacji, **Podsumowanie** widok danych profilowania pojawia się w głównym oknie programu Visual Studio i pojawi się ikona nowej sesji w **Eksplorator wydajności** okna.  
  
## <a name="Step2"></a> Krok 2: Analizowanie danych próbkowania  
 Po zakończeniu pracy z sesją wydajności **Podsumowanie** widok raportu profilowania pojawia się w głównym oknie programu Visual Studio.  
  
 Zaleca się rozpocząć analizowanie danych, sprawdzając **ścieżka aktywna** , a następnie listy funkcji, które wykonują najwięcej pracy i ostatecznie przez skupienie się na inne funkcje za pomocą **podsumowania osi czasu** . Można również wyświetlać sugestie profilowania i ostrzeżenia w **lista błędów** okna.  
  
 Należy pamiętać, że metoda pobierania próbek może nie dać użytkownikowi potrzebnych informacji. Na przykład próbki są pobierane tylko wtedy, gdy aplikacja wykonuje kod w trybie użytkownika. W związku z tym niektóre funkcje, takie jak operacje wejścia i wyjścia, nie są przechwytywane przez pobieranie próbek. Narzędzia profilowania zapewniają kilka metod zbierania, które umożliwiają skupić się na ważnych danych. Aby uzyskać więcej informacji o innych metodach, zobacz [jak: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md).  
  
 Każdy ponumerowany obszar na rysunku dotyczy kroku procedury.  
  
 ![Wyświetl raport podsumowujący dla pobierania próbek](../profiling/media/summary-sampling.png "Summary_Sampling")  
  
#### <a name="to-analyze-sampling-data"></a>Aby przeanalizować dane próbkowania  
  
1. W **Podsumowanie** widoku **ścieżka aktywna** zawiera gałąź drzewa wywołań aplikacji z najwyższymi próbkami włącznie. Jest to ścieżka wykonania, która był najbardziej aktywna, gdy zbierano dane. Wysokie wartości włącznie może wskazywać, że algorytm, który generuje drzewo wywołań, mogą być optymalizowane. Znajdź funkcję w kodzie, która jest najniższa w ścieżce. Należy zauważyć, że ścieżka może również zawierać funkcje systemu lub funkcje zewnętrznych modułów.  
  
     ![Profiler Hot Path](../profiling/media/profiler-hotpath.png "Profiler_HotPath")  
  
    1. **Próbki włączne** wskazuje, ile pracy zostało wykonanej przez funkcję i wszystkie funkcje wywoływane przez nią. Wysoka wartość łączna wskazuje funkcje, które są najbardziej kosztowne.  
  
    2. **Próbki wyłączne** wskazuje, ile pracy zostało wykonanej przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały przez nią wywołane. Wysoka pozostałych może wskazać wąskie gardło w samej funkcji.  
  
2. Kliknij nazwę funkcji, aby wyświetlić **Szczegóły funkcji** widoku danych profilowania. **Szczegóły funkcji** widoku przedstawia widok graficzny danych profilowania dla wybranej funkcji, przedstawiający wszystkie funkcje, które wywoływały tą funkcję i wszystkie funkcje, które były wywoływane przez wybraną funkcję.  
  
    - Rozmiar bloków wywołujących i wywołanych funkcji reprezentuje względną częstotliwość, z którą funkcje wywoływane funkcje lub były wywoływane.  
  
    - Można kliknąć nazwę wywołującej lub wywoływanej funkcji, aby stał się wybrać funkcję widoku szczegółów funkcji.  
  
    - W dolnym okienku **Szczegóły funkcji** system windows wyświetli sam kod funkcji. Jeśli sprawdzono kod i znaleziono szansę zoptymalizowania wydajności, kliknij nazwę pliku źródłowego, aby otworzyć go w edytorze programu Visual Studio.  
  
3. Aby kontynuować analizę, powróć do **Podsumowanie** widoku, wybierając **Podsumowanie** z listy rozwijanej widoku. Następnie zbadaj funkcje w **funkcje wykonujące najwięcej pracy poszczególnych**. Lista ta wyświetla funkcje z najwyższą wartością wyłączną próbek. Kod w treści funkcji z tych funkcji wykonuje znaczną pracę i można ją zoptymalizować. Do dalszej analizy określonej funkcji, kliknij nazwę funkcji, aby wyświetlić ją w **Szczegóły funkcji** widoku.  
  
     ![Lista funkcji, które wykonują najwięcej pracy](../profiling/media/functions-mostwork.png "Functions_MostWork")  
  
     Aby kontynuować badanie uruchomienia profilowania, użytkownik może ponownie przeanalizować segment danych profilowania za pomocą osi czasu w **Podsumowanie** widok, aby pokazać **ścieżka aktywna** i **funkcji Wykonując najbardziej samodzielnej pracy** z wybranego segmentu. Na przykład skupiając się na mniejszych pikach na osi czasu może ujawnić drogie wywołań i funkcje, które nie były pokazane w analizie całego uruchomienia profilowania.  
  
     Aby ponownie przeanalizować segment, zaznacz segment w polu Podsumowanie osi czasu, a następnie kliknij przycisk **filtru według zaznaczenia**.  
  
     ![Oś czasu widoku podsumowania wydajności](../profiling/media/performancesummary.png "PerformanceSummary")  
  
4. Profiler używa także zestawu reguł, sugerujących sposoby poprawy uruchomienia profilowania i identyfikowania możliwych problemów z wydajnością. Jeśli problem zostanie znaleziony, wyświetlane jest ostrzeżenie w **lista błędów** okna. Aby otworzyć **lista błędów** okna na **widoku** kliknij menu **lista błędów**.  
  
    - Aby zobaczyć funkcję, która wzbudziła ostrzeżenie **Szczegóły funkcji** wyświetlić, kliknij dwukrotnie ostrzeżenie.  
  
    - Aby wyświetlić szczegółowe informacje na temat ostrzeżenia, kliknij prawym przyciskiem myszy błąd, a następnie kliknij przycisk **Pokaż Pomoc błędu**  
  
## <a name="Step3"></a> Krok 3: Poprawa kodu i ponowne uruchomienie sesji  
 Po znalezieniu i zoptymalizowaniu jednej lub więcej funkcji, można powtórzyć uruchomienie profilowania i porównać dane, aby wyświetlić tą różnicą, że wprowadzono zmiany wydajności aplikacji.  
  
#### <a name="to-revise-code-and-rerun-the-profiler"></a>Aby poprawić kod i uruchomić ponownie program profiler  
  
1. Zmień swój kod.  
  
2. Aby otworzyć **Eksplorator wydajności**na **debugowania** kliknij menu **Profiler**, następnie **Eksplorator wydajności** a następnie kliknij przycisk **Pokaż Eksploratora wydajności**.  
  
3. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję, który chcesz ponownie uruchomić, a następnie kliknij przycisk **uruchamianie z profilowaniem.**  
  
4. Po ponownym uruchomieniu sesji inny plik danych jest dodawany do **raporty** folder dla sesji w **Eksplorator wydajności**. Wybierz zarówno oryginał, a nowe dane profilowania, kliknij prawym przyciskiem myszy zaznaczenie, a następnie kliknij przycisk **Porównaj wydajność raportów**.  
  
     Zostanie otwarte nowe okno raportu, wyświetlające wyniki porównania. Aby uzyskać więcej informacji na temat sposobu korzystania z widoku porównania, zobacz [jak: Porównywanie plików danych dotyczących wydajności](../profiling/how-to-compare-performance-data-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Omówienia](../profiling/overviews-performance-tools.md)
