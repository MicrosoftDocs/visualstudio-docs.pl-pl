---
title: Widok drzewa wywołań — dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed0d8a2ccf8e33b493ddcb71f9ce3a794a06862
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150755"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Widok drzewa wywołań — dane próbkowania pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji wymieniono wszystkie funkcje, które go wywołały i dane alokacji pamięci .NET o tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do liczby całkowitej lub rozmiar alokacji podczas uruchomienia profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżka aktywna wykonywania  
 Widok drzewa wywołania można rozwijać i Podświetlenie ścieżki wykonywania procesu lub funkcja, która utworzyła największy lub większości obiektów w pamięci. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij **Rozwiń ścieżkę aktywną**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawienie węzeł główny drzewa wywołań  
 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widok drzewa wywołania do innego węzła, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz pozycję **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Możesz przywrócić węzła głównego węzła, który był wyświetlany; Kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **resetowania głównego**.  
  
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
|**Poziom**|Głębokość funkcji w drzewie wywołań.|  
|**Przydziały włączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów włącznych tej funkcji.|  
|**Przydziały wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów wyłącznych wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
|**Bajty włączne**|Liczba bajtów w pamięci, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów włącznych tej funkcji.|  
|**Bajty wyłączne**|Liczba bajtów w pamięci, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje alokacji dokonanych przez funkcje podrzędnych.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów wyłącznych tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)
