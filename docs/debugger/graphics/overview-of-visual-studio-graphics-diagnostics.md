---
title: Omówienie diagnostyki grafiki | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b15e45d464c78aa24fa6fed7292b3eb7140835
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831381"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Omówienie diagnostyki grafiki w programie Visual Studio
Program Visual Studio *Graphics Diagnostics* to zestaw narzędzi do rejestrowania i następnie analizowania problemów renderowania i wydajności w aplikacjach Direct3D. Diagnostyka grafiki może służyć w aplikacjach, które działają lokalnie na komputerze z systemem Windows lub na zdalnym komputerze lub urządzeniu.  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Używanie Graphics Diagnostics do debugowania problemów z renderowaniem  
 Debugowanie problemów z renderowaniem w aplikacji rozbudowanej graficznie nie jest tak proste, jak uruchomienie debugera i krokowe wykonywanie kodu. W każdej klatce są produkowane setki tysięcy unikatowych pikseli, każdy na podstawie złożonego zestawu stanu, danych, parametrów i kodu — możliwe, że tylko kilka z powyższych pikseli pokaże problem, który próbujesz zdiagnozować. Aby jeszcze bardziej skomplikować sprawy, kod, który generuje każdy piksel, jest wykonywany na wyspecjalizowanym sprzęcie, który przetwarza setki pikseli równolegle. Tradycyjne narzędzia i techniki debugowania, z których trudno się korzysta nawet w kodzie mało skomplikowanym pod względem wątków, są nieskuteczne w obliczu tak dużej ilości danych.  
  
 Narzędzia Graphics Diagnostics w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mają na celu pomóc Ci znaleźć problemy z renderowaniem, rozpoczynając od artefaktów wizualizacji, które wskazują problem, a następnie Śledzenie wstecz do źródła problemu, koncentrując się tylko na odnośnym kodzie cieniowania, potoku etapy, rysowania wywołań, zasobów i stan urządzenia — w kodzie źródłowym własnych aplikacji.  
  
## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX  
 Graphics Diagnostics obsługuje aplikacje korzystające z programu Direct3D 10 lub nowszy i udostępnia ograniczoną obsługę aplikacji, które używają Direct2D. Nie obsługuje aplikacji, które używają starszych wersji Direct3D, DirectDraw lub innych graficznych interfejsów API.  
  
### <a name="windows-10-and-direct3d-12"></a>System Windows 10 i Direct3D 12  
 Wprowadzona w systemie Windows 10 *Direct3D 12*, która różni się znacznie od Direct3D 10 i Direct3D 11. Te różnice przywrócić DirectX wyrównanie sprzętu grafiki nowoczesnych i unleashing swój pełny potencjał, ale również przenieść duże zmiany interfejsu API i umieścić większą odpowiedzialność na programisty należy zarządzać okresy istnienia zasobu i rywalizacji o zasoby. Mimo różnic narzędzie Diagnostyka grafiki przy użyciu Direct3D 12 zachowuje równoważności funkcji diagnostyki grafiki przy użyciu Direct3D 11.2.
  
 Windows 10 udostępnia również obsługę dla starszych wersji Direct3D, gry i aplikacje, które zależą od nich. Diagnostyka grafiki w programie Visual Studio w dalszym ciągu obsługuje Direct3D 10 i Direct3D 11 w systemie Windows 10.
  
### <a name="limited-direct2d-support"></a>Ograniczona obsługa Direct2D  
 Ponieważ Direct2D to API trybu użytkownika, który jest zbudowany na bazie Direct3D, można użyć diagnostyki grafiki do debugowania problemów z renderowaniem w aplikacjach, które używają Direct2D. Jednak ponieważ rejestrowane są tylko podstawowe zdarzenia Direct3D, a nie zdarzenia Direct2D wyższego poziomu, zdarzenia Direct2D nie pojawią się na liście zdarzeń grafiki. Ponadto, ponieważ relacja między zdarzeniami Direct2D i wynikowymi zdarzeniami Direct3D nie jest zawsze jasna, używanie Graphics Diagnostics do debugowania problemów z renderowaniem w aplikacjach, które używają Direct2D, nie jest proste. Nadal można korzystać z Graphics Diagnostics, aby uzyskać informacje dotyczące problemów renderowania niskiego poziomu w aplikacjach, które korzystają z Direct2D.  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Funkcje diagnostyki grafiki w programie Visual Studio  
 Diagnostyka grafiki ma dedykowanego interfejsu — okno analizator grafiki — do diagnozowania problemów z renderowaniem, ale dodaje także niektóre narzędzia do interfejsu programu Visual Studio.  
  
