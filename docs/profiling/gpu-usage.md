---
title: Użycie procesora GPU | Microsoft Docs
description: Dowiedz się, jak używać narzędzia użycie procesora GPU w profilerze wydajności, aby lepiej zrozumieć użycie sprzętu przez aplikację Direct3D na wysokim poziomie.
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78f847acaf67a61064e64b765d9c138ec2fe93a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959028"
---
# <a name="gpu-usage"></a>Użycie procesora GPU

Użyj narzędzia użycie procesora GPU w profilerze wydajności, aby lepiej zrozumieć użycie sprzętu przez aplikację Direct3D na wysokim poziomie. Pomaga sprawdzić, czy wydajność aplikacji jest związana z procesorem CPU lub procesorem GPU, oraz uzyskać wgląd w to, jak wydajniej korzystać z sprzętu platformy. Użycie procesora GPU obsługuje aplikacje korzystające z funkcji Direct3D 12, Direct3D 11 i Direct3D 10. Nie obsługuje innych graficznych interfejsów API, takich jak Direct2D lub OpenGL.

Oto jak wygląda okno **raport użycia procesora GPU** :

![Zrzut ekranu przedstawiający raport użycia procesora GPU z osiami czasu procesora CPU i procesora GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Wymagania

Oprócz wymagań dotyczących Diagnostyka grafiki, do korzystania z narzędzia użycia procesora GPU wymagane są następujące elementy:

- Procesor GPU i sterownik obsługujący wymaganą instrumentację chronometrażu.

  > [!NOTE]
  > Aby uzyskać więcej informacji na temat obsługiwanego sprzętu i sterowników, zapoznaj się z tematem [Obsługa sprzętu i sterowników](#hwsupport) na końcu tego dokumentu.

Aby uzyskać więcej informacji na temat wymagań Diagnostyka grafiki, zobacz [wprowadzenie](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>Korzystanie z narzędzia użycie procesora GPU

Po uruchomieniu aplikacji w narzędziu Użycie procesora GPU program Visual Studio tworzy sesję diagnostyczną. Ta sesja przedstawia ogólne informacje na temat wydajności renderowania aplikacji i użycia procesora GPU w czasie rzeczywistym.

Aby uruchomić narzędzie użycie procesora GPU:

1. W menu głównym wybierz kolejno opcje **Debuguj**  >  **wydajność i Diagnostyka** (lub na klawiaturze naciśnij kombinację klawiszy Alt + F2).

2. W centrum **wydajności i diagnostyki** zaznacz pole wyboru obok opcji **użycie procesora GPU**. Opcjonalnie zaznacz pola obok innych interesujących Cię narzędzi. Jednocześnie można uruchomić kilka narzędzi do oceny wydajności i diagnostyki, aby uzyskać pełniejszy obraz wydajności aplikacji.

    ![Zrzut ekranu przedstawiający narzędzie Performance profiler z wybranym użyciem procesora GPU](media/gpuusageselected.png "Wybrane użycie procesora GPU")

   > [!NOTE]
   > Nie wszystkie narzędzia do oceny wydajności i diagnostyki mogą być używane jednocześnie.

3. W dolnej części centrum **wydajności i diagnostyki** wybierz pozycję **Rozpocznij** , aby uruchomić aplikację w obszarze wybranych narzędzi.

Informacje wysokiego poziomu wyświetlane w czasie rzeczywistym obejmują chronometraż ramki, szybkość klatek i użycie procesora GPU. Każdy z tych informacji jest przedstawiany niezależnie, ale wszystkie te informacje korzystają ze wspólnej skali czasu, dzięki czemu można łatwo zrozumieć relacje.

Wykresy **czasu ramki (MS)** i **klatki na sekundę (FPS)** każdy mają dwie czerwone, poziome linie, które pokazują cele wydajności 60 i 30 klatek na sekundę. W grafie czasu ramki aplikacja przekracza obiekt docelowy wydajności, gdy wykres znajduje się poniżej linii, a obiekt docelowy zostanie pominięty, gdy wykres znajduje się nad wierszem. W przypadku klatek na sekundę wykres jest odwrotny: aplikacja przekracza obiekt docelowy wydajności, gdy wykres znajduje się nad wierszem, a obiektem docelowym jest, gdy wykres znajduje się poniżej wiersza. Te wykresy są używane głównie w celu uzyskania wysokiego poziomu wydajności aplikacji i zidentyfikowania spowolnienia, które warto zbadać. Na przykład, dalsze badanie może być uzasadnione, Jeśli zobaczysz nagłe porzucanie szybkości klatek lub wzrost użycia procesora GPU.

Gdy aplikacja jest uruchamiana w narzędziu Użycie procesora GPU, sesja diagnostyki zbiera także szczegółowe informacje o zdarzeniach graficznych, które zostały uruchomione na procesorze GPU. Te informacje służą do generowania bardziej szczegółowego raportu o tym, jak aplikacja korzysta ze sprzętu. Ponieważ ten raport zajmuje trochę czasu na wygenerowanie z zebranych informacji, jest dostępny tylko po zakończeniu sesji diagnostycznej zbierania informacji.

Jeśli chcesz dokładniej zapoznać się z wydajnością lub wykorzystaniem problemu, Zatrzymaj zbieranie informacji o wydajności, aby można było wygenerować raport.

Aby wygenerować i wyświetlić raport użycia procesora GPU:

1. W dolnej części okna sesji diagnostycznej wybierz łącze **Zatrzymaj zbieranie** lub wybierz pozycję **Zatrzymaj** w lewym górnym rogu.

   ![Zrzut ekranu przedstawiający okno sesji diagnostyki w narzędziu Użycie procesora GPU, pokazujący ramki na sekundę, użycie procesora GPU, przycisk Zatrzymaj i łącze Zatrzymaj zbieranie.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. W górnej części raportu wybierz sekcję z jednego z grafów, który pokazuje problem, który chcesz zbadać. Wybór może być dłuższy niż 3 sekundy. Dłuższe sekcje są obcinane do początku.

   ![Zrzut ekranu przedstawiający okno sesji diagnostyki w narzędziu Użycie procesora GPU z wybraną częścią osi czasu sesji diagnostycznej.](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Aby wyświetlić szczegółową oś czasu zaznaczenia, w dolnej części raportu w **... Kliknij tutaj, aby wyświetlić szczegóły użycia procesora GPU dla tego komunikatu zakresu** , wybierz pozycję **Wyświetl szczegóły**.

   ![Zrzut ekranu przedstawiający okno sesji diagnostyki z wybranym zakresem](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Wybranie tej opcji spowoduje otwarcie nowego dokumentu z kartami zawierającym raport. Raport użycia procesora GPU pozwala zobaczyć, kiedy zdarzenie grafiki jest uruchamiane na procesorze CPU, gdy osiągnie procesor GPU i ile czasu procesor GPU ma uruchamiać go. Te informacje mogą pomóc identyfikować wąskie gardła i możliwości w celu zwiększenia równoległości kodu.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Eksportuj do narzędziu gpuview lub analizatora wydajności systemu Windows

Począwszy od programu Visual Studio 2017, można otworzyć te dane za pomocą [narzędziu gpuview](/windows-hardware/drivers/display/using-gpuview) i [analizatora wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer). Po prostu wybierz pozycję **Otwórz w narzędziu gpuview** lub **Otwórz w usłudze WPA** znajdującą się w prawym dolnym rogu sesji diagnostycznej.

![Zrzut ekranu przedstawiający okno sesji diagnostyki z wyróżnionymi łączami](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Korzystanie z raportu użycia procesora GPU

W górnej części raportu o użyciu procesora GPU przedstawiono osie czasu dla działania przetwarzania procesora CPU, działania renderowania procesora GPU i działania kopiowania procesora GPU. Te osie czasu są podzielone przez jasne Szare słupki pionowe, które wskazują synchronizację w pionie ekranu (pionie). Częstotliwość wyświetlania słupków jest zgodna z szybkością odświeżania jednego z ekranów (wybraną przy użyciu listy rozwijanej **Display** ), z której zostały zebrane dane użycia procesora GPU.

Ponieważ wyświetlacz może mieć wyższą częstotliwość odświeżania niż wartość docelową wydajności aplikacji, może nie być relacji 1-do-1 między pionie i szybkością klatek, która ma osiągnąć aplikacja. Aby sprostać obiektowi docelowemu wydajności, aplikacja musi ukończyć wszystkie przetwarzanie, wykonać renderowanie i `Present()` nawiązać połączenie z ukierunkowaną szybkością klatek. Renderowane ramka nie będzie pokazywana do następnej pionie po `Present()` , chociaż.

Dolna część raportu użycia procesora GPU zawiera listę zdarzeń grafiki, które wystąpiły w czasie trwania raportu. Po wybraniu zdarzenia znacznik pojawia się na odpowiednich zdarzeniach na odpowiednich osiach czasu. Zazwyczaj jedno zdarzenie w wątku procesora CPU pokazuje wywołanie interfejsu API, a inne zdarzenie na jednym z osi czasu procesora GPU pokazuje, kiedy procesor GPU ukończył zadanie. Analogicznie, po wybraniu zdarzenia na osi czasu raport wyróżnia odpowiednie zdarzenie grafiki w dolnej części raportu.

Po powiększeniu wartości z osi czasu w górnej części raportu są widoczne tylko najbardziej czasochłonne zdarzenia. Aby wyświetlić zdarzenia, które mają krótszy czas trwania, Powiększ do osi czasu za pomocą klawiszy CTRL + kółka na urządzeniu wskazującym lub kontrolki skalowania w lewym dolnym rogu górnego panelu. Możesz również przeciągnąć zawartość panelu Oś czasu, aby przejść przez zarejestrowane zdarzenia.

Aby ułatwić znalezienie tego, czego szukasz, przefiltruj raport użycia procesora GPU na podstawie nazw procesów, identyfikatorów wątków i nazwy zdarzenia. Ponadto możesz wybrać, która częstotliwość odświeżania ekranu określa vysnc wierszy. Można sortować zdarzenia hierarchicznie, jeśli aplikacja używa interfejsu [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) do grupowania poleceń renderowania.

 Poniżej przedstawiono więcej informacji:

|Formant filtru|Opis|
|--------------------|-----------------|
|**Proces**|Nazwa żądanego procesu. Wszystkie procesy, które używały procesora GPU podczas sesji diagnostycznej, znajdują się na liście rozwijanej. Kolor skojarzony z procesem jest kolorem działania wątku na osi czasu.|
|**Nici**|Identyfikator wątku, który Cię interesuje. W aplikacji wielowątkowej te informacje mogą ułatwić odizolowanie konkretnych wątków należących do procesu, który Cię interesuje. Zdarzenia skojarzone z wybranym wątkiem są wyróżnione na każdej osi czasu.|
|**Wyświetlanie**|Liczba wyświetlaczy, których częstotliwość odświeżania jest pokazywana. Niektóre sterowniki można skonfigurować tak, aby wyświetlały wiele fizycznych wyświetlaczy jako pojedyncze, duże, wirtualne. Może pojawić się tylko jeden ekran na liście, nawet jeśli na komputerze jest dołączonych wiele ekranów.|
|**Filtr**|Słowa kluczowe, które Cię interesują. Zdarzenia w dolnej części raportu będą zawierać tylko te, które pasują do słowa kluczowego, w całości lub częściowo. Można określić wiele słów kluczowych, rozdzielając je średnikami (;).|
|**Sortowanie hierarchii**|Pole wyboru wskazujące, czy hierarchie zdarzeń zdefiniowane za pomocą znaczników użytkownika są zachowywane lub ignorowane.|

Lista zdarzeń w dolnej części raportu użycia procesora GPU przedstawia szczegóły każdego zdarzenia.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa zdarzenia**|Nazwa zdarzenia graficznego. Zdarzenie zazwyczaj odpowiada zdarzeniu w osi czasu wątku procesora i zdarzenia osi czasu procesora GPU. Nazwy zdarzeń mogą być *nieprzypisane* , jeśli użycie procesora GPU nie jest w stanie określić nazwy zdarzenia. Aby uzyskać więcej informacji, zapoznaj się z uwagą poniżej tej tabeli.|
|**Uruchomienie procesora CPU (NS)**|Czas inicjalizacji zdarzenia w PROCESORze, wywołując interfejs API Direct3D. Czas jest mierzony w nanosekundach względem momentu uruchomienia aplikacji.|
|**Uruchomienie procesora GPU (NS)**|Czas, w którym zdarzenie zostało zainicjowane na procesorze GPU. Czas jest mierzony w nanosekundach względem momentu uruchomienia aplikacji.|
|**Czas trwania procesora GPU (NS)**|Czas trwania zdarzenia w nanosekundach na procesorze GPU.|
|**Nazwa procesu**|Nazwa aplikacji, z której pochodzi zdarzenie.|
|**Identyfikator wątku**|Identyfikator wątku, z którego pochodzi zdarzenie.|

> [!IMPORTANT]
> Jeśli procesor GPU lub sterownik nie obsługują niezbędnych funkcji instrumentacji, wszystkie zdarzenia będą wyświetlane jako bez *atrybutu*. Jeśli wystąpi ten problem, zaktualizuj sterownik procesora GPU i spróbuj ponownie. Aby uzyskać więcej informacji, zobacz temat [Obsługa sprzętu i sterowników](#hwsupport) na końcu tego dokumentu.

## <a name="gpu-usage-settings"></a>Ustawienia użycia procesora GPU

Można skonfigurować narzędzie użycie procesora GPU, aby odroczyć zbieranie informacji o profilowania, zamiast rozpoczynać zbieranie informacji zaraz po uruchomieniu aplikacji. Ponieważ rozmiar informacji o profilach może być znaczący, ta akcja jest przydatna, gdy wiesz, że spowolnienie działania aplikacji nie będą wyświetlane do czasu późniejszego.

Aby odłożyć profilowanie od początku aplikacji:

1. W menu głównym wybierz kolejno opcje **Debuguj**  >  **wydajność i Diagnostyka** (lub na klawiaturze naciśnij kombinację klawiszy Alt + F2).

2. W centrum **wydajności i diagnostyki** obok opcji **użycie procesora GPU** wybierz link **Ustawienia** .

3. W obszarze **Konfiguracja profilowania procesora GPU** na stronie właściwości **Ogólne** Usuń zaznaczenie pola wyboru **Rozpocznij profilowanie podczas uruchamiania aplikacji** , aby odroczyć profilowanie.

   ![Zrzut ekranu przedstawiający strony właściwości obiektu, pokazujący opcje kolekcji](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> W tej chwili nie można odroczyć profilowania dla aplikacji Direct3D 12.

Po uruchomieniu aplikacji w narzędziu Użycie procesora GPU w dolnej części okna narzędzia użycie procesora GPU zostanie udostępniona dodatkowa link. Aby rozpocząć zbieranie informacji o profilowania, wybierz link **Rozpocznij** w polu **Rozpocznij zbieranie dodatkowych szczegółowych danych o użyciu procesora GPU** .

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Obsługa sprzętu i sterowników

Obsługiwane są następujące sprzętowe i sterowniki procesora GPU:

|Dostawca|Opis procesora GPU|Wymagana wersja sterownika|
|------------|---------------------|-----------------------------|
|Intel®|4. generacja procesorów Intel® Core ("Haswell")<br /><br /> — Grafika firmy Intel® HD (GT1)<br />-Intel® HD Graphics 4200 (GT2)<br />-Intel® HD Graphics 4400 (GT2)<br />-Intel® HD Graphics 4600 (GT2)<br />— Intel® HD Graphics P4600 (GT2)<br />— Intel® HD Graphics P4700 (GT2)<br />-Intel® HD Graphics 5000 (GT3)<br />-® Iris firmy Intel™ Graphics 5100 (GT3)<br />-Intel® Iris™ Pro Graphics 5200 (GT3e)|(Użyj najnowszych sterowników)|
|® AMD|Najczęściej jest to seria AMD Radeon™ HD 7000 (wyklucza procesor AMD Radeon™ HD 7350-7670)<br /><br /> Procesor AMD Radeon™ GPU, procesory GPU AMD FirePro™ i akceleratory procesora GPU AMD FirePro z architekturą GCN (Graphics Core Next)<br /><br /> Procesory AMD® E-Series i AMD A serii A (APUs) wyposażone w architekturę GCN (Graphics Core) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14,7 RC3 lub nowszy|
|NVIDIA®|Najwięcej z nich, ponieważ NVIDIA® GeForce® 400 — seria<br /><br /> NVIDIA® GeForce® procesorów GPU, NVIDIA Quadro® GPU i NVIDIA® Tesla™ akceleratory procesora GPU z Fermi™, Kepler™ lub Maxwell™ architektury|343,37 lub nowszy|

 Konfiguracje wieloprocesorowe, takie jak NVIDIA® SLI™ i AMD CrossFire™, nie są obecnie obsługiwane. Obsługiwane są ustawienia hybrydowej grafiki, takie jak NVIDIA® Optimus™ i AMD Enduro™.
