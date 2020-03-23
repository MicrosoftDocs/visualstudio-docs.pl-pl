---
title: Użycie GPU | Dokumenty firmy Microsoft
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f16a518542e8acab636da6e395fdfee8d7a25085
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969879"
---
# <a name="gpu-usage"></a>Użycie gpu

Użyj narzędzia Użycie procesora GPU w Centrum wydajności i diagnostyki programu Visual Studio, aby lepiej zrozumieć użycie sprzętu wysokiego poziomu aplikacji Direct3D. Pomaga sprawdzić, czy wydajność aplikacji jest związana z procesorem CPU lub GPU i uzyskać wgląd w sposób, w jaki można efektywniej korzystać ze sprzętu platformy. Użycie procesora gpu obsługuje aplikacje korzystające z funkcji Direct3D 12, Direct3D 11 i Direct3D 10; nie obsługuje innych interfejsów API grafiki, takich jak Direct2D lub OpenGL.

Ten zrzut ekranu przedstawia okno **Raport użycia procesora GPU:**

![Raport użycia procesora GPU z osiami czasu procesora i procesora graficznego](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Wymagania

Następujące wymagania dotyczące korzystania z narzędzia Użycie procesora GPU dodać do wymagań diagnostyki grafiki.

- Gpu i sterownik, które obsługują niezbędne oprzyrządowanie rozrządu.

  > [!NOTE]
  > Aby uzyskać więcej informacji na temat obsługiwanego sprzętu i sterowników, zobacz [Obsługa sprzętu i sterowników](#hwsupport) na końcu tego dokumentu.

  Aby uzyskać więcej informacji na temat wymagań dotyczących diagnostyki grafiki, zobacz [Wprowadzenie](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="using-the-gpu-usage-tool"></a>Korzystanie z narzędzia GPU

 Po uruchomieniu aplikacji w narzędziu użycia procesora GPU program Visual Studio tworzy sesję diagnostyczną, która wykresy wysokiego poziomu informacji o wydajności renderowania aplikacji i użycia procesora GPU w czasie rzeczywistym.

**Aby uruchomić narzędzie Użycie procesora GPU:**

1. W menu głównym wybierz **polecenie Debug ,** a następnie **performance i diagnostyka** (klawiatura: Naciśnij klawisze Alt+F2).

2. W centrum Wydajność i diagnostyka zaznacz pole wyboru obok pola **Użycie procesora GPU**. Opcjonalnie zaznacz pola obok innych narzędzi, które Cię interesują. Można uruchomić kilka narzędzi wydajności i diagnostyki jednocześnie, aby uzyskać pełniejszy obraz wydajności aplikacji.

    ![Wybierz narzędzia diagnostyczne, których chcesz użyć.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Nie wszystkie narzędzia wydajności i diagnostyki mogą być używane w tym samym czasie.

3. Wybierz niebieski przycisk **Start** u dołu centrum Wydajności i Diagnostyki, aby uruchomić aplikację w obszarze wybranych narzędzi.

   Informacje wysokiego poziomu wyświetlane w czasie rzeczywistym obejmują czas odtwarzania, liczbę klatek na sekundę i użycie procesora GPU. Każda z tych informacji jest wykresów niezależnie, ale należy użyć wspólnej skali czasu, dzięki czemu można łatwo odnosić się między nimi.

   Wykresy **Czas ramki (ms)** i **Klatki na sekundę (FPS)** mają dwie czerwone, poziome linie, które pokazują cele wydajności 60 i 30 klatek na sekundę. Na wykresie **czas ramki** aplikacja przekracza docelową wydajność, gdy wykres znajduje się poniżej wiersza i nie trafia do obiektu docelowego, gdy wykres znajduje się powyżej linii. Dla ramek na sekundę wykres, jest odwrotnie — aplikacja przekracza docelowy wydajności, gdy wykres jest powyżej linii i brakuje obiektu docelowego, gdy wykres jest poniżej linii. Przede wszystkim te wykresy są używane, aby uzyskać wysoki poziom pomysł wydajności aplikacji i zidentyfikować spowolnienia, które można zbadać, takich jak nagły spadek liczby klatek na sekundę lub skok wykorzystania gpu.

   Podczas gdy aplikacja działa w ramach narzędzia Użycie procesora GPU, sesja diagnostyki zbiera również szczegółowe informacje o zdarzeniach graficznych, które zostały wykonane na gpu. Te informacje są używane do generowania bardziej szczegółowy raport, jak aplikacja wykorzystuje sprzęt. Ponieważ ten raport zajmuje trochę czasu, aby wygenerować z zebranych informacji, jest on dostępny tylko po zakończeniu sesji diagnostyki zbierania informacji.

   Jeśli chcesz przyjrzeć się problem wydajności lub wykorzystania bliżej, przestań zbierać informacje o wydajności, tak aby raport może być generowany.

**Aby wygenerować i wyświetlić raport użycia procesora GPU:**

1. W dolnej części okna sesji diagnostycznej wybierz link **Zatrzymaj zbieranie** lub naciśnij **przycisk Zatrzymaj** w lewym górnym rogu.

   ![Zbieraj informacje o czasie procesora GPU i procesora.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. W górnej części raportu wybierz sekcję z jednego z wykresów, która pokazuje problem, który chcesz zbadać. Wybór może trwać do 3 sekund; dłuższe sekcje są obcinane w kierunku początku.

   ![Opublikuj kolekcję&#45;, wybierz zakres, aby wyświetlić szczegóły](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. W dolnej części raportu wybierz link **szczegóły widoku** w **... kliknij tutaj, aby wyświetlić szczegóły użycia gpu dla tego zakresu wiadomości,** aby wyświetlić szczegółową oś czasu wyboru.

   ![Księguj kolekcję&#45;z wybranym zakresem](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   To zaznaczenie powoduje otwarcie nowego dokumentu z kartami zawierającego raport. Raport użycia procesora GPU pomaga zobaczyć, kiedy zdarzenie grafiki jest uruchamiane na procesorze, kiedy osiągnie gpu i jak długo procesor GPU trwa do jego wykonania. Te informacje mogą pomóc w identyfikowaniu wąskich gardeł i możliwości zwiększenia równoległości w kodzie.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Eksportowanie do gpuview lub analizatora wydajności systemu Windows

Począwszy od programu Visual Studio 2017, można otworzyć te dane za pomocą [GPUView](/windows-hardware/drivers/display/using-gpuview) i [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer). Wystarczy wybrać **linki Otwórz w GpuView** lub Otwórz w **WPA** znajdujące się w prawym dolnym momencie sesji diagnostycznej.

![Otwórz w...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Korzystanie z raportu użycia procesora GPU

W górnej części raportu Użycie procesora GPU są wyświetlane osie czasu działania przetwarzania procesora CPU, aktywności renderowania procesora GPU i aktywności kopiowania procesora GPU. Te osie czasu są podzielone przez jasnoszare, pionowe paski wskazujące vsync wyświetlacza. Częstotliwość pasków odpowiada częstotliwości odświeżania jednego z ekranów (wybranego za pomocą listy rozwijanej **Display),** z której zebrano dane użycia procesora GPU. Ponieważ ekran może mieć wyższą częstotliwość odświeżania niż docelowa wydajność aplikacji, może nie istnieć relacja 1-to-1 między vsync i szybkością klatek, którą aplikacja ma osiągnąć. Aby osiągnąć docelowy wydajność, aplikacja musi zakończyć wszystkie przetwarzanie, wykonać renderowanie i wykonać wywołanie Present() przy docelowej szybkości klatek na sekundę. Renderowana ramka nie będzie wyświetlana do następnego vsync po Present(), choć.

W dolnej części wyświetlana jest lista zdarzeń graficznych, które wystąpiły w okresie raportu.

Oto okno **Raport użycia procesora GPU:**

![Raport użycia procesora GPU z osiami czasu procesora i procesora graficznego](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Po wybraniu zdarzenia w dolnej części raportu znacznik pojawia się w odpowiednich zdarzeniach na odpowiednich osiach czasu. Zazwyczaj jedno zdarzenie w wątku procesora CPU pokazuje wywołanie interfejsu API, podczas gdy inne zdarzenie na jednej z osi czasu gpu pokazuje, kiedy procesor GPU wykonał zadanie. Podobnie po wybraniu zdarzenia na osi czasu raport wyróżnia odpowiednie zdarzenie w dolnej części raportu. Po pomniejszeniu osi czasu w górnej części raportu widoczne są tylko najbardziej czasochłonne zdarzenia. Aby wyświetlić zdarzenia o krótszym czasie trwania, powiększ osi czasu za pomocą kółka Ctrl + na urządzeniu wskazującym lub formantu skalowania w lewym dolnym rogu górnego panelu. Można również przeciągnąć zawartość panelu osi czasu, aby przejść przez zarejestrowane zdarzenia.

Aby znaleźć to, czego szukasz, przefiltruj raport użycia procesora GPU na podstawie nazw procesów, identyfikatorów wątków i nazwy zdarzenia. Ponadto można wybrać częstotliwość odświeżania ekranu określa linie vysnc. Zdarzenia można sortować hierarchicznie, jeśli aplikacja używa interfejsu [ID3DUserDedefdefedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) do grupowania poleceń renderowania.

 Poniżej przedstawiono więcej informacji:

|Formant filtru|Opis|
|--------------------|-----------------|
|**Proces**|Nazwa procesu, który Cię interesuje. Wszystkie procesy, które zostały użyte gpu podczas sesji diagnostycznej są uwzględnione w tej listy rozwijanej. Kolor skojarzony z procesem w tej rozwijanej jest kolor aktywności wątku na osiach czasu poniżej.|
|**Wątku**|Identyfikator wątku, który Cię interesuje. W aplikacji wielowątkowej te informacje mogą pomóc w wyodrębnić określone wątki, które należą do procesu, który Cię interesuje. Zdarzenia skojarzone z wybranym wątkiem są wyróżnione na każdej osi czasu.|
|**Wyświetlanie**|Numer wyświetlacza, którego częstotliwość odświeżania jest **wyświetlana Uwaga:** Niektóre sterowniki można skonfigurować tak, aby prezentować wiele wyświetlaczy fizycznych jako pojedynczy, duży wyświetlacz wirtualny. Na liście może pojawić się tylko jeden wyświetlacz, nawet jeśli urządzenie ma podłączone wiele wyświetlaczy.|
|**Filtr**|Słowa kluczowe, które Cię interesują. Zdarzenia w dolnej części raportu będą zawierać tylko te, które pasują do słowa kluczowego w całości lub w części. Można określić wiele słów kluczowych, oddzielając je średnikiem (;).|
|**Sortowanie hierarchii**|Pole wyboru wskazujące, czy hierarchie zdarzeń — zdefiniowane za pomocą znaczników użytkownika — są zachowywane czy ignorowane.|

 Lista zdarzeń w dolnej części raportu użycia procesora GPU wyświetla szczegóły każdego zdarzenia.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa wydarzenia**|Nazwa zdarzenia graficznego. Zdarzenie zwykle odpowiada zdarzenia w oś czasu wątku procesora CPU i zdarzenia osi czasu gpu.<br /><br /> Nazwy zdarzeń mogą być "nieprzypisane", jeśli użycie procesora GPU nie może określić nazwy zdarzenia. Aby uzyskać więcej informacji, zobacz uwagę poniżej tej tabeli.|
|**Uruchomienie procesora (ns)**|Czas, w której zdarzenie zostało zainicjowane na procesorze, wywołując interfejs API Direct3D. Czas jest mierzony w nanosekundach w stosunku do momentu rozpoczęcia aplikacji.|
|**Gpu Start (ns)**|Czas, w której zdarzenie zostało zainicjowane na GPU. Czas jest mierzony w nanosekundach w stosunku do momentu rozpoczęcia aplikacji.|
|**Czas trwania gpu (ns)**|Czas, który zajęło ukończenie zdarzenia na GPU, w nanosekundach.|
|**Nazwa procesu**|Nazwa aplikacji, z której pochodzi zdarzenie.|
|**Identyfikator wątku**|Identyfikator wątku, z którego pochodzi zdarzenie.|

> [!IMPORTANT]
> Jeśli procesor graficzny lub sterownik nie obsługują niezbędnych funkcji instrumentacji, wszystkie zdarzenia będą wyświetlane jako "nieprzypisane". Pamiętaj, aby zaktualizować sterownik gpu i spróbuj ponownie, jeśli wystąpi ten problem. Aby uzyskać więcej informacji, zobacz [obsługa sprzętu i sterowników](#hwsupport) poniżej.

## <a name="gpu-usage-settings"></a>Ustawienia użycia procesora GPU

Narzędzie użycia procesora GPU można skonfigurować w celu odroczenia zbierania informacji o profilowaniu, zamiast rozpoczynać zbieranie informacji zaraz po uruchomieniu aplikacji. Ponieważ rozmiar informacji profilowania może być znaczący, ta akcja jest przydatna, gdy wiesz, że spowolnienie wydajności aplikacji nie pojawi się dopiero później.

**Aby odroczyć profilowanie od początku aplikacji:**

1. W menu głównym wybierz **polecenie Debug ,** a następnie **performance i diagnostyka** (klawiatura: Naciśnij klawisze Alt+F2).

2. W centrum Wydajność i diagnostyka kliknij łącze **ustawień** obok pozycji **Użycie procesora GPU**.

3. W obszarze **Konfiguracja profilowania gpu**, na stronie właściwości **Ogólne,** wyczyść **begin profilowania w aplikacji start,** aby odroczyć profilowanie.

   ![Konfigurowanie uruchamiania kolekcji użycia procesora GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Odkładanie profilowania nie jest obecnie obsługiwane w przypadku aplikacji Direct3D 12.

Po uruchomieniu aplikacji w narzędziu Użycie procesora GPU dodatkowe łącze staje się dostępne w dolnej części okna narzędzia Użycie procesora GPU. Aby rozpocząć zbieranie informacji profilowania, wybierz **start** łącze w **przycisku Rozpocznij zbieranie dodatkowych szczegółowych danych użycia procesora GPU.**

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a>Obsługa sprzętu i sterowników

Obsługiwane są następujące urządzenia i sterowniki gpu:

|Dostawca|Opis gpu|Wymagana wersja sterownika|
|------------|---------------------|-----------------------------|
|Intel®|Procesory Intel® Core 4. generacji ("Haswell")<br /><br /> - Intel® HD Graphics (GT1)<br />- Intel® HD Graphics 4200 (GT2)<br />- Intel® HD Graphics 4400 (GT2)<br />- Intel® HD Graphics 4600 (GT2)<br />- Intel® HD Graphics P4600 (GT2)<br />- Intel® HD Graphics P4700 (GT2)<br />- Intel® HD Graphics 5000 (GT3)<br />- Intel® Iris™ Graphics 5100 (GT3)<br />- Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (używać najnowszych sterowników)|
|AMD®|Najwięcej od amd Radeon™ hd serii 7000 (z wyłączeniem AMD Radeon™ HD 7350-7670)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ gpu i akceleratory GPU AMD FirePro z architekturą Graphics Core Next (GCN).<br /><br /> AMD® serii E i amd serii A Accelerated Processing Units (AU) z architekturą Graphics Core Next (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 lub wyższy|
|NVIDIA®|Najwięcej od nvidia® GeForce® serii 400.<br /><br /> Procesory graficzne NVIDIA® GeForce®, procesory graficzne NVIDIA Quadro® i procesory graficzne NVIDIA® Tesla™ GPU z architekturą Fermi™, Kepler™ lub Maxwell™.|343.37 lub wyższy|

 Konfiguracje wielu procesorów graficznych, takie jak NVIDIA® SLI™ i AMD Crossfire™ nie są obecnie obsługiwane. Obsługiwane są hybrydowe konfiguracje graficzne, takie jak NVIDIA® Optimus™ i AMD Enduro™.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie trudnych problemów graficznych z grą za pomocą narzędzi DirectX (wideo)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [Narzędzie do użycia procesora GPU w programie Visual Studio (wideo)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [Narzędzie do użycia gpu w programie Visual Studio 2013 Update 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [Użycie procesora GPU dla programu DirectX w programie Visual Studio (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [Widok GPU](/windows-hardware/drivers/display/using-gpuview)
- [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)