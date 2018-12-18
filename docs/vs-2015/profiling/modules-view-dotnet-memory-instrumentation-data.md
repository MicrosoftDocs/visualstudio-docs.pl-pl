---
title: Widok modułów - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
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
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85024296eff4fb4d26b3a588217a1e6fe5221d3e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755401"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Widok modułów — dane instrumentacji pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok modułów dane alokacji pamięci .NET zbierane za pomocą metody Instrumentacji grupuje pamięci i danych o chronometrażu przez moduły, które zostały wykonane w trakcie uruchomienia profilowania. Danych profilowania dla funkcji modułu znajduje się poniżej tego węzła modułu.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji lub modułu.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań, które zostały wprowadzone do tej funkcji lub modułu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu, w którym był wykonywany modułu lub funkcji.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji lub modułu z powodu instrumentacji.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji lub modułu i jej funkcji podrzędnych z powodu instrumentacji.|  
  
## <a name="net-memory-values"></a>Wartości pamięci platformy .NET  
 Wartości włącznie pamięci platformy .NET, funkcji wskazuje liczbę (przydziały) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcję i jej funkcji podrzędnych.  
  
 Wartości wyłączne pamięci wskazuje liczbę i rozmiar obiektów, które zostały utworzone przy użyciu funkcji, a nie przez jej funkcji podrzędnych.  
  
 Wartości włączne i wyłączne pamięci modułu są sumę włączne i wyłączne pamięci wartości funkcje w module.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Przydziały włączne**|— Dla funkcji, całkowita liczba obiektów, które zostały utworzone przez funkcję. Liczba ta obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję.<br />— Dla modułu liczbę obiektów w które przebiegu profilowania została przydzielona podczas wykonywania co najmniej jedna funkcja w module. Liczba ta obejmuje przydzielonych obiektów w funkcjach, które zostały wygenerowane przez wywołania z funkcji modułu.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów włącznych modułu lub funkcji.|  
|**Przydziały wyłączne**|— W przypadku funkcji liczbę obiektów, które zostały utworzone podczas wykonywania kodu funkcji w treści funkcji (oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań). Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu, sumę przydziałów wyłącznych funkcje w module.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów wyłącznych modułu lub funkcji.|  
|**Bajty wyłączne**|— Dla funkcji całkowita liczba bajtów pamięci przydzielonych podczas wykonywania kodu funkcji w funkcji treści (to znaczy, gdy funkcja znajdowała się w górnej części stosu wywołań). Ta liczba nie ma przydzielonych bajtów w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu, Suma bajtów wyłącznych, przydzielone przez funkcje w module.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów przydzielonych w uruchomienia profilowania były bajty wyłączne modułu, funkcji, wiersza lub instrukcji.|  
|**Bajty włączne**|— W przypadku funkcji liczba bajtów przydzielonych przez funkcję. Liczba ta obejmuje przydzielonych bajtów w funkcjach, które zostały wywołane przez funkcję.<br />— Dla modułu liczba bajtów przydzielonych w taki sposób, w który przebiegu profilowania została przydzielona podczas wykonywania co najmniej jedna funkcja w module. Liczba ta obejmuje obiekty, które zostały utworzone we wszystkich funkcji, które zostały wywołane przez funkcje modułu.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów przydzielonych w uruchomienia profilowania były bajty włączne modułu lub funkcji.|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmuje czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|— W przypadku funkcji czas spędzony w funkcji. Obejmuje to czas spędzony w funkcji podrzędnych i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Dla modułu, okres, w których co najmniej jedna funkcja w module był na stosie wywołań.|  
|**% Całkowitego czasu, który upłynął**|Łączny czas całkowity czas tego modułu lub funkcji przeznaczony procent całkowity czas całkowity czas uruchomienia profilowania.|  
|**Średnia liczba upłynęło włącznie czasu**|— Dla funkcji ŚREDNIA, który upłynął całkowity czas wywołania tej funkcji.<br />— Dla modułu średnia, który upłynął całkowity czas wszystkie wywołania do funkcji w module.|  
|**Maksymalny czas, który upłynął (włącznie)**|— W przypadku funkcji maksymalną upłynęło całkowity czas wywołania tej funkcji.<br />— Dla modułu maksymalna, który upłynął całkowity czas wszystkie wywołania do funkcji w module.|  
|**Min upłynęło włącznie czasu**|— Dla funkcji minimum, który upłynął całkowity czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimum, który upłynął całkowity czas wszystkie wywołania do funkcji w module.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcji podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|— W przypadku funkcji czas spędzony w modułu lub funkcji. Obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czas spędzony w funkcjach podrzędnych.<br />— Dla modułu sumę, który upłynął czas wyłączny funkcje w module.|  
|**% Wyłącznego czasu, który upłynął**|Łączny czas wyłączny czas tego modułu lub funkcji przeznaczony procent całkowity czas własny czas uruchomienia profilowania.|  
|**Średnia liczba upłynęło wyłącznie czasu**|— Dla funkcji ŚREDNIA, który upłynął własnego czasu wywołania tej funkcji.<br />— Dla modułu średnia, który upłynął własny czas wszystkie wywołania do funkcji w module.|  
|**Maksymalny czas wyłączny, który upłynął**|— W przypadku funkcji maksymalną upłynęło własnego czasu wywołania tej funkcji.<br />— Dla modułu maksymalna, który upłynął własny czas wszystkie wywołania do funkcji w module.|  
|**Min upłynęło wyłącznie czasu**|— Dla funkcji minimum, który upłynął własny czas wywołanie tego modułu lub funkcji.<br />— Dla modułu minimum, który upłynął własny czas wszystkie wywołania do funkcji w module.|  
  
