---
title: Omówienie diagnostyki grafiki | Microsoft Docs
description: Visual Studio Diagnostyka grafiki to zestaw narzędzi do rejestrować działania direct3D i analizować dzienniki w celu rozwiązywania problemów z renderowaniem i wydajnością.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24b67b9585db973e6cbef3b1c28c6068e7c37034
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386205"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Omówienie diagnostyki grafiki w programie Visual Studio
Visual Studio *Diagnostyka grafiki* to zestaw narzędzi do rejestrowania, a następnie analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można używać w aplikacjach działających lokalnie na komputerze z systemem Windows lub na zdalnym komputerze lub urządzeniu.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Używanie Graphics Diagnostics do debugowania problemów z renderowaniem
 Debugowanie problemów z renderowaniem w rozbudowanych graficznie aplikacjach nie jest tak proste jak uruchomienie debugera i krokowe wykonywanie kodu. W każdej klatce są produkowane setki tysięcy unikatowych pikseli, każdy na podstawie złożonego zestawu stanu, danych, parametrów i kodu — możliwe, że tylko kilka z powyższych pikseli pokaże problem, który próbujesz zdiagnozować. Aby jeszcze bardziej skomplikować sprawy, kod, który generuje każdy piksel, jest wykonywany na wyspecjalizowanym sprzęcie, który przetwarza setki pikseli równolegle. Tradycyjne narzędzia i techniki debugowania, z których trudno się korzysta nawet w kodzie mało skomplikowanym pod względem wątków, są nieskuteczne w obliczu tak dużej ilości danych.

 Narzędzia Diagnostyka grafiki w programie ułatwiają znajdowanie problemów z renderowaniem, zaczynając od artefaktów wizualnych wskazujących problem, a następnie śledząc go z powrotem do źródła problemu, koncentrując się tylko na odpowiednim kodzie cieniowania, etapach potoku, wywołaniach rysowania, zasobach i stanie urządzenia — we własnym kodzie źródłowym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacji.

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX
 Diagnostyka grafiki obsługuje aplikacje, które korzystają z usługi Direct3D 10 lub większej, i zapewnia ograniczoną obsługę aplikacji, które używają direct2D. Nie obsługuje aplikacji, które używają starszych wersji Direct3D, DirectDraw lub innych graficznych interfejsów API.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 i Direct3D 12
