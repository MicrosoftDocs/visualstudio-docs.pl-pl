---
title: Analiza klatek grafiki | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b02f1035a8b149ba8cfc1152bb83d1410bd86350
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781275"
---
# <a name="graphics-frame-analysis"></a>Analiza klatek grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj analizy klatek grafiki w analizatora grafiki programu Visual Studio do analizowania i zoptymalizować wydajność renderowania Direct3D grach i aplikacjach.  
  
> [!IMPORTANT]
>  Analizator grafiki programu obsługuje analizy klatek aplikacji, które używają programu Direct3D 11 na obsługiwanych platformach, w tym Windows 10. Analiza klatek nie jest obecnie obsługiwane w przypadku aplikacji korzystających z programu Direct3D 12.  
  
## <a name="frame-analysis"></a>Analiza klatek  
 Analiza klatek używa informacje, które są przechwytywane w pliku dziennika grafiki do celów diagnostycznych, ale używa go do podsumowania wydajność renderowania w zamian. Informacje o wydajności nie jest rejestrowane w dzienniku podczas przechwytywania. Zamiast tego informacje o wydajności jest generowany później, podczas analizy klatek przez zdarzenia czasowe i zbieranie statystyk jak odtworzyć ramki. Takie podejście ma kilka zalet w stosunku do rejestrowania informacji o wydajności podczas przechwytywania:  
  
- Analiza klatek można średnie wyniki z poszczególnymi wielu odtworzeniami tego samego ramki upewnij się, że wydajność podsumowania statystycznie dźwięku.  
  
- Analiza klatek może generować informacji o wydajności, konfiguracji sprzętu i urządzeń, niż to, gdzie informacje zostały przechwycone.  
  
