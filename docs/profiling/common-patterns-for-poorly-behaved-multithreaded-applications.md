---
title: Typowe wzorce dla źle zachowanych aplikacji wielowątkowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aec033266ccb2a6e6dcd0342669b7c31082488a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62788904"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych

Wizualizator współbieżności pomaga deweloperom wizualizować zachowanie aplikacji wielowątkowej. To narzędzie zawiera galerię typowych wzorców dla aplikacji wielowątkowych, które zachowują się źle. Galeria zawiera typowe i rozpoznawalne wzorce wizualne, które są udostępniane za pośrednictwem narzędzia, wraz z wyjaśnieniem zachowania, które jest reprezentowane przez każdy wzorzec, prawdopodobny wynik tego zachowania i najbardziej typowe podejście do jego rozwiązania.

## <a name="lock-contention-and-serialized-execution"></a>Rywalizacja o blokadę i seryjne wykonanie

![Rywalizacja o blokadę skutkuje seryjnym wykonaniem](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Czasami zrównoległa aplikacja uparcie nadal wykonywać szeregowo, mimo że ma kilka wątków i komputer ma wystarczającą liczbę rdzeni logicznych. Pierwszym objawem jest niska wydajność wielowątkowa, być może nawet nieco wolniejsza niż implementacja szeregowa. W widoku wątków nie widać wielu wątków działających równolegle; zamiast tego widać, że tylko jeden wątek jest wykonywany w dowolnym momencie. W tym momencie po kliknięciu segmentu synchronizacji w wątku, można zobaczyć stos wywołań dla zablokowanego wątku (blokowanie stosu wywołań) i wątku, który usunął warunek blokowania (odblokowanie stosu wywołań). Ponadto jeśli odblokowywanie stosu wywołań występuje w procesie, który analizujesz, łącznik gotowy do wątku jest wyświetlany. Od tego momentu można przejść do kodu z blokowania i odblokowywania stosów wywołań, aby zbadać przyczynę serializacji jeszcze bardziej.

Jak pokazano na poniższej ilustracji, wizualizator współbieżności może również uwidaczniać ten symptom w widoku wykorzystania procesora CPU, gdzie pomimo obecności wielu wątków, aplikacja zużywa tylko jeden rdzeń logiczny.

Aby uzyskać więcej informacji, zobacz sekcję "Start z problemem" w artykule Wydajność wątku msdn magazine [— profilowanie współbieżności rywalizacji o zasoby w programie Visual Studio 2010](https://msdn.microsoft.com/magazine/ff714587.aspx).

![Rywalizacja o blokadę](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Nierównomierny rozkład obciążenia

![Nierównomierne obciążenie pracą](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

Gdy występuje nieregularny rozkład pracy w kilku równoległych wątków w aplikacji, typowy wzorzec kroku schodów pojawia się, gdy każdy wątek kończy swoją pracę, jak pokazano na poprzedniej ilustracji. Wizualizator współbieżności najczęściej pokazuje bardzo blisko godzin rozpoczęcia dla każdego wątku równoczesnych. Jednak te wątki zazwyczaj kończą się w sposób nieregularny, a nie kończące się jednocześnie. Ten wzorzec wskazuje nieregularny rozkład pracy między grupę równoległych wątków, co może prowadzić do zmniejszenia wydajności. Najlepszym podejściem do takiego problemu jest ponowna ocena algorytmu, za pomocą którego praca została podzielona między równoległe wątki.

Jak pokazano na poniższej ilustracji, wizualizator współbieżności może również ujawnić ten objaw w widoku wykorzystania procesora CPU jako stopniowy krok w dół wykorzystania procesora CPU.

![Nierównomierne obciążenie pracą](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Nadsubskrypcji

![Nadsubskrypcji](../profiling/media/oversubscription.png "Nadsubskrypcji")

W przypadku nadsubskrypcji liczba aktywnych wątków w procesie jest większa niż liczba dostępnych rdzeni logicznych w systemie. Poprzednia ilustracja przedstawia wyniki nadsubskrypcji, ze znaczącym wywłaszczeniem pasm we wszystkich aktywnych wątkach. Ponadto legenda pokazuje duży procent czasu spędzanego w wywłaszczeniu (84 procent w tym przykładzie). Może to wskazywać, że proces prosi system o wykonanie większej liczby równoczesnych wątków niż liczba rdzeni logicznych. Może to jednak również wskazywać, że inne procesy w systemie używają zasobów, które zostały przyjęte jako dostępne dla tego procesu.

Podczas oceny tego problemu należy wziąć pod uwagę następujące kwestie:

- Ogólny system może być oversubscribed. Należy wziąć pod uwagę, że inne procesy w systemie może być wywłaszczenie wątków. Po wstrzymaniu nad segmentu wywłaszczenia w widoku wątków, etykietka narzędzia zidentyfikuje wątek i proces, który wywłaszczył wątek. Ten proces nie jest koniecznie ten, który został wykonany w ciągu całego czasu, że proces został wywłaszczony, ale zawiera wskazówkę o tym, co stworzył presję wywłaszczenia przeciwko procesowi.

- Oceń, jak proces określa odpowiednią liczbę wątków do wykonania w tej fazie pracy. Jeśli proces bezpośrednio oblicza liczbę aktywnych wątków równoległych, należy rozważyć zmodyfikowanie tego algorytmu, aby lepiej uwzględnić liczbę dostępnych rdzeni logicznych w systemie. Jeśli używasz współbieżności runtime, biblioteki równoległej zadania lub PLINQ, biblioteki te wykonują pracę obliczania liczby wątków.

## <a name="inefficient-io"></a>Nieefektywne we/wy

![Nieefektywne I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Nadużywanie lub niewłaściwe użycie we/wy jest częstą przyczyną nieefektywności w aplikacjach. Należy wziąć pod uwagę poprzednią ilustrację. Profil widocznej osi czasu pokazuje, że 44 procent czasu widocznego wątku jest zużywane przez we/wy. Oś czasu pokazuje duże ilości we/wy, co oznacza, że profilowana aplikacja jest często blokowana przez we/wy. Aby wyświetlić szczegółowe informacje o rodzajach we/wy i miejscu blokowania programu, powiększ problematyczne regiony, sprawdź profil widocznej osi czasu, a następnie kliknij określony blok we/wy, aby wyświetlić bieżące stosy wywołań.

## <a name="lock-convoys"></a>Zablokuj konwoje

![Zablokuj konwoje](../profiling/media/lock_convoys.png "Lock_Convoys")

Konwoje blokady występują, gdy aplikacja nabywa blokady w pierwszym, pierwszym zamówieniu, a szybkość przybycia przy blokadzie jest wyższa niż wskaźnik nabycia. Kombinacja tych dwóch warunków powoduje, że żądania blokady, aby rozpocząć wykonywanie kopii zapasowej. Jednym ze sposobów walki z tym problemem jest użycie "nieuczciwych" zamków lub blokad, które dają dostęp do pierwszego wątku, aby znaleźć je w odblokowanych stanach. Na poprzedniej ilustracji przedstawiono to zachowanie konwoju. Aby rozwiązać ten problem, spróbuj zmniejszyć rywalizację dla obiektów synchronizacji i spróbuj użyć nieuczciwych blokad.

## <a name="see-also"></a>Zobacz też

[Widok wątków](../profiling/threads-view-parallel-performance.md)