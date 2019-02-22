---
title: Czas blokowania raport profilowania | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5c80c768e153ae9469fe43785480bbe6bb1edeaa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623739"
---
# <a name="blocking-time-profile-report"></a>Raport profil czasu blokowania
Profilu, raportów Obejmij zagregowane dane czasu blokowania stosy wywołań, które są specyficzne dla każdej kategorii blokowania (na przykład "We/wy" lub "Synchronizacji"). Raport Wywłaszczania zawiera listę procesów, które przerywane bieżący proces wraz z liczbą wystąpień wywłaszczania. Aby skompilować blokowania raport profilu, narzędzie umożliwia zbieranie informacji o blokadzie wywołań interfejsu API i gromadzi ich do drzewa stosów wywołań. Dane wyświetlane w tych raportach różni się przez bieżącego zakresu czasu, ukrytych wątków i następujące dwa filtry, które mogą być stosowane:

- Jeśli wybrano opcję tylko mój kod, prezentowane są tylko ramki stosu, które mają kod użytkownika i jeden poziom poniżej kod użytkownika.

- Jeśli ustawiono wartość redukcji szumu, sortowane stosów, które mają mniej niż z określoną częstotliwością są pomijane.

  Rozwiń drzewo wywołań zapis wiersza kodu, w którym blokowania jest zużywany czas. Aby zlokalizować wiersz źródła dla wpisu w jego menu skrótów, wybierz opcję **Wyświetl źródło**. Aby zlokalizować wiersza kodu, który wywołał tego jednego, w menu skrótów wybierz **widok wywołań witryn**. Jeśli tylko jedna lokacja wywołania jest dostępna, polecenie łączy się z wyróżniony wiersz kodu do witryny wywołania. Jeśli dostępnych jest wiele wywołań, polecenie powoduje otwarcie okna dialogowego, w którym możesz wybierz wpis, a następnie wybrać **przejdź do źródła** przycisk, aby zlokalizować wyróżnione wywołania. Często jest najbardziej użyteczna wyświetlić kod źródłowy dla lokacji wywołania, która ma najwięcej wystąpień i/lub najwięcej czasu.

## <a name="blocking-time-report-columns"></a>Kolumny raportu czas blokowania
 W poniższej tabeli przedstawiono kolumny dla każdego blokowania czasie — raport.

|Nazwa kolumny|Opis|
|-----------------|-----------------|
|**Nazwa**|Nazwa funkcji dla poszczególnych poziomów stosu wywołań.|
|**Wystąpienia**|Liczba wystąpień wywołania blokowania dla przedziału czasu widoczne.|
|**Czas blokowania włącznych**|Łączny czas spędzony na dla wszystkich stosów, które składają się na tym poziomie drzewo stosu wywołań blokowania. Numer (włącznie) jest sumą własny czas blokowania dla tej funkcji i wyłączny czas blokowania dla wszystkich jego węzłów podrzędnych.|
|**Czas blokowania wyłącznych**|Całkowity czas blokowania spędzonego w taki sposób, w której ta funkcja jest najniższy poziom stosu wywołań. Wpis stosu wywołań unikatowy, która ma wysoką własny czas blokowania może być funkcja zainteresowania.|
|**API/Wait Category**|Pokazano tylko dla funkcji na najniższym poziomie stosu wywołań. W przypadku, gdy zostanie rozpoznany podpis wywołania blokowania, znajduje się nazwa blokowania interfejsu API. Jeśli podpis nie zostanie rozpoznany, który jest zgłaszany przez jądro informacje.|
|**Szczegóły**|W pełni kwalifikowana nazwa funkcji. Obejmuje to liczba wierszy, gdy będzie ona dostępna.|

### <a name="synchronization"></a>Synchronizacja
 Synchronizacja przedstawia wywołania, które są odpowiedzialne za segmentów, które blokują synchronizacji i agregacji, blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas synchronizacji](../profiling/synchronization-time.md)

### <a name="sleep"></a>Stan uśpienia
 Uśpienie przedstawia wywołania, które są odpowiedzialne za blokuje czas, który został przypisany czas spędzony w stanie uśpienia i łączny czas blokowania każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).

### <a name="io"></a>WE/WY
 Operacje We/Wy przedstawia wywołania, które są odpowiedzialne za segmentów, które blokują na We/Wy i agregacji, blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji We/Wy (Widok wątków)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Zarządzanie pamięcią
 Zarządzanie pamięcią przedstawia wywołania, które są odpowiedzialne za segmentów, które blokują na pamięć operacje zarządzania i agregacji blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).

### <a name="preemption"></a>Wywłaszczania
 Raport Wywłaszczania zawiera listę procesów, które przerywane bieżący proces wraz z liczbą wystąpień.  Można rozwinąć każdy proces, aby wyświetlić tylko określone wątki, które zastąpione wątki w bieżącym procesie i wyświetlić podział wywłaszczania wystąpień na wątek. Ten raport blokowania jest mniej informacje z możliwością działania od innych, ponieważ wywłaszczania zazwyczaj nakłada się na proces przez system operacyjny, a nie problemu w kodzie. Aby uzyskać więcej informacji, zobacz [czas Wywłaszczania](../profiling/preemption-time.md).

### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika
 Raport przetwarzania interfejsu użytkownika zawiera wywołania, które są odpowiedzialne za blokuje segmentów, które blokują na bloki przetwarzania interfejsu użytkownika i agregacji, blokuje razy każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Zobacz także
- [Widok wątków](../profiling/threads-view-parallel-performance.md)