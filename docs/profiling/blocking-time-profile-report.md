---
title: Raport profilu czasu blokowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ed24dce0779b9bc7ea9cfd7bedcaa5ca181c68
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926309"
---
# <a name="blocking-time-profile-report"></a>Blokowanie raportu profilu czasu
Raporty profilu zawierają agregujące dane czasu blokowania dla stosów wywołań, które są specyficzne dla każdej kategorii blokowania (na przykład "We/Wy" lub "Synchronizacja"). Raport wywłaszczenia zawiera listę procesów, które wywłaszczyły bieżący proces wraz z liczbą wystąpień wywłaszczenia. Aby utworzyć raport profilu blokowania, narzędzie zbiera blokowanie wywołań interfejsu API i gromadzi je w drzewie stosów wywołań. Dane wyświetlane w tych raportach różnią się w zależności od bieżącego zakresu czasu, ukrytych wątków i dwóch następujących filtrów, które mogą być stosowane:

- Jeśli jest zaznaczona opcja Tylko mój kod, wyświetlane są tylko ramki stosu, które mają kod użytkownika, plus jeden poziom poniżej kodu użytkownika.

- Jeśli ustawiona jest wartość redukcji szumów, posortowane stosy, które mają mniej niż określona częstotliwość są pomijane.

  Rozwiń dowolny wpis drzewa wywołań, aby znaleźć wiersz kodu, w którym spędza się czas blokowania. Aby zlokalizować wiersz źródła wpisu, w menu skrótów wybierz polecenie **Wyświetl źródło**. Aby zlokalizować wiersz kodu, który nazwał ten, w menu skrótów wybierz polecenie **Wyświetl witryny połączeń**. Jeśli dostępna jest tylko jedna lokacja wywołania, polecenie łączy się z wyróżnionym wierszem kodu dla witryny wywołania. Jeśli dostępnych jest wiele witryn połączeń, polecenie otwiera okno dialogowe, w którym można wybrać wpis, a następnie wybrać przycisk **Przejdź do źródła,** aby zlokalizować wyróżnioną witrynę połączeń. Często jest to najbardziej przydatne do wyświetlania kodu źródłowego dla witryny wywołania, która ma najwięcej wystąpień, najwięcej czasu lub obu.

## <a name="blocking-time-report-columns"></a>Blokowanie kolumn raportu czasu
 W poniższej tabeli przedstawiono kolumny dla każdego raportu czasu blokowania.

|Nazwa kolumny|Opis|
|-----------------|-----------------|
|**Nazwa**|Nazwa funkcji dla każdego poziomu stosu wywołań.|
|**Wystąpienia**|Liczba wystąpień wywołania blokowania dla widocznego okresu czasu.|
|**Czas blokowania włącznie**|Całkowity czas blokowania, który jest przeznaczony dla wszystkich stosów, które są zwijane do tego poziomu drzewa stosu wywołań. Liczba włącznie jest sumą wyłącznego czasu blokowania dla tej funkcji i wyłącznego czasu blokowania dla wszystkich węzłów podrzędnych.|
|**Ekskluzywny czas blokowania**|Całkowity czas blokowania, który jest spędzony, podczas którego ta funkcja jest najniższy poziom stosu wywołań. Unikatowy wpis stosu wywołań, który ma wysoki czas blokowania wyłączności może być funkcją zainteresowania.|
|**Kategoria INTERFEJSU API/oczekiwania**|Wyświetlane tylko dla funkcji na najniższym poziomie stosu wywołań. W przypadku rozpoznania podpisu wywołania blokującego podana jest nazwa interfejsu API blokowania. Jeśli podpis nie zostanie rozpoznany, informacje zgłaszane przez jądro są dostarczane.|
|**Szczegóły**|W pełni kwalifikowana nazwa funkcji. Obejmuje to liczbę wierszy, gdy jest dostępna.|

### <a name="synchronization"></a>Synchronizacja
 Raport synchronizacji pokazuje wywołania, które są odpowiedzialne za segmenty, które blokują synchronizację i agregujące czasy blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas synchronizacji](../profiling/synchronization-time.md).

### <a name="sleep"></a>Uśpij
 Raport Uśpienie pokazuje wywołania, które są odpowiedzialne za blokowanie czasu, który został przypisany do czasu spędzonego w trybie uśpienia i agregacji czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas uśpienia](../profiling/sleep-time.md).

### <a name="io"></a>WE/WY
 Raport we/wy pokazuje wywołania, które są odpowiedzialne za segmenty, które blokują we/wy, a agregując czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas we/wy (widok wątków)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Zarządzanie pamięcią
 Raport Zarządzanie pamięcią pokazuje wywołania, które są odpowiedzialne za segmenty, które blokują operacje zarządzania pamięcią i agregujące czasy blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas zarządzania pamięcią](../profiling/memory-management-time.md).

### <a name="preemption"></a>Wywłaszczanie
 Raport wywłaszczenia zawiera listę procesów, które wywłaszczyły bieżący proces wraz z liczbą wystąpień.  Można rozwinąć każdy proces, aby wyświetlić określone wątki, które zastąpiły wątki w bieżącym procesie i wyświetlić podział wystąpień wywłaszczenia na wątek. Ten raport blokowania jest mniej zasysanych niż inne, ponieważ wywłaszczenie jest zazwyczaj nakładane na proces przez system operacyjny, a nie przez problem w kodzie. Aby uzyskać więcej informacji, zobacz [Czas wywłaszczenia](../profiling/preemption-time.md).

### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika
 Raport przetwarzania interfejsu użytkownika pokazuje wywołania, które są odpowiedzialne za blokowanie segmentów, które blokują bloki przetwarzania interfejsu użytkownika i agregujące czasy blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [Czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)