### <a name="the-graphics-toolbar-visual-studio"></a>Pasek narzędzi grafika (Visual Studio)  
 Pasek narzędzi grafika zapewnia szybki dostęp do poleceń Graphics Diagnostics.  
  
 **Rozpocznij diagnostykę** przycisk uruchamia aplikację pod nadzorem diagnostyki grafiki. Gdy aplikacja jest uruchomiona w ramach diagnostyki grafiki **Przechwyć następną renderowaną ramkę** przycisk jest aktywny.  
  
### <a name="diagnostics-capture-interface"></a>Narzędzia diagnostyczne przechwycić interfejsu  
 Podczas uruchamiania aplikacji w obszarze Diagnostyka grafiki programu Visual Studio wyświetla interfejs sesji diagnostyki, można użyć, aby przechwycić ramki, i również powoduje wyświetlenie bieżącego obciążenia procesora CPU i procesora GPU. Obciążenie procesora CPU i procesora GPU jest wyświetlany, aby pomóc w zidentyfikowaniu klatek, które można przechwycić z powodu ich charakterystyk wydajności, a nie błędy renderowania.  
  
 To nie jest jedynym sposobem, aby przechwycić ramki, mimo że. Istnieje również możliwość przechwytywania z ramki za pomocą interfejsu Przechwytywanie programistyczne lub przy użyciu programu wiersza polecenia do przechwytywania dxcap.exe.  
  
 Zobacz [Capturing Graphics Information](capturing-graphics-information.md) Aby uzyskać więcej informacji.  
  
### <a name="gpu-usage"></a>Użycie procesora GPU  
 Diagnostyka grafiki również profilować wydajności aplikacji Direct3D. Ponieważ dane profilowania będą pochylony przez rejestrowanie szczegółów zdarzenia grafiki, to różni się od przechwytywanie ramek, które ma być używany z analizatora grafiki.  
  
 Zobacz [użycie procesora GPU](/visualstudio/profiling/gpu-usage) Aby uzyskać więcej informacji.  
  
### <a name="directx-control-panel"></a>Panel sterowania DirectX  
 Panel sterowania DirectX to składnik DirectX, którego można użyć, aby zmienić sposób zachowania DirectX — na przykład włączyć wersję składników wykonawczych DirectX przeznaczoną do debugowania, wybrać rodzaj komunikatów debugowania, które są raportowane, oraz uniemożliwić korzystanie z niektórych funkcji sprzętowych karty graficznej w celu emulacji mniej zaawansowanego sprzętu. Ten poziom kontroli nad DirectX może pomóc w debugowaniu i testowaniu aplikacji DirectX. Dostęp do panelu sterowania DirectX można uzyskać z Visual Studio.  
  
#### <a name="to-open-the-directx-control-panel"></a>Aby otworzyć panel sterowania DirectX  
  
-   Na pasku menu wybierz **debugowania**, **grafiki**, **Panel sterowania DirectX**.  
  
