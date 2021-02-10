---
title: Typowe wzorce dla źle działających aplikacji wielowątkowych
description: Wizualizator współbieżności dostarcza wykresy dla aplikacji wielowątkowych i galerię popularnych wzorców niewłaściwie zachowywać się.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fc83fd49184a0bb784b44ec80588571e8d6e560
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941323"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Typowe nieprawidłowo działające wzorce dla aplikacji wielowątkowych

Narzędzie Concurrency Visualizer pomaga deweloperom wizualizować zachowanie aplikacji wielowątkowej. To narzędzie zawiera galerię popularnych wzorców dla aplikacji wielowątkowych, które zachowują się nieprawidłowo. Galeria zawiera typowe i rozpoznawalne wzorce wizualne, które są udostępniane za pomocą narzędzia, wraz z wyjaśnieniem zachowania, które jest reprezentowane przez każdy z wzorców, prawdopodobnie tym zachowaniem i najbardziej typowym podejściem do jego rozwiązania.

## <a name="lock-contention-and-serialized-execution"></a>Zablokuj rywalizację i wykonywanie serializowane

![Zablokuj rywalizację z powodu serializowanego wykonania](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Czasami równoległe aplikacje stubbornly nadal są wykonywane szeregowo nawet wtedy, gdy ma kilka wątków, a komputer ma wystarczającą liczbę rdzeni logicznych. Pierwszy objaw ma niską wydajność wielowątkową, a nawet nieco mniejszą niż implementacja szeregowa. W widoku wątki nie widzisz równolegle wielu wątków. Zamiast tego zobaczysz, że w dowolnym momencie wykonujesz tylko jeden wątek. Jeśli w tym momencie klikniesz segment synchronizacji w wątku, zobaczysz stos wywołań dla zablokowanego wątku (blokujący stos wywołań) i wątek, który usunął warunek blokowania (odblokowywanie stosu wywołań). Ponadto, jeśli stos wywołań odblokowywania występuje w procesie analizowanym, zostanie wyświetlony łącznik Thread-Ready. Od tego momentu można nawigować do kodu z stosów wywołań blokujących i odblokowywania, aby badać przyczynę serializacji jeszcze więcej.

Jak pokazano na poniższej ilustracji, Wizualizator współbieżności może również uwidocznić ten objaw w widoku wykorzystania procesora CPU, gdzie mimo obecności wielu wątków aplikacja korzysta tylko z jednego rdzenia logicznego.

Aby uzyskać więcej informacji, zobacz sekcję "Rozpoczynanie pracy z sekcją problemu" w artykule dotyczącym wątków w witrynie MSDN Magazine [— profilowanie współbieżności rywalizacji o zasoby w programie Visual Studio 2010](/archive/msdn-magazine/2010/june/msdn-magazine-thread-performance-resource-contention-concurrency-profiling-in-visual-studio-2010).

![Zablokuj rywalizację](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Nierównomierny rozkład obciążenia

![Zrzut ekranu przedstawiający wykres obciążenia dla wątków równoległych w wizualizatorze współbieżności. Wątki kończą się w różnym czasie, pokazując wzorzec etapu schodów.](../profiling/media/unevenworkload_1.png)

Gdy nieregularna dystrybucja pracy odbywa się w kilku wątkach równoległych w aplikacji, typowy wzorzec etapu schodów pojawia się, gdy każdy wątek ukończy swoją pracę, jak pokazano na poprzedniej ilustracji. Wizualizator współbieżności najczęściej pokazuje godziny rozpoczęcia dla każdego współbieżnego wątku. Jednak te wątki zazwyczaj kończą się nieregularnym sposobem, a nie kończąc jednocześnie. Ten wzorzec wskazuje nieregularną dystrybucję pracy między grupą wątków równoległych, co może prowadzić do zmniejszenia wydajności. Najlepszym podejściem do takiego problemu jest przeszacowanie algorytmu, za pomocą którego działa podzielona między wątki równoległe.

Jak pokazano na poniższej ilustracji, Wizualizator współbieżności może również uwidocznić ten objaw w widoku wykorzystania procesora CPU jako stopniowy krok w mocy procesora CPU.

![Zrzut ekranu przedstawiający widok użycie procesora CPU w wizualizatorze współbieżności pokazujący wzorzec etapu schodów na końcu wykresu użycia procesora.](../profiling/media/unevenworkload_2.png)

## <a name="oversubscription"></a>Nadsubskrypcji

![Zrzut ekranu przedstawiający wykres obciążenia dla wszystkich aktywnych wątków w wizualizatorze współbieżności. Legenda przedstawia ilość czasu spędzonego na wykonywaniu i zastępująniu.](../profiling/media/oversubscription.png)

W przypadku nadsubskrypcji liczba aktywnych wątków w procesie jest większa niż liczba dostępnych rdzeni logicznych w systemie. Poprzednia ilustracja przedstawia wyniki nadsubskrypcji, dzięki czemu można przewyższyć liczbę przedziałów na wszystkie aktywne wątki. Ponadto legenda pokazuje znaczną część czasu poświęcaną na przepełnienie (84 procent w tym przykładzie). Może to wskazywać, że proces żąda od systemu wykonania większej liczby współbieżnych wątków niż liczba rdzeni logicznych. Może to jednak wskazywać, że inne procesy w systemie korzystają z zasobów, które zostały założono, że są dostępne dla tego procesu.

Podczas szacowania tego problemu należy wziąć pod uwagę następujące kwestie:

- Ogólny system może być niesubskrybowany. Należy wziąć pod uwagę, że inne procesy w systemie mogą zastępują wątki. Gdy wstrzymasz od segmentu przejęcia w widoku wątki, etykietka narzędzia zidentyfikuje wątek i proces, który przejdzieł wątek. Ten proces nie jest konieczny, który jest wykonywany w całym czasie, gdy proces został przemieszczony, ale udostępnia wskazówkę na temat tego, co spowodowało wyznaczenie zastępujące względem procesu.

- Oceń, w jaki sposób proces określa odpowiednią liczbę wątków do wykonania w tej fazie pracy. Jeśli proces bezpośrednio oblicza liczbę aktywnych wątków równoległych, warto zmodyfikować ten algorytm, aby lepiej uwzględnić liczbę dostępnych rdzeni logicznych w systemie. Jeśli używasz środowisko uruchomieniowe współbieżności, biblioteki zadań równoległych lub PLINQ, te biblioteki wykonują zadania obliczania liczby wątków.

## <a name="inefficient-io"></a>Niewydajne we/wy

![Niewydajne I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Nadmierne lub nieprawidłowe użycie operacji we/wy jest typową przyczyną nieefektywności aplikacji. Weź pod uwagę poprzednią ilustrację. Profil widocznej osi czasu pokazuje, że 44 procent widocznego czasu wątku jest zużywany przez we/wy. Oś czasu pokazuje duże ilości operacji we/wy, co oznacza, że profilowana aplikacja jest często blokowana przez we/wy. Aby wyświetlić szczegóły dotyczące rodzaju operacji we/wy i miejsce, w którym program jest zablokowany, powiększyć problematyczne regiony, sprawdź widoczny profil osi czasu, a następnie kliknij konkretny blok we/wy, aby zobaczyć bieżące stosy wywołań.

## <a name="lock-convoys"></a>Zablokuj convoys

![Zablokuj convoys](../profiling/media/lock_convoys.png "Lock_Convoys")

Zablokuj convoys występuje, gdy aplikacja uzyskuje blokady w pierwszej, obsługiwanej kolejności, a szybkość przybycia dla blokady jest wyższa niż szybkość pozyskiwania. Kombinacja tych dwóch warunków powoduje, że żądania zablokowania zaczynają tworzyć kopie zapasowe. Jednym ze sposobów zwalczenia tego problemu jest użycie blokad nieuczciwych lub blokad, które zapewniają dostęp do pierwszego wątku, aby znaleźć je w Stanach odblokowane. Na poprzedniej ilustracji przedstawiono zachowanie konwoju. Aby rozwiązać ten problem, spróbuj zmniejszyć rywalizację dla obiektów synchronizacji i spróbuj użyć nieuczciwych blokad.

## <a name="see-also"></a>Zobacz też

[Widok wątków](../profiling/threads-view-parallel-performance.md)