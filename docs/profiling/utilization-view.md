---
title: Widok wykorzystania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70e6fd49e72b3cb6ffdb1ade70dcd1ffb562bdd9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824214"
---
# <a name="utilization-view"></a>Widok wykorzystania
**Widok wykorzystania** Wyświetla informacje o procesorze CPU, procesora GPU i innych zasobów systemowych, które są używane przez bieżący proces (wybierz **analizy** > **współbieżności Wizualizator** można uruchomić narzędzie concurrency visualizer). Pokazuje średnie wykorzystanie przez proces analizy, proces bezczynny, proces systemowy i inne procesy, które są uruchomione w systemie, wraz z upływem czasu. Nie pokazuje, które określonych core jest aktywny w dowolnym momencie. Na przykład jeśli każdy dwa rdzenie są uruchamiane o pojemności 50 procent w określonym czasie, ten widok przedstawia jednego rdzenia logicznego wykorzystywane. Widok jest generowany przez podzielenie podczas profilowania na segmenty krótki czas. Dla każdego segmentu wykres, które to średnia liczba wątków procesów, które są wykonywane na rdzenie logiczne, w tym przedziale.  
  
 ![Widok wykorzystania CPU](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 Na wykresie widać, czas (na osi x) i średni rdzenie logiczne, które są wykorzystywane przez proces docelowy, proces bezczynności i proces systemowy. (Proces bezczynny pokazuje bezczynnych rdzeni. Proces systemowy jest procesem w Windows, które może wykonywać pracę w imieniu innych procesów). Pozostałe procesy, które są uruchomione na koncie systemu w celu wykorzystania pozostałe rdzenie.  
  
 Liczba rdzeni logicznych jest wyświetlane na osi y. Windows traktuje jednoczesnych Obsługa wielowątkowości w sprzęcie jako rdzenie logiczne (na przykład funkcji Hyper-Threading). W związku z tym systemie, w którym obsługującej dwóch wątków sprzętu na każdy rdzeń procesora czterordzeniowe pojawia się jako system 8 logiczne core. Dotyczy to również widoku rdzeni. Aby uzyskać więcej informacji, zobacz [rdzeni widoku](../profiling/cores-view.md).  
  
 Wykres aktywności procesora GPU pokazuje liczbę aparatów DirectX używana wraz z upływem czasu.  Aparat jest używana w przypadku przetwarzania pakietu DMA.  Wykres nie pokazuje konkretnego aparatu programu DirectX (na przykład aparatu 3D, aparat wideo i inne).  
  
## <a name="purpose"></a>Cel  
 Firma Microsoft zaleca widok wykorzystania jako punktu wyjścia do badania wydajności, korzystając z narzędzia Concurrency Visualizer. Ponieważ zapewnia przegląd stopień współbieżności w aplikacji wraz z upływem czasu, można użyć go do szybkie identyfikowanie obszarów, które wymagają dostrajanie wydajności lub przetwarzania równoległego.  
  
 Jeśli interesuje Cię dostrajania wydajności, może podjąć próbę do identyfikowania zachowanie, które nie spełniają Twoich oczekiwań. Możesz również będą szukać istnienie i przyczyny, regionów, które mają niewielkie wykorzystanie logiczne rdzeni procesora CPU. Możesz również poszukać wzorce użycia między GPU i CPU.  
  
 Jeśli interesuje Cię przekształcają aplikacji, prawdopodobnie potrzebujesz albo obszary zależne od Procesora CPU, wykonania lub obszary, w którym nie są używane procesora CPU.  
  
 Obszary zależne od Procesora CPU są zielone. Na wykresie widać jednego rdzenia wykorzystywane, jeśli aplikacja jest szeregowe.  
  
 Obszary, w którym nie są używane procesora CPU są szare. One może reprezentować punkty, w których aplikacja jest w stanie bezczynności lub wykonywania blokowania We/Wy, zapewniające możliwości równoległości przy nakładających się przy użyciu innych zadań intensywnie angażujących Procesor.  
  
 Po znalezieniu zachowanie interesujące, można powiększyć w danym regionie, wybierając ją. Po przejściu, można przełączać się do widoku wątków lub widok rdzeni, aby uzyskać bardziej szczegółową analizę.  
  
 Jeśli używasz procesora GPU przy użyciu języka C++ AMP lub technologii DirectX, może być zainteresowany identyfikowanie Liczba aparatów procesora GPU w użyciu lub obszary, w którym procesor GPU jest nieoczekiwanie bezczynności.  
  
## <a name="zoom"></a>Powiększenie  
 Aby powiększyć wykres wykorzystania procesora CPU lub wykres aktywności procesora GPU, wybierz sekcję lub narzędzie do suwak powiększania powyżej wykresu. Ustawienie powiększenia będzie się powtarzać, jak przełączyć się z innymi widokami. Aby zmniejszyć ponownie, należy użyć narzędzia suwak powiększenia. Możesz także powiększać przy użyciu **Ctrl**+**przewijania**.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok rdzeni](../profiling/cores-view.md)