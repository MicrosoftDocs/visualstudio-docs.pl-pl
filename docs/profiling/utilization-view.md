---
title: Widok wykorzystania | Microsoft Docs
description: Dowiedz się, że widok użycie wyświetla informacje dotyczące procesora CPU, procesora GPU i innych zasobów systemowych, które są używane przez bieżący proces.
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
ms.openlocfilehash: 047c9ef9d5bb03546eb88372ae43a51c7c8e4d32
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723208"
---
# <a name="utilization-view"></a>Widok wykorzystania
**Widok wykorzystania** zawiera informacje dotyczące procesora CPU, procesora GPU i innych zasobów systemowych, które są używane przez bieżący proces (wybierz pozycję **Analizuj**  >  **Wizualizator współbieżności** , aby uruchomić Wizualizator współbieżności). Pokazuje średnie wykorzystanie rdzenia przez przeanalizowany proces, proces bezczynny, proces systemowy i inne procesy, które są uruchamiane w systemie w miarę upływu czasu. Nie wskazuje, który konkretny rdzeń jest aktywny w danym momencie. Na przykład, jeśli dwa rdzenie są uruchamiane o 50 procent pojemności w danym okresie, ten widok pokazuje jeden rdzeń logiczny, który jest używany. Widok jest generowany przez podzielenie czasu profilowania na krótkie segmenty czasu. Dla każdego segmentu wykres przedstawia średnią liczbę wątków procesów, które są wykonywane w przypadku rdzeni logicznych w tym interwale.

 ![Widok wykorzystania procesora CPU](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 Wykres przedstawia czas (na osi x) i średnie rdzenie logiczne, które są wykorzystywane przez proces docelowy, proces bezczynności i proces systemowy. (Bezczynny proces pokazuje rdzenie bezczynne. Proces systemowy to proces w systemie Windows, który może działać w imieniu innych procesów. Pozostałe procesy, które są uruchomione na koncie systemowym w celu wykorzystania wszystkich pozostałych rdzeni.

 Liczba rdzeni logicznych jest pokazywana na osi y. System Windows traktuje równoczesną obsługę wielowątkowości w sprzęcie jako rdzenie logiczne (na przykład funkcja Hyper-Threading). W związku z tym system z procesorem Quad-Core, który obsługuje dwa wątki sprzętowe na rdzeń, pojawia się jako system ośmiu rdzeni. Dotyczy to również widoku rdzeni. Aby uzyskać więcej informacji, zobacz [Widok rdzeni](../profiling/cores-view.md).

 Wykres aktywności procesora GPU przedstawia liczbę aparatów DirectX używanych w czasie.  Aparat jest używany, jeśli przetwarza pakiet DMA.  Na wykresie nie jest wyświetlany konkretny aparat DirectX (na przykład aparat 3W, aparat wideo i inne).

## <a name="purpose"></a>Przeznaczenie
 Jeśli używasz wizualizatora współbieżności, zalecamy widok wykorzystania jako punkt wyjścia dla badań wydajności. Ponieważ zawiera przegląd stopnia współbieżności aplikacji z upływem czasu, można użyć go do szybkiego zidentyfikowania obszarów wymagających dostrajania wydajności lub przetwarzanie równoległe.

 Jeśli interesuje Cię dostrajanie wydajności, możesz spróbować zidentyfikować zachowanie, które nie spełnia oczekiwań. Możesz również wyszukać istnienie i przyczynę regionów, które mają niskie wykorzystanie logicznych rdzeni procesora CPU. Możesz również wyszukać wzorce użycia między procesorem CPU i procesorem GPU.

 Jeśli interesuje Cię przekształcają aplikację, prawdopodobnie szukasz obszarów związanych z procesorem CPU lub obszarów, w których nie korzystasz z procesora.

 Obszary powiązane z PROCESORem są zielone. Na wykresie jest wyświetlany jeden rdzeń, który jest używany, jeśli aplikacja jest serializowana.

 Obszary, w których nie korzystasz z procesora CPU, są szare. Mogą one reprezentować punkty, w których aplikacja jest bezczynna lub blokująca operację we/wy, która zapewnia możliwości równoległości przez nakładanie się na inne prace powiązane z PROCESORem.

 Po znalezieniu zachowania zainteresowania możesz powiększyć ten region, zaznaczając go. Po powiększeniu, możesz przełączyć się do widoku wątki lub widoku rdzenie w celu uzyskania bardziej szczegółowej analizy.

 Jeśli używasz procesora GPU przy użyciu C++ AMP lub DirectX, możesz chcieć zidentyfikować liczbę używanych aparatów GPU lub obszary, w których procesor GPU jest nieoczekiwanie bezczynny.

## <a name="zoom"></a>Zoom
 Aby powiększyć wykres użycia procesora CPU lub wykres aktywności procesora GPU, wybierz sekcję lub użyj suwaka powiększenia powyżej wykresu. Ustawienie powiększenia utrzymuje się w trakcie przełączania do innych widoków. Aby ponownie pomniejszyć, użyj suwaka powiększenia. Możesz również powiększać, używając **klawisza Ctrl** + **Scroll**.

## <a name="see-also"></a>Zobacz także
- [Concurrency Visualizer](../profiling/concurrency-visualizer.md)
- [Widok rdzeni](../profiling/cores-view.md)