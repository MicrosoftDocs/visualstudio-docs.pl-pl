---
title: Widok elementu wywołującego / / wywoływany - dane próbkowania | Dokumentacja firmy Microsoft
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
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e46befbdd8f727485884197a3cfb284fa5a8cf6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796964"
---
# <a name="caller--callee-view---sampling-data"></a>Element wywołujący / widok / / wywoływany - dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany Wyświetla informacje dotyczące profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlany w środkowy siatkę, a pokazuje profilowania informacje dotyczące wybranej funkcji. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i pokazuje poszczególne wkłady wywołującego (nadrzędnego) funkcji do wartości wybranej funkcji (bieżącego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacji dla funkcji elementu wywoływanego (podrzędne) wybranej funkcji, gdy funkcja podrzędnych została wywołana przez bieżącą funkcję.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres funkcji.|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącej funkcji<br />-   **1** — funkcji wywołującej bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji.|  
|**Próbki włączne**|– W przypadku bieżącej funkcji liczba próbek, które zostały zebrane, mimo że wykonywania tej funkcji lub jedna z jej funkcji podrzędnych.<br />— Aby funkcja obiekt wywołujący, liczba włącznych próbek bieżącej funkcji, które zostały zebrane, gdy ta funkcja jest wywoływana bieżącą funkcję.<br />— W przypadku funkcji / / wywoływany liczba włącznych próbek tej funkcji, które zostały zebrane, gdy bieżąca funkcja wywołuje tę funkcję.|  
|**% Włącznych próbek**|Wartość procentowa wszystkie przykłady w uruchomienia profilowania były włącznych próbek w tej funkcji.|  
|**Próbki wyłączne**|-Aby uzyskać bieżącą funkcję liczba próbek w profilowania, zostały zebrane podczas bezpośrednio wykonywania tej funkcji; oznacza to, gdy ta funkcja została w górnej części stosu wywołań. Przykłady, które są zbierane, gdy są wykonywane funkcje podrzędnych tej funkcji nie są uwzględniane w pozostałych.<br />— Aby funkcja obiekt wywołujący, liczba próbek wyłącznych bieżącej funkcji, które zostały zebrane, gdy ta funkcja jest wywoływana bieżącą funkcję.<br />— W przypadku funkcji / / wywoływany liczba próbek wyłącznych tej funkcji, które zostały zebrane, gdy bieżąca funkcja wywołuje tę funkcję.|  
|**% Wyłącznych próbek**|Wartość procentowa wszystkie przykłady w uruchomienia profilowania były wyłącznych próbek w tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)



