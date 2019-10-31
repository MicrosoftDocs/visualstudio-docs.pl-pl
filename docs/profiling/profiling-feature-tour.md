---
title: Mierzenie wydajności za pomocą narzędzi profilowania
description: Zapoznaj się z różnymi narzędziami diagnostycznymi dostępnymi w programie Visual Studio.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c78c56d00f087bdef7733ee1ef2cbf90afd9638
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144762"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Szybki Start: pierwsze spojrzenie na narzędzia profilowania

Program Visual Studio oferuje różne narzędzia profilowania, które ułatwiają diagnozowanie różnych rodzajów problemów z wydajnością w zależności od typu aplikacji.

Narzędzia profilowania, do których można uzyskać dostęp podczas sesji debugowania, są dostępne w oknie narzędzia diagnostyczne. Okno narzędzia diagnostyczne jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby wyświetlić okno, kliknij pozycję **Debuguj/Windows/pokaż narzędzia diagnostyczne**. Po otwarciu okna możesz wybrać narzędzia, dla których mają być zbierane dane.

![Okno narzędzia diagnostyczne](../profiling/media/prof-tour-diagnostic-tools.png "Narzędzia diagnostyczne")

Podczas debugowania można użyć okna **Narzędzia diagnostyczne** do analizowania użycia procesora i pamięci oraz wyświetlania zdarzeń, które zawierają informacje dotyczące wydajności.

