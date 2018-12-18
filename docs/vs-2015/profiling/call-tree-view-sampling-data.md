---
title: Widok drzewa wywołań - dane z próbkowania | Dokumentacja firmy Microsoft
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
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc324b621bfc3e472d6eb86227a6081e3384d2af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798914"
---
# <a name="call-tree-view---sampling-data"></a>Widok drzewa wywołań — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok drzewa wywołania Wyświetla ścieżki wykonywania funkcji, które zostały przesunięta w profilowanej aplikacji.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji Wyświetla wszystkie funkcje, które go wywołały i dane wydajności dotyczące tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji, aby łączna liczba próbek w trakcie uruchomienia profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie ścieżka aktywna wykonywania  
 Widok drzewa wywołania można rozwijać i Podświetlenie ścieżki wykonywania procesu lub funkcja, która została próbkowane najczęściej. Aby wyświetlić najbardziej aktywne ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcji, a następnie kliknij przycisk **Rozwiń ścieżkę aktywną**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawienie węzeł główny drzewa wywołań  
 Każdy proces, w trakcie uruchomienia profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewo wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz pozycję **zestawu głównego**.  
  
 Po ustawieniu węzła głównego, można wyeliminować wszystkie wpisy z widoku, z wyjątkiem drzewo podrzędne wybranego węzła. Aby przywrócić węzła głównego oryginalnego węzła, kliknij prawym przyciskiem myszy w oknie Widok drzewa wywołań i wybierz **resetowania głównego**.  
  
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
|**poziom**|Długość tej funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Próbki wyłączne**|Liczba próbek, które zostały zebrane w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań. Ta liczba nie obejmuje przykładów, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Wyłącznych próbek**|Procent wszystkie przykłady w trakcie uruchomienia profilowania, które były wyłącznych próbek w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
|**Próbki włączne**|Liczba próbek, które zostały zebrane w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań. Liczba ta obejmuje przykładów, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|  
|**% Włącznych próbek**|Procent wszystkie przykłady w trakcie uruchomienia profilowania, które były włącznych próbek w tej funkcji, wywołanego przez funkcję nadrzędnego w drzewie wywołań.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok drzewa wywołań - dane z próbkowania Profiler](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)



