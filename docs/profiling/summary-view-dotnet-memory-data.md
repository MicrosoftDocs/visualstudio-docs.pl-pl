---
title: Widok podsumowania - dane pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1cd06626579697e5da38ac8d0ee0072f941eb473
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55071062"
---
# <a name="summary-view---net-memory-data"></a>Widok podsumowania - dane pamięci platformy .NET
Widok podsumowania Wyświetla informacje o funkcje platformy .NET i typy, które są przydzielane najwięcej pamięci oraz typy, które zostały utworzone w większości przypadków w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem powiadomienie łącza i listy raportów, zobacz [widok podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku podsumowania przedstawia użycie procesora (CPU) według profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania. Wykres osi czasu można użyć do filtrowania widoku, aby w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak: Filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funkcje przydzielające najwięcej pamięci  
 Wyświetla listę funkcji, które przydzielane największą liczbę bajtów pamięci w trakcie uruchomienia profilowania.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Bajtów**|Procent wszystkich przydzielonych bajtów podczas uruchomienia profilowania, które zostały przydzielone przez tę funkcję, lub funkcji podrzędnej, która została wywołana przez tę funkcję.|  
  
## <a name="types-with-most-memory-allocated"></a>Typy z największą ilością przydzielonej pamięci  
 Wyświetla listę typów, dla których największą liczbę bajtów pamięci przydzielonych podczas uruchomienia profilowania.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa typu.|  
|**% Bajtów**|Procent wszystkich przydzielonych bajtów podczas uruchomienia profilowania, które zostały przydzielone dla tego typu.|  
  
## <a name="types-with-most-instances"></a>Typy z największą liczbą wystąpień  
 Wyświetla listę typów, które zostały utworzone najwięcej czasu podczas uruchomienia profilowania. Gdyby  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa typu.|  
|**% Wystąpień**|Całkowita liczba obiektów of.NET, które zostały utworzone w profilowania, wartość procentowa były wystąpień tego typu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania - dane Instrumentacji](../profiling/summary-view-instrumentation-data.md)