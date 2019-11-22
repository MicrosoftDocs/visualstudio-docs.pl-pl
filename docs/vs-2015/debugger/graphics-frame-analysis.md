---
title: analiza klatek grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
ms.assetid: 336c48ba-a1c4-4db9-b2a4-3de4a129cdd6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 331722df4749ca59241259e13c3b387d8303b69f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300508"
---
# <a name="graphics-frame-analysis"></a>Analiza ramek grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj analiza klatek grafiki w analizator grafiki programu Visual Studio, aby przeanalizować i zoptymalizować wydajność renderowania gry lub aplikacji Direct3D.  
  
> [!IMPORTANT]
> Analizator grafiki obsługuje analizę klatek dla aplikacji korzystających z programu Direct3D 11 na obsługiwanych platformach, w tym w systemie Windows 10. Analiza klatek nie jest obecnie obsługiwana w przypadku aplikacji korzystających z programu Direct3D 12.  
  
## <a name="frame-analysis"></a>Analiza klatek  
 Analiza klatek używa tych samych informacji, które są przechwytywane w pliku dziennika grafiki do celów diagnostycznych, ale używa ich do podsumowywania wydajności renderowania. Informacje o wydajności nie są rejestrowane w dzienniku podczas przechwytywania; Zamiast tego informacje o wydajności są generowane później, podczas analizy klatek przez zdarzenia chronometrażu i zbieranie danych statystycznych w miarę odtwarzania ramki. Takie podejście ma kilka korzyści w porównaniu z rejestrowaniem informacji o wydajności podczas przechwytywania:  
  
- Analiza klatek może obliczyć średnią wyniki z wielu oddziałań tej samej ramki, aby upewnić się, że podsumowanie wydajności jest statystycznym dźwiękiem.  
  
- Analiza klatek może generować informacje o wydajności dla konfiguracji sprzętu i urządzeń innych niż te, w których przechwycono informacje.  
  
- Analiza klatek może generować nowe podsumowania wydajności z wcześniej przechwyconych informacji — na przykład gdy sterowniki procesora GPU są zoptymalizowane lub uwidaczniają dodatkowe funkcje debugowania.  
  
  Oprócz tych zalet analiza klatek może również wprowadzać zmiany w sposobie renderowania ramki podczas odtwarzania, aby można było przedstawić informacje o tym, jak te zmiany mogą mieć wpływ na wydajność renderowania aplikacji. Korzystając z tych informacji, można podjąć decyzje dotyczące potencjalnych strategii optymalizacji bez konieczności ich wdrażania, a następnie przechwycić i porównać wszystkie wyniki.  
  
  Chociaż analiza klatek jest przeznaczona głównie do zapewnienia szybszego renderowania wydajności, może być równie pomocna w osiągnięciu lepszej jakości wizualnej dla danego celu wydajności lub zmniejszenia zużycia mocy procesora GPU.  
  
  Aby zapoznać się z pokazem analizy klatek dla aplikacji, możesz obejrzeć film wideo z [programu Visual Studio analiza klatek grafiki](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) w witrynie Channel 9.  
  
## <a name="using-frame-analysis"></a>Korzystanie z analizy klatek  
 Przed rozpoczęciem korzystania z analizy klatek należy przechwycić informacje graficzne z aplikacji podczas jej działania tak samo jak w przypadku korzystania z innych narzędzi analizatora grafiki. Następnie w oknie dokumentu dziennika grafiki (. vsglog) wybierz kartę **Analiza klatek** .  
  
 ![Wybierz kartę Analiza klatek.](../debugger/media/pix-frame-analysis-select-tab.png "pix_frame_analysis_select_tab")  
  
 Po zakończeniu analizy wyniki są wyświetlane. W górnej części karty analiza klatek zostanie wyświetlona oś czasu i tabela podsumowania. Dolna część wyświetla tabele szczegóły. Jeśli błędy lub ostrzeżenia zostały wygenerowane podczas odtwarzania, są one podsumowywane powyżej osi czasu; z tego miejsca możesz skorzystać z linków, aby dowiedzieć się więcej o błędach i ostrzeżeniach.  
  
