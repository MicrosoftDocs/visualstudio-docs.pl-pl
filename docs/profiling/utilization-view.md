---
title: Widok wykorzystania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 926c67261f91aa8787d9be4a33dadbd3a890c568
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62823530"
---
# <a name="utilization-view"></a>Widok wykorzystania
W **widoku Wykorzystanie** są wyświetlane informacje o procesorze CPU, procesorze GRAFICZNYm i innych zasobach systemowych, które są używane przez bieżący proces (wybierz opcję **Analizuj** > **wizualizator współbieżności,** aby uruchomić wizualizator współbieżności). Pokazuje średnie wykorzystanie rdzenia przez analizowany proces, proces bezczynny, proces systemowy i inne procesy, które są uruchomione w systemie w czasie. Nie pokazuje, który konkretny rdzeń jest aktywny w danym momencie. Na przykład jeśli dwa rdzenie są uruchomione na 50 procent pojemności dla danego okresu czasu, a następnie ten widok pokazuje jeden rdzeń logiczny są wykorzystywane. Widok jest generowany przez podzielenie czasu profilowania na krótkie segmenty czasu. Dla każdego segmentu wykres kreśli średnią liczbę wątków procesu, które są wykonywane na rdzeniach logicznych w tym przedziale.

 ![Widok wykorzystania procesora](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Wykres przedstawia czas (na osi x) i średnie rdzenie logiczne, które są wykorzystywane przez proces docelowy, proces bezczynny i proces systemowy. (Proces bezczynny pokazuje bezczynne rdzenie. Proces systemowy jest procesem w systemie Windows, który może wykonywać pracę w imieniu innych procesów.) Pozostałe procesy, które są uruchomione na koncie systemowym do wykorzystania wszystkich pozostałych rdzeni.

 Liczba rdzeni logicznych jest wyświetlana na osi y. System Windows traktuje jednoczesną obsługę wielowątkową w sprzęcie jako rdzenie logiczne (na przykład Hyper-Threading). W związku z tym system, który ma czterordzeniowy procesor, który obsługuje dwa wątki sprzętowe na rdzeń pojawia się jako system ośmiu rdzenia logicznego. Dotyczy to również widoku Rdzenie. Aby uzyskać więcej informacji, zobacz [Widok Rdzenie](../profiling/cores-view.md).

 Wykres aktywności gpu pokazuje liczbę aparatów DirectX używanych w czasie.  Aparat jest używany, jeśli przetwarza pakiet DMA.  Wykres nie pokazuje określonego aparatu DirectX (na przykład silnika 3D, aparatu wideo i innych).

## <a name="purpose"></a>Przeznaczenie
 Zaleca się widok wykorzystania jako punkt wyjścia dla badań wydajności podczas korzystania z wizualizatora współbieżności. Ponieważ zapewnia przegląd stopnia współbieżności w aplikacji w czasie, można go używać do szybkiego identyfikowania obszarów, które wymagają dostrajania wydajności lub równoległości.

 Jeśli jesteś zainteresowany dostrajaniem wydajności, możesz próbować zidentyfikować zachowanie, które nie spełnia Twoich oczekiwań. Możesz również szukać istnienia i przyczyny regionów, które mają niskie wykorzystanie logicznych rdzeni procesora. Możesz również szukać wzorców użycia między procesorem CPU a procesorem GPU.

 Jeśli jesteś zainteresowany równoległości aplikacji, prawdopodobnie szukasz albo obszarów związanych z procesorem CPU wykonania lub obszarów, w których nie są one z wykorzystaniem procesora CPU.

 Obszary związane z procesorem SĄ zielone. Wykres pokazuje jeden rdzeń jest używany, jeśli aplikacja jest szeregowa.

 Obszary, w których procesor nie korzysta z procesora, są szare. Mogą one reprezentować punkty, w których aplikacja jest bezczynna lub wykonywania blokowania we/wy, które zapewniają możliwości równoległości przez nakładanie się z innymi pracami związanymi z procesorem CPU.

 Po znalezieniu interesującego zachowania możesz powiększyć ten region, zaznaczając je. Po powiększeniu można przełączyć się do widoku wątków lub widoku rdzeni, aby uzyskać bardziej szczegółową analizę.

 Jeśli używasz gpu przy użyciu C++ AMP lub DirectX, może być zainteresowany określeniem liczby aparatów GPU w użyciu lub obszarów, w których gpu jest nieoczekiwanie bezczynny.

## <a name="zoom"></a>Zoom
 Aby powiększyć wykres wykorzystania procesora CPU lub wykres aktywności gpu, wybierz sekcję lub użyj narzędzia suwaka powiększenia nad wykresem. Ustawienie powiększenia będzie się powtarzać po przełączeniu się do innych widoków. Aby ponownie pomniejszyć widok, użyj narzędzia suwaka powiększenia. Można również powiększyć za pomocą**zwoju** **Ctrl**+.

## <a name="see-also"></a>Zobacz też
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
- [Widok rdzeni](../profiling/cores-view.md)