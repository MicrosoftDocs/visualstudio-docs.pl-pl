---
title: Widok funkcji - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
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
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bacc61ec9c254ce662854a08fe6a508977a72e2
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "51730189"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Widok funkcji — dane instrumentacji pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok funkcji .NET dane alokacji pamięci profilowania zebrane przy użyciu metody Instrumentacji Wyświetla listę funkcji, które pamięci przydzielonej podczas uruchomienia profilowania. Wiersz funkcji raportów, rozmiaru i liczby alokacji i danych o chronometrażu dla tej funkcji.  
  
## <a name="general"></a>Ogólne  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań, które zostały wprowadzone do tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji ze względu na instrumentacji. Narzut sondy odjęciu z cały czas wyłączny.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Narzut sondy odjęciu z cały czas (włącznie).|  
  
## <a name="net-memory-values"></a>Wartości pamięci platformy .NET  
 Wartości włącznie pamięci platformy .NET, funkcji wskazuje liczbę (przydziały) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcję i jej funkcji podrzędnych.  
  
 Wartości wyłączne pamięci wskazuje liczbę i rozmiar obiektów, które zostały utworzone przy użyciu funkcji, a nie przez jej funkcji podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Przydziały włączne**|Całkowita liczba obiektów, które zostały utworzone w tej funkcji oraz w funkcjach, które zostały wywołane przez tę funkcję.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów włącznych tej funkcji.|  
|**Przydziały wyłączne**|Całkowita liczba obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji. Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów wyłącznych tej funkcji.|  
|**Bajty włączne**|Liczba bajtów pamięci przydzielonych w tej funkcji oraz w funkcjach, które zostały wywołane przez tę funkcję.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były bajty włączne tej funkcji.|  
|**Bajty wyłączne**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję, ale nie przez funkcje, które zostały wywołane przez tę funkcję.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były bajty wyłączne tej funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmuje czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Łączny całkowity czas wszystkie wywołania do tej funkcji, który upłynął.|  
|**% Całkowitego czasu, który upłynął**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, która tracony jest czas całkowity czas tej funkcji.|  
|**Średnia liczba upłynęło włącznie czasu**|Średni całkowity czas wywołania tej funkcji, który upłynął.|  
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalny całkowity czas wywołania tej funkcji, który upłynął.|  
|**Min upłynęło włącznie czasu**|Minimalny całkowity czas wywołania tej funkcji, który upłynął.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|Suma upłynęło własny czas wszystkie wywołania do tej funkcji.|  
|**% Wyłącznego czasu, który upłynął**|Procent sumy, który upłynął własny czas uruchomienia profilowania, która tracony jest czas całkowity czas wyłączny tej funkcji.|  
|**Średnia liczba upłynęło wyłącznie czasu**|Średni własny czas wywołania tej funkcji, który upłynął.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny własny czas wywołania tej funkcji, który upłynął.|  
|**Min upłynęło wyłącznie czasu**|Minimalny własny czas wywołania tej funkcji, który upłynął.|  
  
## <a name="application-inclusive-values"></a>Wartości Włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale ma czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji dla wszystkich wywołań tej funkcji.|  
|**% Całkowitego czasu aplikacji**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, spędzony w kompletnej aplikacji, całkowity czas tej funkcji.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Wartości wyłączne aplikacji wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ani obejmuje czas spędzony w funkcjach podrzędnych.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Łączna liczba własny czas aplikacji dla wszystkich wywołań tej funkcji.|  
|**% Własnego czasu aplikacji**|Procent sumy, który upłynął własny czas uruchomienia profilowania, spędzony w własny czas aplikacji całkowita tej funkcji.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)