### <a name="interpreting-results"></a>Interpretowanie wyników  
 Interpretując wyniki poszczególnych wariantów, można wywnioskować przydatne informacje o wydajności i zachowaniu aplikacji. Aby uzyskać więcej informacji na temat renderowania wariantów, zobacz [warianty](#Variants) w dalszej części tego artykułu.  
  
 Niektóre wyniki bezpośrednio wskazują, w jaki sposób wariant ma wpływ na wydajność renderowania:  
  
- Jeśli wariant filtru tekstury wieloliniowej wykazał zyski z wydajności, użycie funkcji filtrowania tekstury liniowej w aplikacji będzie zawierać podobne zyski wydajności.  
  
- Jeśli wariant okienka ekranu 1x1 wykazał zyski wydajności, zmniejszenie rozmiaru elementów docelowych renderowania w aplikacji poprawi jego wydajność renderowania.  
  
- Jeśli wariant kompresji tekstury BC wykazał zyski z wydajności, a następnie użycie kompresji tekstury BC w aplikacji będzie zawierać podobne zyski wydajności.  
  
- Jeśli wariant 2xMSAA ma prawie taką samą wydajność jak wariant 0xMSAA, możesz włączyć 2xMSAA w aplikacji, aby zwiększyć jakość renderowania bez kosztu wydajności.  
  
  Inne wyniki mogą sugerować dokładniejsze i bardziej subtelne konsekwencje dla wydajności aplikacji:  
  
- Jeśli odmiana wziernika 1x1 zawiera bardzo duże zyski wydajności, aplikacja prawdopodobnie zużywa więcej Fillrate niż jest dostępna. Jeśli ten wariant nie zawiera żadnych korzyści z wydajności, aplikacja prawdopodobnie przetwarza zbyt wiele wierzchołków.  
  
- Jeśli wariant formatu docelowego renderowania 16bpp pokazuje znaczący wzrost wydajności, prawdopodobnie zużywa zbyt dużo przepustowości pamięci.  
  
- Jeśli wariant wymiarów tekstury połówkowej/kwartału pokazuje znaczący wzrost wydajności, tekstury prawdopodobnie zajmują zbyt dużo pamięci, zużywają zbyt dużo przepustowości lub niewydajne użycie pamięci podręcznej tekstury. Jeśli ten wariant nie wskazuje zmiany wydajności, prawdopodobnie możesz użyć większych, bardziej szczegółowych tekstur bez ponoszenia kosztów wydajności.  
  
  Gdy liczniki sprzętu są dostępne, można je wykorzystać do zebrania bardzo szczegółowych informacji o tym, dlaczego wydajność renderowania aplikacji może mieć wpływ. Wszystkie urządzenia o 9,2 i wyższych poziomach obsługują szczegółowe zapytania zamknięcia (**zamknięte licznik pikseli** ) i sygnatury czasowe. Inne liczniki sprzętu mogą być dostępne w zależności od tego, czy producent procesora GPU zaimplementował liczniki sprzętowe i uwidacznia je w jego sterowniku. Za pomocą tych liczników można potwierdzić dokładną przyczynę wyników przedstawionych w tabeli podsumowującej — na przykład można określić, czy przeciągnięcie jest czynnikiem, sprawdzając procent pikseli, które były zamknięte przez test głębokości.  
  
### <a name="timeline-and-summary-table"></a>Oś czasu i tabela podsumowania  
 Domyślnie zostanie wyświetlona oś czasu i tabela podsumowania, a pozostałe sekcje są zwinięte.  
  
#### <a name="timeline"></a>Oś czasu  
 Oś czasu zawiera przegląd chronometrażu rysowania połączeń względem siebie. Ponieważ większe słupki odnoszą się do dłuższego czasu rysowania, można użyć jej do szybkiego zlokalizowania najbardziej kosztownych wywołań rysowania w ramce. Gdy przechwycone ramki zawiera bardzo dużą liczbę wywołań rysowania, wielokrotne wywołania rysowania są łączone na jeden pasek, którego długość jest sumą tych wywołań rysowania.  
  
 ![Oś czasu pokazuje koszty&#45;połączeń.](../debugger/media/pix-frame-analysis-timeline.png "pix_frame_analysis_timeline")  
  
 Możesz obsłużyć wskaźnik na pasku, aby zobaczyć, które zdarzenie rysowania, do którego odnosi się pasek. Wybranie paska powoduje synchronizację listy zdarzeń z tym zdarzeniem.  
  
#### <a name="table"></a>Tabela  
 Tabela liczb poniżej osi czasu pokazuje względną wydajność poszczególnych wariantów renderowania dla każdego wywołania rysowania w odniesieniu do domyślnego renderowania aplikacji. Każda kolumna wyświetla różne warianty renderowania i każdy wiersz reprezentuje inne wywołanie rysowania, które jest identyfikowane w kolumnie z lewej strony. w tym miejscu możesz użyć linku do zdarzenia w oknie Lista zdarzeń grafiki.  
  
 ![W tabeli podsumowującej są wyświetlane różne varients.](../debugger/media/pix-frame-analysis-summary.png "pix_frame_analysis_summary")  
  
 Druga lewa kolumna w tabeli podsumowującej zawiera czas renderowania linii bazowej aplikacji, czyli czas potrzebny na przeprowadzenie wywołania przez domyślne renderowanie przez aplikację. Pozostałe kolumny przedstawiają względną wydajność poszczególnych wariantów renderowania jako procent linii bazowej, dzięki czemu łatwiej jest sprawdzić, czy wydajność jest ulepszona. Wartości procentowe większe niż 100 procent trwały dłużej niż wartość bazowa — to znaczy, że wydajność spadła — a wartości procentowe mniejsze niż 100 procent trwały krócej — wydajność spadła.  
  
 Wartości zarówno bezwzględny czas odniesienia, jak i względny czas dla wariantów renderowania są rzeczywistą średnią orednią wielu przebiegów — domyślnie 5. Ta uśrednianie pomaga zagwarantować, że dane chronometrażu są niezawodne i spójne. Możesz obsłużyć wskaźnik dla każdej komórki w tabeli, aby przeanalizować wartości minimalne, maksymalne, średnie i średniego czasu, które zostały zaobserwowane podczas generowania wyników dla tego wywołania rysowania i wariantu renderowania. Zostanie również wyświetlony chronometraż punktu odniesienia.  
  
#### <a name="hot-draw-calls"></a>Wywołania rysowania "gorąca"  
 Aby zwrócić uwagę na łączenie wywołań, które zużywają większą część całkowitego czasu renderowania lub które mogą być nietypowo powolne z przyczyn, które można uniknąć, wiersz zawierający te wywołania rysowania "gorąca" ma kolor czerwony, gdy jego własny chronometraż jest większy niż jeden odchylenie standardowe dłużej niż średni czas trwania wszystkich wywołań rysowania w ramce.  
  
 ![To wywołanie DrawIndexed ma gorącą i zimną varients.](../debugger/media/pix-frame-analysis-hot-calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Znaczenie statystyczne  
 Aby zwrócić uwagę na renderowanie wariacji o najwyższej istotności, analiza klatek określa statystyczne znaczenie poszczególnych wariantów renderowania i wyświetla znaczące wartości jako pogrubione. Są w nim wyświetlane te, które zwiększają wydajność w kolorze zielonym i zmniejszają wydajność na czerwono. Wyświetla wyniki, które nie są statystycznie znaczące jako typ normalny.  
  
 ![Statystyczne znaczenie wariantu wywołania rysowania](../debugger/media/pix-frame-analysis-summary-stats.png "pix_frame_analysis_summary_stats")  
  
 Aby określić znaczenie statystyczne, analiza klatek używa [testu t-Studenta](https://en.wikipedia.org/wiki/Student's_t-test).  
  
### <a name="details-table"></a>Tabela szczegółów  
 Poniżej tabeli podsumowania jest tabela szczegółów, która jest domyślnie zwinięta. Zawartość tabeli szczegółów zależy od platformy sprzętowej maszyny odtwarzania. Aby uzyskać informacje o obsługiwanych platformach sprzętowych, zobacz temat [Obsługa sprzętu](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Platformy, które nie obsługują liczników sprzętu  
 Większość platform nie obsługuje w pełni sprzętowych liczników procesora GPU — obejmują wszystkie procesory GPU aktualnie oferowane przez firmę Intel, AMD i nVidia. Jeśli nie ma żadnych liczników sprzętowych do zebrania, zostanie wyświetlona tylko jedna tabela szczegółów i zawiera ona średni czas bezwzględny wszystkich wariantów.  
  
 ![Tabela szczegółów i varients odtwarzania.](../debugger/media/pix-frame-analysis-details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Platformy obsługujące liczniki sprzętu  
 W przypadku platform obsługujących liczniki procesora GPU sprzętu — na przykład nVidia T40 SOC i wszystkie Qualcomm SOC — wyświetlane są kilka tabel szczegółów, jeden dla każdego wariantu. Każdy dostępny licznik sprzętu jest zbierany dla każdego wariantu renderowania i wyświetlany w jego własnej tabeli szczegółów.  
  
 ![Liczniki sprzętu są wyświetlane, jeśli są obsługiwane.](../debugger/media/pix-frame.png "pix_frame")  
  
 Informacje o liczniku sprzętu udostępniają bardzo szczegółowy widok określonych zachowań dla platformy dla każdego wywołania rysowania, które mogą ułatwić identyfikację przyczyny wąskich gardeł wydajności.  
  
> [!NOTE]
> Różne platformy sprzętowe obsługują różne liczniki; nie istnieje standardowy. Liczniki i ich znaczenie są określane wyłącznie przez każdego producenta procesora GPU.  
  
### <a name="marker-regions-and-events"></a>Regiony i zdarzenia znacznika  
 Analiza klatek obsługuje zdefiniowane przez użytkownika znaczniki zdarzeń i grupy zdarzeń. Są one wyświetlane w tabeli podsumowującej i w tabelach szczegółów.  
  
 Do tworzenia znaczników i grup można użyć interfejsów API ID3DUserDefinedAnnotation lub starszej rodziny D3DPERF_. W przypadku korzystania z rodziny interfejsów API D3DPERF_ można przypisać każdemu znacznikowi i zgrupować kolor, który jest wyświetlany jako kolorowy pasek w wierszach zawierających znacznik zdarzenia lub znaczniki początku/końca grupy zdarzeń i ich zawartość. Ta funkcja ułatwia szybkie identyfikowanie ważnych zdarzeń renderowania lub grup zdarzeń.  
  
### <a name="warnings-and-errors"></a>Ostrzeżenia i błędy  
 Analiza klatek sporadycznie kończy się z ostrzeżeniami lub błędami, które są podsumowywane powyżej osi czasu, i szczegółowo w dolnej części karty analiza klatek.  
  
 Zazwyczaj ostrzeżenia i błędy są przeznaczone tylko do celów informacyjnych i nie wymagają żadnej interwencji.  
  
 Ostrzeżenia zwykle wskazują na brak obsługi sprzętu, ale mogą być używane, nie można zbierać liczników sprzętu lub niektóre dane dotyczące wydajności mogą nie być niezawodne — na przykład wtedy, gdy obejście negatywnie wpłynie na ten problem.  
  
 Błędy zwykle wskazują, że implementacja analizy klatek zawiera błędy, sterownik ma błędy, Obsługa sprzętu jest niedostępna i nie można jej obejść lub aplikacja próbuje coś, co nie jest obsługiwane przez odtwarzanie.  
  
### <a name="retries"></a>Ponownych prób  
 Jeśli procesor GPU przejdzie do przejścia stanu potęgowego podczas analizy klatek, należy ponowić próbę przeprowadzenia analizy, ponieważ Clockspeed procesora GPU i w związku z tym unieważnione wyniki względnego chronometrażu.  
  
 Analiza klatek ogranicza liczbę ponownych prób do 10. Jeśli platforma ma agresywne zarządzanie zużyciem lub kontroli zegarem, może to spowodować niepowodzenie analizy klatek i zgłosić błąd, ponieważ Przekroczono limit ponownych prób. Może być możliwe uniknięcie tego problemu przez zresetowanie funkcji zarządzania zasilaczami i szybkości zegara, aby było mniej agresywne, jeśli ta platforma zostanie włączona.  
  
## <a name="HardwareSupport"></a>Obsługa sprzętu  
  
### <a name="timestamps-and-occlusion-queries"></a>Sygnatury czasowe i zapytania zamknięcia  
 Sygnatury czasowe są obsługiwane na wszystkich platformach, które obsługują analizę klatek. Głębokości zapytania zamknięcia — wymagane dla pikseli zamknięte licznik — są obsługiwane na platformach, które obsługują funkcję Level 9,2 lub wyższą.  
  
> [!NOTE]
> Mimo że sygnatury czasowe są obsługiwane na wszystkich platformach obsługujących analizę klatek, dokładność i spójność znaczników czasu różni się od platformy do platformy.  
  
### <a name="gpu-counters"></a>Liczniki procesora GPU  
 Obsługa liczników sprzętu procesora GPU jest zależna od sprzętu.  
  
 Ponieważ żaden procesor GPU nie jest obecnie oferowany przez procesor Intel, AMD lub nVidia, nie obsługuje zbyt niezawodnego liczników sprzętowych procesora GPU. Analiza klatek nie zbiera z nich liczników. Jednak analiza klatek zbiera liczniki sprzętowe z tych procesorów GPU, które w niezawodny sposób obsługują:  
  
- Qualcomm SOC (dowolna obsługa Windows Phone)  
  
- nVidia T40 (Tegra4).  
  
  Żadna inna platforma, która nie obsługuje analizy klatek, zbiera liczniki sprzętowe procesora GPU.  
  
> [!NOTE]
> Ponieważ liczniki sprzętowe procesora GPU są zasobami sprzętowymi, może to potrwać wiele przebiegów w celu zebrania kompletnego zestawu liczników sprzętu dla każdego wariantu renderowania. W związku z tym nie określono kolejności, w której zbierane są liczniki GPU.  
  
### <a name="windows-phone"></a>System Windows Phone  
 Sygnatury czasowe, zapytania zamknięcia i liczniki sprzętu procesora GPU są obsługiwane tylko w Windows Phone słuchawki, które pierwotnie zostały dostarczone z Windows Phone 8,1. Analiza klatek wymaga, aby odtworzyć plik dziennika grafiki. Windows Phone słuchawki, które zostały pierwotnie dostarczone z Windows Phone 8 nie obsługują analizy ramek, nawet w przypadku słuchawek, które zostały zaktualizowane do Windows Phone 8,1.  
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Niektóre sposoby używania analizy klatek są nieobsługiwane lub są tylko niewłaściwymi pomysłami.  
  
### <a name="warp"></a>ZNIEKSZTAŁCENI  
 Analiza klatek ma służyć do profilowania i ulepszania wydajności renderowania na rzeczywistym sprzęcie. Uruchamianie analizy klatek na urządzeniach wypaczania nie jest blokowane — Windows Phone Emulator jest uruchamiany przy wypaczeniu — ale nie jest to zwykle wartościowa, ponieważ Wypaczenie działające na wysokim poziomie procesora jest wolniejsze niż nawet najbardziej obsługujące Nowoczesne procesory GPU i ponieważ wydajność ZNIEKSZTAŁCAnia może się różnić znacznie w zależności od konkretnego procesora, na którym jest uruchomiony.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Odtwarzanie przechwytywania wysokiej klasy na urządzeniach niższego poziomu  
 W analizatorze grafiki podczas odtwarzania pliku dziennika grafiki, który korzysta z wyższego poziomu funkcji niż obsługiwana przez maszynę odtwarzania, automatycznie wraca do wypaczenia. W analizie klatek jawnie nie wraca do OSNOWy i generuje błąd — Wypaczenie jest przydatne do sprawdzania poprawności aplikacji Direct3D, ale nie do badania jej wydajności.  
  
> [!NOTE]
> Chociaż warto pamiętać o problemach na poziomie funkcji, można przechwytywać i odtwarzać pliki dzienników grafiki na różnych konfiguracjach sprzętu i urządzeniach. Na przykład można przechwycić informacje graficzne na Windows Phone i odtworzyć je na komputerze stacjonarnym, a także włączyć opcję odwrotną. W obu przypadkach dziennik grafiki może być odtwarzany, o ile plik dziennika nie zawiera interfejsów API lub nie obsługuje poziomów funkcji, które nie są obsługiwane przez maszynę odtwarzania.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 i Lower  
 Analiza klatek jest obsługiwana tylko w przypadku interfejsu API programu Direct3D 11. Jeśli aplikacja wywołuje interfejs API Direct3D 10, analiza klatek nie rozpoznaje ani nie profiluje, nawet jeśli są one rozpoznawane i używane przez inne narzędzia analizatora grafiki. Jeśli aplikacja używa zarówno Direct3D11, jak i interfejsów API programu Direct3D 10, tylko wywołania programu Direct3D 11 są profilowane.  
  
> [!NOTE]
> Dotyczy to tylko wywołań interfejsu API Direct3D, które są używane, a nie poziomów funkcji. O ile korzystasz z interfejsu API Direct3D 11, Direct3D 11,1 lub Direct3D 11,2, możesz użyć dowolnego poziomu funkcji, który chcesz, a analiza klatek będzie działać.  
  
## <a name="Variants"></a>Variant  
 Każda zmiana, którą analiza klatek wprowadza do sposobu renderowania ramki podczas odtwarzania, jest znana jako *wariant*. Warianty, które analizuje analiza klatek, odpowiadają wspólnym, stosunkowo łatwym zmianom, które można zwiększyć w celu poprawy wydajności renderowania lub jakości wizualnej aplikacji — na przykład zmniejszenie rozmiaru tekstury, użycie kompresji tekstury lub włączenie różne rodzaje wygładzania. Warianty przesłaniają zwykły kontekst renderowania i parametry aplikacji. Oto podsumowanie:  
  
|Typu|Opis|  
|-------------|-----------------|  
|**Rozmiar okienka ekranu 1x1**|Zmniejsza wymiary okienka ekranu dla wszystkich obiektów docelowych renderowania do 1x1 pikseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [1x1a rozmiaru okienka ekranu](../debugger/1x1-viewport-size-variant.md)|  
|**0x MSAA**|Wyłącza wiele próbkowania wygładzania (MSAA) na wszystkich celach renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz odmiany w liczbie [0x/2x/4X MSAA](../debugger/0x-2x-4x-msaa-variants.md)|  
|**2x MSAA**|Włącza 2. wygładzanie wielobajtowe (MSAA) na wszystkich celach renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz odmiany w liczbie [0x/2x/4X MSAA](../debugger/0x-2x-4x-msaa-variants.md)|  
|**4x MSAA**|Włącza 4x dla wielobajtowego połączenia (MSAA) dla wszystkich obiektów docelowych renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz odmiany w liczbie [0x/2x/4X MSAA](../debugger/0x-2x-4x-msaa-variants.md)|  
|**Filtrowanie tekstury punktów**|Ustawia tryb filtrowania na `DXD11_FILTER_MIN_MAG_MIP_POINT` (filtr tekstury punktów) dla wszystkich odpowiednich próbek tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [trójliniowego i różne warianty filtrowania tekstury anizotropowego](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie tekstury liniowej**|Ustawia tryb filtrowania na `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtrowanie tekstury liniowej) dla wszystkich odpowiednich próbek tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [trójliniowego i różne warianty filtrowania tekstury anizotropowego](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie tekstury trójliniowego**|Ustawia tryb filtrowania na `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtrowanie tekstury trójliniowego) dla wszystkich odpowiednich próbek tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [trójliniowego i różne warianty filtrowania tekstury anizotropowego](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie tekstury anizotropowego**|Ustawia tryb filtrowania na `DXD11_FILTER_ANISOTROPIC` i `MaxAnisotropy` do `16` (filtr "16x anizotropowego Texture Filter") dla wszystkich odpowiednich próbek tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [trójliniowego i różne warianty filtrowania tekstury anizotropowego](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Format docelowy renderowania 16bpp**|Ustawia format pikseli na `DXGI_FORMAT_B5G6R5_UNORM` (format 565) dla wszystkich obiektów docelowych renderowania i buforów.<br /><br /> Aby uzyskać więcej informacji, zobacz [16Bpp format docelowy renderowania](../debugger/16bpp-render-target-format-variant.md)|  
|**MCI — Generowanie mapy**|Włączenie MCI — odwzorowuje wszystkie tekstury, które nie są obiektami docelowymi.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant generowania mapy MIP](../debugger/mip-map-generation-variant.md).|  
|**Wymiary pół tekstury**|Zmniejsza wymiary tekstury dla wszystkich tekstur, które nie renderują obiektów docelowych do połowy rozmiaru oryginalnego w każdym wymiarze. Na przykład tekstura 256x128 jest zredukowana do 128x64 tekseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [wymiar tekstury połówkowej/kwartalnej](../debugger/half-quarter-texture-dimensions-variant.md).|  
|**Wymiary tekstury kwartału**|Zmniejsza wymiary tekstury dla wszystkich tekstur, które nie renderują obiektów docelowych do kwartału oryginalnego rozmiaru w każdym wymiarze. Na przykład tekstura 256x128 jest zredukowana do 64x32 tekseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [wymiar tekstury połówkowej/kwartalnej](../debugger/half-quarter-texture-dimensions-variant.md).|  
|**Kompresja tekstury BC**|Włącza kompresję blokową dla wszystkich tekstur, które mają wariant formatu B8G8R8X8, B8G8R8A8 lub R8G8B8A8 pikseli. Warianty formatu B8G8R8X8 są kompresowane przy użyciu BC1; Warianty formatu B8G8R8A8 i R8G8B8A8 są kompresowane przy użyciu BC3.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant tekstury kompresji BC](../debugger/bc-texture-compression-variant.md).|  
  
 Wyniki dla większości wariantów są następujące: "zmniejszenie rozmiaru tekstury o połowę jest szybsze o 25%" lub "włączenie dwuprocentowej technologii MSAA". Inne warianty mogą wymagać większej interpretacji — na przykład, jeśli wariant, który zmienia wymiary okienka ekranu na 1x1 pokazuje duży wzrost wydajności, może wskazywać, że renderowanie jest wąskie przez niską szybkość wypełniania; Alternatywnie, jeśli nie ma znaczącej zmiany wydajności, może to wskazywać, że renderowanie jest wąskie przez przetwarzanie wierzchołków.
