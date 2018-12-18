---
title: Widok drzewa wywołań - dane Kontencji | Dokumentacja firmy Microsoft
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
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 003e25121b3761a6e9440dcd4f0885975e0d98c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816465"
---
# <a name="call-tree-view---contention-data"></a>Widok drzewa wywołań — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji. Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które go wywołały, ile razy funkcja została zablokowana i ilość czasu, że funkcja została zablokowana, ponieważ został on rywalizacji o zasób z innych wątkach lub procesach.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji całkowitą liczbę rywalizacji w trakcie uruchomienia profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżka aktywna wykonywania  
 Widok drzewa wywołania można rozwijać i Podświetlenie ścieżki wykonywania procesu lub funkcja, która utworzyła większość rywalizacji.  
  
-   Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij **Rozwiń ścieżkę aktywną**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawienie węzeł główny drzewa wywołań  
 Każdy proces, w trakcie uruchomienia profilowania pojawia się jako węzeł główny. Aby ustawić węzeł początkowy widok drzewa wywołania, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie kliknij przycisk **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem poddrzewo wybranego węzła. Aby przywrócić węzła głównego oryginalnego węzła, kliknij prawym przyciskiem myszy w widoku drzewa wywołań, a następnie kliknij **resetowania głównego**.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czas blokowania**|Czas wystąpienia tej funkcji w tej ścieżce wykonywania zostały zablokowane wykonania podczas uruchomienia profilowania. Czas nie obejmuje czas blokowania funkcji podrzędnych, które zostały wywołane przez funkcję.|  
|**% Własnego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, który był wyłączny czas blokowania dla tej funkcji w tej ścieżce wykonywania.|  
|**Rywalizacje wyłączne**|Liczba rywalizacji, które wystąpiły w wystąpieniach tej funkcji w tej ścieżce wykonywania. Liczba nie ma rywalizacji wywołanych przez funkcję funkcji podrzędnych.|  
|**% Rywalizacji wyłącznych**|Procent wszystkich rywalizacji w trakcie uruchomienia profilowania, które były rywalizacji wyłącznych wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań.|  
|**Adres funkcji**|Adres funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Całkowity czas blokowania**|Łączny czas wykonywania podczas uruchomienia profilowania wystąpienia tej funkcji w tej ścieżce wykonywania został zablokowany. Czas obejmuje czas blokowania wywołanych przez funkcję funkcji podrzędnych.|  
|**% Całkowitego czasu blokowania**|Procent wszystkich czas blokowania w profilowania, był całkowity czas blokowania dla wystąpień tej funkcji w tej ścieżce wykonywania.|  
|**Rywalizacje włączne**|Całkowita liczba rywalizacji, które blokowane wystąpienia tej funkcji w tej ścieżce wykonywania. Liczba uwzględnia rywalizacji wywołanych przez funkcję funkcji podrzędnych.|  
|**% Rywalizacji włącznych**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji włącznych wystąpień tej funkcji w tej ścieżce wykonywania.|  
|**poziom**|Poziom funkcji w drzewie wywołań. Tylko w raportach VSReport, wiersza polecenia. Aby uzyskać więcej informacji, zobacz w [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view.md)   
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)



