---
title: Mierzenie wydajności za pomocą narzędzi do profilowania
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
ms.openlocfilehash: b1ee476a518444bfff7a97a12c9fd814e9509239
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412038"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Szybki start: pierwsze spojrzenie na narzędzia profilowania

Visual Studio udostępnia wiele narzędzi profilowania, które ułatwiają diagnozowanie różnych rodzajów problemów z wydajnością w zależności od typu aplikacji.

Narzędzia profilowania, do których można uzyskać dostęp podczas sesji debugowania, są dostępne w oknie Narzędzia diagnostyczne. Okno Narzędzia diagnostyczne jest wyświetlane automatycznie, chyba że zostało wyłączone. Aby wyświetlić okno, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**. Po otwarciu okna można wybrać narzędzia, dla których mają być zbierane dane.

![Okno Narzędzia diagnostyczne](../profiling/media/prof-tour-diagnostic-tools.png "Narzędzia diagnostyczne")

Podczas debugowania można użyć okna **Narzędzia diagnostyczne** do analizowania użycia procesora CPU i pamięci oraz można wyświetlać zdarzenia, które pokazują informacje związane z wydajnością.

![Widok podsumowania narzędzi diagnostycznych](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Podsumowanie narzędzi diagnostycznych")

**Okna Narzędzia diagnostyczne** jest często preferowanym sposobem profilowania aplikacji, ale dla kompilacji wydania można również wykonać analizę pośmiertną aplikacji zamiast tego. Aby uzyskać więcej informacji na temat różnych podejść, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Aby wyświetlić obsługę narzędzi do profilowania dla różnych typów aplikacji, zobacz [Które narzędzie należy użyć?](#which-tool-should-i-use).

> [!NOTE]
> Narzędzia pośmiertne można używać w systemie Windows 7 lub nowszych. System Windows 8 i nowsze są wymagane do uruchamiania narzędzi profilowania za pomocą debugera (okno**Narzędzia diagnostyczne).**

## <a name="examine-performance-using-perftips"></a>Badanie wydajności przy użyciu porad dotyczących wydajności

Często najprostszym sposobem wyświetlania informacji o wydajności jest użycie [porad dotyczących wydajności](../profiling/perftips.md). Za pomocą perfTips, można wyświetlić informacje o wydajności podczas interakcji z kodem. Można sprawdzić informacje, takie jak czas trwania zdarzenia (mierzona od kiedy debuger został ostatnio wstrzymany lub po uruchomieniu aplikacji). Na przykład jeśli krok po kroku kodu (F10, F11), PerfTips pokaż czas trwania środowiska uruchomieniowego aplikacji od operacji poprzedniego kroku do bieżącego kroku.

![Profilowanie Porad dotyczących wycieczek](../profiling/media/prof-tour-perf-tips.png "Profilowanie Porad dotyczących wycieczek")

Porady dotyczące obrażeń od dostępu można użyć, aby sprawdzić, jak długo trwa dla bloku kodu do wykonania lub jak długo trwa dla jednej funkcji, aby zakończyć.

Porady dotyczące programów zapewniają te same zdarzenia, które również są wyświetlane w widoku **Zdarzenia** narzędzi diagnostycznych. W widoku **Zdarzenia** można wyświetlić różne zdarzenia, które występują podczas debugowania, takie jak ustawienie punktu przerwania lub operacji krokowej kodu.

![Widok zdarzenia narzędzi diagnostycznych](../profiling/media/prof-tour-events.png "Narzędzia diagnostyczne Wyświetl zdarzenia")

 > [!NOTE]
 > Jeśli masz visual studio enterprise, można również zobaczyć [IntelliTrace zdarzenia](../debugger/intellitrace.md) na tej karcie.

## <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora

Narzędzie Użycie procesora CPU jest dobrym miejscem do rozpoczęcia analizowania wydajności aplikacji. Poinformuje cię więcej o zasobach procesora CPU, które aplikacja zużywa. Aby uzyskać bardziej szczegółowe wskazówki dotyczące narzędzia Użycie procesora CPU, zobacz [Mierzenie wydajności aplikacji przez analizowanie użycia procesora .](../profiling/beginners-guide-to-performance-profiling.md)

W widoku **Podsumowanie** narzędzi diagnostycznych wybierz pozycję **Włącz profilowanie procesora CPU** (musisz być w sesji debugowania).

![Włączanie użycia procesora w narzędziach diagnostycznych](../profiling/media/prof-tour-enable-cpu-profiling.png "Narzędzia diagnostyczne umożliwiają użycie procesora")

Aby użyć narzędzia najbardziej efektywnie, należy ustawić dwa punkty przerwania w kodzie, jeden na początku i jeden na końcu funkcji lub regionu kodu, który chcesz analizować. Sprawdź dane profilowania, gdy są wstrzymane w drugim punkcie przerwania.

Widok **Użycie procesora CPU** pokazuje listę funkcji uporządkowanych według najdłuższego działania, z najdłużej działającą funkcją u góry. Może to pomóc w prowadzeniu funkcji, w których występują wąskie gardła wydajności.

![Widok użycia procesora CPU narzędzi diagnostycznych](../profiling/media/prof-tour-cpu-usage.png "Użycie procesora CPU narzędzi diagnostycznych")

Kliknij dwukrotnie funkcję, która Cię interesuje, a zobaczysz bardziej szczegółowy widok "motyla" z wybranym widokiem w środku okna, funkcją wywołującą po lewej stronie i wywoływanymi funkcjami po prawej stronie. **Treść funkcji** Sekcja pokazuje całkowitą ilość czasu (i procent czasu) spędzonego w treści funkcji z wyłączeniem czasu spędzonego podczas wywoływania i wywoływania funkcji. Te dane mogą pomóc w ocenie, czy sama funkcja jest wąskim gardłem wydajności.

![Narzędzia diagnostyczne wywoływany widok "motyl"](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Widok wywoływania wywołującego narzędzia diagnostyczne")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Okno **Narzędzia diagnostyczne** umożliwia również ocenę użycia pamięci w aplikacji za pomocą narzędzia **Użycie pamięci.** Na przykład można spojrzeć na liczbę i rozmiar obiektów na stercie. Aby uzyskać bardziej szczegółowe instrukcje dotyczące analizowania pamięci, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md). Inne narzędzie do analizy pamięci, [narzędzie .NET Object Allocation,](../profiling/dotnet-alloc-tool.md)pomaga zidentyfikować wzorce alokacji i anomalie w kodzie platformy .NET.

Aby przeanalizować użycie pamięci za pomocą użycia pamięci zintegrowanej z debugerem, należy wykonać co najmniej jedną migawkę pamięci. Często najlepszym sposobem analizowania pamięci jest podjęcie dwóch migawek; pierwsze prawo przed podejrzewanym problemem z pamięcią, a drugie migawka zaraz po wystąpieniu podejrzewanego problemu z pamięcią. Następnie można wyświetlić różnice z dwóch migawek i zobaczyć dokładnie, co się zmieniło.

![Tworzenie migawki w narzędziach diagnostycznych](../profiling/media/prof-tour-take-snapshots.gif "Narzędzia diagnostyczne do robienia zdjęć")

Po wybraniu jednego z łączy strzałek zostanie podany widok różnicowy sterty (czerwona strzałka w górę ![Zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zwiększenie użycia pamięci") pokazuje rosnącą liczbę obiektów (po lewej) lub zwiększający się rozmiar sterty (po prawej)). Jeśli klikniesz prawe łącze, otrzymasz widok sterty różnicowej uporządkowany według obiektów, które zwiększyły się najbardziej w rozmiarze sterty. Może to pomóc w określić problemy z pamięcią. Na przykład na poniższej ilustracji bajty używane przez `ClassHandlersStore` obiekty powiększone o 3492 bajty w drugiej migawce.

![Widok różnic sterty sterty narzędzi diagnostycznych](../profiling/media/prof-tour-mem-usage-diff-heap.png "Widok różnicy sterty sterty narzędzi diagnostycznych")

Jeśli klikniesz łącze po lewej stronie zamiast w widoku **Użycie pamięci,** widok sterty jest zorganizowany według liczby obiektów; obiekty określonego typu, które zwiększyły się najbardziej w liczbie są wyświetlane u góry (posortowane według kolumny **Count Diff).**

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a>Kompilacje wersji profilu bez debugera

Narzędzia profilowania, takie jak użycie procesora CPU i użycie pamięci, mogą być używane z debugerem (zobacz wcześniejsze sekcje) lub można uruchomić narzędzia profilowania po śmierć przy użyciu profilera wydajności, który ma na celu zapewnienie analizy kompilacji **wydania.** W programie Performance Profiler można zbierać informacje diagnostyczne, gdy aplikacja jest uruchomiona, a następnie sprawdzić zebrane informacje po zatrzymaniu aplikacji. Aby uzyskać więcej informacji na temat tych różnych podejść, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Dodatkowe narzędzia, takie jak [narzędzie .NET Object Allocation,](../profiling/dotnet-alloc-tool.md) są również dostępne w programie Performance Profiler.

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "Profiler wydajności")

Otwórz program Profiler wydajności, wybierając pozycję **Debug** > **Performance Profiler**.

Okno umożliwia wybranie wielu narzędzi profilowania w niektórych scenariuszach. Narzędzia, takie jak użycie procesora CPU może zapewnić dodatkowe dane, które można użyć, aby pomóc w analizie. Można również użyć [profilera wiersza polecenia,](../profiling/profile-apps-from-command-line.md) aby włączyć scenariusze obejmujące wiele narzędzi profilowania.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdzanie zdarzeń wydajności i ułatwień dostępu interfejsu użytkownika (UWP)

W aplikacjach platformy uniwersalnej systemu Windows można włączyć **analizę interfejsu użytkownika** w oknie Narzędzia **diagnostyczne.** Narzędzie wyszukuje typowe problemy z wydajnością lub dostępnością i wyświetla je w widoku **Zdarzenia** podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą pomóc w rozwiązaniu problemów.

![Wyświetlanie zdarzeń analizy interfejsu użytkownika w narzędziach diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "Narzędzia diagnostyczne Wyświetl zdarzenia analizy interfejsu użytkownika")

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, takich jak aplikacje WPF dla komputerów stacjonarnych systemu Windows i aplikacje platformy uniwersalnej systemu Windows, można analizować zużycie zasobów za pomocą narzędzia Oś czasu aplikacji. Na przykład można analizować czas spędzony przez aplikację przygotowanie ramek interfejsu użytkownika (układ i renderowanie), obsługa żądań sieciowych i dysków oraz w scenariuszach, takich jak uruchamianie aplikacji, ładowanie strony i rozmiar okna. Aby użyć tego narzędzia, wybierz pozycję **Oś czasu aplikacji** w programie Profiler wydajności, a następnie wybierz pozycję **Start**. W aplikacji przejdź przez scenariusz z podejrzanym problemem zużycia zasobów, a następnie wybierz pozycję **Zatrzymaj kolekcję,** aby wygenerować raport.

Niska liczba klatek na sekundę na wykresie **przepływności wizualnej** może odpowiadać problemom wizualnym widocznym podczas uruchamiania aplikacji. Podobnie wysokie liczby na wykresie **wykorzystania wątku interfejsu** użytkownika mogą również odpowiadać problemom z odpowiedzią interfejsu użytkownika. W raporcie można wybrać okres z podejrzeniem problemu z wydajnością, a następnie sprawdzić szczegółowe działania wątku interfejsu użytkownika w widoku szczegółów osi czasu (dolnym okienku).

![Narzędzie do profilowania osi czasu aplikacji](../profiling/media/prof-tour-application-timeline.gif "Profilowanie oś czasu aplikacji przewodnika")

W widoku szczegóły osi czasu można znaleźć informacje, takie jak typ działania (lub zaangażowany element interfejsu użytkownika) wraz z czasem trwania działania. Na przykład na ilustracji **Layout** zdarzenie dla Grid kontroli trwa 57.53 ms.

Aby uzyskać więcej informacji, zobacz [Oś czasu aplikacji](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analizowanie użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (składniki Direct3D muszą być w języku C++) można sprawdzić aktywność na procesorze GPU i analizować problemy z wydajnością. Aby uzyskać więcej informacji, zobacz [Użycie procesora GPU](/visualstudio/debugger/graphics/gpu-usage). Aby użyć tego narzędzia, wybierz pozycję **Użycie procesora GPU** w programie Profiler wydajności, a następnie wybierz pozycję **Start**. W aplikacji przejdź przez scenariusz, który cię interesuje w profilowaniu, a następnie wybierz **pozycję Zatrzymaj kolekcję,** aby wygenerować raport.

Po wybraniu okresu na wykresach i wybraniu **szczegółów widoku**w dolnym okienku pojawi się widok szczegółowy. W widoku szczegółowym można sprawdzić, ile aktywności dzieje się na każdym procesorze CPU i procesorze GPU. Wybierz zdarzenia w najniższym okienku, aby uzyskać wyskakujące okienka na osi czasu. Na przykład wybierz **zdarzenie Prezentuj,** aby wyświetlić wyskakujące okienka **połączeń Present.** (Jasnoszare pionowe linie Vsync mogą służyć jako odwołanie, aby **zrozumieć,** czy niektóre obecne wywołania nieodebrane Vsync. Musi istnieć jedno **obecne** wywołanie między co dwa Vsyncs, aby aplikacja stale trafiać 60 FPS.)

![Narzędzie do profilowania użycia gpu](../profiling/media/prof-tour-gpu-usage.png "Zastosowanie diag GPU")

Można również użyć wykresów, aby określić, czy istnieją wąskie gardła wydajności związane z procesorem CPU lub GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizowanie wydajności (środowisko Platformy uniwersalnej systemu JavaScript)

W przypadku aplikacji platformy uniwersalnej systemu Windows można użyć narzędzia Pamięć JavaScript i narzędzia Do reagowania interfejsu użytkownika HTML.

Narzędzie Pamięć JavaScript jest podobne do narzędzia Użycie pamięci dostępnego dla innych typów aplikacji. Za pomocą tego narzędzia można zrozumieć użycie pamięci i znaleźć przecieki pamięci w aplikacji. Aby uzyskać więcej informacji na temat narzędzia, zobacz [Pamięć JavaScript](../profiling/javascript-memory.md).

![Narzędzie do profilowania pamięci JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory ( DiagJSMemory )")

Aby zdiagnozować czas reakcji interfejsu użytkownika, powolny czas ładowania i powolne aktualizacje wizualne w aplikacjach platformy uniwersalnej systemu Windows, użyj narzędzia Czas reakcji interfejsu użytkownika HTML. Użycie jest podobne do narzędzia Osi czasu aplikacji dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [reagowanie interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md).

![Narzędzie do profilowania reakcji interfejsu użytkownika HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp ( DiagHTMLResp )")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (platforma UWP)

W aplikacjach platformy uniwersalnej systemu Windows `Windows.Web.Http` można analizować operacje sieciowe wykonywane za pomocą interfejsu API. To narzędzie może pomóc w rozwiązaniu problemów, takich jak problemy z dostępem i uwierzytelnianiem, nieprawidłowe użycie pamięci podręcznej oraz niska wydajność wyświetlania i pobierania. Aby użyć tego narzędzia, wybierz pozycję **Sieć** w programie Profiler wydajności, a następnie wybierz pozycję **Start**. W aplikacji przejdź przez scenariusz, `Windows.Web.Http`który używa , a następnie wybierz **pozycję Zatrzymaj kolekcję,** aby wygenerować raport.

![Narzędzie do profilowania użycia sieci](../profiling/media/prof-tour-network-usage.png "Zużycie sieci Diag")

Wybierz operację w widoku podsumowania, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje w narzędziu Do korzystania z sieci](../profiling/media/prof-tour-network-usage-details.png "Diag Szczegóły wykorzystania sieci")

Aby uzyskać więcej informacji, zobacz [Użycie sieci](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (starsze narzędzia)

::: moniker range="vs-2017"
Jeśli potrzebujesz funkcji, takich jak instrumentacja, które nie są obecnie obecne w narzędziach Użycie procesora CPU lub Użycie pamięci, a korzystasz z aplikacji pulpitu lub ASP.NET, możesz użyć Eksploratora wydajności do profilowania. (Nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows). Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 starszy Eksplorator wydajności i powiązane narzędzia profilowania, takie jak Kreator wydajności, zostały złożone do programu Profiler wydajności, który można otworzyć za pomocą **programu Debug** > **Performance Profiler**. W programie Performance Profiler dostępne narzędzia diagnostyczne zależą od wybranego celu i bieżącego, otwartego projektu startowego. Narzędzie Użycie procesora CPU zapewnia możliwość próbkowania wcześniej obsługiwane w Kreatorze wydajności. Narzędzie Instrumentacja zapewnia funkcję profilowania instrumentowanego (do precyzyjnej liczby wywołań i czasów trwania), która znajdowała się w Kreatorze wydajności. Dodatkowe narzędzia pamięci są również wyświetlane w programie Performance Profiler.
::: moniker-end

![Narzędzie Eksplorator wydajności](../profiling/media/prof-tour-performance-explorer.png "Eksplorator wydajności")

## <a name="which-tool-should-i-use"></a>Którego narzędzia należy użyć?

Oto tabela, która zawiera listę różnych narzędzi, które oferuje program Visual Studio i różne typy projektów, z którymi można ich używać:

::: moniker range=">=vs-2019"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|Rdzeń ASP.NET/ASP.NET|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora](../profiling/cpu-usage.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Alokacja obiektów .NET](../profiling/dotnet-alloc-tool.md)|tak (tylko.NET)|tak|tak|
|[Użycie procesora GPU](/visualstudio/debugger/graphics/gpu-usage)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak|tak|nie|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak dla XAML, nie dla HTML|tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|nie|tak|
|[IntelliTrace](../debugger/intellitrace.md)|.NET tylko z programem Visual Studio Enterprise|.NET tylko z programem Visual Studio Enterprise|.NET tylko z programem Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Narzędzie wydajności|Pulpit systemu Windows|Platforma UWP|Rdzeń ASP.NET/ASP.NET|
|----------------------|---------------------|-------------|-------------|
|[Użycie procesora](../profiling/cpu-usage.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak|
|[Użycie procesora GPU](/visualstudio/debugger/graphics/gpu-usage)|tak|tak|nie|
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak|tak|nie|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak dla XAML, nie dla HTML|tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|nie|tak|
|[IntelliTrace](../debugger/intellitrace.md)|.NET tylko z programem Visual Studio Enterprise|.NET tylko z programem Visual Studio Enterprise|.NET tylko z programem Visual Studio Enterprise|
|[Użycie sieci](../profiling/network-usage.md)|nie|tak|nie|
|[Czas odpowiedzi interfejsu użytkownika języka HTML](../profiling/html-ui-responsiveness.md)|nie|Tak dla HTML, nie dla XAML|nie|
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|nie|Tak dla HTML, nie dla XAML|nie|
::: moniker-end


## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md)
