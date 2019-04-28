---
title: Opis metodami zbierania danych wydajności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e398d7e5e297daa68663902efb8a9fa0775c86fa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431640"
---
# <a name="understanding-performance-collection-methods"></a>Opis metodami zbierania danych wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakiet Visual Studio Profiling Tools oferuje pięć metod zbierania informacji o wydajności. W tym temacie opisano różne metody oraz zasugerowano kilka scenariuszy zbierania danych za pomocą konkretnych metod.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Próbkowania](#sampling)|Zbiera dane statystyczne o pracy wykonanej przez aplikację.|  
|[Instrumentacja](#instrumentation)|Zbiera szczegółowe informacje o czasach wywołania każdej funkcji.|  
|[Współbieżność](#concurrency)|Zbiera szczegółowe informacje o aplikacjach wielowątkowych.|  
|[Pamięć .NET](#net_memory)|Zbiera szczegółowe informacje o przydzielaniu pamięci i wyrzucania elementów bezużytecznych w środowisku .NET.|  
|[Interakcje między warstwami](#tier_interaction)|Zbiera informacje o synchronicznych wywołaniach funkcji środowiska ADO.NET do bazy danych programu SqlServer.<br /><br /> Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] i [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)], natomiast obejrzeć takie dane można tylko w programach [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] i [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|  
  
 Za pomocą niektórych metod profilowania można również gromadzić inne dane, takie jak informacje z liczników wydajności oprogramowania i sprzętu. Aby uzyskać więcej informacji, zobacz [zbieranie dodatkowych danych wydajności](../profiling/collecting-additional-performance-data.md).  
  
## <a name="sampling"></a> Próbkowania  
 Metoda profilowania Próbkowanie zbiera dane statystyczne o pracy wykonywanej przez aplikację w trakcie sesji profilowania. Mechanizm próbkowania ma uproszczoną konstrukcję i w bardzo niewielkim stopniu wpływa na wykonywanie metod aplikacji.  
  
 Próbkowanie jest metodą domyślną w pakiecie Visual Studio Profiling Tools. Najlepiej sprawdza się w następujących zastosowaniach:  
  
- Początkowe badania wydajności aplikacji.  
  
- Badanie problemów z wydajnością nawiązujących do wykorzystania procesora (CPU).  
  
  Metoda profilowania Próbkowanie przerywa działanie procesora komputera w ustalonych odstępach czasu i sczytuje stos wywołań funkcji. Liczby próbek wyłącznych są zwiększane dla funkcji wykonywanej, natomiast liczby próbek włącznych są zwiększane dla wszystkich funkcji wywołujących w stosie wywołań. Raporty z próbkowania przedstawiają łączne wartości tych liczb dla profilowanego modułu, funkcji, wiersza kodu źródłowego i instrukcji.  
  
  Domyślnie profiler ustawia interwał próbkowania równy długości cyklu procesora. Można zmienić typ interwału na inny licznik wydajności procesora, a także ustawić liczbę zdarzeń licznika dla tego interwału. Istnieje też możliwość gromadzenia danych o profilowaniu interakcji między warstwami (TIP), które dostarczają informacji o zapytaniach wykonywanych w bazie danych programu SQL Serwer za pośrednictwem środowiska ADO.NET.  
  
  [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [Zapoznanie z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)  
  
  [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)  
  
## <a name="instrumentation"></a> Instrumentacja  
 Metoda profilowania Instrumentacja zbiera szczegółowe informacje o czasach wywołania funkcji w profilowanej aplikacji. Profilowanie za pomocą instrumentacji najlepiej sprawdza się w następujących sytuacjach:  
  
- Badanie wąskich gardeł na wejściu/wyjściu, takich jak interfejsy we/wy dysku.  
  
- Dokładne badanie konkretnego modułu lub zbioru funkcji.  
  
  Metoda Instrumentacja wprowadza do pliku binarnego kod, który wykrywa informacje o czasie działania każdej funkcji w instrumentowanym pliku oraz o każdym wywołaniu funkcji wykonanym przez te funkcje. Metoda rozpoznaje również, kiedy funkcja wywołuje operacje takie jak zapisywanie do pliku. Raporty z instrumentacji zawierają cztery wartości pokazujące łączny czas spędzony w funkcji lub wierszu kodu źródłowego:  
  
- Upłynęło włącznie — Łączny czas spędzony na wykonywaniu funkcji lub wiersza kodu źródłowego.  
  
- Aplikacja włącznie — Czas spędzony na wykonywaniu funkcji lub wiersza kodu źródłowego, z wyłączeniem czasu spędzonego w wywołaniach do systemu operacyjnego.  
  
- Upłynęło wyłącznie — Czas spędzony na wykonywaniu kodu w treści funkcji lub wierszu kodu źródłowego. Nie obejmuje czasu spędzonego na wykonywaniu funkcji wywołanych przez funkcję lub wiersz kodu źródłowego.  
  
- Aplikacja wyłącznie — Czas spędzony na wykonywaniu kodu w treści funkcji lub wierszu kodu źródłowego. Nie obejmuje czasu spędzonego na wykonywaniu wywołań do systemu operacyjnego ani czasu spędzonego na wykonywaniu funkcji wywołanych przez funkcję lub wiersz kodu źródłowego.  
  
  Metoda Instrumentacja pozwala gromadzić dane z liczników wydajności procesora i oprogramowania.  
  
  [Zapoznanie z wartościami danych instrumentacji](../profiling/understanding-instrumentation-data-values.md)  
  
  [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)  
  
## <a name="concurrency"></a> Współbieżność  
 Metoda profilowania Współbieżność zbiera informacje o aplikacjach wielowątkowych. Metoda profilowania Rywalizacja o zasoby zbiera szczegółowe informacje o stosie wywołań w każdym przypadku, gdy konkurencyjne wątki są zmuszone czekać na dostęp do wspólnego zasobu. Mechanizm wizualizacji współbieżności zbiera również bardziej ogólne informacje o wewnętrznych interakcjach aplikacji wielowątkowej, a także o jej interakcjach ze sprzętem, systemem operacyjnym i innymi procesami na komputerze hosta:  
  
- Raporty z rywalizacji o zasoby pokazują łączną liczbę zdarzeń rywalizacji oraz całkowity czas spędzony przez moduły, funkcje, wiersze kodu źródłowego i instrukcje w oczekiwaniu na zasoby. Wykresy z osią czasu pokazują również momenty, w których dochodzi do rywalizacji.  
  
- Wizualizator współbieżności przedstawia w formie graficznej informacje mogące służyć do identyfikowania wąskich gardeł wydajności, zdarzeń niepełnego wykorzystania procesora, rywalizacji wątków i migracji wątków, opóźnień synchronizacji, obszarów nakładania się wejść/wyjść itd. W miarę możliwości prezentacja graficzna zawiera odwołania do odnośnych danych w wywołaniach stosów i kodzie źródłowym. Wizualizacje współbieżności można generować tylko dla aplikacji wiersza polecenia i aplikacji systemu Windows.  
  
  [Zapoznanie z wartościami danych rywalizacji o zasoby](../profiling/understanding-resource-contention-data-values.md)  
  
  [Zbieranie danych współbieżności dla wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)  
  
  [Concurrency Visualizer](../profiling/concurrency-visualizer.md)  
  
## <a name="net_memory"></a> Pamięć .NET  
 Metoda profilowania za pomocą alokacji pamięci środowiska .NET przerywa działanie procesora komputera na każdym zdarzeniu przydziału obiektu środowiska .NET Framework w profilowanej aplikacji. Jeśli są zbierane również informacje o okresie istnienia obiektu, profiler przerywa działanie procesora po każdym zdarzeniu wyrzucania elementów bezużytecznych w środowisku .NET Framework.  
  
 Profiler gromadzi informacje o typie, rozmiarze i liczbie obiektów utworzonych w alokacji lub zniszczonych podczas wyrzucania elementów bezużytecznych.  
  
- Gdy wystąpi zdarzenie alokacji, profiler zbiera dodatkowe informacje o stosie wywołań funkcji. Liczby alokacji wyłącznych są zwiększane dla funkcji aktualnie wykonywanej, natomiast liczby alokacji włącznych są zwiększane dla wszystkich funkcji wywołujących w stosie wywołań. Raporty ze środowiska .NET przedstawiają łączne wartości tych liczb dla profilowanych typów, modułów, funkcji, wierszy kodu źródłowego i instrukcji.  
  
- Jeśli dochodzi do wyrzucania elementów bezużytecznych, profiler zbiera dane o obiektach zniszczonych oraz obiektach uwzględnionych we wszystkich generacjach wyrzucania. Na zakończenie sesji profilowania profiler zapisuje dane o obiektach, które nie zostały jawnie zniszczone. Raport o okresie istnienia obiektu przedstawia łączne wartości dla wszystkich typów przydzielonych w sesji profilowania.  
  
  Profilowania pamięci środowiska .NET można używać w trybach próbkowania i instrumentacji. Wybrany tryb nie wpływa na raporty o alokacji i okresie istnienia obiektu specyficzne dla tej metody profilowania:  
  
- Gdy profilowanie pamięci .NET jest wykonywane w trybie próbkowania, profiler środowiska .NET jako interwału używa zdarzeń alokacji pamięci, a liczbę przydzielonych obiektów i łączną liczbę przydzielonych bajtów pokazuje w raportach jako wartości włączne i wyłączne.  
  
- Jeśli profilowanie pamięci .NET odbywa się w trybie instrumentacji, są zbierane szczegółowe informacje o czasie oraz o wartościach alokacji włącznie i wyłącznie.  
  
  [Zapoznanie z alokacją pamięci i wartościami danych o okresie istnienia obiektu](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="tier_interaction"></a> Interakcje między warstwami  
 Metoda profilowania na podstawie interakcji między warstwami dodaje do pliku danych profilowania informacje o synchronicznych wywołaniach [!INCLUDE[vstecado](../includes/vstecado-md.md)] między stroną utworzoną w środowisku [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] lub inną aplikacją a bazą danych programu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dane obejmują liczbę i godziny wywołań oraz maksymalne i minimalne czasy trwania wywołań. Dane interakcji między warstwami można dodawać do danych profilowania zbieranych za pomocą metod Próbkowanie, Instrumentacja, Pamięć .NET i Współbieżność.  
  
 ![Dane profilowanie interakcji pomiędzy warstwami](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
Dane interakcji między warstwami gromadzone przez narzędzia pakietu Profiling Tools  
  
 [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)  
  
 [Widoki interakcji między warstwami](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zbieranie danych dotyczących wydajności dla witryny sieci Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)
