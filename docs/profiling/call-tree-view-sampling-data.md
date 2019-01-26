---
title: Widok drzewa wywołań - dane z próbkowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41b6a9fca008e7f457eb75b52d9ace3a38451262
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933016"
---
# <a name="call-tree-view---sampling-data"></a>Widok drzewa wywołań — dane próbkowania
Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji Wyświetla wszystkie funkcje, które go wywołały i dane wydajności dotyczące tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji, aby łączna liczba próbek w trakcie uruchomienia profilowania.  
  
## <a name="highlight-the-execution-hot-path"></a>Wyróżnij ścieżkę aktywną wykonywania  
 Widok drzewa wywołania można rozwijać i Podświetlenie ścieżki wykonywania procesu lub funkcja, która została próbkowane najczęściej. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**.  
  
## <a name="set-the-call-tree-root-node"></a>Ustaw węzeł główny drzewa wywołań  
 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewo wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz pozycję **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Aby przywrócić węzła głównego oryginalnego węzła, kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **resetowania głównego**.  
  
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
|**Poziom**|Długość tej funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Próbki wyłączne**|Liczba próbek, które zostały zebrane w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przykładów, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Wyłącznych próbek**|Procent wszystkie przykłady w trakcie uruchomienia profilowania, które były wyłącznych próbek w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Próbki włączne**|Liczba próbek, które zostały zebrane w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje przykładów, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Włącznych próbek**|Procent wszystkie przykłady w trakcie uruchomienia profilowania, które były włącznych próbek w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań - dane z próbkowania profilera](../profiling/call-Tree-view-sampling-data.md)   
 [Drzewo wywołań view - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)