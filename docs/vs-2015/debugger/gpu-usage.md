---
title: Użycie procesora GPU | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7dee579f726a1edfc81e1f3e1ec62bf7d8beba4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437952"
---
# <a name="gpu-usage"></a>Użycie procesora GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj narzędzie użycie procesora GPU w programie Visual Studio Centrum wydajności i diagnostyki, aby lepiej zrozumieć wykorzystanie sprzętu wysokiego poziomu aplikacji Direct3D. Służy do określenia, czy wydajność aplikacji jest zależne od Procesora CPU lub powiązane z procesora GPU i Uzyskaj wgląd w korzystania z platformy sprzętowe bardziej efektywnie. Użycie procesora GPU obsługuje aplikacje, które używają Direct3D 12, Direct3D 11 i Direct3D 10; Program nie obsługuje innych graficznych interfejsów API, takich jak Direct2D lub OpenGL.  
  
 Jest to **raport użycia procesora GPU** okna:  
  
 ![Raport użycia procesora GPU, z osiami czasu procesora CPU i procesora GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Wymagania  
 Poniżej przedstawiono wymagania dotyczące korzystania z narzędzia użycie procesora GPU, które obowiązują oprócz wymagań diagnostyki grafiki.  
  
- Procesora GPU i sterowników, które obsługują Instrumentacji niezbędne chronometrażu.  
  
  > [!NOTE]
  > Aby uzyskać więcej informacji na temat obsługiwanego sprzętu i sterowniki, zobacz [sprzętu i sterowników, które obsługują](#hwsupport) na końcu tego dokumentu.  
  
  Aby uzyskać więcej informacji na temat wymagań dotyczących diagnostyki grafiki, zobacz [wprowadzenie](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Za pomocą narzędzia użycie procesora GPU  
 Po uruchomieniu aplikacji w narzędziu użycie procesora GPU, Visual Studio tworzy sesję diagnostyki, wykresów ogólne informacje o aplikacji wydajność renderowania i użycie procesora GPU w czasie rzeczywistym.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Aby uruchomić narzędzie użycie procesora GPU:  
  
1. W menu głównym wybierz **debugowania**, następnie **wydajności i diagnostyki** (klawiatury: Naciśnij klawisze Alt + F2).  
  
2. W Centrum wydajności i diagnostyki, zaznacz pole wyboru obok pozycji **użycie procesora GPU**. Opcjonalnie zaznacz pola wyboru obok inne narzędzia, których interesuje Cię. Możesz uruchomić kilka wydajności i narzędzia diagnostyczne jednocześnie, aby uzyskać pełniejszy obraz wydajności Twojej aplikacji.  
  
    ![Wybierz narzędzia diagnostyczne, którego chcesz użyć. ](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   > Nie wszystkie narzędzia wydajności i diagnostyki, można w tym samym czasie.  
  
3. Wybierz niebieski **Start** znajdujący się u dołu Centrum wydajności i diagnostyki, aby uruchomić aplikację w obszarze narzędzia wybrane.  
  
   Ogólne informacje, które jest wyświetlane w czasie rzeczywistym obejmuje czas ramki, szybkości klatek i użycia procesora GPU. Każda z tych rodzajów informacji wykresie przedstawia możliwościom niezależnie, ale Użyj skali typowy moment, można łatwo powiązać między nimi.  
  
   **Ramki czas (ms)** i **klatek na sekundę (kl. / s)** wykresów zawiera dwa czerwony, poziomych linii przeznaczonego wydajności reprezentują 60 i 30 klatek na sekundę. W **ramki czasu** wykres, Twoja aplikacja jest przekroczenie element docelowy wydajności, gdy wykres jest poniżej wiersza i go brakuje, gdy wykres jest powyżej wiersza. Liczba klatek na drugi wykres jest przeciwieństwem — Twoja aplikacja jest przekroczenie element docelowy wydajności, gdy wykres jest powyżej wiersza i go brakuje, gdy wykres jest poniżej wiersza. Przede wszystkim te wykresy są używane, można pobrać pomysłem wysokiego poziomu wydajności Twojej aplikacji i zidentyfikować slow-downs, które możesz chcieć zbadać — na przykład, szybkości klatek nagły spadek lub wzrost użycia procesora GPU.  
  
   Podczas wykonywania aplikacji w narzędziu użycie procesora GPU, sesja diagnostyki zbiera również szczegółowe informacje dotyczące zdarzenia grafiki, które zostały wykonane na procesorze GPU. Te informacje jest używane do generowania bardziej szczegółowy raport o jak Twoja aplikacja korzysta z sprzętu. Ponieważ ten raport wymaga pewnego czasu, aby wygenerować z zebranych informacji, jest on dostępny tylko po wykonaniu czynności zbieranie informacji o sesji diagnostycznej.  
  
   Podczas chcesz Przyjrzyj się wydajności lub wykorzystania wystawiać dokładniej, zatrzymać zbieranie informacji o wydajności, dzięki czemu można wygenerować raport.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Aby wygenerować i wyświetlić raport użycia procesora GPU:  
  
1. W dolnej części okna sesji diagnostyki wybierz **Zatrzymaj Kolekcjonowanie** łącze lub naciśnij **zatrzymać** w lewym górnym rogu.  
  
    ![Zbieraj informacje o czasie procesorów GPU i CPU. ](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. W górnej części raportu wybierz sekcję jeden z wykresów, które przedstawiono ten problem, które chcesz zbadać. Wybór może być maksymalnie 3 sekundy długie. dłużej sekcje są obcinane w kierunku początku.  
  
    ![Wpis&#45;kolekcji, wybierz zakres, aby wyświetlić szczegóły](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. W dolnej części raportu, wybierz **wyświetlić szczegóły** łącze w **... Kliknij tutaj, aby wyświetlić szczegóły użycia procesora GPU dla tego zakresu** komunikat, aby wyświetlić szczegółowe osi czasu zaznaczenia.  
  
    ![Wpis&#45;kolekcji z zakresem wybrane](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Spowoduje to otwarcie nowego dokumentu z zakładkami, który zawiera raport. Raport użycia procesora GPU pomaga Zobacz rozpoczęcia zdarzenia grafiki na procesorze CPU, po dotarciu serwerów do procesora GPU i czas trwania procesora GPU do jego wykonania. Te informacje mogą pomóc w identyfikacji wąskich gardeł i możliwości zwiększenia równoległości w kodzie.  
  
## <a name="using-the-gpu-usage-report"></a>Za pomocą funkcji Zgłoś użycie procesora GPU  
 Górna część raport użycia procesora GPU przedstawia wykorzystanie Procesora działania, procesora GPU renderowanie aktywności i działania kopiowania procesora GPU osi czasu. Te osi czasu są podzielone według jasnoszary, pionowych słupków, które reprezentują pionie wyświetlania; częstotliwość pasków odpowiada częstotliwość odświeżania jednego zawiera (wybrany za pomocą **wyświetlania** listy rozwijanej) zostały zebrane tych danych użycia procesora GPU. Ponieważ wyświetlanie może być wyższa częstotliwość odświeżania od elementu docelowego wydajności aplikacji może nie być relacja 1 do 1 pionie i chcesz, aby aplikację, aby osiągnąć szybkość klatek. Do swojego docelowego wydajności aplikacji musi ukończenia całego procesu przetwarzania, wykonywanie renderowania i wywoływania Present() w docelowej szybkość klatek, ale Wyrenderowana ramka nie będą wyświetlane do czasu następnego pionie po Present().  
  
 W dolnej części Wyświetla listę zdarzeń grafiki, które wystąpiły w okresie raportu.  
  
 Oto **raport użycia procesora GPU** okna:  
  
 ![Raport użycia procesora GPU, z osiami czasu procesora CPU i procesora GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Wybranie jednego ze zdarzeń w dolnej części raportu umieszcza znacznik na pokrewnych zdarzeń w odpowiednich osi czasu, zwykle jedno zdarzenie w wątku Procesora, który reprezentuje wywołanie interfejsu API i inne zdarzenie na jednym z osi czasu procesora GPU, które reprezentuje kiedy procesora GPU Ukończone zadania. Podobnie wybranie jednego ze zdarzeń na osi czasu wyróżnia odpowiadające zdarzenie w dolnej części raportu. Gdy element z osi czasu w górnej części raportu, tylko najbardziej czasochłonne zdarzenia są widoczne. Aby wyświetlić zdarzenia, które mają krótszy czas, powiększenie osi czasu, za pomocą klawiszy Ctrl + obrót kółkiem na urządzenia wskazującego lub skalowania formantu w lewym dolnym rogu górnym panelu. Można również przeciągać zawartość panelu osi czasu, aby przeglądać zarejestrowane zdarzenia.  
  
 Aby pomóc Ci znaleźć, czego szukasz, możesz filtrować raport użycia procesora GPU, na podstawie nazwy procesu, wątku identyfikatorów i nazwą zdarzeń; Ponadto można wybrać, które wyświetlania częstotliwość odświeżania określa wiersze vysnc i Sortuj zdarzenia hierarchicznie Jeśli aplikacja używa interfejsu ID3DUserDefinedAnnotation do grupy poleceń renderowania.  
  
 Poniżej przedstawiono więcej informacji:  
  
|Formant filtru|Opis|  
|--------------------|-----------------|  
|**Proces**|Nazwa procesu, który Cię interesuje. Wszystkie procesy, które używały procesora GPU podczas sesji diagnostycznej znajdują się na tej liście rozwijanej. Kolor skojarzony z procesu w tej listy rozwijanej jest kolor działanie wątku na osiach czasu poniżej.|  
|**Wątek**|Identyfikator wątku, który Cię interesuje. W przypadku aplikacji wielowątkowych to może pomóc wyizolować określoną wątków, które należą do procesu, który chcesz wziąć. Zdarzenia związane z wybranym wątku są wyróżnione w każdym osi czasu.|  
|**Wyświetlanie**|Liczba wyświetlania, w których częstotliwość odświeżania jest wyświetlana **Uwaga:**  Niektóre sterowniki można skonfigurować do przedstawienia wielu ekranów fizycznych jako pojedyncze, duże ekran wirtualnego. Widoczne mogą być tylko jeden ekran, na liście, nawet wtedy, gdy komputer ma wiele ekranów dołączone.|  
|**Filtr**|Słowa kluczowe, które Cię interesuje. Zdarzenia w dolnej części raportu będzie zawierał tylko te, które odpowiadają — słowo kluczowe w całości lub części. Można określić wiele słów kluczowych, oddzielając je średnikami (;).|  
|**Sortuj hierarchii**|Pole wyboru, która wskazuje, czy hierarchie zdarzeń — definiowane przy użyciu znaczniki użytkownika — są zachowywane lub zignorować.|  
  
 Lista zdarzeń w dolnej części raportu użycia procesora GPU przedstawiono szczegóły każdego zdarzenia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa zdarzenia**|Nazwa zdarzenia grafiki. Zdarzenie odnosi się zazwyczaj jedno zdarzenie na osi czasu wątku procesora CPU i jedno zdarzenie na osi czasu procesora GPU.<br /><br /> Nazwy zdarzeń może być "unattributed", jeśli użycie procesora GPU nie może określić nazwę zdarzenia. Aby uzyskać więcej informacji zobacz uwagi pod tą tabelą.|  
|**Uruchomienie procesora CPU (ns)**|Czas zdarzenia zostało zainicjowane na procesorze CPU, wywołując interfejs API Direct3D. Czas jest mierzony w nanosekundach względem podczas uruchamiania aplikacji.|  
|**Uruchomienie procesora GPU (ns)**|Czas zdarzenia zostało zainicjowane na procesorze GPU. Czas jest mierzony w nanosekundach względem podczas uruchamiania aplikacji.|  
|**Czas trwania procesora GPU (ns)**|Czas zdarzenia na procesorze GPU w nanosekundach.|  
|**Nazwa procesu**|Nazwa aplikacji, z której pochodzi zdarzenie.|  
|**Identyfikator wątku**|Identyfikator wątku, z której pochodzi zdarzenie.|  
  
> [!IMPORTANT]
> Windows 8.1 jest wymagany dla zdarzeń: uznanie autorstwa. Ponadto jeśli sterownik lub procesora GPU, na których nie obsługują funkcji niezbędne instrumentacji, wszystkie zdarzenia będą wyświetlane jako "unattributed". Pamiętaj zaktualizować sterownik procesora GPU i spróbuj ponownie. Jeśli wystąpi ten problem. Aby uzyskać więcej informacji, zobacz [sprzętu i sterowników, które obsługują](#hwsupport) poniżej.  
  
## <a name="gpu-usage-settings"></a>Ustawienia użycia procesora GPU  
 Można skonfigurować narzędzie użycie procesora GPU można odroczyć kolekcji profilowania informacje, a nie od umożliwiają zebranie informacji dotyczących zaraz po uruchomieniu aplikacji. Ponieważ rozmiar profilowania informacje mogą być istotne, jest to przydatne, gdy wiesz, że spowolnienie wydajności Twojej aplikacji nie będzie wyświetlane dopiero po pewnym czasie.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Aby odłożyć profilowania od samego początku aplikacji:  
  
1. W menu głównym wybierz **debugowania**, następnie **wydajności i diagnostyki** (klawiatury: Naciśnij klawisze Alt + F2).  
  
2. W Centrum wydajności i diagnostyki, postępuj zgodnie z **ustawienia** łącze obok **użycie procesora GPU**.  
  
3. W obszarze **Konfiguracja profilowania procesora GPU**na **ogólne** strony właściwości, wyczyść **rozpocząć profilowanie przy uruchamianiu aplikacji** pole wyboru, aby odłożyć profilowania.  
  
     ![Skonfiguruj, kiedy rozpoczyna się zbieranie użycia procesora GPU](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
> Odracza profilowania nie jest obecnie obsługiwane w przypadku aplikacji Direct3D 12.  
  
 Odroczysz zbierania informacji profilowania za pomocą tego ustawienia dodatkowe łącze staje się dostępna w dolnej części okna narzędzia użycie procesora GPU po uruchomieniu aplikacji w narzędziu użycie procesora GPU. Aby rozpocząć zbieranie informacji o profilowania, wybierz opcję **Start** łącze w **Start zbieranie dodatkowych szczegółowych danych użycia procesora GPU** wiadomości.  
  
## <a name="hwsupport"></a> Sprzęt i obsłudze sterowników  
 Obsługiwane są następujące sprzęcie procesora GPU i sterowniki:  
  
|Dostawcy|Opis procesora GPU|Wymagana wersja sterownika|  
|------------|---------------------|-----------------------------|  
|Intel®|4th Generation Intel® Core Processors (‘Haswell’)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|--(Użyj najnowsze sterowniki)|  
|AMD®|Większość od serii 7000 HD™ AMD Radeon (AMD Radeon™ HD 7350 7670 z wyłączeniem)<br /><br /> Akceleratory AMD Radeon™ GPU, AMD FirePro™ GPU i procesora GPU FirePro AMD oferujący funkcje architektury grafiki Core dalej (GCN).<br /><br /> Seria E AMD® i serii AMD A Accelerated przetwarzania jednostki (APU) oferujący funkcje grafiki Core dalej (GCN) architektury ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 lub nowszej|  
|NVIDIA®|Najbardziej od 400 serii NVIDIA GeForce®.<br /><br /> Procesory GPU NVIDIA® GeForce®, procesory GPU NVIDIA Quadro® i procesor GPU Tesla™ NVIDIA® akceleratorów, oferujący funkcje Fermi™, Kepler™ lub Maxwell™ architektury.|343.37 lub nowszej|  
  
 Konfiguracje wieloma procesorami GPU, takie jak NVIDIA® SLI™ i AMD Crossfire™ nie są obsługiwane w tej chwili. Ustawienia grafiki hybrydowe, takie jak NVIDIA® Optimus™ i AMD Enduro™ są obsługiwane.  
  
## <a name="see-also"></a>Zobacz także  
  
- [Rozwiązywanie trudnych problemów grafiki, za pomocą swoich gier przy użyciu technologii DirectX narzędzi (wideo)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
- [Narzędzie użycie procesora GPU w programie Visual Studio (wideo)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
- [Narzędzie użycie procesora GPU w programie Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
  
- [Użycie procesora GPU dla technologii DirectX w programie Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)
