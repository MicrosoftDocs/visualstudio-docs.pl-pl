---
title: Wprowadzenie do narzędzi profilowania
description: Przyjrzyj się krótko różnym narzędziom diagnostycznym dostępnym w Visual Studio.
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5fb35c1cd30f872d2a58504f73596357cc60025
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729328"
---
# <a name="first-look-at-profiling-tools"></a>Pierwsze spojrzenie na narzędzia profilowania

Visual Studio udostępnia różne narzędzia profilowania, które ułatwiają diagnozowanie różnych rodzajów problemów z wydajnością w zależności od typu aplikacji. W tym artykule podajemy krótkie informacje na temat najpopularniejszych narzędzi profilowania.

Aby wyświetlić obsługę narzędzi profilowania dla różnych typów aplikacji, zobacz [Którego narzędzia należy użyć?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Mierzenie wydajności podczas debugowania

Narzędzia profilowania, do których można uzyskać dostęp podczas sesji debugowania, są dostępne w narzędzia diagnostyczne oknie. Okno narzędzia diagnostyczne jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby wyświetlić okno, kliknij pozycję **Debuguj/Windows/Pokaż narzędzia diagnostyczne** (lub naciśnij **klawisze Ctrl**  +  **Alt**  +  **F2).** Po otwarciu okna możesz wybrać narzędzia, dla których chcesz zbierać dane.

![narzędzia diagnostyczne okno](../profiling/media/prof-tour-diagnostic-tools.png "narzędzia diagnostyczne")

Podczas debugowania można użyć  okna narzędzia diagnostyczne do analizowania użycia procesora CPU i pamięci oraz wyświetlić zdarzenia, które pokazują informacje dotyczące wydajności.

![narzędzia diagnostyczne podsumowanie](../profiling/media/prof-tour-cpu-and-memory-graph.gif "narzędzia diagnostyczne podsumowanie")

Okno **narzędzia diagnostyczne** jest częstym sposobem profilowania aplikacji, ale w przypadku kompilacji wydania można również wykonać analizę post mortem aplikacji. Aby uzyskać więcej informacji na temat różnych podejść, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Aby wyświetlić obsługę narzędzi profilowania dla różnych typów aplikacji, zobacz [Którego narzędzia należy użyć?](#which-tool-should-i-use)

Narzędzia dostępne w oknie narzędzia diagnostyczne debugowania lub podczas sesji debugowania obejmują:
- [Użycie procesora](../profiling/beginners-guide-to-performance-profiling.md)
- [Użycie pamięci](../profiling/memory-usage.md)
- [Wskazówki dotyczące wydajności](../profiling/perftips.md)

> [!NOTE]
> Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera **(narzędzia diagnostyczne** okno). Narzędzia post [mortem można używać](#post_mortem) w systemie Windows 7 lub nowszym. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Mierzenie wydajności w kompilacjach wydania

Narzędzia w profiler wydajności są przeznaczone do analizy **kompilacji** wydania. W profiler wydajności można zbierać informacje diagnostyczne, gdy aplikacja jest uruchomiona, a następnie badać zebrane informacje po zatrzymaniu aplikacji (analiza po zakończeniu analizy).

Otwórz okno profiler wydajności, wybierając opcję   >  **Debuguj profiler wydajności** (lub **Alt + F2).**

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "Profiler wydajności")

Aby uzyskać więcej informacji na temat korzystania z narzędzia użycie procesora CPU lub pamięci w narzędziu profiler wydajności a narzędziami zintegrowanymi z debugerem, zobacz Uruchamianie narzędzi profilowania z [debugerem](../profiling/running-profiling-tools-with-or-without-the-debugger.md)lub bez niego. 

Narzędzia dostępne w profiler wydajności obejmują:

- [Użycie procesora](../profiling/cpu-usage.md)
- [Alokacja obiektów .NET](../profiling/dotnet-alloc-tool.md)
- [Użycie pamięci](../profiling/memory-usage-without-debugging2.md)
- [Narzędzie asynchroniczne .NET](../profiling/analyze-async.md)
- [Narzędzie bazy danych](../profiling/analyze-database.md)
- [Użycie procesora GPU](../profiling/gpu-usage.md)

Aby wyświetlić obsługę narzędzi profilowania dla różnych typów aplikacji, zobacz [Którego narzędzia należy użyć?](#which-tool-should-i-use)

W niektórych scenariuszach okno umożliwia wybranie wielu [narzędzi profilowania.](../profiling/use-multiple-profiler-tools-simultaneously.md) Narzędzia, takie jak użycie procesora CPU, mogą dostarczać uzupełniające się dane, których można użyć, aby ułatwić analizę. Profiler wiersza [polecenia](../profiling/profile-apps-from-command-line.md) umożliwia również obsługę scenariuszy obejmujących wiele narzędzi profilowania.

## <a name="examine-performance-using-perftips"></a>Badanie wydajności przy użyciu perfTips

Często najprostszym sposobem wyświetlenia informacji o wydajności jest użycie [perfTips](../profiling/perftips.md). Za pomocą perfTips, można wyświetlić informacje o wydajności podczas interakcji z kodem. Możesz sprawdzić informacje, takie jak czas trwania zdarzenia (mierzone od czasu ostatniego wstrzymania debugera lub czasu rozpoczęcia aplikacji). Jeśli na przykład przechodzisz przez kod (F10, F11), w etykietkach funkcji PerfTips jest pokazywany czas trwania środowiska uruchomieniowego aplikacji od operacji poprzedniego kroku do bieżącego kroku.

![PerfTips przewodnika profilowania](../profiling/media/prof-tour-perf-tips.png "Wskazówki dotyczące perftips przewodnika profilowania")

Możesz użyć funkcji PerfTips, aby sprawdzić, jak długo trwa wykonywanie bloku kodu lub jak długo trwa wykonywanie pojedynczej funkcji.

PerfTips pokaż te same zdarzenia, które są również wyświetlane w **widoku zdarzenia** narzędzia diagnostyczne. W **widoku Zdarzenia** można wyświetlić różne zdarzenia występujące podczas debugowania, takie jak ustawienie punktu przerwania lub wykonywanie krokowe kodu.

![narzędzia diagnostyczne zdarzeń](../profiling/media/prof-tour-events.png "narzędzia diagnostyczne zdarzeń")

 > [!NOTE]
 > Jeśli masz już Visual Studio Enterprise, na tej karcie można również zobaczyć zdarzenia [IntelliTrace.](../debugger/intellitrace.md)

## <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Narzędzie Użycie procesora CPU jest dobrym miejscem, aby rozpocząć analizowanie wydajności aplikacji. Zawiera on więcej informacji na temat zasobów procesora CPU zużywanych przez aplikację. Możesz użyć narzędzia Użycie procesora CPU zintegrowanego [z debugerem](../profiling/beginners-guide-to-performance-profiling.md) lub narzędzia użycie procesora CPU po [jego użyciu.](../profiling/cpu-usage.md)

W przypadku korzystania z narzędzia użycie procesora CPU zintegrowanego z debugerem otwórz okno Narzędzie diagnostyczne (jeśli jest zamknięte, wybierz pozycję **Debuguj/Windows/Pokaż narzędzia diagnostyczne).** Podczas debugowania otwórz widok **Podsumowanie,** a następnie wybierz pozycję **Rekorduj profil procesora CPU.**

![Włącz użycie procesora CPU w narzędzia diagnostyczne](../profiling/media/prof-tour-enable-cpu-profiling.png "narzędzia diagnostyczne włączyć użycie procesora CPU")

Jednym ze sposobów użycia narzędzia jest ustawienie dwóch punktów przerwania w kodzie: jednego na początku i jednego na końcu funkcji lub regionu kodu, który chcesz analizować. Sprawdź dane profilowania po wstrzymaniu w drugim punkcie przerwania.

W **widoku Użycie** procesora CPU jest wyświetlona lista funkcji uporządkowanych według najdłużej działającej funkcji na górze. Może to pomóc w guide you to functions where performance bottlenecks are happening.

![narzędzia diagnostyczne użycia procesora CPU](../profiling/media/prof-tour-cpu-usage.png "narzędzia diagnostyczne procesora CPU")

Kliknij dwukrotnie funkcję, która Cię interesuje, i zobaczysz bardziej szczegółowy widok "okienka" z trzema okienkami, z wybraną funkcją w środku okna, funkcją wywołującą po lewej stronie i wywołaną funkcjami po prawej stronie. Sekcja **Treść funkcji** przedstawia łączny czas (i procent czasu) spędzony w treści funkcji z wyłączeniem czasu spędzonego na wywoływaniu funkcji i wywołaniu funkcji. Te dane mogą ułatwić ocenę, czy sama funkcja jest wąskim gardłem wydajności.

![narzędzia diagnostyczne wywołujący wywołujący widok "wywoływcy"](../profiling/media/prof-tour-cpu-usage-caller-callee.png "narzędzia diagnostyczne wywołujący wywołujący widok wywołujący")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Okno **narzędzia diagnostyczne** umożliwia również ocenę użycia pamięci w aplikacji przy użyciu narzędzia **Użycie** pamięci. Na przykład można sprawdzić liczbę i rozmiar obiektów na stercie. Możesz użyć narzędzia użycie pamięci [zintegrowane z debugerem](../profiling/memory-usage.md) lub narzędzia użycie pamięci po [mortem](../profiling/memory-usage-without-debugging2.md) w profiler wydajności.

Deweloperzy .NET mogą wybrać narzędzie [alokacji obiektów .NET](../profiling/dotnet-alloc-tool.md) lub [narzędzie użycie](../profiling/memory-usage.md) pamięci.

- Narzędzie **alokacji obiektów .NET** pomaga identyfikować wzorce alokacji i anomalie w kodzie .NET oraz pomaga identyfikować typowe problemy z odzyskiwaniem pamięci. To narzędzie działa tylko jako narzędzie po mortem. To narzędzie można uruchomić na maszynach lokalnych lub zdalnych.
- Narzędzie **Użycie pamięci** jest przydatne w identyfikowaniu przecieków pamięci, które zwykle nie są typowe w aplikacjach .NET. Jeśli musisz używać funkcji debugera podczas sprawdzania pamięci, takich jak wykonywanie krokowe kodu, zalecane jest użycie pamięci zintegrowane [z debugerem.](../profiling/beginners-guide-to-performance-profiling.md)

Aby analizować użycie pamięci za pomocą **narzędzia Użycie** pamięci, należy utworzyć co najmniej jedną migawkę pamięci. Często najlepszym sposobem analizowania pamięci jest tworzenie dwóch migawek. pierwsza prawa przed podejrzanym problemem z pamięcią, a druga migawka bezpośrednio po problemie z podejrzaną pamięcią. Następnie możesz wyświetlić różnicę dwóch migawek i zobaczyć dokładnie, co się zmieniło. Na poniższej ilustracji przedstawiono tworzenie migawki za pomocą narzędzia zintegrowanego z debugerem.

![Tworzenie migawki w narzędzia diagnostyczne](../profiling/media/prof-tour-take-snapshots.gif "narzędzia diagnostyczne tworzenie migawek")

Po wybraniu jednego z linków strzałek zostanie nadany widok różnicowy ![](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci") sterty (czerwona strzałka w górę Wzrost użycia pamięci pokazuje rosnącą liczbę obiektów (po lewej) lub zwiększający się rozmiar sterty (po prawej)). Kliknięcie linku po prawej stronie umożliwia wyświetlenie różnicowego widoku sterty uporządkowanego według obiektów, które najbardziej zwiększyły rozmiar sterty. Może to pomóc w wskazać problemy z pamięcią. Na przykład na poniższej ilustracji liczba bajtów używanych przez obiekty wzrosła o `ClassHandlersStore` 3492 bajty w drugiej migawce.

![narzędzia diagnostyczne widoku różnic sterty](../profiling/media/prof-tour-mem-usage-diff-heap.png "narzędzia diagnostyczne różnic sterty")

Po kliknięciu linku po lewej stronie w widoku **Użycie** pamięci widok sterty jest zorganizowany według liczby obiektów. Obiekty określonego typu, które zwiększyły najwięcej liczb, są wyświetlane u góry (posortowane według **kolumny Zlicz różnice).**

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, takich jak klasyczne aplikacje WPF systemu Windows i aplikacje platformy uniwersalnej systemu Windows, można analizować zużycie zasobów za pomocą Oś czasu aplikacji narzędzi. Można na przykład przeanalizować czas spędzony przez aplikację, przygotowując ramki interfejsu użytkownika (układ i renderowanie), obsługę żądań sieci i dysków oraz w scenariuszach takich jak uruchamianie aplikacji, ładowanie strony i zmiana rozmiaru okna. Aby użyć tego narzędzia, wybierz **Oś czasu aplikacji** na profiler wydajności, a następnie wybierz pozycję **Uruchom.** W aplikacji przejdź przez scenariusz z podejrzanym problemem z zużyciem zasobów, a następnie wybierz pozycję **Zatrzymaj** zbieranie, aby wygenerować raport.

Niska szybkość klatek na wykresie **przepływności wizualizacji** może odpowiadać problemom wizualnym, które są dostrzegane podczas uruchamiania aplikacji. Podobnie wysokie liczby na wykresie **wykorzystania** wątku interfejsu użytkownika mogą również odpowiadać problemom z odpowiedziami interfejsu użytkownika. W raporcie możesz wybrać okres z podejrzanym problemem z wydajnością, a następnie zbadać szczegółowe działania wątku interfejsu użytkownika w widoku Szczegóły osi czasu (dolne okienko).

![Oś czasu aplikacji profilowania](../profiling/media/prof-tour-application-timeline.gif "Przewodnik profilowania Oś czasu aplikacji")

W widoku Szczegóły osi czasu można znaleźć informacje, takie jak typ działania (lub zaangażowany element interfejsu użytkownika) wraz z czasem trwania działania. Na przykład na ilustracji zdarzenie **Układ** dla kontrolki Siatka trwa 57,53 ms.

Aby uzyskać więcej informacji, zobacz [Oś czasu aplikacji](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Badanie zdarzeń aplikacji

Przeglądarka [](../profiling/events-viewer.md) zdarzeń ogólnych umożliwia wyświetlanie aktywności aplikacji za pomocą listy zdarzeń, takich jak ładowanie modułów, uruchamianie wątków i konfiguracje systemu, aby ułatwić lepsze diagnozowanie działania aplikacji bezpośrednio w profilerze Visual Studio. To narzędzie jest dostępne w profiler wydajności. Otwórz okno profiler wydajności, wybierając opcję   >  **Debuguj profiler wydajności** (lub **Alt + F2).**

Narzędzie wyświetla każde zdarzenie w widoku listy. Kolumny zawierają informacje o każdym zdarzeniu, takie jak nazwa zdarzenia, sygnatura czasowa i identyfikator procesu.

![Podgląd zdarzeń śledzenia](../profiling/media/eventviewertrace.png "Podgląd zdarzeń śledzenia")

## <a name="analyze-asynchronous-code-net"></a>Analizowanie kodu asynchronicznego (.NET)

Narzędzie [.NET Async umożliwia](../profiling/analyze-async.md) analizowanie wydajności kodu asynchronicznego w aplikacji. To narzędzie jest dostępne w profiler wydajności. Otwórz okno profiler wydajności, wybierając opcję   >  **Debuguj profiler wydajności** (lub **Alt + F2).**

Narzędzie wyświetla każdą operację asynchroniczną w widoku listy. Można wyświetlić informacje, takie jak godzina rozpoczęcia, godzina zakończenia i łączny czas operacji asynchronicznej.

![.NET Async zatrzymane](../profiling/media/async-tool-opened.png ".NET Async zatrzymane narzędzie")

## <a name="analyze-database-performance-net-core"></a>Analizowanie wydajności bazy danych (.NET Core)

W przypadku aplikacji .NET Core, które korzystają ADO.NET [](../profiling/analyze-database.md) lub Entity Framework Core, narzędzie baza danych umożliwia rejestrowanie zapytań bazy danych, które aplikacja wykonuje podczas sesji diagnostycznej. Następnie możesz analizować informacje o poszczególnych zapytaniach, aby znaleźć miejsca, w których można poprawić wydajność aplikacji. To narzędzie jest dostępne w profiler wydajności. Otwórz okno profiler wydajności, wybierając opcję   >  **Debuguj profiler wydajności** (lub **Alt + F2).**

Narzędzie wyświetla każde zapytanie w widoku listy. Możesz wyświetlić informacje, takie jak czas rozpoczęcia i czas trwania zapytania.

![Alokacji](./media/db-gotosource.png "Alokacja")

## <a name="visualize-net-counters-net-core"></a>Wizualizacja liczników .NET (.NET Core)

Począwszy od Visual Studio 2019 r. w wersji 16.7, można użyć narzędzia [liczników .NET](../profiling/dotnet-counters-tool.md) w programie Visual Studio do wizualizacji liczników wydajności. Można wizualizować liczniki utworzone przy użyciu [liczników dotnet](/dotnet/core/diagnostics/dotnet-counters). Liczniki dotnet obsługują wiele liczników, takich jak użycie procesora CPU i rozmiar sterty modułu odśmiecania pamięci.

Narzędzie wyświetla wartości na żywo dla każdego licznika w widoku listy.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Zbieranie narzędzia licznika .NET.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdzanie zdarzeń dotyczących wydajności i ułatwień dostępu interfejsu użytkownika (UWP)

W aplikacjach platformy UWP możesz włączyć analizę **interfejsu** użytkownika w **narzędzia diagnostyczne** aplikacji. Narzędzie wyszukuje typowe problemy z wydajnością lub ułatwieniami dostępu i wyświetla je w widoku **Zdarzenia** podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą pomóc w rozwiązywaniu problemów.

![Wyświetlanie zdarzeń analizy interfejsu użytkownika w narzędziach diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "narzędzia diagnostyczne zdarzeń analizy interfejsu użytkownika")

## <a name="analyze-gpu-usage-direct3d"></a>Analizowanie użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (składniki Direct3D muszą być w języku C++) można sprawdzić aktywność procesora GPU i przeanalizować problemy z wydajnością. Aby uzyskać więcej informacji, zobacz [Użycie procesora GPU.](./gpu-usage.md) Aby użyć tego narzędzia, wybierz pozycję **Użycie procesora GPU** w profiler wydajności, a następnie wybierz pozycję **Uruchom.** W aplikacji przejdź przez scenariusz, który Cię interesuje profilowanie, a następnie wybierz pozycję **Zatrzymaj** zbieranie, aby wygenerować raport.

Po wybraniu okresu na wykresach i wybraniu szczegółów widoku w dolnym okienku zostanie wyświetlony szczegółowy widok. W widoku szczegółowym można sprawdzić, ile aktywności dzieje się na poszczególnych procesorach CPU i procesorach GPU. Wybierz zdarzenia w najniższym okienku, aby uzyskać wyskakujące okienka na osi czasu. Na przykład wybierz zdarzenie **Prezentuj,** aby wyświetlić **wyskakujące okienka** Prezentuj wywołania. (Jasnoszare pionowe linie VSync mogą służyć jako odwołanie do zrozumienia, czy niektóre wywołania Present **pominięto** VSync. Musi być jedno obecne **wywołanie** między każdymi dwoma synchronizacjami VSync, aby aplikacja stale osiągnąć 60 - 000 USD.

![Narzędzie profilowania użycia procesora GPU](../profiling/media/prof-tour-gpu-usage.png "Diag GPU Usage")

Możesz również użyć grafów, aby określić, czy występują wąskie gardła wydajności powiązane z procesorem CPU, czy gpu.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizowanie wydajności (JavaScript UWP)

W przypadku aplikacji platformy uniwersalnej systemu Windows można użyć narzędzia Pamięć JavaScript i narzędzia czas odpowiedzi interfejsu użytkownika HTML.

Narzędzie pamięć języka JavaScript jest podobne do narzędzia Użycie pamięci dostępnego dla innych typów aplikacji. To narzędzie umożliwia zrozumienie użycia pamięci i znalezienie przecieków pamięci w aplikacji. Aby uzyskać więcej informacji o narzędziu, zobacz [Pamięć języka JavaScript.](../profiling/javascript-memory.md)

![Narzędzie profilowania pamięci języka JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Aby zdiagnozować czas odpowiedzi interfejsu użytkownika, wolny czas ładowania i powolne aktualizacje wizualizacji w aplikacjach platformy uniwersalnej systemu Windows, użyj narzędzia Czas odpowiedzi interfejsu użytkownika HTML. Użycie jest podobne do Oś czasu aplikacji dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [Czas odpowiedzi interfejsu użytkownika HTML.](../profiling/html-ui-responsiveness.md)

![Narzędzie profilowania czasu odpowiedzi interfejsu użytkownika HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (platforma UWP)

W aplikacjach platformy uniwersalnej systemu Windows można analizować operacje sieciowe wykonywane przy użyciu interfejsu `Windows.Web.Http` API. To narzędzie może pomóc w rozwiązywaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, niepoprawne użycie pamięci podręcznej oraz niska wydajność wyświetlania i pobierania. Aby użyć narzędzia, wybierz pozycję **Sieć** w profiler wydajności, a następnie wybierz pozycję **Uruchom.** W aplikacji przejdź przez scenariusz, który używa , `Windows.Web.Http` a następnie wybierz pozycję **Zatrzymaj** zbieranie, aby wygenerować raport.

![Narzędzie profilowania użycie sieci](../profiling/media/prof-tour-network-usage.png "Diag Network Usage")

Wybierz operację w widoku podsumowania, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Użycie sieci](../profiling/media/prof-tour-network-usage-details.png "Diag Network Usage Details")

Aby uzyskać więcej informacji, zobacz [Użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (starsze narzędzia)

::: moniker range="vs-2017"
Jeśli potrzebujesz funkcji, takich jak instrumentacja, które nie są obecnie dostępne w narzędziach Użycie procesora CPU lub Użycie pamięci, i korzystasz z aplikacji klasycznych lub ASP.NET, możesz użyć Eksplorator wydajności do profilowania. (Nie jest obsługiwane w aplikacjach platformy UWP). Aby uzyskać więcej informacji, [zobacz Eksplorator wydajności](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
W Visual Studio 2019 r. starsze narzędzia Eksplorator wydajności i powiązane narzędzia profilowania, takie jak Kreator wydajności, zostały złożone w interfejsie profiler wydajności, który można otworzyć przy użyciu narzędzia debugowania  >  **profiler wydajności**. W profiler wydajności narzędzia diagnostyczne zależą od wybranego celu i bieżącego, otwartego projektu startowego. Narzędzie Użycie procesora CPU udostępnia możliwość próbkowania obsługiwaną wcześniej w Kreatorze wydajności. Narzędzie Instrumentacja udostępnia instrumentowane możliwości profilowania (dla dokładnej liczby wywołań i czasów trwania), które były w Kreatorze wydajności. Dodatkowe narzędzia pamięci są również wyświetlane w profiler wydajności.
::: moniker-end

![Eksplorator wydajności narzędziu](../profiling/media/prof-tour-performance-explorer.png "Eksplorator wydajności")

## <a name="which-tool-should-i-use"></a>Którego narzędzia należy użyć?

Oto tabela, która zawiera listę różnych narzędzi dostępnych Visual Studio i różnych typów projektów, z których można ich używać:

::: moniker range=">=vs-2019"
|Narzędzie do wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak|tak|
|[Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Alokacja obiektów .NET](../profiling/dotnet-alloc-tool.md)|tak (tylko .NET)|tak|tak|
|[Użycie procesora GPU](./gpu-usage.md)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak (XAML)|tak|nie|
|[Podgląd zdarzeń](../profiling/events-viewer.md)|tak|tak|tak|
|[.NET Async](../profiling/analyze-async.md)|tak (tylko .NET)|tak|tak|
|[Liczniki .NET](../profiling/dotnet-counters-tool.md)|tak (tylko program .NET Core)|nie|tak (tylko ASP.NET Core)|
|[Database](../profiling/analyze-database.md) (Baza danych)|tak (tylko program .NET Core)|nie|tak (tylko ASP.NET Core)|
|[Eksplorator wydajności](#analyze-performance-legacy-tools)|nie|nie|nie|
|[IntelliTrace](../debugger/intellitrace.md)|.NET z Visual Studio Enterprise tylko|.NET z Visual Studio Enterprise tylko|.NET z Visual Studio Enterprise tylko|
::: moniker-end

::: moniker range="vs-2017"
|Narzędzie do wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Użycie procesora GPU](./gpu-usage.md)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak (XAML)|tak|nie|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak dla JĘZYKA XAML, nie dla języka HTML|tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|nie|tak|
|[IntelliTrace](../debugger/intellitrace.md)|.NET z Visual Studio Enterprise tylko|.NET z Visual Studio Enterprise tylko|.NET z Visual Studio Enterprise tylko|
|[Użycie sieci](../profiling/network-usage.md)|nie|tak|nie|
|[Czas odpowiedzi interfejsu użytkownika języka HTML](../profiling/html-ui-responsiveness.md)|nie|tak dla kodu HTML, nie dla XAML|nie|
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|nie|tak dla kodu HTML, nie dla XAML|nie|
::: moniker-end


## <a name="see-also"></a>Zobacz też
- [Debugowanie w Visual Studio](../debugger/debugger-feature-tour.md)