> [!NOTE]
> Visual Studio PIX w systemie Windows dla gier DirectX 12. [PIX w systemie Windows](https://aka.ms/PIXonWindows) to narzędzie do dostrajania i debugowania wydajności, które w pełni obsługuje technologię DirectX 12. [Dowiedz się więcej lub pobierz](visual-studio-graphics-diagnostics-directx-12.md) [tutaj](https://aka.ms/downloadPIX).


 Windows 10 wprowadzono *direct3D 12,* który znacznie różni się od Direct3D 10 i Direct3D 11. Te różnice wprowadzają z powrotem directx do nowoczesnego sprzętu graficznego i uwolnią jego pełny potencjał, ale również wprowadzają duże zmiany interfejsu API i niosą większą odpowiedzialność na programistę za zarządzanie okresami istnienia zasobów i konfliktami. Pomimo różnic, Diagnostyka grafiki Direct3D 12 utrzymuje parzystość funkcji z Diagnostyka grafiki Direct3D 11.2.

 Windows 10 obsługuje również poprzednie wersje direct3D oraz gry i aplikacje, które na nich polegają. Diagnostyka grafiki w Visual Studio nadal obsługuje direct3D 10 i Direct3D 11 na Windows 10.

### <a name="limited-direct2d-support"></a>Ograniczona obsługa Direct2D
 Ponieważ Direct2D jest interfejsem API w trybie użytkownika, który jest zbudowany na podstawie direct3D, można użyć usługi Diagnostyka grafiki do debugowania problemów z renderowaniem w aplikacjach, które używają direct2D. Jednak ponieważ rejestrowane są tylko podstawowe zdarzenia Direct3D, a nie zdarzenia Direct2D wyższego poziomu, zdarzenia Direct2D nie pojawią się na liście zdarzeń grafiki. Ponadto, ponieważ relacja między zdarzeniami Direct2D i wynikowymi zdarzeniami Direct3D nie jest zawsze jasna, używanie Graphics Diagnostics do debugowania problemów z renderowaniem w aplikacjach, które używają Direct2D, nie jest proste. Nadal można korzystać z Graphics Diagnostics, aby uzyskać informacje dotyczące problemów renderowania niskiego poziomu w aplikacjach, które korzystają z Direct2D.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Diagnostyka grafiki funkcji w Visual Studio
 Diagnostyka grafiki ma dedykowany interfejs — okno Analizator grafiki — do diagnozowania problemów z renderowaniem, ale także dodaje niektóre narzędzia do interfejsu Visual Studio graficznego.

### <a name="the-graphics-toolbar-visual-studio"></a>Pasek narzędzi grafiki (Visual Studio)
 Pasek narzędzi Grafika zapewnia szybki dostęp do Diagnostyka grafiki poleceń.

 Przycisk **Rozpocznij diagnostykę** uruchamia aplikację w obszarze Diagnostyka grafiki. Gdy aplikacja jest uruchomiona w obszarze Diagnostyka grafiki, przycisk **Przechwyć następną wyrenderowana** ramkę jest włączony.

### <a name="diagnostics-capture-interface"></a>Interfejs przechwytywania diagnostyki
 Po uruchomieniu aplikacji w obszarze Diagnostyka grafiki program Visual Studio interfejs sesji diagnostyki, którego można użyć do przechwytywania ramek, a także wyświetla bieżące obciążenie procesora CPU i procesora GPU. Obciążenie procesora CPU i procesora GPU jest wyświetlane, aby ułatwić identyfikowanie ramek, które mogą być przechwytywane ze względu na ich charakterystykę wydajności, a nie błędy renderowania.

 Nie jest to jednak jedyny sposób przechwytywania ramek. Ramki można również przechwytywać przy użyciu interfejsu przechwytywania programowego lub przy użyciu programu przechwytywania wiersza polecenia, dxcap.exe.

 Aby [uzyskać więcej informacji,](capturing-graphics-information.md) zobacz Przechwytywanie informacji graficznych.

### <a name="gpu-usage"></a>Użycie procesora GPU
 Diagnostyka grafiki profilować wydajność aplikacji Direct3D. Ponieważ dane profilowania byłyby skośne przez rejestrowanie szczegółów zdarzeń graficznych, jest to oddzielone od przechwytywania ramek do zbadania za pomocą Analizatora grafiki.

 Aby uzyskać [więcej informacji,](../../profiling/gpu-usage.md) zobacz Użycie procesora GPU.

### <a name="directx-control-panel"></a>Panel sterowania DirectX
 Panel sterowania DirectX to składnik DirectX, którego można użyć, aby zmienić sposób zachowania DirectX — na przykład włączyć wersję składników wykonawczych DirectX przeznaczoną do debugowania, wybrać rodzaj komunikatów debugowania, które są raportowane, oraz uniemożliwić korzystanie z niektórych funkcji sprzętowych karty graficznej w celu emulacji mniej zaawansowanego sprzętu. Ten poziom kontroli nad DirectX może pomóc w debugowaniu i testowaniu aplikacji DirectX. Dostęp do panelu sterowania DirectX można uzyskać z Visual Studio.

#### <a name="to-open-the-directx-control-panel"></a>Aby otworzyć panel sterowania DirectX

- Na pasku menu wybierz pozycje **Debugowanie,** **Grafika,** **DirectX Panel sterowania.**

## <a name="graphics-analyzer"></a>Analizator grafiki
 Interfejs analizator grafiki programu Visual Studio jest dedykowanym interfejsem do badania problemów z renderowaniem i wydajnością w przechwyconych już ramkach. Wewnątrz analizatora grafiki znajduje się kilka narzędzi, które ułatwiają eksplorowanie i zrozumienie zachowania renderowania aplikacji. Każde narzędzie uwidacznia inny rodzaj informacji o sprawdzanych ramkach, a narzędzia są zaprojektowane tak, aby były używane do intuicyjnego zawężania źródła problemu renderowania, począwszy od jego wyglądu w ramce.

 Na tej ilustracji przedstawiono typowy układ narzędzi w Analizatorze grafiki.

 ![Wszystkie okna debugera grafiki](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Pasek narzędzi grafiki (Analizator grafiki)
 Pasek narzędzi Grafika zapewnia szybki dostęp do okien narzędzi Analizator grafiki.

 ![Pasek narzędzi Grafika w trybie diagnostyki grafiki](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Dokument dziennika grafiki
 W analizatorze grafiki najbardziej widocznym oknem narzędzi jest dokument dziennika grafiki. To okno reprezentuje wszystkie przechwycone ramki, uruchamiając aplikację w obszarze Diagnostyka grafiki. W tym miejscu możesz wybrać inną ramkę do zbadania lub wybrać określony piksel do zbadania za pomocą narzędzia Historia pikseli. Obraz framebuffer wyświetlany w tym dokumencie zmienia się w celu odzwierciedlenia aktualnie wybranego zdarzenia, dzięki czemu można zobaczyć, jak w czasie ma to wpływ na element framebuffer.

 Dokument [dziennika](graphics-log-document.md) grafiki jest również punktem wejścia do narzędzia do analizy ramek, które pomaga zrozumieć wydajność ramki, zmieniając sposób konfigurowania niektórych aspektów renderowania i dostarczając wyniki testów porównawczych do porównania z oryginalnym.

### <a name="event-list"></a>Lista zdarzeń
 Zdarzenia graficzne oznaczają każde wywołanie interfejsu API Direct3D i zdarzenie zdefiniowane przez użytkownika.

 Lista [zdarzeń zawiera](graphics-event-list.md) wszystkie zdarzenia grafiki, które zostały zarejestrowane podczas badania ramki. Aby ułatwić znalezienie ważnych informacji, listę zdarzeń można wyświetlać hierarchicznie — z ostatnimi zmianami stanu poniżej kolejnego wywołania rysowania — lub jako oś czasu. Ponadto zdarzenia są kodowane kolorami na podstawie kolejki, do której należą, i można filtrować listę, aby uwzględnić tylko zdarzenia, które Cię interesują.

 Po wybraniu zdarzenia na liście pozostałe narzędzia do analizy grafiki odzwierciedlają stan ramki w czasie tego zdarzenia. W ten sposób można zobaczyć wpływ dowolnego zdarzenia na procesor GPU. Na przykład można zobaczyć natychmiastowy wpływ dowolnego wywołania rysowania na ramkę, nawet jeśli zostanie on zasłonięte przez kolejne wywołania rysowania. Niektóre zdarzenia mają również hiperlinki, które można śledzić, aby wyświetlić więcej szczegółowych informacji o jego parametrach lub powiązanych obiektach zasobów.

### <a name="pipeline-stages"></a>Etapy potoku
 Każde wywołanie rysowania w aplikacji przechodzi przez potok grafiki dostarczony przez direct3D. Na każdym etapie potoku dane wyjściowe z poprzedniego etapu są przekształcane przez mały program nazywany cieniem, a następnie przekazywane do następnego etapu, aż w końcu zostanie wyrenderowany na ekranie. Wiele błędów renderowania występuje na granicy między etapami potoku, gdy format danych wyjściowych różni się od oczekiwań następnego etapu lub gdy jakikolwiek jeden etap po prostu generuje nieprawidłowe wyniki. Zwykle wyniki są tylko takie, jak na ekranie, i nie można łatwo określić, gdzie w potoku wystąpił błąd.

 Okno [Etapy potoku](graphics-pipeline-stages.md) wizualizuje wynik każdego etapu niezależnie, dzięki czemu można łatwiej określić, na którym etapie najpierw pojawia się problem z renderowaniem. Po oknie Etapy potoku możesz rozpocząć debugowanie jego cieniowania.

### <a name="graphics-state"></a>Stan grafiki
 Operacje renderowania zależą od wielu stanu, który jest zwykle rozłożony na wiele obiektów. Wiele rodzajów problemów z renderowaniem jest spowodowanych błędnie skonfigurowanym stanem.

 Okno [Stan](graphics-state.md) zbiera informacje o stanie związane z każdym wywołaniem rysowania w jednym miejscu, aby było łatwiejsze do znalezienia, a także wyróżnia zmiany stanu, które wystąpiły od poprzedniego wywołania rysowania.

### <a name="pixel-history"></a>Historia pikseli
 W złożonych scenach nierzadko piksel może być zacieniony wielokrotnie w jednej ramce. Czasami wcześniejszy kolor jest po prostu zastępowany, ale innym razem kolory są łączone w celu uzyskania efektów, takich jak przezroczystość. Gdy wynik połączenia ich ze sobą nie ma odpowiedniego wyglądu, nie można łatwo stwierdzić, czy jest to spowodowane tym, że jeden z kolorów był nieprawidłowy, czy wystąpił problem ze sposobem ich połączenia. Czasami może wydawać się, że brakuje obiektu, ponieważ jego udział w pikselu został z jakiegoś powodu odrzucony.

 Okno [Historia pikseli](graphics-pixel-history.md) wizualizuje pełną historię cieniowania każdego piksela w ramce, w tym odrzucony wkład. W przypadku wkładu, który nie został odrzucony, wyświetlane są nieprzetworzone wyniki cieniowania oraz sposób, w jaki każdy nowy kolor został połączony z poprzednim. Dzięki tym informacjom znacznie łatwiej jest zlokalizować źródło błędów w pikselach, które zawierają wyniki cieniowania, lub gdy brakuje renderowanego obiektu, ponieważ jego udział w pikselu został niepoprawnie odrzucony.

### <a name="event-call-stack"></a>Stos wywołań zdarzeń
 Kod cieniowania nie jest jedynym źródłem problemów z renderowaniem w aplikacji Direct3D, czasami kod źródłowy aplikacji przekazuje nieprawidłowy parametr lub nie konfiguruje funkcji Direct3D w odpowiedni sposób. Jednym z rodzajów błędów, który może pomóc w odnalezieniu wcześniej omówionej funkcji, jest brak renderowanego obiektu, ponieważ wszystkie jego piksele zostały odrzucone. Ten rodzaj błędu zwykle występuje, gdy nieprawidłowo skonfigurowano ustawienie, takie jak to, które kontroluje sposób wykonania testu głębokości, i zwykle błąd można znaleźć gdzieś w stosie wywołań wywołania draw brakującego obiektu.

 Okno [Stos wywołań zdarzeń](graphics-event-call-stack.md) wyświetla pełny stos wywołań każdego zdarzenia graficznego na liście zdarzeń, a nawet umożliwia przejście do kodu źródłowego aplikacji, jeśli są dostępne informacje debugowania. Jest to zaawansowane narzędzie do pominiania błędu z miejsca, w którym po raz pierwszy pojawia się na procesorze GPU, do miejsca, z którego pochodzi kod źródłowy aplikacji.

### <a name="object-table"></a>Tabela obiektów
 Każda ramka renderowana przez aplikację jest prawdopodobnie zapasowa przez setki, a nawet tysiące obiektów zasobów. Mogą one obejmować bufory wstecz i obiekty docelowe renderowania, tekstury, bufory wierzchołków, bufory indeksów, bufory ogólne — prawie wszystko, co direct3D pamięta, jest obiektem.

 Tabela [obiektów wyświetla](graphics-object-table.md) wszystkie obiekty, które istnieją w momencie zdarzenia grafiki wybranego na liście zdarzeń. Ponieważ większość obiektów w typowej aplikacji to tekstury, lista zdarzeń jest zoptymalizowana pod kątem szybkich szczegółów dotyczących obrazów. Kolumna Typ zawiera informacje o rodzaju obiektu w każdym wierszu, a kolumna Format dodatkowo pokazuje podtyp lub wersję obiektu. Wyświetlane są również inne szczegóły. Niektóre obiekty mają również hiperlinki, które można śledzić, aby wyświetlić obiekt za pomocą bardziej wyspecjalizowanej przeglądarki, takiej jak tekstury (można wyświetlić teksturę jako obraz) lub bufory (można wybrać sposób analizowania i wyświetlania nieprzetworzonych bajtów buforu przez zdefiniowanie formatu buforu).

### <a name="frame-analysis"></a>Analiza ramek
 Grafiki aplikacji nie muszą być po prostu poprawne — muszą być również szybkie. Nawet w przypadku mniej wydajnych urządzeń, takich jak laptopy ze zintegrowaną grafiką lub telefonami komórkowymi. Nadal muszą również wyglądać świetnie.

 Narzędzie [do analizy ramek](graphics-frame-analysis.md) bada potencjalne optymalizacje wydajności, automatycznie zmieniając sposób, w jaki aplikacja korzysta z direct3D, i udostępniając wyniki testów porównawczych do porównania. Na przykład analiza ramek może włączyć mapowanie mip dla każdej tekstury, co może ujawnić tekstury, które mogą skorzystać z mapowania mip, ale nie mają go obecnie włączone. Na sprzęcie, który go obsługuje, analiza ramek przedstawia również informacje zebrane z liczników wydajności procesora GPU — ten poziom informacji może identyfikować problemy z wydajnością na poziomie sprzętu, takie jak duża liczba zatrzymań pobierania tekstury lub chybienia pamięci podręcznej.

 Jednak analiza ramek to nie tylko szybkie działanie — jest to uzyskanie jak najwyższej wydajności przy jednoczesnym rezygnacji z najmniejszej jakości wizualizacji. Czasami kosztowny efekt, który wygląda świetnie na dużym ekranie, nie ma tego samego wpływu w przypadku wyświetlania na małym ekranie telefonu, gdzie prostszy efekt może wyglądać równie dobrze bez opróżniania baterii. Automatyczne zmiany i testy porównawcze zapewniane przez analizę grafiki mogą ułatwić znalezienie równowagi odpowiedniej dla aplikacji na wielu urządzeniach.

## <a name="see-also"></a>Zobacz też
- [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)
- [Debuger HLSL](hlsl-shader-debugger.md)
