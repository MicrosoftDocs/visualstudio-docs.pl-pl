---
title: Mierzenie wydajności za pomocą narzędzi profilowania
description: Zapoznaj się z różnymi narzędziami diagnostycznymi dostępnymi w programie Visual Studio.
ms.custom: ''
ms.date: 09/08/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebc2a2e7c4b10d835a20abcdd8392fb1851596a
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90074926"
---
# <a name="first-look-at-profiling-tools"></a>Pierwsze spojrzenie na narzędzia profilowania

Program Visual Studio oferuje różne narzędzia profilowania, które ułatwiają diagnozowanie różnych rodzajów problemów z wydajnością w zależności od typu aplikacji. W tym artykule podajemy szybki przegląd najpopularniejszych narzędzi profilowania.

Aby wyświetlić obsługę narzędzia profilowania dla różnych typów aplikacji, zobacz [narzędzie, którego należy użyć?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Mierzenie wydajności podczas debugowania

Narzędzia profilowania, do których można uzyskać dostęp podczas sesji debugowania, są dostępne w oknie narzędzia diagnostyczne. Okno narzędzia diagnostyczne jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby wyświetlić okno, kliknij pozycję **Debuguj/Windows/pokaż narzędzia diagnostyczne**. Po otwarciu okna możesz wybrać narzędzia, dla których mają być zbierane dane.

![Okno narzędzia diagnostyczne](../profiling/media/prof-tour-diagnostic-tools.png "narzędzia diagnostyczne")

Podczas debugowania można użyć okna **Narzędzia diagnostyczne** do analizowania użycia procesora i pamięci oraz wyświetlania zdarzeń, które zawierają informacje dotyczące wydajności.

![Widok podsumowania narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Podsumowanie narzędzia diagnostyczne")

Okno **Narzędzia diagnostyczne** jest typowym sposobem profilowania aplikacji, ale w przypadku kompilacji wydania można również przeanalizować aplikację. Aby uzyskać więcej informacji na temat różnych metod, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Aby wyświetlić obsługę narzędzia profilowania dla różnych typów aplikacji, zobacz [narzędzie, którego należy użyć?](#which-tool-should-i-use)

Narzędzia dostępne w oknie narzędzia diagnostyczne lub podczas sesji debugowania obejmują:
- [Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Użycie pamięci](../profiling/memory-usage.md)
- [Wskazówki dotyczące wydajności](../profiling/perftips.md)

> [!NOTE]
> System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ). Można używać narzędzi [po](#post_mortem) stronie programu z systemem Windows 7 lub nowszym. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Mierzenie wydajności w kompilacjach wydania

Narzędzia w programie Performance Profiler mają na celu zapewnienie analizy dla kompilacji **wydań** . W profilerze wydajności można zbierać informacje diagnostyczne, gdy aplikacja jest uruchomiona, a następnie przeanalizować zebrane informacje po zatrzymaniu aplikacji (analiza po zakończeniu).

Otwórz Profiler wydajności, wybierając pozycję **Debuguj**  >  **Profiler wydajności** (lub **ALT + F2**).

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "Profiler wydajności")

W niektórych scenariuszach okno umożliwia wybranie [wielu narzędzi profilowania](../profiling/use-multiple-profiler-tools-simultaneously.md). Narzędzia takie jak użycie procesora CPU mogą zapewnić uzupełniające dane, których można użyć do analizy. Możesz również użyć [profilera wiersza polecenia](../profiling/profile-apps-from-command-line.md) , aby włączyć scenariusze obejmujące wiele narzędzi profilowania.

Narzędzia dostępne w profilerze wydajności obejmują:

- [Użycie procesora CPU](../profiling/cpu-usage.md)
- [Użycie pamięci dla kodu platformy .NET](../profiling/dotnet-alloc-tool.md)
- [Użycie pamięci](#analyze-memory-usage)
- [Narzędzie asynchroniczne .NET](../profiling/analyze-async.md)
- [Narzędzie bazy danych](../profiling/analyze-database.md)
- [Użycie procesora GPU](../profiling/gpu-usage.md)

Aby wyświetlić obsługę narzędzia profilowania dla różnych typów aplikacji, zobacz [narzędzie, którego należy użyć?](#which-tool-should-i-use)

Aby uzyskać więcej informacji na temat użycia procesora CPU lub narzędzia użycie pamięci w profilerze wydajności a narzędzia zintegrowane z debugerem, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

## <a name="examine-performance-using-perftips"></a>Sprawdzanie wydajności przy użyciu funkcja PerfTip

Często najprostszym sposobem wyświetlania informacji o wydajności jest użycie [Funkcja PerfTip](../profiling/perftips.md). Za pomocą funkcja PerfTip można przeglądać informacje o wydajności podczas korzystania z kodu. Można sprawdzić informacje, takie jak czas trwania zdarzenia (mierzone od momentu ostatniego wstrzymania debugera lub uruchomienia aplikacji). Na przykład po przekroczeniu kodu (F10, F11) funkcja PerfTip pokaże czas wykonywania aplikacji z poprzedniej operacji kroku do bieżącego kroku.

![Profilowanie samouczka funkcja PerfTip](../profiling/media/prof-tour-perf-tips.png "Profilowanie samouczka funkcja PerfTip")

Można użyć funkcja PerfTip do sprawdzenia, jak długo trwa wykonywanie bloku kodu, lub czas trwania pojedynczej funkcji.

Funkcja PerfTip Pokaż te same zdarzenia, które również są wyświetlane w widoku **zdarzeń** narzędzia diagnostyczne. W widoku **zdarzenia** można przeglądać różne zdarzenia, które wystąpiły podczas debugowania, takie jak ustawienie punktu przerwania lub operacji taktowania kodu.

![Widok zdarzeń narzędzia diagnostyczne](../profiling/media/prof-tour-events.png "Zdarzenia widoku narzędzia diagnostyczne")

 > [!NOTE]
 > Jeśli masz Visual Studio Enterprise, na tej karcie można także zobaczyć [zdarzenia IntelliTrace](../debugger/intellitrace.md) .

## <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Narzędzie użycie procesora CPU jest dobrym miejscem, aby rozpocząć analizowanie wydajności aplikacji. Poinformuje więcej o zasobach procesora CPU zużywanych przez aplikację. Możesz użyć [Narzędzia zintegrowanego do debugera procesora CPU](../profiling/beginners-guide-to-performance-profiling.md) lub narzędzia do [użycia procesora CPU](../profiling/cpu-usage.md).

W przypadku korzystania z narzędzia do zintegrowanego użycia procesora CPU w debugerze Otwórz okno narzędzia diagnostyczne (jeśli zostało zamknięte, wybierz polecenie **Debuguj/Windows/pokaż narzędzia diagnostyczne**). Podczas debugowania Otwórz widok  **podsumowania** , a następnie wybierz pozycję **zarejestruj profil procesora**.

![Włącz użycie procesora CPU w narzędzia diagnostyczne](../profiling/media/prof-tour-enable-cpu-profiling.png "narzędzia diagnostyczne Włącz użycie procesora CPU")

Jednym ze sposobów korzystania z narzędzia jest ustawienie dwóch punktów przerwania w kodzie, jeden na początku i jeden na końcu funkcji lub regionu kodu, który ma zostać przeanalizowany. Sprawdzanie danych profilowania po wstrzymaniu w drugim punkcie przerwania.

Widok **użycie procesora CPU** pokazuje listę funkcji uporządkowanych według najdłuższych uruchomionych, z największą uruchomioną funkcją w górnej części. Może to ułatwić wykonywanie zadań, w których są wykonywane wąskie gardła wydajności.

![Widok użycia procesora CPU narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-usage.png "Użycie procesora narzędzia diagnostyczne")

Kliknij dwukrotnie odpowiednią funkcję, a zobaczysz bardziej szczegółowy widok "motylkowy" z trzema okienkiem, z wybraną funkcją w środku okna, funkcję wywołującą po lewej stronie i o nazwie funkcje po prawej stronie. Sekcja **treść funkcji** pokazuje łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. Te dane mogą pomóc w ocenie, czy sama funkcja jest wąskim gardłem wydajności.

![Narzędzia diagnostyczne widok "motylkowy" wywołującego](../profiling/media/prof-tour-cpu-usage-caller-callee.png "narzędzia diagnostyczne widok wywoływany przez wywołującego")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Okno **Narzędzia diagnostyczne** umożliwia również ocenę użycia pamięci w aplikacji za pomocą narzędzia **użycie pamięci** . Na przykład można przyjrzeć się liczbie i rozmiarze obiektów na stercie. [Narzędzie użycie pamięci zintegrowanej debugera](../profiling/memory-usage.md) lub narzędzie użycie pamięci można użyć w [profilerze wydajności](#post_mortem). Inne narzędzie do analizy pamięci, [Narzędzie alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md), pomaga identyfikować wzorce i anomalie alokacji w kodzie .NET.

Aby analizować użycie pamięci, należy wykonać co najmniej jedną migawkę pamięci. Często najlepszym sposobem analizowania pamięci jest wykonanie dwóch migawek: pierwszy z prawej strony przed problemem z pamięcią, a druga migawka jest bezpośrednio po wystąpieniu podejrzanej pamięci. Następnie można wyświetlić różnice między dwiema migawkami i zobaczyć dokładnie te zmiany. Na poniższej ilustracji przedstawiono tworzenie migawek przy użyciu narzędzia zintegrowanego z debugerem.

![Zrób migawkę w narzędzia diagnostyczne](../profiling/media/prof-tour-take-snapshots.gif "narzędzia diagnostyczne wykonaj migawki")

Po wybraniu jednego z łączy ze strzałką zostanie wyświetlony widok różnicowy sterty ( ![zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci") przez czerwoną strzałkę w górę powoduje zwiększenie liczby obiektów (po lewej stronie) lub zwiększenie rozmiaru sterty (po prawej). Po kliknięciu odpowiedniego linku zostanie wyświetlony widok sterty różnicowej uporządkowany według obiektów, które zwiększyły największy rozmiar sterty. Może to pomóc w wydaniu problemów z pamięcią. Na przykład na poniższej ilustracji bajty używane przez `ClassHandlersStore` obiekty wzrosły o 3 492 bajtów w drugiej migawce.

![Widok diff narzędzia diagnostyczne sterty](../profiling/media/prof-tour-mem-usage-diff-heap.png "Widok diff narzędzia diagnostyczne sterty")

Po kliknięciu linku po lewej stronie w widoku **użycie pamięci** widok sterty jest zorganizowany według liczby obiektów; obiekty określonego typu, które zwiększyły największą liczbę, są wyświetlane u góry (posortowane według kolumny **różnic liczby** ).

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, takich jak aplikacje WPF dla systemu Windows i aplikacje platformy UWP, można analizować użycie zasobów za pomocą narzędzia Oś czasu aplikacji. Na przykład można analizować czas spędzony przez aplikację do przygotowywania ramek interfejsu użytkownika (układu i renderowania), obsługi żądań sieci i dysku, a także w scenariuszach, takich jak uruchamianie aplikacji, ładowanie stron i zmiana rozmiaru okna. Aby użyć narzędzia, wybierz **oś czasu aplikacji** w profilerze wydajności, a następnie wybierz **Uruchom**. W aplikacji przejdź przez scenariusz do podejrzanego problemu dotyczącego użycia zasobów, a następnie wybierz polecenie **Zatrzymaj zbieranie danych** w celu wygenerowania raportu.

Niska szybkość klatek w grafie **przepływności wizualnej** może odpowiadać problemom wizualnym widocznym podczas uruchamiania aplikacji. Podobnie duże liczby w grafie **wykorzystania wątków interfejsu użytkownika** mogą również odpowiadać problemom odpowiedzi interfejsu użytkownika. W raporcie można wybrać okres z podejrzanym problemem związanym z wydajnością, a następnie sprawdzić szczegółowe działania wątku interfejsu użytkownika w widoku szczegółów osi czasu (dolnym okienku).

![Oś czasu aplikacji narzędzia profilowania](../profiling/media/prof-tour-application-timeline.gif "Oś czasu aplikacji przewodnika profilowania")

W widoku Szczegóły osi czasu można znaleźć informacje takie jak typ działania (lub element interfejsu użytkownika) wraz z czasem trwania działania. Na przykład na ilustracji zdarzenie **układu** dla kontrolki siatki trwa 57,53 MS.

Aby uzyskać więcej informacji, zobacz [oś czasu aplikacji](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Sprawdzanie zdarzeń aplikacji

W [Podglądzie zdarzeń](../profiling/events-viewer.md) ogólnych można przeglądać aktywność aplikacji za pomocą listy zdarzeń, takich jak obciążenie modułu, uruchamianie wątków i konfiguracje systemu, aby lepiej zdiagnozować, jak aplikacja działa bezpośrednio w programie Visual Studio profiler. To narzędzie jest dostępne w profilerze wydajności. Otwórz Profiler wydajności, wybierając pozycję **Debuguj**  >  **Profiler wydajności** (lub **ALT + F2**).

Narzędzie pokazuje każde zdarzenie w widoku listy. Kolumny zawierają informacje dotyczące każdego zdarzenia, takie jak nazwa zdarzenia, sygnatura czasowa i identyfikator procesu.

![Śledzenie Podgląd zdarzeń](../profiling/media/eventviewertrace.png "Śledzenie Podgląd zdarzeń")

## <a name="analyze-asynchronous-code-net"></a>Analizowanie kodu asynchronicznego (.NET)

[Narzędzie asynchroniczne platformy .NET](../profiling/analyze-async.md) umożliwia analizowanie wydajności kodu asynchronicznego w aplikacji. To narzędzie jest dostępne w profilerze wydajności. Otwórz Profiler wydajności, wybierając pozycję **Debuguj**  >  **Profiler wydajności** (lub **ALT + F2**).

Narzędzie wyświetli każdą operację asynchroniczną w widoku listy. Można wyświetlić informacje takie jak godzina rozpoczęcia, godzina zakończenia i łączny czas operacji asynchronicznej.

![Zatrzymano narzędzie asynchroniczne platformy .NET](../profiling/media/async-tool-opened.png "Zatrzymano narzędzie asynchroniczne platformy .NET")

## <a name="analyze-database-performance-net-core"></a>Analizowanie wydajności bazy danych (.NET Core)

W przypadku aplikacji .NET Core, które używają ADO.NET lub Entity Framework Core, [Narzędzie Database Tool](../profiling/analyze-database.md) pozwala rejestrować zapytania bazy danych, które aplikacja wykonuje podczas sesji diagnostycznej. Następnie można analizować informacje o poszczególnych zapytaniach w celu znalezienia miejsc, w których można ulepszyć wydajność aplikacji. To narzędzie jest dostępne w profilerze wydajności. Otwórz Profiler wydajności, wybierając pozycję **Debuguj**  >  **Profiler wydajności** (lub **ALT + F2**).

Narzędzie wyświetla każde zapytanie w widoku listy. Można wyświetlić informacje takie jak godzina rozpoczęcia zapytania i czas trwania.

![Alokacja](./media/db-gotosource.png "Alokacja")

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdzanie wydajności interfejsu użytkownika i zdarzeń dostępności (platformy UWP)

W aplikacjach platformy UWP można włączyć **analizę interfejsu użytkownika** w oknie **Narzędzia diagnostyczne** . Narzędzie wyszukuje typowe problemy z wydajnością lub dostępnością i wyświetla je w widoku **zdarzenia** podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą pomóc w rozwiązywaniu problemów.

![Wyświetlanie zdarzeń analizy interfejsu użytkownika w narzędziach diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "narzędzia diagnostyczne Wyświetl zdarzenia analizy interfejsu użytkownika")

## <a name="analyze-gpu-usage-direct3d"></a>Analizowanie użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (składniki Direct3D muszą znajdować się w języku C++) można sprawdzić aktywność procesora GPU i analizować problemy z wydajnością. Aby uzyskać więcej informacji, zobacz [użycie procesora GPU](./gpu-usage.md). Aby użyć narzędzia, wybierz pozycję **użycie procesora GPU** w profilerze wydajności, a następnie wybierz polecenie **Uruchom**. W aplikacji przejdź do scenariusza, który Cię interesuje, a następnie wybierz pozycję **Zatrzymaj zbieranie** , aby wygenerować raport.

Po wybraniu przedziału czasowego na wykresach i wybraniu opcji **Wyświetl szczegóły**w dolnym okienku pojawi się widok szczegółowy. W widoku szczegółowym można sprawdzić, jaka część działania odbywa się na każdym procesorze CPU i procesorze GPU. Wybierz pozycję zdarzenia w dolnym okienku, aby wyświetlić okna podręczne na osi czasu. Na przykład wybierz **istniejące** zdarzenie, aby wyświetlić **wyświetlane** okna podręczne wywołań. (Jasne szare linie pionie mogą służyć jako odwołanie, aby zrozumieć, czy niektóre **obecne** wywołania zostały pominięte pionie. Aby aplikacja mogła stale osiągnąć 60 FPS, musi istnieć jedno **istniejące** wywołanie między wszystkimi dwoma Vsyncs.

![Narzędzie profilowania użycia procesora GPU](../profiling/media/prof-tour-gpu-usage.png "Użycie procesora GPU")

Możesz również użyć wykresów, aby określić, czy istnieją wąskie gardła procesora lub wydajności związane z procesorem GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizowanie wydajności (JavaScript platformy UWP)

W przypadku aplikacji platformy UWP można użyć narzędzia pamięci JavaScript i narzędzia odpowiedzi interfejsu użytkownika HTML.

Narzędzie pamięci JavaScript jest podobne do narzędzia użycie pamięci dostępnego dla innych typów aplikacji. Za pomocą tego narzędzia można zrozumieć użycie pamięci i wyszukać przecieki pamięci w aplikacji. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [JavaScript Memory](../profiling/javascript-memory.md).

![Narzędzie profilowania pamięci JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Aby zdiagnozować czas odpowiedzi interfejsu użytkownika, powolne obciążenie i wolno przeprowadzić aktualizacje wizualne w aplikacjach platformy UWP, użyj narzędzia do odpowiedzi interfejsu użytkownika HTML. Użycie jest podobne do narzędzia Oś czasu aplikacji dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md).

![Narzędzie profilowania czas odpowiedzi interfejsu użytkownika HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (platforma UWP)

W aplikacjach platformy UWP można analizować operacje sieciowe wykonywane przy użyciu `Windows.Web.Http` interfejsu API. To narzędzie może pomóc w rozwiązywaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, niepoprawna pamięć podręczna oraz niska wydajność wyświetlania i pobierania. Aby użyć narzędzia, wybierz **Sieć** w profilerze wydajności, a następnie wybierz polecenie **Uruchom**. W aplikacji przejdź do scenariusza, który używa programu `Windows.Web.Http` , a następnie wybierz polecenie **Zatrzymaj zbieranie** w celu wygenerowania raportu.

![Narzędzie profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "Użycie sieci diag")

Wybierz operację w widoku Podsumowanie, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Użycie sieci](../profiling/media/prof-tour-network-usage-details.png "Szczegóły użycia sieci diag")

Aby uzyskać więcej informacji, zobacz temat [użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (starsze narzędzia)

::: moniker range="vs-2017"
Jeśli potrzebujesz funkcji, takich jak Instrumentacja, która nie jest obecnie dostępna w narzędziach użycie procesora CPU lub pamięci, i używasz aplikacji Desktop lub ASP.NET, możesz użyć Eksplorator wydajności do profilowania. (Nieobsługiwane w aplikacjach platformy UWP). Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 starsze Eksplorator wydajności i powiązane narzędzia profilowania, takie jak Kreator wydajności, zostały złożone do profilera wydajności, który można otworzyć za pomocą **Debug**  >  **profilera wydajności**debugowania. W profilerze wydajności dostępne narzędzia diagnostyczne zależą od wybranego elementu docelowego i bieżącego otwartego projektu startowego. Narzędzie użycie procesora CPU zapewnia funkcję próbkowania obsługiwaną wcześniej w Kreatorze wydajności. Narzędzie Instrumentacja udostępnia funkcję profilowania PROFILOWANEGO (dla precyzyjnej liczby wywołań i czasów trwania), która była w Kreatorze wydajności. Dodatkowe narzędzia pamięci są również wyświetlane w profilerze wydajności.
::: moniker-end

![Narzędzie Eksplorator wydajności](../profiling/media/prof-tour-performance-explorer.png "Eksplorator wydajności")

## <a name="which-tool-should-i-use"></a>Którego narzędzia należy użyć?

Poniżej znajduje się tabela zawierająca listę różnych narzędzi oferowanych przez program Visual Studio i różne typy projektów, z których można korzystać:

::: moniker range=">=vs-2019"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET rdzeń|
|----------------------|---------------------|-------------|-------------|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak|tak|
|[Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Alokacja obiektu platformy .NET](../profiling/dotnet-alloc-tool.md)|tak (tylko platforma .NET)|tak|tak|
|[Użycie procesora GPU](/visualstudio/debugger/graphics/gpu-usage)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak (XAML)|tak|nie|
|[Podgląd zdarzeń](../profiling/events-viewer.md)|tak|tak|tak|
|[.NET Async](../profiling/analyze-async.md)|tak (tylko platforma .NET)|tak|tak|
|[Database](../profiling/analyze-database.md) (Baza danych)|tak (tylko platforma .NET Core)|nie|tak (tylko ASP.NET Core)|
|[Eksplorator wydajności](#analyze-performance-legacy-tools)|nie|nie|nie|
|[IntelliTrace](../debugger/intellitrace.md)|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET rdzeń|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora CPU](../profiling/beginners-guide-to-performance-profiling.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Użycie procesora GPU](/visualstudio/debugger/graphics/gpu-usage)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak (XAML)|tak|nie|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak dla języka XAML, nie dla HTML|tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|nie|tak|
|[IntelliTrace](../debugger/intellitrace.md)|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|
|[Użycie sieci](../profiling/network-usage.md)|nie|tak|nie|
|[Czas odpowiedzi interfejsu użytkownika języka HTML](../profiling/html-ui-responsiveness.md)|nie|tak dla języka HTML, nie dla języka XAML|nie|
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|nie|tak dla języka HTML, nie dla języka XAML|nie|
::: moniker-end


## <a name="see-also"></a>Zobacz także
- [Debugowanie w Visual Studio](../debugger/debugger-feature-tour.md)