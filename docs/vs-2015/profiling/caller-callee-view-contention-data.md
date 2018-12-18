---
title: Widok elementu wywołującego wywoływanego — dane rywalizacji o zasoby | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e226cb5a44923e73d64a9374eb1d170e18d2428
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797614"
---
# <a name="caller--callee-view----contention-data"></a>Element wywołujący / widok / / wywoływany - dane Kontencji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany Wyświetla informacje rywalizacji o zasoby dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** są wyświetlane w siatce Środkowej i zawiera informacje rywalizacji o zasoby dla wybranej funkcji. Wartości obejmują wszystkie rywalizacje blokowania dla tej funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i pokazuje poszczególne wkłady wywołującego (nadrzędnego) funkcji do wartości wybranej funkcji (bieżącego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** są wyświetlane w siatce dolnej i zawiera informacje rywalizacji o zasoby dla wywoływanego (podrzędne) funkcje wybranej funkcji gdy funkcja podrzędnych została wywołana przez bieżącą funkcję.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącej funkcji<br />-   **1** — funkcji wywołującej bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Wyłączny czas blokowania**|— Aby uzyskać bieżącą funkcję czas, jaki ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Czas blokowania w funkcjach wywoływanych przez funkcję nie jest włączony.<br />— Aby wywołujący funkcję część wyłączny czas blokowania bieżącej funkcji, który wystąpił podczas tej funkcji wywołującemu bieżącą funkcję.<br />— W przypadku funkcji / / wywoływany czas, który został zablokowany wykonywania własnego kodu, gdy ta funkcja została wywołana przez bieżącą funkcję tę funkcję. Czas blokowania w funkcjach podrzędnych wywołane przez funkcję / / wywoływany nie jest włączony.|  
|**% Własnego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, która była wyłączny czas blokowania dla tej funkcji, w tym kontekście.|  
|**Rywalizacje wyłączne**|— Dla bieżącej funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Rywalizacji, które wystąpiły w funkcje, które zostały wywołane przez funkcję nie są uwzględniane.<br />— Aby funkcja obiekt wywołujący, liczba rywalizacji wyłącznych bieżącej funkcji, który wystąpił podczas tej funkcji wywołującemu bieżącą funkcję.<br />— Dla funkcji / / wywoływany, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacji, które wystąpiły w funkcjach wywoływanych przez funkcję wywoływanego nie są uwzględniane.|  
|**% Rywalizacji wyłącznych**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji wyłącznych dla tej funkcji, w tym kontekście.|  
|**Adres funkcji**|Adres funkcji lub token.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Całkowity czas blokowania**|– W przypadku bieżącej funkcji czasu, która tej funkcji lub jednej z funkcji, które były wywoływane przez tę funkcję, została zablokowana wykonania. Czas blokowania w funkcjach, które zostały wywołane przez bieżącą funkcję jest dołączony.<br />— Aby wywołujący funkcję czas bieżącej funkcji, który wystąpił podczas tej funkcji wywołującemu bieżącą funkcję blokowania część włącznie.<br />— W przypadku funkcji / / wywoływany czas, jaki ta funkcja lub jedna z funkcji, które zostało wywołane przez funkcję zablokowano wykonywania, gdy ta funkcja została wywołana przez bieżącą funkcję. Czas blokowania w funkcjach, które zostały wywołane przez funkcję / / wywoływany jest dołączony.|  
|**% Całkowitego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, która była całkowity czas blokowania dla tej funkcji, w tym kontekście.|  
|**Rywalizacje włączne**|— Dla bieżącej funkcji, ile razy ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję zablokowano wykonywania. Uwzględniono rywalizacji, które wystąpiły w funkcje, które zostały wywołane przez funkcję.<br />— Aby funkcja obiekt wywołujący, liczba rywalizacji włącznych bieżącej funkcji, który wystąpił podczas tej funkcji wywołującemu bieżącą funkcję.<br />— Dla funkcji / / wywoływany, ile razy ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję zablokowano wykonywania, gdy ta funkcja została wywołana przez bieżącą funkcję. Uwzględniono rywalizacji, które wystąpiły w funkcjach wywoływanych przez funkcję / / wywoływany.|  
|**% Rywalizacji włącznych**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji wyłącznych dla tej funkcji, w tym kontekście.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wystąpił rywalizacji.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md)   
 [Element wywołujący / widok / / wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)



