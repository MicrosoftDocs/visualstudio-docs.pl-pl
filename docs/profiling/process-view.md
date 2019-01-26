---
title: Widok procesu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2e87613cc73682548c278942e17c59026828d6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55068969"
---
# <a name="process-view"></a>Widok procesu
Widok procesu wyświetla danych profilowania dla procesów i wątków, które zostały wykonane podczas uruchomienia profilowania.  
  
 Procesy są wyświetlane według nazwy. Wątki są wyświetlane jako węzły podrzędne procesu, który je utworzył. Wątki są nazywane przez funkcję, która jest uruchomiona w wątku lub etykieta **[ntdll.dll]** Jeśli brak symboli są dostępne.  
  
 Aby dodać lub usunąć kolumny, kliknij prawym przyciskiem myszy w widoku, a następnie wybierz **Dodaj/Usuń kolumny**. Ponadto możesz sortować dane, klikając nazwę kolumny. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).  
  
 Kolumny w widoku procesu są takie same dla danych, który jest generowany przy użyciu metody próbkowania i instrumentacji i danych, która zawiera dane pamięci platformy .NET. W poniższej tabeli opisano wartości w kolumnach.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Unikatowy identyfikator**|Identyfikator wygenerowany przez program profilujący jest unikatowy dla proces lub wątek.|  
|**Identyfikator**|Wygenerowana przez system identyfikator proces lub wątek.|  
|**Nazwa**|Nazwa proces lub wątek.|  
|**Czas rozpoczęcia**|Liczba milisekund, czyli cykli procesora od rozpoczęcia profilowania do początku proces lub wątek.|  
|**Godzina zakończenia**|Liczba milisekund, czyli cykli procesora od czasu rozpoczęcia profilowania do końca proces lub wątek.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)   
 [Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)