## <a name="graphics-analyzer"></a>Analizator grafiki  
 Analizator grafiki programu Visual Studio jest dedykowany interfejs do badania problemów renderowania i wydajności w ramkach, który został już przechwycony. Wewnątrz analizatora grafiki znajdziesz kilka narzędzi, które pomagają poznać i zrozumieć sposób renderowania w aplikacji. Każde narzędzie udostępnia inny rodzaj informacji o ramce, która jest poddawana i narzędzia są przeznaczone do użytku z optymalizacją intuicyjnie zawęzić-w w źródle problem z renderowaniem, rozpoczynając od jego wyglądem w bufor ramki.  
  
 Ta ilustracja przedstawia typowy układ narzędzia w analizatorze grafiki.  
  
 ![Wszystkie grafiki okna debugera](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>Pasek narzędzi grafika (analizator grafiki programu)  
 Pasek narzędzi grafika zapewnia szybki dostęp do okna narzędzi analizatora grafiki.  
  
 ![Pasek narzędzi grafika w trybie diagnostyki grafiki](media/vsg_toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>Dokument dziennika grafiki  
 Wewnątrz analizatora grafiki dokument dziennika grafiki jest najbardziej znaczącym okna narzędzi. W tym oknie reprezentuje wszystkie ramek, które są przechwytywane, uruchamiając aplikację pod nadzorem diagnostyki grafiki. W tym miejscu można wybrać innej ramki, aby sprawdzić, lub wybierz określone piksel, który chcesz zbadać za pomocą narzędzia historii pikseli. Bufor ramki obraz, który wyświetlane w tej zmiany dokumentu, aby uwzględnić aktualnie wybranego zdarzenia, dzięki czemu możesz zobaczyć wpływ bufor ramki wraz z upływem czasu.  
  
 [Dokument dziennika grafiki](graphics-log-document.md) jest również punkt wejścia do narzędzia analizy klatek, które pomoże Ci zrozumieć wydajność ramki zmianę sposobu, w niektórych aspektów renderowania są skonfigurowane i podając wyniki testów porównawczych, aby Porównaj z oryginałem.  
  
### <a name="event-list"></a>Lista zdarzeń  
 Zdarzenia grafiki oznaczyć każdego wywołania interfejsu API Direct3D i zdarzenie zdefiniowane przez użytkownika.  
  
 [Listy zdarzeń](graphics-event-list.md) pokazuje wszystkie zdarzenia grafiki, które zostały zarejestrowane horyzoncie one badanie. Aby ułatwić znajdowanie, co jest ważne, lista zdarzeń mogą być wyświetlane hierarchicznie — z ostatnich zmian stanu poniżej kolejne wywołania rysowania — lub w postaci osi czasu. Ponadto zdarzenia są oznaczone kolorami w oparciu o kolejki, do których należą, oraz można filtrować listę obejmujący tylko zdarzenia, które interesują Cię.  
  
 Po wybraniu zdarzenia na liście pozostałymi narzędziami analizy grafiki odzwierciedlają stan ramki w czasie tego zdarzenia. W ten sposób można zobaczyć efekt dowolnego zdarzenia w procesorze GPU. Na przykład widać skutkiem natychmiastowym wszelkie rysowania wywołać dla obiektu, nawet wtedy, gdy staje się zasłonięte wywołania rysowania kolejnej. Niektóre zdarzenia mają również hiperłącza, które można wykonać, aby zobaczyć więcej szczegółów na temat jego parametrów lub obiektów powiązanych zasobów.  
  
### <a name="pipeline-stages"></a>Etapy potoku  
 Każde wywołanie rysowania w swojej aplikacji przechodzi przez potok grafiki, dostarczone przez Direct3D. Na każdym etapie w potoku dane wyjściowe z poprzedniego etapu jest przekształcane przez mały program o nazwie cieniowania i następnie przekazywane do kolejnego etapu, dopóki na koniec jest renderowany na ekranie. Wiele błędów renderowania wystąpić na granicy między etapy potoku, gdy format wyjściowy jest inny niż oczekiwany kolejnego etapu lub dowolnego jednego etapu po prostu tworzy niepoprawnych wyników. Zazwyczaj można tylko otrzymać ostateczne wyniki wyświetlany na ekranie i nie można łatwo sprawdzić, gdzie w potoku wystąpił błąd.  
  
 [Etapy potoku](graphics-pipeline-stages.md) okna wizualizuje wynik każdego etapu niezależnie, dzięki czemu można łatwiej określić etap z problemem renderowania po raz pierwszy występuje w. Po określeniu, to znaczy etap, możesz uruchomić debugowanie cieniowania, jego bezpośrednio w oknie etapy potoku.  
  
### <a name="graphics-state"></a>Stan grafiki  
 Operacje renderowania zależą od mnóstwo stanu, które są rozmieszczone na wielu obiektów. Wiele rodzajów problemów z renderowaniem są spowodowane przez nieprawidłowo stanu.  
  
 [Stanu](graphics-state.md) okno służy do zbierania informacji o stanie odpowiednie do każdego wywołania rysowania razem w jednym miejscu, aby łatwiej znaleźć, a także najważniejsze zmiany stanu które miały miejsce od poprzedniego wywołania rysowania.  
  
### <a name="pixel-history"></a>Historia pikseli  
 W złożonych scen nie jest niczym niezwykłym pikseli być cieniowanie wielokrotnie w jednej ramce. Czasami wcześniej kolorów jest czas po prostu zastąpione, ale inne kolory są łączone ze sobą, aby uzyskać efekty, takie jak przezroczystości. Jeśli wynik łącząc je ze sobą nie ma prawo wygląd nie może łatwo sprawdzić, czy ma ponieważ jeden z kolorów jest niepoprawne lub jeśli występuje problem ze sposobem zostały połączone. W innych sytuacjach obiektu może pojawić się nieobecnego, ponieważ jej udziału piksel został odrzucony przyczyny.  
  
 [Historii pikseli](graphics-pixel-history.md) okna wizualizuje historii pełną programu do cieniowania każdego piksela ramki, w tym wkładów odrzucone. Wkładów, które nie zostały odrzucone wyświetla wyniki pierwotne programu do cieniowania i jak każdy nowy kolor zostało połączone z poprzedniego. Dzięki tym informacjom jest znacznie łatwiejsze do zlokalizowania źródłem błędów w pikselach, który blend wyników programu do cieniowania lub po renderowanych obiektu brakuje ponieważ wkładzie piksel niepoprawnie został odrzucony.  
  
### <a name="event-call-stack"></a>Stos wywołań zdarzeń  
 Kod programu do cieniowania nie tylko źródło problemów z renderowaniem w aplikacji Direct3D, czasami kod źródłowy aplikacji przekazuje parametr nieprawidłowy lub nie powoduje skonfigurowania Direct3D całkowicie poprawny. Jeden rodzaj błędu, który pomoże Ci znaleźć funkcję już wspomniano, Historia pikseli jest, gdy renderowanych brakuje obiektu, ponieważ wszystkie jej piksele zostały odrzucone. Tego rodzaju błąd się dzieje zazwyczaj, gdy użytkownik błędnie skonfigurowane ustawienia, takie jak taki, który określa sposób test głębi i zazwyczaj można znaleźć błąd w jakimś miejscu w stosie wywołań brakuje obiektu wywołania rysowania.  
  
 [Stos wywołań zdarzenia](graphics-event-call-stack.md) okno wyświetla pełny stos wywołań dla każdego zdarzenia grafiki na liście zdarzeń, a nawet pozwala przejść do swojej aplikacji kod źródłowy, jeśli informacje o debugowaniu są dostępne. Jest to zaawansowane narzędzie do po błąd, z którym najpierw wydaje się, w procesorze GPU, do którego pochodzi w kodzie źródłowym aplikacji.  
  
### <a name="object-table"></a>Tabela obiektów  
 Każdej klatce, Twoja aplikacja renderuje prawdopodobnie jest wspierana przez setki lub nawet tysiące obiektów zasobów. Te obejmują buforów Wstecz i renderowanie elementów docelowych, tekstury, bufory wierzchołków, buforów indeksu, ogólne buforów — prawie wszystko, co pamięta Direct3D jest obiektem.  
  
 [Tabeli obiektów](graphics-object-table.md) Wyświetla wszystkie obiekty istniejące w czasie zdarzenia grafiki, wybrane listy zdarzeń. Ponieważ większość obiektów w typowej aplikacji tekstury, lista zdarzeń jest zoptymalizowany do Pokaż szczegóły dotyczą obrazów na pierwszy rzut oka. Kolumna typu pozwalają określić rodzaj obiektu w każdym wierszu, a dodatkowo kolumna formatu zawiera podtyp lub wersji obiektu. Inne szczegóły są także wyświetlane. Niektóre obiekty mają również hiperłącza, które można wykonać w celu wyświetlania obiektu przy użyciu bardziej wyspecjalizowane przeglądarki, takich jak tekstury (można wyświetlić tekstury w formie obrazu) lub buforów (możesz wybrać sposób Podgląd buforu analizuje i wyświetla bajtów surowy bufor, definiując buforu Format).  
  
### <a name="frame-analysis"></a>Analiza klatek  
 Grafiki aplikacji nie musi mieć po prostu poprawne — muszą być zbyt szybko. Nawet w przypadku mniejszej mocy urządzeń, takich jak komputery przenośne przy użyciu zintegrowanego grafiki lub telefony komórkowe. I nadal potrzebują zbyt wygląda świetnie.  
  
 [Analizy klatek](graphics-frame-analysis.md) narzędzie analizuje potencjalnych optymalizacji wydajności, automatycznie zmienia sposób aplikacja używa technologii Direct3D i zapewniając wyniki testu dla porównania. Na przykład funkcja analizy klatek można włączyć mip mapowania na każdy tekstury, którego może ujawnić tekstury, które mogą odnieść korzyści z mapowania mip, ale obecnie go nie masz włączony. Na sprzęcie, który ją obsługuje, analiza klatek przedstawia również informacje zebrane z liczników wydajności procesora GPU — poziom informacji może zidentyfikować problemy wydajności na poziomie sprzętu, takich jak dużej liczby wstrzymania pobierania tekstury lub liczba chybień pamięci podręcznej.  
  
 Ale analiza klatek nie jest niemal przechodząc fast — o uzyskiwaniu większość wydajności, podczas gdy rezygnacji z najmniejszą ilością jakość wizualną. Czasami efektu kosztowne, która wygląda doskonale na dużym nie czyni to ten sam wpływ, patrząc na małym ekranie telefon, gdy efekt prostsze może wyglądać tak dobrze bez opróżniania baterii. Automatyczne zmiany i wzorce, które udostępnia analizy grafiki może pomóc w znalezieniu proporcję, która jest odpowiednia dla twojej aplikacji na różnych urządzeniach.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)   
 [Debuger HLSL](hlsl-shader-debugger.md)