## <a name="application-inclusive-values"></a>Wartości Włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, ale ma czas spędzony w funkcjach podrzędnych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|— W przypadku funkcji czas spędzony w wywołaniach funkcji. Obejmuje to czas, jaki był poświęcony funkcji podrzędnych, ale nie obejmuje wywołania do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br />— Dla modułu, okres, w których co najmniej jedna funkcja w module był w stosie wywołań, z wyłączeniem czas spędzony w wywołaniach do systemu operacyjnego.|  
|**% Całkowitego czasu aplikacji**|Procent sumy, który upłynął całkowity czas uruchomienia profilowania, która spędzono w całkowity czas aplikacji tego modułu lub funkcji.|  
|**Średni całkowity czas aplikacji**|— Dla funkcji, całkowity czas aplikacji średnią rozmowy dotyczących wyłącznie tej funkcji.<br />— Dla modułu, całkowity czas aplikacji średnia dla wszystkich wywołań do funkcji w module.|  
|**Maksymalny całkowity czas aplikacji**|— Dla funkcji, całkowity czas aplikacji maksymalna wywołania tej funkcji.<br />— Dla modułu, całkowity czas aplikacji maksymalną dla wszystkich wywołań do funkcji w module.|  
|**Minimalny całkowity czas aplikacji**|— Dla funkcji, całkowity czas aplikacji minimalne wywołania do tego modułu lub funkcji.<br />— Dla modułu, całkowity czas minimalny aplikacji dla wszystkich wywołań do funkcji w module.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Aplikacja wyłączne wartości wskazują czas spędzony w module lub funkcji, z wyłączeniem czas spędzony w funkcjach podrzędnych. Wskazany czas także wyklucza wywołań do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|— W przypadku funkcji własny czas aplikacji łączna liczba wywołań tej funkcji.<br />— Dla modułu, własny czas aplikacji łączna liczba wszystkich wywołań funkcji w module.|  
|**% Własnego czasu aplikacji**|Procent sumy, który upłynął własny czas uruchomienia profilowania, która spędzono w własny czas aplikacji tego modułu lub funkcji.|  
|**Średni własny czas aplikacji**|— W przypadku funkcji własny czas aplikacji średnią rozmowy dotyczących wyłącznie tej funkcji.<br />— Dla modułu, własny czas aplikacji średnia dla wszystkich wywołań do funkcji w module.|  
|**Maksymalny własny czas aplikacji**|— W przypadku funkcji własny czas aplikacji maksymalna wywołania tej funkcji.<br />— Dla modułu, własny czas aplikacji maksymalną dla wszystkich wywołań do funkcji w module.|  
|**Minimalny własny czas aplikacji**|— W przypadku funkcji własny czas aplikacji minimalne wywołania do tego modułu lub funkcji.<br />— Dla modułu, własny czas aplikacji minimalną dla wszystkich wywołań do funkcji w module.|  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)



