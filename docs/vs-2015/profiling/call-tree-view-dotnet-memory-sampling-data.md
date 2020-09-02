---
title: Widok drzewa wywołań — dane próbkowania pamięci platformy .NET | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150755"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Widok drzewa wywołań — dane próbkowania pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W widoku drzewa wywołań są wyświetlane ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera wszystkie funkcje, które zostały wywołane i dane alokacji pamięci .NET dotyczące tych wywołań funkcji.  
  
 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z łączną liczbą lub rozmiarem alokacji w ramach uruchomienia profilowania.  
  
## <a name="highlighting-the-execution-hot-path"></a>Wyróżnianie gorącej ścieżki wykonywania  
 Widok drzewa wywołań może rozwijać i wyróżniać ścieżkę wykonywania procesu lub funkcji, która utworzyła największe lub większość obiektów pamięci. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę gorącą**.  
  
## <a name="setting-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań  
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewa wywołań na inny węzeł, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz polecenie **Ustaw katalog główny**.  
  
 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Możesz zresetować węzeł główny z powrotem do węzła, który był przeglądany; Kliknij prawym przyciskiem myszy w oknie widok drzewa wywołań i wybierz polecenie **Zresetuj katalog główny**.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres funkcji.|  
|**Poziomie**|Głębokość funkcji w drzewie wywołań.|  
|**Przydziały włączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba obejmuje przydziały, które zostały wykonane przez funkcje podrzędne.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były przydzielone do tej funkcji.|  
|**Alokacje wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały wykonane przez funkcje podrzędne.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które wystąpiły na wyłączność alokacji wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.|  
|**Bajty włączne**|Liczba bajtów w pamięci przydzielonej przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba obejmuje przydziały, które zostały wykonane przez funkcje podrzędne.|  
|**% Bajtów włącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która obejmuje przydziały tej funkcji.|  
|**Bajty wyłączne**|Liczba bajtów w pamięci przydzielonej przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały wykonane przez funkcje podrzędne.|  
|**% Bajtów wyłącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która wystąpiła na wyłączność alokacji tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok drzewa wywołań-Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)
