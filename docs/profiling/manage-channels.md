---
title: Zarządzanie kanałami | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 535b11f4ee27bd30301b983b34075a3d70947162
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853369"
---
# <a name="manage-channels"></a>Zarządzanie kanałami
W **Widok wątków** w Wizualizatorze współbieżności można organizować kanały dla procesu, dzięki czemu można sprawdzić określonego wzorców. Można sortować kanały, przenieś je w górę i w dół i ukryć lub pokazać je.  
  
## <a name="sort-by"></a>Sortuj według  
 Kontrolka Sortuj według umożliwia sortowanie wątki według różnych kryteriów, w oparciu o bieżący poziom powiększenia. Jest to szczególnie przydatne w przypadku, gdy potrzebujesz określonego wzorca. Można sortować według tych kryteriów:  
  
|Kryteria|Definicja|  
|--------------|----------------|  
|Godzina rozpoczęcia|Sortuje wątki według ich godziny rozpoczęcia. Jest to domyślny porządek sortowania.|  
|Godzina zakończenia|Sortuje wątki według ich zakończenia.|  
|Wykonanie|Sortuje wątki według wartości procentowej czasu spędzonego na wykonanie.|  
|Synchronizacja|Sortuje wątki według wartości procentowej czasu spędzonego w synchronizacji.|  
|WE/WY|Sortuje wątki według wartości procentowej czasu spędzonego w operacji We/Wy (odczytywania i zapisywania danych).|  
|Stan uśpienia|Sortuje wątki według wartości procentowej czasu spędzonego w trybie uśpienia.|  
|Stronicowania|Sortuje wątki według wartości procentowej czasu spędzonego w stronicowania.|  
|Wywłaszczania|Sortuje wątki według wartości procentowej czasu spędzonego w wywłaszczania.|  
|Przetwarzanie interfejsu użytkownika|Sortuje wątki według wartości procentowej czasu spędzonego w przetwarzania interfejsu użytkownika.|  
  
## <a name="move-selected-channel-up-or-down"></a>Przenieś wybrany kanał w górę lub w dół  
 Te kontrolki umożliwia przenoszenie kanał w górę lub w dół na liście. Można na przykład umieść powiązane kanały obok siebie, aby pomóc sprawdzić określonego wzorca lub relacji między wątkami.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Przenieś wybrany kanał do góry lub u dołu  
 Tak, aby zbadać określonego wzorca lub przenoszenia niektórych kanałów na bok, po sprawdzeniu innych, można przenieść do góry lub u dołu listy wybranych kanałów.  
  
## <a name="hide-selected-channels"></a>Ukryj wybrane kanały  
 Wybierz tę kontrolkę, gdy chcesz ukryć kanałów. Na przykład jeśli wątek jest synchronizacja 100 procent dla cyklu życia procesu zarządzanego, należy można go ukryć jak inne wątki.  
  
> [!NOTE]
>  Ukrywanie wątku spowoduje również usunięcie go z czas obliczeń, który jest wyświetlany w legendzie aktywnego i w profilu, raportów.  
  
## <a name="show-all-channels"></a>Pokaż wszystkie kanały  
 Ten formant jest aktywny, jeśli co najmniej jednego kanału są ukryte. Jeśli został wybrany, wszystkie ukryte elementy są wyświetlane i są zwracane do obliczeń czasu.  
  
## <a name="move-markers-to-top"></a>Przenieś znaczniki na początek  
 Jeśli śledzenia zawiera znacznika zdarzenia, można użyć tego polecenia, można przenieść kanały znacznika początku osi czasu. Ich względną kolejność jest zachowywana.  
  
## <a name="group-markers-by-thread"></a>Grupuj znaczniki według wątku  
 Jeśli śledzenia zawiera znacznika zdarzenia, można użyć tego polecenia, aby grupa znacznika kanałów w obszarze wątku, który wygenerował znacznika zdarzenia.  Kanały dysku zostaną przeniesione na początku listy kanałów i kanały GPU zostaną przeniesione do dołu.  
  
## <a name="see-also"></a>Zobacz także  
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)   
 [Tryb pomiarowy wł. / wył.](../profiling/measure-mode-on-off.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)