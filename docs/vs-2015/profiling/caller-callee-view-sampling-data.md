---
title: Widok elementu wywołującego / / wywoływany - dane próbkowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5e3c28d7aa24f46bb3fc09045574030f8eb03db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803926"
---
# <a name="caller--callee-view---sampling-data"></a>Element wywołujący / widok / / wywoływany - dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok wywołujący/wywoływany Wyświetla informacje dotyczące profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.  
  
 **Bieżąca funkcja** jest wyświetlany w środkowy siatkę, a pokazuje profilowania informacje dotyczące wybranej funkcji. Wartości obejmują wszystkie próbki wywołania funkcji.  
  
 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i pokazuje poszczególne wkłady wywołującego (nadrzędnego) funkcji do wartości wybranej funkcji (bieżącego).  
  
 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w siatce dolnej i pokazuje profilowania informacji dla funkcji elementu wywoływanego (podrzędne) wybranej funkcji, gdy funkcja podrzędnych została wywołana przez bieżącą funkcję.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Kolumna|Opis|  
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
