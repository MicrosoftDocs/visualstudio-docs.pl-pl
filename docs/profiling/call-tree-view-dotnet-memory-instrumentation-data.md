---
title: Widok drzewa wywołań - dane Instrumentacji pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 51bdbe7f36b37ffbc0e1c911a8aa122cd3a44dd2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917569"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Widok drzewa wywołań - dane Instrumentacji pamięci platformy .NET
Widok drzewa wywołań .NET dane alokacji pamięci profilowania zebrane przy użyciu metody Instrumentacji Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, który ją wywołuje się, a pamięci .NET i danych o chronometrażu dla funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do liczby całkowitej lub rozmiar alokacji podczas uruchomienia profilowania.  
  
## <a name="highlight-the-execution-hot-path"></a>Wyróżnij ścieżkę aktywną wykonywania  
 Widok drzewa wywołania można rozwijać i Podświetlenie ścieżki wykonywania procesu lub funkcja, która utworzyła największy lub większości obiektów w pamięci. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij **Rozwiń ścieżkę aktywną**.  
  
## <a name="set-the-call-tree-root-node"></a>Ustaw węzeł główny drzewa wywołań  
 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Począwszy od węzła widok drzewa wywołania można ustawić prawym przyciskiem myszy węzeł, w której chcesz ustawić jako węzeł początkowy, a następnie wybierając **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Węzeł główny można zresetować do węzła, który oglądasz; Kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **resetowania głównego**.  
  
## <a name="general"></a>Ogólne  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Liczba wywołań**|Całkowita liczba wywołań wykonanych dla tej funkcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|  
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, która jest spowodowany przez instrumentacji. Narzut sondy odjęciu z cały czas wyłączny.|  
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych spowodowany za pomocą Instrumentacji. Narzut sondy odjęciu z cały czas (włącznie).|  
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** -bieżącej funkcji<br />-   **1** — funkcji wywołującej bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Nazwa głównej funkcji**|Nazwa bieżącej funkcji. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
  
## <a name="net-memory-values"></a>Wartości pamięci platformy .NET  
 Wartości włącznie pamięci platformy .NET, funkcji wskazuje liczbę (przydziały) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcji i funkcji, które zostały wywołane przez funkcję.  
  
 Wartości wyłączne pamięci wskazuje liczbę i rozmiar obiektów, które zostały utworzone przez kod w treści funkcji, a nie przez funkcje, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Przydziały włączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów włącznych wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
|**Przydziały wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów wyłącznych wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości  
 Upłynęło wartości włącznie wskazują godzinę, będący funkcji na stosie wywołań. Czas obejmuje czas spędzony w funkcjach, które zostały wywołane przez funkcję, jak i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas, który upłynął**|Suma, który upłynął całkowity czas wszystkie wywołania do tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Całkowitego czasu, który upłynął**|Procent sumy, który upłynął całkowity czas spędzony w całkowity czas całkowity czas tę funkcję, wywołanego przez funkcję nadrzędnego w drzewie wywołań profilowania.|  
|**Średnia liczba upłynęło włącznie czasu**|Średnia, który upłynął całkowity czas wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalna, który upłynął całkowity czas wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Min upłynęło włącznie czasu**|Minimum, który upłynął całkowity czas wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości  
 Czas wyłączny wartości wskazują godzinę, wykonywanej funkcji bezpośrednio w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia. Jednak podczas nie obejmuje czas spędzony w funkcji, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Czas wyłączny, który upłynął**|Suma upłynęło własny czas wszystkie wywołania do tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Wyłącznego czasu, który upłynął**|Procent sumy, który upłynął własny czas spędzony w całkowity czas własny czas tę funkcję, wywołanego przez funkcję nadrzędnego w drzewie wywołań profilowania.|  
|**Średnia liczba upłynęło wyłącznie czasu**|Średnia, który upłynął własnego czasu wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny czas wyłączny, który upłynął**|Maksymalna, który upłynął własnego czasu wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Min upłynęło wyłącznie czasu**|Minimum, który upłynął własnego czasu wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="application-inclusive-values"></a>Wartości włączne aplikacji  
 Aplikacji wartości włącznie wskazują czasu, która funkcja była w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia. Czas obejmują czas spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji dla wszystkich wywołań tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Całkowitego czasu aplikacji**|Procent sumy, który upłynął całkowity czas spędzony w kompletnej aplikacji, całkowity czas tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań profilowania.|  
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji  
 Aplikacja wyłączne wartości wskazują czas spędzony w funkcji bez czasu spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję. Czas także wyklucza wywołań do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Własny czas aplikacji**|Łączna liczba własny czas aplikacji dla wszystkich wywołań tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**% Własnego czasu aplikacji**|Procent sumy, który upłynął własny czas spędzony w własny czas aplikacji całkowita tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań profilowania.|  
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji wywołanego przez funkcję nadrzędnego w drzewie wywołań.|