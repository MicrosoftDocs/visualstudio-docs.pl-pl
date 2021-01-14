---
title: Raport profilu czasu blokowania | Microsoft Docs
description: 'Raporty profilu czasu blokowania zapewniają zagregowany czas blokowania danych. Istnieje sześć typów raportów: synchronizacja, uśpienie, we/wy, pamięć, zastępujące i interfejs użytkownika.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 74cfeb0b93b1819b4491b18b8e455b3c8d49be4d
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204582"
---
# <a name="blocking-time-profile-report"></a>Raport profilu czasu blokowania
Raporty profilu zapewniają zagregowane dane czasu blokowania dla stosów wywołań, które są specyficzne dla każdej kategorii blokującej (na przykład "we/wy" lub "Synchronizacja"). Raport zastępujący zawiera listę procesów, które zastępują bieżący proces wraz z liczbą wystąpień zastępujące. Aby skompilować Raport z profilem blokującym, narzędzie zbiera blokowane wywołania interfejsu API i gromadzi je w drzewie stosów wywołań. Dane, które są wyświetlane w tych raportach, różnią się w zależności od bieżącego zakresu czasu, przez ukryte wątki oraz następujących dwóch filtrów, które mogą być stosowane:

- Jeśli Tylko mój kod jest zaznaczone, wyświetlane są tylko ramki stosu, które mają kod użytkownika, oraz jeden poziom poniżej kodu użytkownika.

- Jeśli ustawiona jest wartość Redukcja szumu, posortowane stosy, które mają mniej niż określona częstotliwość, są pomijane.

  Rozwiń wszystkie wpisy drzewa wywołań, aby znaleźć wiersz kodu, w którym jest poświęcony czas blokowania. Aby zlokalizować wiersz źródła dla wpisu, w menu skrótów wybierz polecenie **Wyświetl źródło**. Aby zlokalizować wiersz kodu o nazwie ten, w menu skrótów wybierz polecenie **Wyświetl Lokacje wywołań**. Jeśli dostępna jest tylko jedna lokacja wywołania, polecenie nawiązuje połączenie z wyróżnionym wierszem kodu dla witryny wywołania. Jeśli dostępnych jest wiele lokacji wywołań, polecenie otwiera okno dialogowe, w którym można wybrać wpis, a następnie wybrać przycisk **Przejdź do źródła** , aby zlokalizować wyróżnioną lokację wywołania. Często jest to przydatne do wyświetlania kodu źródłowego dla witryny wywołania, która ma najwięcej wystąpień, w większości przypadków lub obu.

## <a name="blocking-time-report-columns"></a>Kolumny raportów czasu blokowania
 W poniższej tabeli przedstawiono kolumny dla każdego raportu czasu blokowania.

|Nazwa kolumny|Opis|
|-----------------|-----------------|
|**Nazwa**|Nazwa funkcji dla każdego poziomu stosu wywołań.|
|**Wystąpienia**|Liczba wystąpień wywołania blokującego dla widocznego okresu.|
|**Włączny czas blokowania**|Łączny czas blokowania zużyty dla wszystkich stosów, które są rzutowane na ten poziom drzewa stosu wywołań. Liczba włącznie jest sumą czasu blokowania wyłącznych dla tej funkcji i wyłącznego czasu blokowania dla wszystkich jego węzłów podrzędnych.|
|**Czas blokowania wyłącznego**|Łączny czas blokowania spędzony w czasie, gdy ta funkcja jest najniższym poziomem stosu wywołań. Unikatowy wpis stosu wywołań, który ma wysoką, wyłączny czas blokowania może być funkcją zainteresowania.|
|**Kategoria interfejsu API/oczekiwania**|Wyświetlane tylko dla funkcji na najniższym poziomie stosu wywołań. Gdzie jest rozpoznawany podpis wywołania blokującego, jest dostępna nazwa blokującego interfejsu API. Jeśli sygnatura nie zostanie rozpoznana, podane są informacje zgłaszane przez jądro.|
|**Szczegóły**|W pełni kwalifikowana nazwa funkcji. Obejmuje to liczbę wierszy, gdy jest dostępna.|

### <a name="synchronization"></a>Synchronizacja
 Raport synchronizacji przedstawia wywołania, które są odpowiedzialne za segmenty, które blokują synchronizację, oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [godzina synchronizacji](../profiling/synchronization-time.md).

### <a name="sleep"></a>Uśpij
 Raport uśpienia zawiera wywołania, które są odpowiedzialne za czas blokowania, który był przeznaczony do czasu spędzonego na stanie uśpienia, i łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas uśpienia](../profiling/sleep-time.md).

### <a name="io"></a>WE/WY
 Raport we/wy przedstawia wywołania, które są odpowiedzialne za segmenty, które blokują we/wy i łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas operacji we/wy (Widok wątków)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Zarządzanie pamięcią
 Raport zarządzanie pamięcią zawiera wywołania, które są odpowiedzialne za segmenty, które blokują operacje zarządzania pamięcią, oraz łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas zarządzania pamięcią](../profiling/memory-management-time.md).

### <a name="preemption"></a>Wywłaszczania
 Raport zastępujący zawiera listę procesów, które zastępują bieżący proces wraz z liczbą wystąpień.  Każdy proces można rozwinąć, aby wyświetlić określone wątki, które zastąpiły wątki w bieżącym procesie i wyświetlić podział wystąpień zastępujący na wątek. Ten raport blokowania jest mniej funkcjonalny od innych, ponieważ przełożenie jest zwykle nakładane na proces przez system operacyjny, a nie przez problem w kodzie. Aby uzyskać więcej informacji, zobacz [czas zastępujący](../profiling/preemption-time.md).

### <a name="ui-processing"></a>Przetwarzanie interfejsu użytkownika
 Raport przetwarzania interfejsu użytkownika przedstawia wywołania, które są odpowiedzialne za blokowanie segmentów, które blokują bloki przetwarzania interfejsu użytkownika i łączny czas blokowania dla każdego stosu wywołań. Aby uzyskać więcej informacji, zobacz [czas przetwarzania interfejsu użytkownika](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)