![Widok podsumowania narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Podsumowanie narzędzia diagnostyczne")

Okno **Narzędzia diagnostyczne** jest często preferowanym sposobem profilowania aplikacji, ale w przypadku kompilacji wydania można również przeanalizować aplikację. Aby uzyskać więcej informacji na temat różnych metod, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Aby wyświetlić obsługę narzędzia profilowania dla różnych typów aplikacji, zobacz [narzędzie, którego należy użyć?](#which-tool-should-i-use).

> [!NOTE]
> Można używać narzędzi po stronie programu z systemem Windows 7 lub nowszym. System Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania przy użyciu debugera (okno**Narzędzia diagnostyczne** ).

## <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora

Narzędzie użycie procesora CPU jest dobrym miejscem, aby rozpocząć analizowanie wydajności aplikacji. Poinformuje więcej o zasobach procesora CPU zużywanych przez aplikację. Aby zapoznać się z bardziej szczegółowym omówieniem narzędzia użycia procesora CPU, zapoznaj [się z przewodnikiem po stronie początkującej dotyczącej profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md).

W widoku **podsumowania** narzędzia diagnostyczne wybierz opcję **Włącz profilowanie procesora CPU** (musisz być w sesji debugowania).

![Włącz użycie procesora CPU w narzędzia diagnostyczne](../profiling/media/prof-tour-enable-cpu-profiling.png "narzędzia diagnostyczne Włącz użycie procesora CPU")

Aby korzystać z tego narzędzia, należy ustawić dwa punkty przerwania w kodzie, jeden na początku i jeden na końcu funkcji lub region kodu, który ma zostać przeanalizowany. Sprawdzanie danych profilowania po wstrzymaniu w drugim punkcie przerwania.

Widok **użycie procesora CPU** pokazuje listę funkcji uporządkowanych według najdłuższych uruchomionych, z największą uruchomioną funkcją w górnej części. Może to ułatwić wykonywanie zadań, w których są wykonywane wąskie gardła wydajności.

![Widok użycia procesora CPU narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-usage.png "Użycie procesora narzędzia diagnostyczne")

Kliknij dwukrotnie odpowiednią funkcję, a zobaczysz bardziej szczegółowy widok "motylkowy" z trzema okienkiem, z wybraną funkcją w środku okna, funkcję wywołującą po lewej stronie i o nazwie funkcje po prawej stronie. Sekcja **treść funkcji** pokazuje łączny czas (i procent czasu) spędzony w treści funkcji, z wyłączeniem czasu spędzonego na wywoływaniu i wywołaniu funkcji. Te dane mogą pomóc w ocenie, czy sama funkcja jest wąskim gardłem wydajności.

![Narzędzia diagnostyczne widok "motylkowy" wywołującego](../profiling/media/prof-tour-cpu-usage-caller-callee.png "narzędzia diagnostyczne widok wywoływany przez wywołującego")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Okno **Narzędzia diagnostyczne** umożliwia również ocenę użycia pamięci w aplikacji. Na przykład można przyjrzeć się liczbie i rozmiarze obiektów na stercie. Aby uzyskać bardziej szczegółowe instrukcje dotyczące analizowania pamięci, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md).

Aby analizować użycie pamięci, podczas debugowania należy wykonać co najmniej jedną migawkę pamięci. Często najlepszym sposobem analizowania pamięci jest wykonanie dwóch migawek: pierwszy z prawej strony przed problemem z pamięcią, a druga migawka jest bezpośrednio po wystąpieniu podejrzanej pamięci. Następnie można wyświetlić różnice między dwiema migawkami i zobaczyć dokładnie te zmiany.

![Zrób migawkę w narzędzia diagnostyczne](../profiling/media/prof-tour-take-snapshots.gif "narzędzia diagnostyczne wykonaj migawki")

Po wybraniu jednego z łączy ze strzałką zostanie wyświetlony widok różnicowy sterty ( ![zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci") przez czerwoną strzałkę w górę powoduje zwiększenie liczby obiektów (po lewej stronie) lub zwiększenie rozmiaru sterty (po prawej). Po kliknięciu odpowiedniego linku zostanie wyświetlony widok sterty różnicowej uporządkowany według obiektów, które zwiększyły największy rozmiar sterty. Może to pomóc w wydaniu problemów z pamięcią. Na przykład na poniższej ilustracji bajty używane przez `ClassHandlersStore` obiekty wzrosły o 3 492 bajtów w drugiej migawce.

![Widok diff narzędzia diagnostyczne sterty](../profiling/media/prof-tour-mem-usage-diff-heap.png "Widok diff narzędzia diagnostyczne sterty")

Po kliknięciu linku po lewej stronie w widoku **użycie pamięci** widok sterty jest zorganizowany według liczby obiektów; obiekty określonego typu, które zwiększyły największą liczbę, są wyświetlane u góry (posortowane według kolumny **różnic liczby** ).

## <a name="examine-performance-events"></a>Sprawdzanie zdarzeń wydajności

Widok **zdarzenia** w narzędzia diagnostyczne pokazuje różne zdarzenia, które występują podczas debugowania, takie jak ustawienie punktu przerwania lub operacji taktowania kodu. Można sprawdzić informacje, takie jak czas trwania zdarzenia (mierzone od momentu ostatniego wstrzymania debugera lub uruchomienia aplikacji). Na przykład w przypadku przechodzenia przez kod (F10, F11) widok **zdarzenia** pokazuje czas wykonywania aplikacji z poprzedniej operacji kroku do bieżącego kroku.

![Widok zdarzeń narzędzia diagnostyczne](../profiling/media/prof-tour-events.png "Zdarzenia widoku narzędzia diagnostyczne")

 > [!NOTE]
 > Jeśli masz Visual Studio Enterprise, na tej karcie można także zobaczyć [zdarzenia IntelliTrace](../debugger/intellitrace.md) .

Te same zdarzenia są również wyświetlane w edytorze kodu, który można wyświetlić jako funkcja PerfTip.

![Profilowanie samouczka funkcja PerfTip](../profiling/media/prof-tour-perf-tips.png "Profilowanie samouczka funkcja PerfTip")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdzanie wydajności interfejsu użytkownika i zdarzeń dostępności (platformy UWP)

W aplikacjach platformy UWP można włączyć **analizę interfejsu użytkownika** w oknie **Narzędzia diagnostyczne** . Narzędzie wyszukuje typowe problemy z wydajnością lub dostępnością i wyświetla je w widoku **zdarzenia** podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą pomóc w rozwiązywaniu problemów.

![Wyświetlanie zdarzeń analizy interfejsu użytkownika w narzędziach diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "narzędzia diagnostyczne Wyświetl zdarzenia analizy interfejsu użytkownika")

## <a name="post_mortem"></a>Tworzenie wersji profilu kompilacji bez debugera

Narzędzia profilowania, takie jak użycie procesora CPU i użycie pamięci, mogą być używane z debugerem (zobacz wcześniejsze sekcje) lub uruchamianie narzędzi profilowania z użyciem profilera wydajności, który jest przeznaczony do zapewnienia analizy kompilacji **wydań** . W profilerze wydajności można zbierać informacje diagnostyczne, gdy aplikacja jest uruchomiona, a następnie przeanalizować zebrane informacje po zatrzymaniu aplikacji. Aby uzyskać więcej informacji na temat różnych metod, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "Profiler wydajności")

Otwórz Profiler wydajności, wybierając kolejno opcje **debuguj** > **Performance Profiler**.

Okno umożliwi wybranie wielu narzędzi profilowania w niektórych scenariuszach. Narzędzia takie jak użycie procesora CPU mogą zapewnić uzupełniające dane, których można użyć do analizy.

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, takich jak aplikacje WPF dla systemu Windows i aplikacje platformy UWP, można analizować użycie zasobów za pomocą narzędzia Oś czasu aplikacji. Na przykład można analizować czas spędzony przez aplikację do przygotowywania ramek interfejsu użytkownika (układu i renderowania), obsługi żądań sieci i dysku, a także w scenariuszach, takich jak uruchamianie aplikacji, ładowanie stron i zmiana rozmiaru okna. Aby użyć narzędzia, wybierz **oś czasu aplikacji** w profilerze wydajności, a następnie wybierz **Uruchom**. W aplikacji przejdź przez scenariusz do podejrzanego problemu dotyczącego użycia zasobów, a następnie wybierz polecenie **Zatrzymaj zbieranie danych** w celu wygenerowania raportu.

Niska szybkość klatek w grafie **przepływności wizualnej** może odpowiadać problemom wizualnym widocznym podczas uruchamiania aplikacji. Podobnie duże liczby w grafie **wykorzystania wątków interfejsu użytkownika** mogą również odpowiadać problemom odpowiedzi interfejsu użytkownika. W raporcie można wybrać okres z podejrzanym problemem związanym z wydajnością, a następnie sprawdzić szczegółowe działania wątku interfejsu użytkownika w widoku szczegółów osi czasu (dolnym okienku).

![Oś czasu aplikacji narzędzia profilowania](../profiling/media/prof-tour-application-timeline.gif "Oś czasu aplikacji przewodnika profilowania")

W widoku Szczegóły osi czasu można znaleźć informacje takie jak typ activitiy (lub związany z elementem interfejsu użytkownika) wraz z czasem trwania działania. Na przykład na ilustracji zdarzenie **układu** dla kontrolki siatki trwa 57,53 MS.

Aby uzyskać więcej informacji, zobacz [oś czasu aplikacji](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analizowanie użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (składniki Direct3D muszą znajdować C++się w programie) można sprawdzić aktywność procesora GPU i analizować problemy z wydajnością. Aby uzyskać więcej informacji, zobacz [użycie procesora GPU](../debugger/gpu-usage.md). Aby użyć narzędzia, wybierz pozycję **użycie procesora GPU** w profilerze wydajności, a następnie wybierz polecenie **Uruchom**. W aplikacji przejdź do scenariusza, który Cię interesuje, a następnie wybierz pozycję **Zatrzymaj zbieranie** , aby wygenerować raport.

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
## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (platformy UWP)

W aplikacjach platformy UWP można analizować operacje sieciowe wykonywane przy użyciu interfejsu API `Windows.Web.Http`. To narzędzie może pomóc w rozwiązywaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, niepoprawna pamięć podręczna oraz niska wydajność wyświetlania i pobierania. Aby użyć narzędzia, wybierz **Sieć** w profilerze wydajności, a następnie wybierz polecenie **Uruchom**. W aplikacji przejdź przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz polecenie **Zatrzymaj zbieranie** , aby wygenerować raport.

![Narzędzie profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "Użycie sieci diag")

Wybierz operację w widoku Podsumowanie, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Użycie sieci](../profiling/media/prof-tour-network-usage-details.png "Szczegóły użycia sieci diag")

Aby uzyskać więcej informacji, zobacz temat [użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (starsze narzędzia)

Jeśli potrzebujesz funkcji, takich jak Instrumentacja, która nie jest obecnie dostępna w narzędziach użycie procesora CPU lub pamięci, i używasz aplikacji Desktop lub ASP.NET, możesz użyć Eksplorator wydajności do profilowania. (Nieobsługiwane w aplikacjach platformy UWP). Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

![Narzędzie Eksplorator wydajności](../profiling/media/prof-tour-performance-explorer.png "Eksplorator wydajności")

## <a name="which-tool-should-i-use"></a>Którego narzędzia należy użyć?

Poniżej znajduje się tabela zawierająca listę różnych narzędzi oferowanych przez program Visual Studio i różne typy projektów, z których można korzystać:

::: moniker range=">=vs-2019"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET rdzeń|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora CPU](../profiling/cpu-usage.md)|opcję|opcję|opcję|
|[Użycie pamięci](../profiling/memory-usage.md)|opcję|opcję|opcję|
|[Użycie procesora GPU](../debugger/gpu-usage.md)|opcję|opcję|znaleziono|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|opcję|opcję|znaleziono|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|opcję|tak dla języka XAML, nie dla HTML|opcję|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|opcję|znaleziono|opcję|
|[IntelliTrace](../debugger/intellitrace.md)|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET rdzeń|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora CPU](../profiling/cpu-usage.md)|opcję|opcję|opcję|
|[Użycie pamięci](../profiling/memory-usage.md)|opcję|opcję|opcję|
|[Użycie procesora GPU](../debugger/gpu-usage.md)|opcję|opcję|znaleziono|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|opcję|opcję|znaleziono|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|opcję|tak dla języka XAML, nie dla HTML|opcję|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|opcję|znaleziono|opcję|
|[IntelliTrace](../debugger/intellitrace.md)|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|Tylko platforma .NET z Visual Studio Enterprise|
|[Użycie sieci](../profiling/network-usage.md)|znaleziono|opcję|znaleziono|
|[Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)|znaleziono|tak dla języka HTML, nie dla języka XAML|znaleziono|
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|znaleziono|tak dla języka HTML, nie dla języka XAML|znaleziono|
::: moniker-end


## <a name="see-also"></a>Zobacz także
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour)
