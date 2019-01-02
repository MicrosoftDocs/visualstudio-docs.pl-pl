---
title: Miara wydajności o narzędziach profilowania
description: Przyjrzyj się krótki opis różnych narzędzi diagnostycznych dostępnych w programie Visual Studio.
ms.custom: mvc
ms.date: 05/18/2017
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cfa2bcb98e686c04af359900a3c925686659df5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880315"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Szybki start: Pierwsze spojrzenie na narzędziach profilowania

Program Visual Studio oferuje szeroką gamę narzędzi, dzięki którym możesz diagnozować różne rodzaje problemów z wydajnością w zależności od typu aplikacji profilowania.

Narzędzia profilowania, które są dostępne podczas sesji debugowania są dostępne w oknie narzędzia diagnostyczne. Okno narzędzia diagnostyczne pojawia się automatycznie, o ile nie została ona wyłączona. Aby wyświetlić okno, kliknij przycisk **debugowanie / Windows / Pokaż narzędzia diagnostyczne**. Po otwarciu okna wybierz pozycję Narzędzia, które mają być zbierane dane.

![Okno narzędzia diagnostyczne](../profiling/media/prof-tour-diagnostic-tools.png "narzędzia diagnostyczne")

Podczas debugowania, można użyć **narzędzia diagnostyczne** okna do analizowania procesora CPU i użycie pamięci, a można wyświetlać zdarzenia, przedstawiających informacje związane z wydajnością.

![Diagnostyczne Widok Podsumowanie narzędzia](../profiling/media/prof-tour-cpu-and-memory-graph.gif "podsumowanie narzędzia diagnostyki")

**Narzędzia diagnostyczne** okno często jest preferowanym sposobem tworzenia profilu aplikacji, ale dla kompilacji wydania można również wykonać analizy po zakończeniu działania aplikacji zamiast tego. Aby uzyskać więcej informacji na temat różnych metod, zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Aby dowiedzieć się, profilowanie Obsługa narzędzi dla różnych typów aplikacji, zobacz [narzędzie, które należy używać?](#which-tool-should-i-use).

> [!NOTE]
> Można użyć narzędzia późniejszej analizy, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno).

## <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Narzędzie użycie procesora CPU jest dobrym miejscem do rozpoczynania analizowania wydajności Twojej aplikacji. Jego informuje o więcej informacji na temat zasobów procesora CPU, które zużywa Twojej aplikacji. Aby uzyskać bardziej szczegółowy przewodnik dotyczący narzędzie użycie procesora CPU, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md).

Z **Podsumowanie** wyświetlić narzędzi diagnostycznych, wybierz **Włącz profilowanie procesora CPU** (musi być w sesji debugowania).

![Włącz użycie procesora CPU w narzędziach diagnostycznych](../profiling/media/prof-tour-enable-cpu-profiling.png "użycie procesora CPU Włącz narzędzia diagnostyczne")

Aby najbardziej efektywnie korzystać z narzędzia, należy ustawić dwa punkty przerwania w kodzie, jeden na początku, a drugi na końcu funkcji lub region, kod, który chcesz analizować. Przeanalizuj dane profilowania po zostało wstrzymane w drugim punkcie przerwania.

**Użycie procesora CPU** widok zawiera listę funkcji uporządkowane według najdłuższy uruchamiania, za pomocą funkcji najdłużej działających u góry. Może to ułatwić, wskazówki dotyczące przejścia do funkcji gdzie występują wąskie gardła wydajności.

![Diagnostyczne widoku narzędzia użycie procesora CPU](../profiling/media/prof-tour-cpu-usage.png "diagnostyki użycia procesora CPU narzędzia")

Kliknij dwukrotnie funkcję, że jesteś zainteresowany i zostanie wyświetlony bardziej szczegółowy widok trzy okienka "motylkowy", przy użyciu wybranej funkcji w trakcie okna funkcji wywołującej po lewej stronie oraz nazywany funkcje po prawej stronie. **Treści funkcji** sekcja przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i nazywane funkcjami. Te dane mogą pomóc Ci ocenić, czy ta funkcja jest wąskim gardłem wydajności.

