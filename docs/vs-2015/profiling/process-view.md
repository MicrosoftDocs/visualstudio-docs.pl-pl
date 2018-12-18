---
title: Widok procesu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56fb301436b3fbe9374301fa4f7a8fd421485cbb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794507"
---
# <a name="process-view"></a>Widok procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok procesu wyświetla danych profilowania dla procesów i wątków, które zostały wykonane podczas uruchomienia profilowania.  
  
 Procesy są wyświetlane według nazwy. Wątki są wyświetlane jako węzły podrzędne procesu, który je utworzył. Wątki są nazywane przez funkcję, która jest uruchomiona w wątku lub etykieta **[ntdll.dll]** Jeśli brak symboli są dostępne.  
  
 Aby dodać lub usunąć kolumny, kliknij prawym przyciskiem myszy w widoku, a następnie wybierz **Dodaj/Usuń kolumny**. Ponadto możesz sortować dane, klikając nazwę kolumny. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).  
  
 Kolumny w widoku procesu są takie same dla danych, który jest generowany przy użyciu metody próbkowania i instrumentacji i danych, która zawiera dane pamięci platformy .NET. W poniższej tabeli opisano wartości w kolumnach.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Unikatowy identyfikator**|Identyfikator wygenerowany przez program profilujący jest unikatowy dla proces lub wątek.|  
|**ID**|Wygenerowana przez system identyfikator proces lub wątek.|  
|**Nazwa**|Nazwa proces lub wątek.|  
|**Czas rozpoczęcia**|Liczba milisekund, czyli cykli procesora od rozpoczęcia profilowania do początku proces lub wątek.|  
|**Godzina zakończenia**|Liczba milisekund, czyli cykli procesora od czasu rozpoczęcia profilowania do końca proces lub wątek.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)   
 [Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



