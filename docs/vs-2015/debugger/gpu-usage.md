---
title: Użycie procesora GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b2e827b180ae218f3dd42b124500e01260e72d82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297394"
---
# <a name="gpu-usage"></a>Użycie procesora GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj narzędzia użycie procesora GPU w centrum wydajności i diagnostyki programu Visual Studio, aby lepiej zrozumieć użycie sprzętu przez aplikację Direct3D na wysokim poziomie. Można jej użyć do określenia, czy wydajność aplikacji jest związana z procesorem CPU czy z procesorem GPU, oraz uzyskać wgląd w to, jak wydajniej korzystać z sprzętu platformy. Użycie procesora GPU obsługuje aplikacje korzystające z funkcji Direct3D 12, Direct3D 11 i Direct3D 10. nie obsługuje innych graficznych interfejsów API, takich jak Direct2D lub OpenGL.  
  
 Jest to okno **raport użycia procesora GPU** :  
  
 ![Raport użycia procesora GPU z osią czasu procesora i procesora GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Wymagania  
 Poniżej przedstawiono wymagania dotyczące korzystania z narzędzia użycie procesora GPU, które jest oprócz wymagań Diagnostyka grafiki.  
  
- Procesor GPU i sterownik obsługujący wymaganą instrumentację chronometrażu.  
  
  > [!NOTE]
  > Aby uzyskać więcej informacji na temat obsługiwanego sprzętu i sterowników, zapoznaj się z tematem [Obsługa sprzętu i sterowników](#hwsupport) na końcu tego dokumentu.  
  
  Aby uzyskać więcej informacji na temat wymagań Diagnostyka grafiki, zobacz [wprowadzenie](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Korzystanie z narzędzia użycie procesora GPU  
 Po uruchomieniu aplikacji w narzędziu Użycie procesora GPU program Visual Studio tworzy sesję diagnostyczną, która przedstawia ogólne informacje na temat wydajności renderowania aplikacji i użycia procesora GPU w czasie rzeczywistym.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Aby uruchomić narzędzie użycie procesora GPU:  
  
1. W menu głównym wybierz **Debuguj**, a następnie **wydajność i Diagnostyka** (klawiatura: naciśnij klawisze ALT + F2).  
  
2. W centrum wydajności i diagnostyki zaznacz pole wyboru obok opcji **użycie procesora GPU**. Opcjonalnie zaznacz pola obok innych interesujących Cię narzędzi. Jednocześnie można uruchomić kilka narzędzi do oceny wydajności i diagnostyki, aby uzyskać pełniejszy obraz wydajności aplikacji.  
  
    ![Wybierz Narzędzia diagnostyczne, których chcesz użyć.](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   > Nie wszystkie narzędzia do oceny wydajności i diagnostyki mogą być używane jednocześnie.  
  
3. Wybierz przycisk niebieski **Start** w dolnej części centrum wydajności i diagnostyki, aby uruchomić aplikację w obszarze wybranych narzędzi.  
  
   Informacje wysokiego poziomu, które są wyświetlane w czasie rzeczywistym, obejmują chronometraż ramki, szybkość klatek i użycie procesora GPU. Każda z tych informacji jest tworzona niezależnie, ale używana jest wspólna Skala czasu, dzięki czemu można łatwo powiązać między nimi.  
  
   Wykresy **czasu ramki (MS)** i **klatek na sekundę (FPS)** zawierają dwie czerwone, poziome linie, które reprezentują cele wydajności 60 i 30 klatek na sekundę. Na wykresie **czasu ramki** Twoja aplikacja przekracza miejsce docelowe wydajności, gdy wykres znajduje się poniżej linii i brakuje go, gdy wykres znajduje się nad wierszem. Na wykresie dla klatek na sekundę jest to przeciwieństwo — Twoja aplikacja przekracza obiekt docelowy wydajności, gdy wykres znajduje się nad linią i brakuje go, gdy wykres znajduje się poniżej wiersza. Przede wszystkim wykresy te służą do uzyskania wysokiego poziomu wydajności aplikacji i ustalenia spowolnienia, które warto zbadać — na przykład, nagłe porzucanie szybkości klatek lub zwiększenie użycia procesora GPU.  
  
   Gdy aplikacja jest uruchamiana w narzędziu Użycie procesora GPU, sesja diagnostyki zbiera także szczegółowe informacje o zdarzeniach graficznych, które zostały wykonane na procesorze GPU. Te informacje służą do generowania bardziej szczegółowego raportu o tym, jak aplikacja korzysta ze sprzętu. Ponieważ ten raport zajmuje trochę czasu na wygenerowanie z zebranych informacji, jest dostępny tylko po zakończeniu sesji diagnostycznej zbierania informacji.  
  
   Jeśli chcesz dokładniej zapoznać się z wydajnością lub wykorzystaniem problemu, Zatrzymaj zbieranie informacji o wydajności, aby można było wygenerować raport.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Aby wygenerować i wyświetlić raport użycia procesora GPU:  
  
1. W dolnej części okna sesji diagnostycznej wybierz link **Zatrzymaj zbieranie** lub naciśnij przycisk **Zatrzymaj** w lewym górnym rogu.  
  
    ![Zbieraj informacje o procesorach GPU i procesora CPU.](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. W górnej części raportu wybierz sekcję z jednego z grafów, który pokazuje problem, który chcesz zbadać. Wybór może być dłuższy niż 3 sekundy; dłuższe sekcje są obcinane do początku.  
  
    ![Opublikuj&#45;kolekcji, wybierz zakres, aby wyświetlić szczegóły](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. W dolnej części raportu wybierz link **Wyświetl szczegóły** w **... Kliknij tutaj, aby wyświetlić szczegóły użycia procesora GPU dla tego komunikatu zakresu,** aby wyświetlić szczegółową oś czasu zaznaczenia.  
  
    ![Opublikuj&#45;kolekcji z wybranym zakresem](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Spowoduje to otwarcie nowego dokumentu z kartami zawierającym raport. Raport użycia procesora GPU pozwala zobaczyć, kiedy zdarzenie grafiki jest uruchamiane na procesorze CPU, gdy osiągnie procesor GPU i ile czasu procesor GPU ma go wykonać. Te informacje mogą pomóc identyfikować wąskie gardła i możliwości w celu zwiększenia równoległości kodu.  
  
## <a name="using-the-gpu-usage-report"></a>Korzystanie z raportu użycia procesora GPU  
 W górnej części raportu użycia procesora GPU są wyświetlane osie czasu dla działania przetwarzania procesora CPU, działania renderowania GPU i działania kopiowania procesora GPU. Te osie czasu są podzielone przez jasne i Szare słupki, które reprezentują pionie wyświetlania. częstotliwość wyświetlania słupków jest zgodna z szybkością odświeżania jednego z wyświetlaczy (wybraną z listy rozwijanej **Display** ), z której zostały zebrane dane użycia procesora GPU. Ponieważ wyświetlacz może mieć wyższą częstotliwość odświeżania niż miejsce docelowe wydajności aplikacji, może nie być relacji 1-do-1 między pionie i szybkością klatek, które ma osiągnąć aplikacja. Aby zaspokoić miejsce docelowe wydajności, aplikacja musi ukończyć wszystkie przetwarzanie, wykonać renderowanie i utworzyć obecne wywołanie () na docelowej szybkości klatek, ale renderowane ramki nie będą wyświetlane do następnego pionie po obecnym ().  
  
 Dolna część wyświetla listę zdarzeń grafiki, które wystąpiły w czasie trwania raportu.  
  
 Oto okno **raport użycia procesora GPU** :  
  
 ![Raport użycia procesora GPU z osią czasu procesora i procesora GPU](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Wybranie jednego ze zdarzeń w dolnej części raportu powoduje umieszczenie znacznika w odpowiednich zdarzeniach na odpowiednich osiach czasu, zazwyczaj jedno zdarzenie w wątku procesora, które reprezentuje wywołanie interfejsu API i inne zdarzenie na jednym z osi czasu procesora GPU, które reprezentuje czas wykonania zadania przez procesor GPU. Analogicznie, wybranie jednego ze zdarzeń na osi czasu powoduje wyróżnienie odpowiedniego zdarzenia w dolnej części raportu. W przypadku powiększania z osi czasu w górnej części raportu są widoczne tylko najbardziej czasochłonne zdarzenia. Aby wyświetlić zdarzenia, które mają krótszy czas trwania, Powiększ do osi czasu za pomocą klawiszy CTRL + kółka na urządzeniu wskazującym lub kontrolki skalowania w lewym dolnym rogu górnego panelu. Możesz również przeciągnąć zawartość panelu Oś czasu, aby przejść przez zarejestrowane zdarzenia.  
  
 Aby pomóc w znalezieniu tego, czego szukasz, możesz filtrować raport użycia procesora GPU na podstawie nazw procesów, identyfikatorów wątków i nazwy zdarzenia. Ponadto możesz wybrać, która częstotliwość odświeżania ekranu określa vysnc linie i można sortować zdarzenia hierarchicznie, jeśli aplikacja używa interfejsu ID3DUserDefinedAnnotation do grupowania poleceń renderowania.  
  
 Poniżej przedstawiono więcej informacji:  
  
|Formant filtru|Opis|  
|--------------------|-----------------|  
|**Proces**|Nazwa żądanego procesu. Wszystkie procesy, które używały procesora GPU podczas sesji diagnostycznej, znajdują się na liście rozwijanej. Kolor skojarzony z procesem w tym menu rozwijanym jest kolorem działania wątku na osiach czasu poniżej.|  
|**Nici**|Identyfikator wątku, który Cię interesuje. W aplikacji wielowątkowej może to pomóc w wyodrębnieniu określonych wątków należących do procesu, który Cię interesuje. Zdarzenia skojarzone z wybranym wątkiem są wyróżnione na każdej osi czasu.|  
|**Wyświetlanie**|Liczba wyświetleń, których częstotliwość odświeżania jest wyświetlana **Uwaga:**  niektóre sterowniki można skonfigurować w taki sposób, aby przedstawić wiele fizycznych wyświetlaczy jako pojedynczy, duży ekran wirtualny. Może pojawić się tylko jeden ekran na liście, nawet jeśli na komputerze jest dołączonych wiele ekranów.|  
|**Filtr**|Słowa kluczowe, które Cię interesują. Zdarzenia w dolnej części raportu będą zawierać tylko te, które pasują do słowa kluczowego w całości lub w części. Można określić wiele słów kluczowych, rozdzielając je średnikami (;).|  
|**Sortowanie hierarchii**|Pole wyboru wskazujące, czy hierarchie zdarzeń — zdefiniowane za pomocą znaczników użytkownika — są zachowywane lub ignorowane.|  
  
 Lista zdarzeń w dolnej części raportu użycia procesora GPU zawiera szczegóły każdego zdarzenia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa zdarzenia**|Nazwa zdarzenia graficznego. Zdarzenie zazwyczaj odpowiada jednemu zdarzeniu w osi czasu wątku procesora i jednym zdarzeniu na osi czasu procesora GPU.<br /><br /> Nazwy zdarzeń mogą mieć wartość "unattributed", jeśli użycie procesora GPU nie było w stanie określić nazwy zdarzenia. Aby uzyskać więcej informacji, zobacz uwagi pod tą tabelą.|  
|**Uruchomienie procesora CPU (NS)**|Czas inicjalizacji zdarzenia w PROCESORze, wywołując interfejs API Direct3D. Czas jest mierzony w nanosekundach względem momentu uruchomienia aplikacji.|  
|**Uruchomienie procesora GPU (NS)**|Czas, w którym zdarzenie zostało zainicjowane na procesorze GPU. Czas jest mierzony w nanosekundach względem momentu uruchomienia aplikacji.|  
|**Czas trwania procesora GPU (NS)**|Czas, jaki zajęło ukończenie zdarzenia na procesorze GPU w nanosekundach.|  
|**Nazwa procesu**|Nazwa aplikacji, z której pochodzi zdarzenie.|  
|**Identyfikator wątku**|Identyfikator wątku, z którego pochodzi zdarzenie.|  
  
> [!IMPORTANT]
> Do przypisywania zdarzeń jest wymagane Windows 8.1. Ponadto jeśli procesor GPU lub sterownik nie obsługują niezbędnych funkcji instrumentacji, wszystkie zdarzenia będą wyświetlane jako "unattributeed". Upewnij się, że sterownik procesora GPU został zaktualizowany, i spróbuj ponownie, jeśli wystąpi ten problem. Aby uzyskać więcej informacji, [Zobacz poniżej](#hwsupport) .  
  
## <a name="gpu-usage-settings"></a>Ustawienia użycia procesora GPU  
 Można skonfigurować narzędzie użycie procesora GPU, aby odroczyć zbieranie informacji o profilowania, zamiast rozpoczynać zbieranie informacji zaraz po uruchomieniu aplikacji. Ponieważ rozmiar informacji o profilach może być znaczący, jest to przydatne, gdy wiesz, że spowalniania wydajności aplikacji nie będą wyświetlane do czasu ich późniejszego użycia.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Aby odłożyć profilowanie od początku aplikacji:  
  
1. W menu głównym wybierz **Debuguj**, a następnie **wydajność i Diagnostyka** (klawiatura: naciśnij klawisze ALT + F2).  
  
2. W centrum wydajności i diagnostyki postępuj zgodnie z linkiem **Ustawienia** obok pozycji **użycie procesora GPU**.  
  
3. W obszarze **Konfiguracja profilowania procesora GPU**na stronie właściwości **Ogólne** Usuń zaznaczenie pola wyboru **Rozpocznij profilowanie podczas uruchamiania aplikacji** , aby odroczyć profilowanie.  
  
     ![Skonfiguruj, kiedy rozpocznie się zbieranie danych o użyciu procesora GPU](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
> Przełożenie profilowania nie jest obecnie obsługiwane w przypadku aplikacji Direct3D 12.  
  
 Po odłożeniu kolekcji informacji profilowania przy użyciu tego ustawienia dodatkowe łącze jest dostępne w dolnej części okna narzędzia użycie procesora GPU po uruchomieniu aplikacji w narzędziu Użycie procesora GPU. Aby rozpocząć zbieranie informacji o profilowania, wybierz link **Rozpocznij** w polu **Rozpocznij zbieranie dodatkowych szczegółowych danych o użyciu procesora GPU** .  
  
## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Obsługa sprzętu i sterowników  
 Obsługiwane są następujące sprzętowe i sterowniki procesora GPU:  
  
|Dostawca|Opis procesora GPU|Wymagana wersja sterownika|  
|------------|---------------------|-----------------------------|  
|Intel®|4. generacja procesorów Intel® Core ("Haswell")<br /><br /> — Grafika firmy Intel® HD (GT1)<br />-Intel® HD Graphics 4200 (GT2)<br />-Intel® HD Graphics 4400 (GT2)<br />-Intel® HD Graphics 4600 (GT2)<br />— Intel® HD Graphics P4600 (GT2)<br />— Intel® HD Graphics P4700 (GT2)<br />-Intel® HD Graphics 5000 (GT3)<br />-® Iris firmy Intel™ Graphics 5100 (GT3)<br />-Intel® Iris™ Pro Graphics 5200 (GT3e)|--(Użyj najnowszych sterowników)|  
|® AMD|Większość niż AMD Radeon™ HD 7000 — seria (wyklucza procesor AMD Radeon™ HD 7350-7670)<br /><br /> Procesor AMD Radeon™ GPU, procesory GPU AMD FirePro™ i akceleratory procesora GPU AMD FirePro z architekturą Next Core Graphics (GCN).<br /><br /> Procesory AMD® E-Series i AMD A serii A (APUs) wyposażone w architekturę GCN (Graphics Core) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14,7 RC3 lub nowszy|  
|NVIDIA®|Najczęściej jest to NVIDIA® GeForce® 400.<br /><br /> NVIDIA® GeForce® procesorów GPU, NVIDIA Quadro® GPU i NVIDIA® Tesla™ akceleratory procesora GPU z Fermi™, Kepler™ lub Maxwell™ architekturą.|343,37 lub więcej|  
  
 W tej chwili nie są obsługiwane konfiguracje wieloprocesorowe, takie jak NVIDIA® SLI™ i AMD CrossFire™. Obsługiwane są ustawienia hybrydowej grafiki, takie jak NVIDIA® Optimus™ i AMD Enduro™.  
  
## <a name="see-also"></a>Zobacz też  
  
- [Rozwiązywanie trudnych problemów graficznych z grą przy użyciu narzędzi DirectX (wideo)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
- [Narzędzie użycie procesora GPU w programie Visual Studio (wideo)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
- [Narzędzie użycie procesora GPU w Visual Studio 2013 Update 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)  
  
- [Użycie procesora GPU dla programu DirectX w programie Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