![Narzędzia diagnostyczne obiekt wywołujący / / wywoływany "motylkowy" Widok](../profiling/media/prof-tour-cpu-usage-caller-callee.png "diagnostycznych widok wywoływany obiekt wywołujący narzędzia")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

**Narzędzia diagnostyczne** okno umożliwia również ocena użycia pamięci w aplikacji. Na przykład możesz obejrzeć liczbę i rozmiar obiektów na stosie. Aby uzyskać szczegółowe instrukcje, aby analizować pamięci, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md).

Aby analizować użycie pamięci, należy wykonać co najmniej jedną migawkę pamięci podczas debugowania. Często jest najlepszym sposobem na analizowanie pamięci do wykonania dwóch migawek; pierwszy po prawej stronie przed problem podejrzanych pamięci, a drugi migawki po prawej stronie po wystąpieniu problemu podejrzanych pamięci. Następnie możesz wyświetlać różnica dwóch migawek i dokładnie co się zmieniło.

![Utwórz migawkę w oknie narzędzi diagnostycznych](../profiling/media/prof-tour-take-snapshots.gif "migawek zająć narzędzia diagnostyczne")

Po wybraniu jednego z linków strzałkę otrzymują różnicowej widok sterty (czerwona strzałka w górę ![zwiększyć użycie pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "zwiększyć użycie pamięci") pokazuje zwiększenie liczby obiektów (po lewej) lub zwiększenie Rozmiar sterty (po prawej)). Jeśli możesz kliknąć odpowiednie łącze, zostanie wyświetlony widok sterty różnicowej uporządkowane według obiektów, które wzrosła większość Rozmiar sterty. To może pomóc w określeniu problemów z pamięcią. Na przykład na poniższej ilustracji bajtów posługują się `ClassHandlersStore` obiektów wzrosła o 3,492 bajtów w drugim migawki.

![Narzędzia diagnostyczne sterty widoku różnic](../profiling/media/prof-tour-mem-usage-diff-heap.png "widoku różnic narzędzi diagnostycznych w stercie")

Jeśli zamiast tego kliknij link po lewej stronie w **użycie pamięci** widoku widok sterty jest zorganizowana według liczby obiektów; obiekty określonego typu, zwiększenie najbardziej w liczbie są wyświetlane u góry (posortowane według **różnicy liczby** kolumny).

## <a name="examine-performance-events"></a>Zbadaj zdarzenia wydajności

**Zdarzenia** widoku w narzędziach diagnostycznych pokazuje różnych zdarzeń występujących podczas debugowania, takie jak ustawienie punktu przerwania lub operacją wykonywania kodu. Możesz sprawdzić informacje, takie jak czas trwania zdarzenia (mierzony od kiedy debuger ostatnio została wstrzymana, lub podczas uruchamiania aplikacji). Na przykład, jeśli krok po kroku przez kod (F10, F11) **zdarzenia** widok pokazuje czas wykonywania aplikacji z poprzedniej operacji krok do bieżącego kroku.

![Wyświetl zdarzenia narzędzi diagnostycznych](../profiling/media/prof-tour-events.png "zdarzenia narzędzi diagnostycznych w widoku")

 > [!NOTE]
 > Jeśli masz program Visual Studio Enterprise, widać również [zdarzenia IntelliTrace](../debugger/intellitrace.md) na tej karcie.

Te same zdarzenia również widoczne w edytorze kodu można wyświetlić jako Perftip.

![Profilowanie Perftip samouczek](../profiling/media/prof-tour-perf-tips.png "profilowania Perftip samouczek")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdź zdarzenia interfejsu użytkownika wydajność i dostępność (systemu Windows UWP)

W aplikacjach platformy uniwersalnej systemu Windows, aby umożliwić **analiza interfejsu użytkownika** w **narzędzia diagnostyczne** okna. Narzędzie wyszukiwania typowych problemów z wydajnością lub dostępności i wyświetla je w **zdarzenia** wyświetlanie podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą ułatwić rozwiązanie problemów.

![Wyświetl zdarzenia analizy interfejsu użytkownika w oknie narzędzi diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "zdarzenia narzędzi diagnostycznych wyświetlanie interfejsu użytkownika analizy")

## <a name="post_mortem"></a> Kompilacje wydania profilu bez debugera

