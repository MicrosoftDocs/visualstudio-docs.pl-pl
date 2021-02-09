---
title: Informacje o metodach zbierania danych o wydajności | Microsoft Docs
description: Zapoznaj się z różnymi scenariuszami, w których zbierane są dane przy użyciu określonej metody.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8126d2331e126cf9162a0334b59be239684754c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886096"
---
# <a name="understand-performance-collection-methods"></a>Zrozumienie metod zbierania danych o wydajności

Narzędzia profilowania programu Visual Studio zapewniają pięć metod zbierania danych o wydajności. W tym artykule opisano różne metody i zasugerowano scenariusze, w których zbierane są dane przy użyciu określonej metody.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Metoda|Opis|
|------------|-----------------|
|[Próbkowanie](#sampling)|Zbiera dane statystyczne o pracy wykonanej przez aplikację.|
|[WMI](#instrumentation)|Zbiera szczegółowe informacje o czasach wywołania każdej funkcji.|
|[Współbieżność](#concurrency)|Zbiera szczegółowe informacje o aplikacjach wielowątkowych.|
|[Pamięć .NET](#net-memory)|Zbiera szczegółowe informacje o przydzielaniu pamięci i wyrzucania elementów bezużytecznych w środowisku .NET.|
|[Interakcje między warstwami](#tier-interaction)|Zbiera informacje o synchronicznych wywołaniach funkcji ADO.NET do bazy danych SQL Server.<br /><br /> Wszystkie wersje programu Visual Studio mogą zbierać dane profilu interakcji warstwowej. Można jednak wyświetlać te dane tylko w Visual Studio Enterprise.|

Korzystając z niektórych metod profilowania, można również zbierać dodatkowe dane, takie jak liczniki wydajności oprogramowania i sprzętu. Aby uzyskać więcej informacji, zobacz [zbieranie dodatkowych danych dotyczących wydajności](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Próbkowanie

Metoda profilowania próbkowania zbiera dane statystyczne o pracy wykonywanej przez aplikację podczas przebiegu profilowania. Metoda próbkowania jest lekki i ma niewielki wpływ na wykonywanie metod aplikacji.

Próbkowanie jest domyślną metodą narzędzi profilowania programu Visual Studio. Jest to przydatne w przypadku następujących zadań:

- Początkowe eksploracje wydajności aplikacji
- Badanie problemów z wydajnością, które obejmują wykorzystanie mikroprocesora (CPU)

Metoda profilowania próbkowania przerywa procesor komputera w ustalonych odstępach czasu i zbiera stos wywołań funkcji. Liczba wyłącznych próbek jest zwiększana dla funkcji, która jest uruchomiona. Liczby włączne są zwiększane dla wszystkich funkcji wywołujących w stosie wywołań. Raporty z próbkowania przedstawiają łączną liczbę tych liczb dla profilowanych modułów, funkcji, wierszy kodu źródłowego i instrukcji.

Domyślnie profiler ustawia interwał próbkowania równy długości cyklu procesora. Można zmienić typ interwału na inny licznik wydajności procesora lub ustawić liczbę zdarzeń licznika dla interwału. Można również zbierać dane dotyczące profilowania (w ramach interakcji z warstwą). Te dane zawierają informacje o zapytaniach do bazy danych SQL Server za pomocą ADO.NET.

[Zbieranie statystyk wydajności za pomocą próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)

[Przykładowe widoki danych metody](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Oprzyrządowanie

Metoda profilowania Instrumentacji zbiera szczegółowy czas dla wywołań funkcji w profilowanej aplikacji. Profilowanie Instrumentacji jest przydatne w następujących zadaniach:

- Badanie wąskich gardeł danych wejściowych/wyjściowych, takich jak we/wy dysku
- Zamknij badanie określonego modułu lub zestawu funkcji

Metoda Instrumentacji wprowadza kod do pliku binarnego. Kod przechwytuje informacje o chronometrażu dla wszystkich funkcji w pliku instrumentacji, a każda funkcja wywołuje te funkcje. Instrumentacja określa również, kiedy funkcja wywołuje system operacyjny w celu wykonywania operacji, takich jak zapis do pliku.

Raporty Instrumentacji wykorzystują te cztery wartości do reprezentowania łącznego czasu spędzonego w wierszu funkcji lub kodu źródłowego:

- Czas włączny — łączny czas, w którym jest wykonywane działanie funkcji lub wiersza kodu źródłowego.

- Aplikacja włącznie — czas poświęcony na uruchomienie funkcji lub wiersza kodu źródłowego. Wywołania systemu operacyjnego są wykluczone.

- Czas, który upłynął, w trakcie wykonywania funkcji lub wiersza kodu źródłowego. Wywołania innych funkcji są wykluczone.

- Aplikacja na wyłączność — czas spędzony na wykonywaniu funkcji lub wiersza kodu źródłowego. Wywołania systemu operacyjnego lub innych funkcji są wykluczone.

Liczniki wydajności procesora i oprogramowania można również zbierać przy użyciu metody instrumentacji.

[Opis wartości danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)

[Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Współbieżność

Profilowanie współbieżności zbiera informacje o aplikacjach wielowątkowych. Profilowanie rywalizacji o zasoby zbiera szczegółowe informacje o stosie wywołań, gdy konkurujące wątki oczekują na dostęp do zasobu udostępnionego. Wizualizacja współbieżności zbiera również bardziej ogólne informacje o sposobie interakcji aplikacji wielowątkowej z:

- Sam.
- Sprzęt.
- System operacyjny.
- Inne procesy na komputerze-hoście.

Raporty rywalizacji o zasoby przedstawiają łączną liczbę rywalizacji. Zgłaszają one również łączny czas, przez który moduły, funkcje, wiersze kodu źródłowego i instrukcje oczekują na zasób. Wykresy osi czasu pokazują rywalizacje w miarę ich wystąpienia.

Wizualizator współbieżności wyświetla informacje graficzne pomocne w odnalezieniu:

- Wąskie gardła wydajności.
- Niedostateczne wykorzystanie procesora CPU.
- Rywalizacja o wątki.
- Migracja wątku.
- Opóźnienia synchronizacji.
- Obszary nakładających się operacji we/wy.

  Gdy jest to możliwe, graficzne dane wyjściowe łączą się z danymi z stosu wywołań i kodu źródłowego. Dane wizualizacji współbieżności można zbierać tylko dla aplikacji wiersza polecenia i aplikacji systemu Windows.

[Opis wartości danych rywalizacji o zasoby](../profiling/understanding-resource-contention-data-values.md)

[Zbieranie danych współbieżności dla wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)

[Widoki danych rywalizacji o zasoby](../profiling/resource-contention-data-views.md)

[Concurrency Visualizer](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Pamięć .NET

Metoda profilowania dla alokacji pamięci platformy .NET przerywa procesor CPU przy każdej alokacji obiektu .NET Framework w profilowanej aplikacji. Gdy profiler zbiera również dane o okresie istnienia obiektu, przerywa procesor po każdym .NET Framework wyrzucania elementów bezużytecznych.

Profiler zbiera informacje o typie, rozmiarze i liczbie obiektów utworzonych w alokacji lub zniszczonych w wyrzucaniu elementów bezużytecznych.

- Gdy wystąpi zdarzenie alokacji, profiler zbiera dodatkowe informacje o stosie wywołań funkcji. Profiler zwiększa liczbę wyłącznych alokacji dla aktualnie uruchomionej funkcji. Zwiększa również liczby łącznych wartości dla wszystkich funkcji wywołujących w stosie wywołań. Raporty platformy .NET przedstawiają łączną liczbę tych liczb dla profilowanych typów, modułów, funkcji, wierszy kodu źródłowego i instrukcji.

- Gdy następuje wyrzucanie elementów bezużytecznych, profiler zbiera dane dotyczące zniszczonych obiektów i informacji o obiektach w każdej generacji wyrzucania elementów bezużytecznych. Po zakończeniu przebiegu profilowania Profiler rejestruje dane dotyczące obiektów, które nie zostały jednoznacznie zniszczone. Raport okres istnienia obiektu przedstawia sumy dla każdego typu przydzieloną w przebiegu profilowania.

Można użyć profilowania pamięci platformy .NET w trybie próbkowania lub Instrumentacji. Wybrany tryb nie ma wpływu na raporty dotyczące alokacji i okresu istnienia obiektu, które są unikatowe dla profilowania pamięci platformy .NET.

- Po uruchomieniu profilowania pamięci platformy .NET w trybie próbkowania Profiler używa zdarzeń alokacji pamięci jako interwału. Wyświetla również łączną liczbę przydzieloną obiektów i bajtów jako wartości łączne i wyłączne w raportach.

- Po uruchomieniu profilowania pamięci platformy .NET w trybie instrumentacji profiler zbiera szczegółowe informacje o chronometrażu wraz z wartościami alokacji włącznie i wyłącznymi.

[Opis alokacji pamięci i wartości danych czasu istnienia obiektu](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interakcje między warstwami

Profilowanie interakcji między warstwami dodaje informacje do pliku danych profilowania dotyczące [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] wywołań synchronicznych między [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stroną lub inną aplikacją a [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazą danych. Dane obejmują liczbę i godzinę wywołań oraz maksymalny i minimalny czas. Można dodać dane interakcji warstwy do profilowania danych zbieranych przy użyciu metody próbkowania, instrumentacji, pamięci .NET lub współbieżności.

![Przepływu danych profilowanie interakcji z warstwą](../profiling/media/tierinteraction_profilingtools.png "Przepływu danych profilowanie interakcji z warstwą")

Aby uzyskać informacje dotyczące danych interakcji warstwowych zbieranych przez narzędzia profilowania, zobacz następujące artykuły.

[Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)

[Widoki interakcji między warstwami](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Zobacz też

[Instrukcje: zbieranie danych wydajności dla witryny sieci Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)