- Analiza klatek może generować nowe podsumowania wydajności z wcześniej przechwycone informacje — na przykład, gdy sterowniki procesora GPU są zoptymalizowane pod kątem lub udostępnienia dodatkowych funkcji debugowania.  
  
  Oprócz tych korzyści analizy klatek można również zmienić sposób renderowania ramki podczas odtwarzania, aby jest obecny, aby dowiedzieć się, jak te zmiany mogą mieć wpływ na wydajność renderowania aplikacji. Te informacje służy do określania między strategii optymalizacji w potencjalne bez konieczności zaimplementować je wszystkie i następnie przechwytywanie i porównaj wszystkie wyniki samodzielnie.  
  
  Mimo że funkcja analizy klatek jest przeznaczona głównie do pomagają zwiększyć wydajność renderowania, może równie pomóc Ci osiągnąć lepszą jakość wizualną dla elementu docelowego wydajności danego lub ograniczyć zużycie energii procesora GPU.  
  
  Aby wyświetlić pokaz działania analizy klatek czynności dla aplikacji, możesz obejrzeć [analiza klatek grafiki programu Visual Studio](http://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo w witrynie Channel 9.  
  
## <a name="using-frame-analysis"></a>Za pomocą analizy klatek  
 Zanim będzie możliwe użycie analizy klatek, należy przechwytywać informacje graficzne z aplikacji po jej uruchomieniu, tak samo jak przy użyciu jednej z innych narzędzi Analizator grafiki programu. Następnie w oknie grafiki (.vsglog) dokumentu dziennika wybierz **analizy klatek** kartę.  
  
 ![Wybierz kartę analizy klatek.](../debugger/media/pix-frame-analysis-select-tab.png "pix_frame_analysis_select_tab")  
  
 Po zakończeniu analizy, wyniki są wyświetlane. W górnej części kartę analizy klatek przedstawia oś czasu i tabelę podsumowania. W dolnej części Wyświetla tabele szczegółowe informacje. Jeśli błędy lub ostrzeżenia zostały wygenerowane podczas odtwarzania, ich podsumowanie znajduje się powyżej osi czasu; z tego miejsca możesz wykonać łącza, aby dowiedzieć się więcej na temat błędów i ostrzeżeń.  
  
### <a name="interpreting-results"></a>Interpretowanie wyników  
 Interpretując wyniki każdego wariantu, można wywnioskować, że przydatne informacje na temat aplikacji przez renderowanie, wydajności i zachowań. Aby uzyskać więcej informacji na temat renderowanie wariantów zobacz [wariantów](#Variants) w dalszej części tego artykułu.  
  
 Niektóre wyniki wskazują bezpośrednio, jak wariant wpływa na wydajność renderowania:  
  
- Jeśli wariant warianty punktowego filtrowania tekstur wykazało, że wzrost wydajności, wówczas używanie tekstury warianty punktowego filtrowania w aplikacji zostaną wyświetlone podobne wzrost wydajności.  
  
- Jeśli wariantu 1 x 1 okienka ekranu wykazało, że wzrost wydajności, następnie zmniejszenie rozmiaru elementów docelowych renderowania w aplikacji będą zwiększyć jej wydajność renderowania.  
  
- Jeśli wariant kompresji tekstury BC wykazało, że wzrost wydajności, następnie w aplikacji przy użyciu kompresji tekstury BC zostaną wyświetlone podobne wzrost wydajności.  
  
- Jeśli wariant 2xMSAA ma prawie ta sama wydajność co wariant 0xMSAA, można włączyć 2xMSAA w swojej aplikacji, aby poprawiać jego jakość renderowanie, bez ponoszenia kosztów w wydajności.  
  
  Inne wyniki może sugerować głębiej, bardziej subtelne wpływ na wydajność Twojej aplikacji:  
  
- Jeśli wariantu 1 x 1 okienka ekranu przedstawia bardzo dużych wzrostów wydajności, aplikacja prawdopodobnie zużywa fillrate więcej niż jest dostępne. Jeśli ten wariant wskazuje nie wzrost wydajności, aplikacja jest prawdopodobnie przetwarzania zbyt wielu wierzchołków.  
  
- Jeśli wariant formatu docelowego renderowania 16bpp wskazuje znaczący wzrost wydajności, aplikacja prawdopodobnie zużywa zbyt dużej ilości pamięci przepustowość.  
  
- Jeśli wariant wymiarów tekstury Half/Quarter pokazuje znaczący wzrost wydajności, Twoje tekstury prawdopodobnie zajmować dużo pamięci, używać zbyt dużej ilości przepustowości lub nieefektywnie Użyj pamięci podręcznej tekstury. Jeśli ten wariant wskazuje bez zmian, wydajność, prawdopodobnie można tekstury większych i bardziej szczegółowy bez konieczności płacenia spadek wydajności.  
  
  Gdy będzie dostępnych liczników sprzętowych umożliwia ich zbierania bardzo szczegółowe informacje na temat dlaczego może cierpiących wydajność renderowania Twojej aplikacji. I przez urządzenia do 9.2 lub nowszy poziom funkcji obsługi zapytań zamknięcia głębokość (**pikseli zamknięte** licznika) i sygnatury czasowe. Innych liczników sprzętowych mogą być dostępne, w zależności od tego, czy producent procesora GPU ma zaimplementowany liczników sprzętowych i udostępniane im w jej sterownika. Te liczniki można użyć, aby potwierdzić przyczynę dokładne wyniki wyświetlane w tabeli podsumowania — na przykład można określić, czy overdraw jest czynnikiem, sprawdzając wartość procentowa piksele, które zostały zamknięte przez test głębi.  
  
### <a name="timeline-and-summary-table"></a>Oś czasu i tabelę podsumowania  
 Domyślnie oś czasu i tabeli podsumowania są wyświetlane, a pozostałe sekcje są zwinięte.  
  
#### <a name="timeline"></a>Oś czasu  
 Oś czasu przedstawia omówienie czasów wywołanie rysowania względem siebie nawzajem. Ponieważ większych paski odpowiadają wydłużenie czasu rysowania, umożliwia on szybko znaleźć najbardziej kosztowne wywołania rysowania w ramce. Gdy przechwyconej ramki zawiera bardzo dużej liczby wywołań rysowania, wiele rysowania który wywołania są połączone w jeden pasek którego długość jest sumą tych narysuj wywołania.  
  
 ![Oś czasu pokazuje rysowania&#45;wywołać kosztów. ](../debugger/media/pix-frame-analysis-timeline.png "pix_frame_analysis_timeline")  
  
 Wskaźnik na pasku, aby zobaczyć, które zdarzenie wywołania rysowania pasku odpowiada. Wybierając słupek powoduje, że lista zdarzeń, które mają być synchronizowane tego zdarzenia.  
  
#### <a name="table"></a>tabela  
 W tabeli liczb poniżej osi czasu przedstawiono względną wydajność każdego wariantu renderowania dla każdego wywołania rysowania w odniesieniu do aplikacji domyślne renderowanie. Każda kolumna Wyświetla typ variant renderowania różnią i każdy wiersz reprezentuje wywołanie rysowania różnych, która jest identyfikowana w skrajnej lewej kolumnie; w tym miejscu możesz wykonać łącze do zdarzenia w oknie Lista zdarzeń grafiki.  
  
 ![Podsumowanie tabeli przedstawiono różne varients. ](../debugger/media/pix-frame-analysis-summary.png "pix_frame_analysis_summary")  
  
 W drugiej kolumnie tabeli podsumowania skrajnie po lewej wyświetla czasu renderowania linii bazowej Twojej aplikacji — oznacza to, że czas potrzebny aplikacji domyślne renderowanie do ukończenia wywołania rysowania. Pozostałe kolumny Pokaż względną wydajność każdego wariantu renderowania jako wartość procentowa linii bazowej, tak, aby łatwiej zobaczyć, czy można zwiększyć wydajność. Przekracza 100 procent wartości procentowych trwało dłużej niż linii bazowej — czyli wydajności zakończył działanie — i mniejsze niż 100 procent zajęło mniej czasu na wartości procentowe — wydajności zmieniał.  
  
 Wartości bezwzględne chronometraż linii bazowej i względnego chronometrażu wariantów renderowania są faktycznie mean średnie wielu przebiegów — 5 domyślnie. Średnia wartość ta pomaga, upewnij się, że dane chronometrażu niezawodnych i spójnych. Umieszczeniu wskaźnika myszy na każdej komórki w tabeli, aby zbadać minimalna, maksymalna, średnia i wartości mediana czasu, które zaobserwowano wyniki w tym rysowania wywołania i renderowanie wariantów zostały wygenerowane. Czas punktu odniesienia jest również wyświetlany.  
  
#### <a name="hot-draw-calls"></a>"Problematyczna" Rysuj wywołania  
 Aby zwrócić uwagę na rysowanie wywołania, które zużywają więcej ogólną czasu renderowania lub które mogą być niezwykle powolne dla powody, dla których można uniknąć, wiersz, który zawiera te wywołania rysowania "gorącymi" jest przyciemnione czerwony, gdy terminy odniesienia jest więcej niż jeden Odchylenie standardowe jest dłuższa niż średniego czasu linii bazowej dla wszystkich wywołań rysowania w ramce.  
  
 ![To wywołanie DrawIndexed ma varients gorące i zimne. ](../debugger/media/pix-frame-analysis-hot-calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Obserwowane  
 Aby zwrócić uwagę na renderowanie zmian, które mają największą zgodność, analiza klatek określa statystyczne znaczenie każdego wariantu renderowania i wyświetla te znaczące jak pogrubienie. Wyświetla te, które zwiększają wydajność co w kolorze zielonym i te, które obniżenie wydajności w kolorze czerwonym. Wyświetla wyniki, które nie są statystycznie istotne jako normalnych typów.  
  
 ![Statystyczne przydatność wariant wywołanie rysowania](../debugger/media/pix-frame-analysis-summary-stats.png "pix_frame_analysis_summary_stats")  
  
 Aby ustalić istotność statystycznych, analiza klatek używa [t Studenta](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Tabela szczegółów  
 Poniżej podsumowania jest tabela szczegółów, która domyślnie jest zwinięta. Zawartość tabeli Szczegóły, zależy od platformy sprzętowej maszyny odtwarzania. Aby uzyskać informacje o platformach obsługiwanego sprzętu, zobacz [pomoc techniczna dotycząca sprzętu](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Platformy, które nie obsługują liczników sprzętowych  
 Większość platform nie obsługują w pełni liczniki procesora GPU sprzętu — dotyczy to wszystkich procesorach GPU znajdujących się obecnie oferowane przez firmy Intel, AMD i firmy nVidia. Jeśli nie ma żadnych liczników sprzętowych, aby zbierać, jest wyświetlana tylko jedna tabela szczegółów i zawiera średni bezwzględny czas wszystkich wariantów.  
  
 ![Tabela szczegółów i niektóre varients odtwarzania. ](../debugger/media/pix-frame-analysis-details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Temat platform obsługujących liczników sprzętowych  
 Dla platform, które obsługują liczniki procesora GPU sprzęt — na przykład procesory GPU nVidia T40 SOC i wszystkie Soc Qualcomm — kilka tabel szczegóły są wyświetlane, jeden dla każdego wariantu. Każdego licznika sprzętu są zbierane dla każdego wariantu renderowania i wyświetlane w tabeli Szczegóły.  
  
 ![Liczniki sprzętu są wyświetlane, jeśli są obsługiwane. ](../debugger/media/pix-frame.png "pix_frame")  
  
 Informacje o liczniku sprzętu zawiera bardzo szczegółowe widok zachowań określonych platforma sprzętowa dla każdego wywołania rysowania, które mogą pomóc Ci przyczynie wąskich gardeł wydajności bardzo dokładnie.  
  
> [!NOTE]
>  Platformy sprzętowe obsługują różne liczniki; nie istnieje standard. Liczniki i ich znaczenie są określane wyłącznie przez każdego producenta procesora GPU.  
  
### <a name="marker-regions-and-events"></a>Znacznik regionów i zdarzenia  
 Analiza klatek obsługuje znaczniki zdarzenie zdefiniowane przez użytkownika i grupy zdarzeń. Są one wyświetlane w tabeli podsumowania, a w tabelach szczegółów.  
  
 Interfejsy API ID3DUserDefinedAnnotation lub starszej wersji rodziny D3DPERF_ interfejsów API umożliwia tworzenie znaczniki i grup. Korzystając z rodziny D3DPERF_ interfejsu API, można przypisać każdego znacznika i grupy kolor, który jest analiza klatek jest wyświetlany jako kolorowy poza pasmem w wierszach, które zawierają znacznik zdarzenia lub znaczników rozpoczęcia/zakończenia grupy zdarzeń i ich zawartość. Ta funkcja może pomóc szybko zidentyfikować ważne renderowania zdarzeń lub grup zdarzeń.  
  
### <a name="warnings-and-errors"></a>Ostrzeżenia i błędy  
 Analiza klatek czasami kończy się ostrzeżenia lub błędy, które są podsumowane powyżej osi czasu i szczegółowe u dołu kartę analizy klatek.  
  
 Zwykle ostrzeżenia i błędy służą tylko do celów informacyjnych i nie wymaga żadnej interwencji.  
  
 Ostrzeżenia zazwyczaj oznacza, że pomoc techniczna dotycząca sprzętu Brak, ale możesz pracować nad całym, nie można zebrać liczników sprzętowych lub niektóre dane dotyczące wydajności może nie być wiarygodne — na przykład, gdy obejście negatywny wpływ na jej.  
  
 Błędy zazwyczaj wskazują, że implementacji analizy klatek ma usterek, sterownik ma usterek, pomoc techniczna dotycząca sprzętu braku i nie może odbywać się w całym lub aplikacja próbuje coś, co nie jest obsługiwana przez odtwarzanie.  
  
### <a name="retries"></a>Ponowne próby  
 Jeśli procesora GPU podlega przejściu stanu zasilania podczas analizy klatek, dotyczy analizy przejście musi zostać powtórzone, ponieważ szybkość zegara procesora GPU zmienione, a tym samym unieważnione wyniki względnego chronometrażu.  
  
 Analiza klatek ogranicza liczbę ponownych prób do 10. Jeśli platformą zarządzania energią agresywne lub uzyskania bramowego zegara, może spowodować analizy klatek zakończyć się niepowodzeniem i zgłoś błąd, ponieważ przekroczyła limit ponownych prób. Może być w stanie rozwiązać ten problem, resetując używanej platformy zarządzania energią i zegara, szybkość ograniczania jako łagodniej, umożliwia platformie.  
  
##  <a name="HardwareSupport"></a> Pomoc techniczna dotycząca sprzętu  
  
### <a name="timestamps-and-occlusion-queries"></a>Zapytania sygnatury czasowe i zamknięcia.  
 Sygnatury czasowe są obsługiwane na wszystkich platformach, które obsługują analizy klatek. Głębokość zamknięcia zapytania — wymagana dla licznika zamknięte pikseli — są obsługiwane na platformach, które obsługują poziom funkcji 9.2 lub nowszej.  
  
> [!NOTE]
>  Choć sygnatur czasowych są obsługiwane na wszystkich platformach, które obsługują analizy klatek, dokładność i spójność sygnatury czasowe różni się w zależności od platformy.  
  
### <a name="gpu-counters"></a>Liczniki procesora GPU  
 Pomoc dotycząca liczników sprzętowych procesora GPU jest zależna od sprzętu.  
  
 Ponieważ żaden komputer GPU obecnie oferowane przez firmy Intel, AMD lub nVidia obsługuje liczników sprzętowych procesora GPU niezawodne, analiza klatek nie zbiera liczniki z nich. Jednak funkcja analizy klatek zbierania liczników sprzętowych z tych procesorów GPU, które w niezawodny sposób będą obsługiwać takiej osoby:  
  
- SOC Qualcomm, (wszystkie obsługującego Windows Phone)  
  
- nVidia T40 (Tegra4).  
  
  Żadna inna platforma, która obsługuje analizy klatek zbiera dane liczników sprzętowych procesora GPU.  
  
> [!NOTE]
>  Ponieważ liczników sprzętowych procesora GPU zasobów sprzętowych, może upłynąć wielu przebiegów, aby zebrać pełny zestaw liczników sprzętowych dla poszczególnych wariantu renderowania. W rezultacie kolejność, w którym procesor GPU zbieranymi licznikami jest nieokreślona.  
  
### <a name="windows-phone"></a>Windows phone  
 Sygnatury czasowe, zamknięcia zapytania i liczników sprzętowych procesora GPU są obsługiwane tylko w aparaty telefoniczne Windows Phone, które dostarczonych z systemem Windows Phone 8.1. Analiza klatek wymaga je w celu odtwarzania, że plik dziennika grafiki. Aparaty telefoniczne Windows Phone, dostarczonych pierwotnie wraz z programem Windows Phone 8 nie obsługują analizy ramek, nawet w przypadku aparaty telefoniczne, które zostały zaktualizowane do wersji Windows Phone 8.1.  
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Niektóre sposoby korzystania z analizy klatek nie są obsługiwane lub są dobrym pomysłem.  
  
### <a name="warp"></a>WARP  
 Analiza klatek jest przeznaczona do użycia na potrzeby profilowania i poprawić wydajność renderowania na sprzęt rzeczywisty. Uruchomiona analiza klatek na urządzenia WARP nie uniemożliwia — emulator Windows Phone, który jest uruchamiany na WARP — ale nie jest zazwyczaj zwiększonej wykonywania, ponieważ WARP systemem wysokiej klasy procesora CPU jest mniejsza niż nawet zdolne do najmniejszej nowoczesnych procesorów GPU i WARP wydajność może się zmieniać znacznie w zależności od określonego Procesora działa on.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Odtwarzanie wysokiej funkcji poziomu przechwycone dane urządzenia niskiego poziomu  
 W analizatorze grafiki podczas odtwarzania pliku dziennika grafiki, która używa wyższy poziom funkcji nie obsługuje maszynę odtwarzającą, jego automatycznie powraca do WARP. Analiza klatek go jawnie nie wracały do WARP i generuje błąd, — WARP jest przydatne, sprawdzając poprawność aplikacja Direct3D, ale nie sprawdzenie jego wydajności.  
  
> [!NOTE]
>  Chociaż jest to ważne, aby pamiętać, poziom funkcji problemów, można przechwytywać i odtwarzać że dziennika grafiki plików na urządzeniach i różne konfiguracje sprzętu. Na przykład można przechwytywać informacje graficzne na Windows Phone i odtwarzać je z powrotem na komputerze stacjonarnym i odwrotnie jest również obsługiwany. W obu przypadkach dziennik grafiki można odtwarzać ponownie tak długo, jak w pliku dziennika nie zawiera interfejsów API lub użyć poziomów funkcji, które nie są obsługiwane na maszynie odtwarzającej.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 i niższy  
 Analiza klatek jest obsługiwana tylko dla interfejsu API programu Direct3D 11. Jeśli aplikacja wymaga interfejsu API Direct3D 10, analiza klatek nie rozpoznaje lub ich profil, nawet jeśli ich rozpoznawany i używany przez inne narzędzia Analizator grafiki programu. Jeśli aplikacja używa Direct3D11 i interfejsów API Direct3D 10, są profilowane tylko wywołania Direct3D 11.  
  
> [!NOTE]
>  Dotyczy to tylko do wywołań interfejsu API Direct3D, których używasz, nie poziomów funkcji. Tak długo, jak długo używasz Direct3D 11, Direct3D 11.1 i Direct3D 11.2 API, można użyć dowolnego poziomu funkcji, które chcesz i analiza klatek tylko będą działać.  
  
##  <a name="Variants"></a> Wariantów  
 Każda zmiana, który sprawia, że funkcja analizy klatek sposób renderowania ramki podczas odtwarzania jest znany jako *wariant*. Warianty, które sprawdza, czy analiza klatek odnoszą się do wspólnego, stosunkowo łatwa zmiany, które można wprowadzić ulepszenia wydajności renderowania i jakość wizualną aplikacji — na przykład, zmniejszenie rozmiaru tekstury, przy użyciu kompresji tekstury lub włączenie różne rodzaje wygładzanie. Warianty zastąpić kontekstu zwykle renderowania i parametrów w aplikacji. Poniżej przedstawiono podsumowanie:  
  
|Variant|Opis|  
|-------------|-----------------|  
|**Rozmiaru 1 x 1 okienka ekranu**|Maksymalne wymiary okienka ekranu na wszystkie elementy docelowe renderowania na 1 x 1 pikseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant rozmiaru okienka ekranu 1 x 1](../debugger/1x1-viewport-size-variant.md)|  
|**0x MSAA**|Wyłącza wielu przykładowe Wygładzanie (MSAA) na wszystkie elementy docelowe renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](../debugger/0x-2x-4x-msaa-variants.md)|  
|**2x MSAA**|Umożliwia 2 x wielu przykładowe Wygładzanie (MSAA) dla wszystkich elementów docelowych renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](../debugger/0x-2x-4x-msaa-variants.md)|  
|**4x MSAA**|Umożliwia 4 x wielu przykładowe Wygładzanie (MSAA) dla wszystkich elementów docelowych renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](../debugger/0x-2x-4x-msaa-variants.md)|  
|**Filtrowanie punktów tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_MIP_POINT` (punkt filtrowania tekstur) dla wszystkich przykładów odpowiednie tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [punkt dwuliniowa Trilinear i wariantów Anizotropowego filtrowania tekstur](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie warianty punktowego tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (warianty punktowego tekstury filtrowanie) dla wszystkich przykładów odpowiednie tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [punkt dwuliniowa Trilinear i wariantów Anizotropowego filtrowania tekstur](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie trójliniowego tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (trójliniowego tekstury filtrowanie) dla wszystkich przykładów odpowiednie tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [punkt dwuliniowa Trilinear i wariantów Anizotropowego filtrowania tekstur](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie anizotropowe tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_ANISOTROPIC` i `MaxAnisotropy` do `16` (16 x filtrowanie anizotropowe tekstury) dla wszystkich przykładów odpowiednie tekstury.<br /><br /> Aby uzyskać więcej informacji, zobacz [punkt dwuliniowa Trilinear i wariantów Anizotropowego filtrowania tekstur](../debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Formatu docelowego renderowania 16bpp**|Ustawia format pikseli `DXGI_FORMAT_B5G6R5_UNORM` (16bpp 565 formacie) dla wszystkich renderowania obiektów docelowych i backbuffers.<br /><br /> Aby uzyskać więcej informacji, zobacz [16bpp renderowania docelowy Format typu Variant](../debugger/16bpp-render-target-format-variant.md)|  
|**Generacji mipmapy**|Umożliwia mapy mip na wszystkie tekstury, które nie są renderowane elementów docelowych.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant generowania mipmapy](../debugger/mip-map-generation-variant.md).|  
|**Wymiary tekstury w wysokości równej połowie**|Maksymalne wymiary tekstury na wszystkie tekstury, które nie są elementy docelowe renderowania, do połowy ich oryginalnego rozmiaru każdego wymiaru. Na przykład tekstury 256 x 128 jest ograniczone do tekseli 128 x 64.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant wymiarów tekstury Half/Quarter](../debugger/half-quarter-texture-dimensions-variant.md).|  
|**Wymiary tekstury kwartał**|Maksymalne wymiary tekstury na wszystkie tekstury, które nie są renderowane obiekty docelowe do czwartej ich oryginalnego rozmiaru każdego wymiaru. Na przykład tekstury 256 x 128 jest ograniczone do 64 x 32 tekseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant wymiarów tekstury Half/Quarter](../debugger/half-quarter-texture-dimensions-variant.md).|  
|**Kompresji tekstury BC**|Umożliwia zablokowanie kompresji dla wszystkich tekstury, które mają B8G8R8X8, B8G8R8A8 lub R8G8B8A8 wariant format pikseli. Warianty format B8G8R8X8 są kompresowane przy użyciu formantów BC1; B8G8R8A8 i wariantów format R8G8B8A8 są kompresowane przy użyciu BC3.<br /><br /> Aby uzyskać więcej informacji, zobacz [wariant kompresji tekstury BC](../debugger/bc-texture-compression-variant.md).|  
  
 Większość wariantów powstaje przetestowanego rozwiązania ze szczegółami: "25 procent szybciej jest zmniejszenie rozmiaru tekstura o połowę" lub "Włączanie 2 x MSAA jest tylko 2% wolniej". Inne odmiany może wymagać interpretacji więcej — na przykład, jeśli wariant, który zmienia rozmiary okienka ekranu do 1 x 1 wykazuje duże są bardziej wydajne, może to wskazywać, że renderowanie jest bottlenecked przez współczynnik wypełnienia niski; Alternatywnie Jeśli nie ma żadnych istotnych zmian w wydajności, może to wskazywać, renderowanie jest bottlenecked przez przetwarzanie wierzchołka.