Profilowanie narzędzi, takich jak użycie procesora CPU i użycie pamięci, które mogą być używane za pomocą debugera (zobacz wcześniejsze sekcje), można też uruchomić profilowania narzędzia do późniejszej analizy przy użyciu Profiler wydajności, które mają na celu dostarczenie analiza **wersji** kompilacji . W Profiler wydajności można zbierać informacje diagnostyczne, gdy aplikacja jest uruchomiona i następnie zbadaj zebranych informacji po zatrzymaniu aplikacji. Aby uzyskać więcej informacji na temat tych różnych rozwiązań, zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "Profiler wydajności")

Otwórz Profiler wydajności, wybierając **debugowania** > **Profiler wydajności**.

Okno pozwoli wybrać wiele narzędzi do profilowania w niektórych scenariuszach. Narzędzia, takie jak użycie Procesora może dostarczyć dodatkowe dane, które służy do pomocy w analizy.

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, takich jak aplikacje WPF pulpitu Windows i aplikacje platformy uniwersalnej systemu Windows można analizować zużycie zasobów za pomocą narzędzia oś czasu aplikacji. Na przykład można analizować czas spędzony przez aplikację na przygotowanie ramek interfejsu użytkownika (układ i renderowania), obsługi żądań dysku i sieci i w przypadku takich scenariuszy uruchomienia aplikacji, strony, obciążenia i rozmiaru okna. Aby użyć narzędzia, wybierz opcję **oś czasu aplikacji** w Profiler wydajności, a następnie wybierz **Start**. W swojej aplikacji, należy przejść przez scenariusz, problem zużycia zasobów potencjalnie złośliwych programów, a następnie wybierz **Zatrzymaj Kolekcjonowanie** podczas generowania raportu.

Mało framerates w **przepustowość wizualna** wykresu może odpowiadać visual problemów, które są wyświetlane podczas uruchamiania aplikacji. Podobnie, dużej liczby w elemencie **wykorzystanie wątku interfejsu użytkownika** wykresu może również odpowiadać problemów z czasem odpowiedzi interfejsu użytkownika. W raporcie wybierz okres, z problemu z wydajnością potencjalnie złośliwych programów i obejrzyj szczegółowe działania wątku interfejsu użytkownika w widoku szczegółów oś czasu (w dolnym okienku).

![Narzędzia profilowania oś czasu aplikacji](../profiling/media/prof-tour-application-timeline.gif "profilowania samouczek oś czasu aplikacji")

W widoku Szczegóły osi czasu można znaleźć informacje, takie jak typ organ (lub zaangażowane elementu interfejsu użytkownika), oraz czas trwania działania. Na przykład na ilustracji **układ** zdarzeń dla formantu siatki przyjmuje 57.53 ms.

Aby uzyskać więcej informacji, zobacz [oś czasu aplikacji](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analiza użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (Direct3D składniki muszą się znajdować w języku C++) możesz sprawdzić działanie procesora GPU i analizowania problemów z wydajnością. Aby uzyskać więcej informacji, zobacz [użycie procesora GPU](../debugger/gpu-usage.md). Aby użyć narzędzia, wybierz opcję **użycie procesora GPU** w Profiler wydajności, a następnie wybierz **Start**. W swojej aplikacji, należy przejść przez scenariusz, w którym interesuje Cię profilowania, a następnie wybierz **Zatrzymaj Kolekcjonowanie** do wygenerowania raportu.

Po wybraniu przedziale czasu na wykresach i **wyświetlić szczegóły**, szczegółowy widok, który pojawia się w dolnym okienku. W widoku szczegółowym można sprawdzić, ile działania dzieje się na każdym GPU i CPU. Wybierz zdarzenia w okienku najniższy można pobrać okna podręczne na osi czasu. Na przykład wybierz **obecne** zdarzenia w celu wyświetlenia **obecne** wywołania okna podręczne. (Światła szare pionowe linie pionie może służyć jako odwołanie do zrozumienia, czy niektóre **obecne** wywołania pominięte w pionie. Musi zawierać jeden **obecne** wywołań między co dwa Vsyncs w kolejności dla aplikacji, aby stale trafić 60 kl. / s.)

![Użycie procesora GPU, narzędzia profilowania](../profiling/media/prof-tour-gpu-usage.png "Diag użycie procesora GPU")

Wykresy umożliwia również ustalić, czy istnieją powiązane procesora CPU lub GPU powiązany wąskich gardeł wydajności.

## <a name="analyze-performance-javascript-uwp"></a>Analizowanie wydajności (JavaScript dla platformy UWP)

W przypadku aplikacji platformy uniwersalnej systemu Windows można użyć narzędzi pamięć języka JavaScript i HTML UI Responsiveness.

Narzędzi pamięć języka JavaScript jest podobne do dostępnych dla innych typów aplikacji Narzędzie użycie pamięci. To narzędzie służy do zrozumienia użycia pamięci i znaleźć przecieki pamięci w aplikacji. Aby uzyskać więcej informacji o tym narzędziu, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).

