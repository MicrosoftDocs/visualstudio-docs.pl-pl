---
title: Zarządzanie kanałami | Microsoft Docs
description: Dowiedz się, w jaki sposób można organizować kanały dla procesu, aby można było sprawdzić określone wzorce w widoku wątki w wizualizatorze współbieżności.
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
ms.openlocfilehash: b0dd8643f63a7a3e67400f09f00b999fff33f09e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721271"
---
# <a name="manage-channels"></a>Zarządzanie kanałami
W **widoku wątki** w wizualizatorze współbieżności można organizować kanały dla procesu, aby umożliwić badanie określonych wzorców. Można sortować kanały, przenosić je w górę i w dół, a także ukrywać lub wyświetlać je.

## <a name="sort-by"></a>Sortuj według
 Można użyć Sortuj według kontrolki, aby posortować wątki według różnych kryteriów na podstawie bieżącego poziomu powiększenia. Jest to szczególnie przydatne w przypadku szukania określonego wzorca. Można sortować według kryteriów:

|Kryteria|Definicja|
|--------------|----------------|
|Godzina rozpoczęcia|Sortuje wątki według ich godzin rozpoczęcia. Jest to domyślna kolejność sortowania.|
|Czas zakończenia|Sortuje wątki według ich czasów zakończenia.|
|Wykonanie|Sortuje wątki według wartości procentowej czasu spędzonego na wykonywaniu.|
|Synchronizacja|Sortuje wątki według procentu czasu poświęcanego na synchronizację.|
|WE/WY|Sortuje wątki według wartości procentowej czasu spędzonego we/wy (odczytywanie i zapisywanie danych).|
|Uśpij|Sortuje wątki według wartości procentowej czasu spędzonego w stanie uśpienia.|
|Stronicowanie|Sortuje wątki według wartości procentowej czasu spędzonego w stronicowaniu.|
|Wywłaszczania|Sortuje wątki według wartości procentowej czasu poświęcanego na przepełnienie.|
|Przetwarzanie interfejsu użytkownika|Sortuje wątki według wartości procentowej czasu spędzonego w przetwarzaniu interfejsu użytkownika.|

## <a name="move-selected-channel-up-or-down"></a>Przenieś wybrany kanał w górę lub w dół
 Za pomocą tych formantów można przenieść kanał w górę lub w dół na liście. Na przykład można umieścić powiązane kanały obok siebie, aby ułatwić badanie określonego wzorca lub relacji między wątkami.

## <a name="move-selected-channel-to-top-or-bottom"></a>Przenieś wybrany kanał do góry lub do dołu
 Możesz przenieść wybrane kanały do góry lub u dołu listy, aby można było sprawdzić konkretny wzorzec lub przenieść niektóre kanały z metody podczas badania innych.

## <a name="hide-selected-channels"></a>Ukryj wybrane kanały
 Wybierz tę kontrolkę, jeśli chcesz ukryć kanały. Na przykład jeśli wątek jest 100 procent synchronizacji w okresie istnienia zarządzanego procesu, można go ukryć podczas analizowania innych wątków.

> [!NOTE]
> Ukrycie wątku powoduje również usunięcie go z czasu obliczeń, który jest wyświetlany w aktywnej legendzie i w raportach profilów.

## <a name="show-all-channels"></a>Pokaż wszystkie kanały
 Ten formant jest aktywny, gdy co najmniej jeden kanał jest ukryty. W przypadku wybrania tej opcji wszystkie ukryte elementy zostaną wyświetlone i zostaną zwrócone do obliczeń czasu.

## <a name="move-markers-to-top"></a>Przesuń znaczniki na początek
 Jeśli ślad zawiera zdarzenia znacznika, można użyć tego polecenia do przenoszenia kanałów znacznika w górę osi czasu. Ich kolejność względna jest zachowywana.

## <a name="group-markers-by-thread"></a>Grupuj znaczniki według wątku
 Jeśli ślad zawiera zdarzenia znacznika, można użyć tego polecenia do grupowania kanałów znacznika w wątku, który wygenerował zdarzenia znacznika.  Kanały dysku są przenoszone na górę listy kanałów, a kanały GPU są przenoszone na dół.

## <a name="see-also"></a>Zobacz także
- [Kontrolka powiększenia (Widok wątków)](../profiling/zoom-control-threads-view.md)
- [Włącz/Wyłącz tryb miary](../profiling/measure-mode-on-off.md)
- [Widok wątków](../profiling/threads-view-parallel-performance.md)