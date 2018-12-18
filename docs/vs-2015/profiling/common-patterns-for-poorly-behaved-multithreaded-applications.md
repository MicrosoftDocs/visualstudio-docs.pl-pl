---
title: Wspólne wzorce dla nieprawidłowo działających aplikacji wielowątkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
ms.assetid: 00d10629-e20f-4d6d-8643-c59a3879812e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e0dfcb9408c67acc754f687903b4be2d13f9ff4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755819"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie Concurrency Visualizer pomaga deweloperom do wizualizacji zachowania aplikacji wielowątkowych. To narzędzie zawiera galerię wspólne wzorce dla aplikacji wielowątkowych, które zachowują się nieprawidłowo w inny sposób. Galeria zawiera typowe i rozpoznawalny visual wzorców, które są udostępniane za pośrednictwem narzędzia, wraz z wyjaśnieniem zachowanie, który jest reprezentowany przez każdy wzorzec prawdopodobnie wynik tego zachowania i najbardziej typowym podejściem go rozwiązać.  
  
## <a name="lock-contention-and-serialized-execution"></a>Rywalizacja o blokady i wykonywanie serializacji  
 ![Blokowanie rywalizacji skutkuje wykonywania serializacji](../profiling/media/lockcontention-serialized.png "LockContention_Serialized")  
  
 Czasami aplikacja równoległego stubbornly nadal wykonywane szeregowo, nawet jeśli ma on wiele wątków i komputer ma wystarczającej liczby rdzeni logicznych. Pierwszy symptomem jest niską wydajnością wielowątkowych, wręcz Fatalne nieco wolniej niż serial implementacji. W widoku wątków nie ma wiele wątków, uruchamianych równolegle; Zamiast tego zostanie wyświetlony tylko jeden wątek wykonuje w dowolnym momencie. W tym momencie Jeśli klikniesz pozycję segment synchronizacji w wątku, zostanie wyświetlony stos wywołań zablokowanych wątków (blokujący stos wywołań) i wątku, który usunięte blokowania warunek (stos wywołań odblokowania). Ponadto jeśli stos wywołań odblokowania wystąpi proces analizowania, łącznik gotowości wątku jest wyświetlany. Od tego momentu możesz przejść do kodu za pomocą stosów wywołań blokowania i odblokowywania, aby zbadać przyczynę serializacji jeszcze więcej.  
  
 Jak pokazano na poniższej ilustracji, Concurrency Visualizer również może narazić ten symptom w widoku wykorzystania procesora CPU, where, niezależnie od obecności wielu wątków, aplikacja używa tylko jednego rdzenia logicznego.  
  
 Aby uzyskać więcej informacji, zobacz "Wydajność wzorzec 1: Identyfikowanie Rywalizacja o blokady" w Hazim Shafi [równoległej wydajności Tools For Windows](http://go.microsoft.com/fwlink/?LinkID=160569) blogu w witrynie sieci Web blog MSDN.  
  
 ![Rywalizacja o blokady](../profiling/media/lockcontention-2.png "LockContention_2")  
  
## <a name="uneven-workload-distribution"></a>Rozkład normalny obciążenia  
 ![Nierównomiernego obciążenia](../profiling/media/unevenworkload-1.png "UnevenWorkLoad_1")  
  
 W przypadku nieregularne rozkład pracy między wiele równoległych wątków w aplikacji, wzorzec typowe schodki pojawia się zgodnie z każdego wątku ukończy pracę, jak pokazano na poprzedniej ilustracji. Narzędzie Concurrency Visualizer zawiera w większości przypadków godziny rozpoczęcia ścisłe dla każdego wątku współbieżnych. Jednak te wątki zazwyczaj kończy się w sposób nieprawidłowy zamiast końcowy jednocześnie. Ten wzorzec wskazuje nieregularne rozkład pracy między grupą równoległych wątków, które może spowodować obniżenie wydajności. Najlepszym podejściem do takiego problemu jest to ponowne ocenienie algorytm, za pomocą którego został podzielony między równoległych wątków roboczych.  
  
 Jak pokazano na poniższej ilustracji, Concurrency Visualizer również może narazić ten symptom w widok wykorzystania CPU jako step-down stopniowy wzrost użycia procesora CPU.  
  
 ![Nierównomiernego obciążenia](../profiling/media/unevenworkload-2.png "UnevenWorkload_2")  
  
## <a name="oversubscription"></a>Nadsubskrypcja  
 ![Nadsubskrypcja](../profiling/media/oversubscription.png "Nadsubskrypcji")  
  
 W przypadku nadsubskrypcji liczba aktywnych wątków w procesie jest większa niż liczba dostępnych rdzeni logicznych w systemie. Na poprzedniej ilustracji przedstawiono wyniki nadsubskrypcji z znaczne wywłaszczania pominiętym w wszystkich aktywnych wątków. Ponadto legendy pokazuje, że znaczną część czasu działania jest Wywłaszczania (procent 84 w tym przykładzie). Może to oznaczać, że proces jest zapytaniem systemu na potrzeby wykonywania większą liczbę jednoczesnych wątków niż liczba rdzeni logicznych. Jednak może to również wskazywać innych procesów w systemie korzystania zasoby, które zostały zakłada, że mają być dostępne dla tego procesu.  
  
 Podczas oceny tego problemu, należy wziąć pod uwagę następujące czynności:  
  
-   Może być oversubscribed całego systemu. Należy wziąć pod uwagę, że inne procesy w systemie może wywłaszczanie wątki. W przypadku wstrzymania przez segment wywłaszczania w widoku wątków etykietka narzędzia będzie identyfikować wątku i procesu, który wątek przerywane. Ten proces niekoniecznie jest ten, który jest wykonywany podczas procesu została przeniesiona przez cały czas, ale stanowi wskazówkę o tym, co tworzone wykorzystanie wywłaszczania względem procesu.  
  
-   Należy ocenić, jak proces określa odpowiedniej liczby wątków do wykonania w tej fazie pracy. Jeśli proces bezpośrednio oblicza liczbę aktywnych wątków równoległych, należy rozważyć zmodyfikowanie tego algorytmu do lepszego konta liczbę dostępnych rdzeni logicznych w systemie. Jeśli używasz środowiska uruchomieniowego współbieżności, biblioteka zadań równoległych lub PLINQ tych bibliotek wykonywania pracy obliczającej liczbę wątków.  
  
## <a name="inefficient-io"></a>Nieefektywne operacji We/Wy  
 ![Inefficient I&#47;O](../profiling/media/inefficient-io.png "Inefficient_IO")  
  
 Nadmierne zużycie lub ich nieuprawnione użycie operacji We/Wy jest typową przyczyną nieefektywności w aplikacjach. Należy wziąć pod uwagę poprzedniej ilustracji. Profil widocznej osi czasu pokazuje, że 42 procent czasu widoczny wątku jest wykorzystywana przez operacje We/Wy. Oś czasu zawiera dużą ilością operacji We/Wy, co oznacza, że profilowanej aplikacji często jest zablokowany przez operacje We/Wy. Aby wyświetlić szczegółowe informacje o rodzajach operacji We/Wy i gdy program jest zablokowany, powiększenie problematyczne regionów, sprawdź profil widocznej osi czasu, a następnie kliknij określonego bloku operacji We/Wy, aby wyświetlić stosy wywołań bieżącego.  
  
## <a name="lock-convoys"></a>Konwojów blokady  
 ![Blokowanie konwojów](../profiling/media/lock-convoys.png "Lock_Convoys")  
  
 Konwojów blokady występują, gdy aplikacja uzyskuje blokady w kto, obsługiwane w pierwszej kolejności, a kiedy wskaźnik przybycia na blokady jest wyższy niż szybkości pozyskiwania. Kombinacja tych dwóch warunków powoduje, że żądania na blokadę rozpocząć tworzenie kopii zapasowej. Jednym ze sposobów, aby walczyć z tego problemu jest użycie "nieuczciwych" blokady lub blokad, które zapewniają dostęp do pierwszego wątku, aby je znaleźć w Stanach odblokowane. Na poprzedniej ilustracji przedstawiono to zachowanie konwoju. Aby rozwiązać ten problem, spróbuj zmniejszyć rywalizację dla obiektów synchronizacji, a następnie spróbuj użyć nieuczciwych blokad.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