![Pamięć języka JavaScript, narzędzia profilowania](../profiling/media/diagjsmemory.png "DiagJSMemory")

Do diagnozowania czasu odpowiedzi interfejsu użytkownika, powolne ładowanie czasu i powolne aktualizacji visual w aplikacji platformy uniwersalnej systemu Windows, należy użyć narzędzia HTML UI Responsiveness. Użycie jest podobny do narzędzia oś czasu aplikacji dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [HTML UI responsiveness](../profiling/html-ui-responsiveness.md).

![HTML UI Responsiveness, narzędzia profilowania](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (systemu Windows UWP)

W aplikacjach platformy uniwersalnej systemu Windows, można analizować operacje sieciowe, wykonywane przy użyciu `Windows.Web.Http` interfejsu API. To narzędzie może pomóc rozwiązać problemy, takie jak problemy dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i pobrać wydajności. Aby użyć narzędzia, wybierz opcję **sieci** w Profiler wydajności, a następnie wybierz **Start**. W swojej aplikacji, przechodzą przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz **Zatrzymaj Kolekcjonowanie** podczas generowania raportu.

![Użycie narzędzia profilowania sieci](../profiling/media/prof-tour-network-usage.png "Diag użycia sieci")

Wybierz operację podsumowania bardziej szczegółowo widokami.

![Szczegółowe informacje w narzędziu użycie sieci](../profiling/media/prof-tour-network-usage-details.png "szczegółów użycia sieci Diag")

Aby uzyskać więcej informacji, zobacz [użycie sieci](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (Narzędzia graficzne w starszej wersji)

Jeśli potrzebujesz funkcji, takich jak Instrumentacja, które nie są aktualnie dostępne w menu Narzędzia użycie procesora CPU i użycie pamięci i korzystasz z pulpitu lub aplikacji w technologii ASP.NET, można użyć Eksploratora wydajności pod kątem profilowania. (Nieobsługiwane w aplikacjach platformy UWP). Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

![Okno Eksploratora wydajności](../profiling/media/prof-tour-performance-explorer.png "Eksploratora wydajności")

## <a name="which-tool-should-i-use"></a>Narzędzie, które należy używać?  

Poniżej przedstawiono listę różnych narzędzi oferowanych przez program Visual Studio i różnych typach projektów można ich używać za pomocą:
  
|Narzędzia wydajności|Pulpit systemu Windows|Platforma UWP|ASP.NET/ASP.NET Core| 
|----------------------|---------------------|-------------|-------------|  
|[Użycie procesora CPU](../profiling/cpu-usage.md)|tak|tak|tak|
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|tak| 
|[Użycie procesora GPU](../debugger/gpu-usage.md)|tak|tak|Brak| 
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak|tak|Brak|
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak, aby XAML nie dla kodu HTML|tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|Brak|tak|
|[IntelliTrace](../debugger/intellitrace.md)|.NET przy użyciu Visual Studio Enterprise|.NET przy użyciu Visual Studio Enterprise|.NET przy użyciu Visual Studio Enterprise|
|[Użycie sieci](../profiling/network-usage.md)|Brak|tak|Brak|
|[Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)|Brak|tak w języku HTML, nie dla XAML|Brak| 
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|Brak|tak w języku HTML, nie dla XAML|Brak|

## <a name="see-also"></a>Zobacz także  
 [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour)
