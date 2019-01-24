---
title: Widok funkcji - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef2375fc4132e0274e7cded6daf5bdd0a58891c4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769032"
---
# <a name="functions-view---instrumentation-data"></a>Widok funkcji — dane instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok raportu funkcji Wyświetla listę danych profilowania nazwą funkcji.  
  
## <a name="general"></a>Ogólne  
 Ogólne kolumn identyfikować ich funkcję w wierszu widoku.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań, które zostały wprowadzone do tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, która jest spowodowany przez instrumentacji. Nie obejmuje obciążenie w funkcjach, które zostały wywołane przez funkcję. Narzut sondy odjęciu z cały czas wyłączny.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych spowodowany za pomocą Instrumentacji. Obejmuje koszty w funkcjach, które zostały wywołane przez funkcję. Narzut sondy odjęciu z cały czas (włącznie).|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmują czas spędzony w funkcji, które zostały wywołane przez funkcję i czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Łączny całkowity czas wszystkie wywołania do tej funkcji, który upłynął.|  
|**% Całkowitego czasu, który upłynął**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, która tracony jest czas całkowity czas tej funkcji.|  
|**Średnia liczba upłynęło włącznie czasu**|Średni całkowity czas wywołania tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalny całkowity czas wywołania tej funkcji, który upłynął.|  
|**Min upłynęło włącznie czasu**|Minimalny całkowity czas wywołania tej funkcji, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują czasu, czy funkcja została wykonywanie kodu w treści funkcji, oznacza to, gdy funkcja znajdowała się w górnej części stosu wywołań. Czas uwzględnia czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcjach, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|Suma upłynęło własny czas wszystkie wywołania do tej funkcji.|  
|**% Wyłącznego czasu, który upłynął**|Procent sumy, który upłynął własny czas uruchomienia profilowania, która tracony jest czas całkowity czas wyłączny tej funkcji.|  
|**Średnia liczba upłynęło wyłącznie czasu**|Średni własny czas wywołania tej funkcji, który upłynął.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny własny czas wywołania tej funkcji, który upłynął.|  
|**Min upłynęło wyłącznie czasu**|Minimalny własny czas wywołania tej funkcji, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości Włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale ma czas spędzony w funkcjach, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji dla wszystkich wywołań tej funkcji.|  
|**% Całkowitego czasu aplikacji**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, spędzony w kompletnej aplikacji, całkowity czas tej funkcji.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Wartości wyłączne aplikacji wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia i nie obejmuje czas spędzony w funkcjach, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Łączna liczba własny czas aplikacji dla wszystkich wywołań tej funkcji.|  
|**% Własnego czasu aplikacji**|Procent sumy, który upłynął własny czas uruchomienia profilowania, spędzony w własny czas aplikacji całkowita tej funkcji.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji — Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
