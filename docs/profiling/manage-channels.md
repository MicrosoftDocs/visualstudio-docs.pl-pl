---
title: Zarządzanie kanałami | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1480bab2f52383a8ca3a5b0ac22fd56acb5e01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "64779244"
---
# <a name="manage-channels"></a>Zarządzanie kanałami
W **widoku wątków** w wizualizatorze współbieżności można zorganizować kanały dla procesu, dzięki czemu można zbadać określone wzorce. Możesz sortować kanały, przesuwać je w górę i w dół oraz ukrywać lub pokazywać.

## <a name="sort-by"></a>Sortuj według
 Za pomocą formantu Sortuj według można sortować wątki według różnych kryteriów na podstawie bieżącego poziomu powiększenia. Jest to szczególnie przydatne, gdy szukasz konkretnego wzorca. Można sortować według następujących kryteriów:

|Kryteria|Definicja|
|--------------|----------------|
|Godzina rozpoczęcia|Sortuje wątki według ich czasów rozpoczęcia. Jest to domyślna kolejność sortowania.|
|Godzina zakończenia|Sortuje wątki według ich czasów zakończenia.|
|Wykonanie|Sortuje wątki według procentu czasu spędzonego w wykonaniu.|
|Synchronizacja|Sortuje wątki według procentu czasu spędzonego w synchronizacji.|
|WE/WY|Sortuje wątki według procentu czasu spędzonego w we/wy (odczytywanie i zapisywanie danych).|
|Uśpij|Sortuje wątki według procentu czasu spędzonego we śnie.|
|Stronicowanie|Sortuje wątki według procentu czasu spędzonego na stronicowaniu.|
|Wywłaszczanie|Sortuje wątki według procentu czasu spędzonego w wywłaszczenia.|
|Przetwarzanie interfejsu użytkownika|Sortuje wątki według procentu czasu spędzonego w przetwarzaniu interfejsu użytkownika.|

## <a name="move-selected-channel-up-or-down"></a>Przenoszenie zaznaczonego kanału w górę lub w dół
 Za pomocą tych kontrolek można przenieść kanał w górę lub w dół listy. Na przykład można umieścić powiązane kanały obok siebie, aby ułatwić badanie określonego wzorca lub relacji między wątkami.

## <a name="move-selected-channel-to-top-or-bottom"></a>Przenoszenie zaznaczonego kanału na górę lub na dół
 Można przenieść wybrane kanały na górę lub u dołu listy, aby zbadać określony wzorzec lub przenieść niektóre kanały z drogi podczas badania innych.

## <a name="hide-selected-channels"></a>Ukrywanie zaznaczonych kanałów
 Wybierz tę kontrolę, jeśli chcesz ukryć kanały. Na przykład jeśli wątek jest 100 procent synchronizacji dla żywotności zarządzanego procesu, można go ukryć podczas analizowania innych wątków.

> [!NOTE]
> Ukrywanie wątku usuwa go również z czasu obliczania, który jest wyświetlany w aktywnej legendzie i w raportach profilu.

## <a name="show-all-channels"></a>Pokaż wszystkie kanały
 Ten formant jest aktywny, gdy jeden lub więcej kanałów są ukryte. Jeśli wybierzesz go, wszystkie ukryte elementy są wyświetlane i są zwracane do obliczeń czasu.

## <a name="move-markers-to-top"></a>Przenoszenie znaczników do góry
 Jeśli śledzenie zawiera zdarzenia znacznika, można użyć tego polecenia, aby przenieść kanały znaczników na górę osi czasu. Ich względna kolejność jest zachowywana.

## <a name="group-markers-by-thread"></a>Grupowanie znaczników według wątku
 Jeśli śledzenie zawiera zdarzenia znacznika, można użyć tego polecenia do grupowania kanałów znaczników pod wątkiem, który wygenerował zdarzenia znacznika.  Kanały dysków zostaną przeniesione na górę listy kanałów, a kanały GPU zostaną przeniesione na dół.

## <a name="see-also"></a>Zobacz też
- [Kontrolka powiększenia (widok wątków)](../profiling/zoom-control-threads-view.md)
- [Tryb pomiaru włączania/wyłączania](../profiling/measure-mode-on-off.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)