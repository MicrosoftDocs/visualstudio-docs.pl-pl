---
title: Widok funkcji - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
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
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfdfbab17538648b816c094409f9396cc5f638b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788319"
---
# <a name="functions-view---net-memory-sampling-data"></a>Widok funkcji — dane próbkowania pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok funkcji danych, które zostały zebrane przy użyciu metody pobierania próbek profilowania alokacji pamięci .NET zawiera listę funkcji, które pamięci przydzielonej podczas uruchomienia profilowania i zgłasza rozmiar i liczba przydziałów.  
  
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
|**Przydziały włączne**|Całkowita liczba przydzielonych w tej funkcji i jej funkcji podrzędnych obiektów.|  
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów włącznych tej funkcji.|  
|**Przydziały wyłączne**|Liczba obiektów, które zostały utworzone podczas wykonywania bezpośrednio w górnej części stosu wywołań funkcji. Ta liczba nie obejmuje obiekty, które zostały utworzone w funkcjach podrzędnych.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów wyłącznych tej funkcji.|  
|**Bajty włączne**|Liczba bajtów pamięci, które zostały przydzielone przez tej funkcji i jej funkcji podrzędnych.|  
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były bajty włączne tej funkcji.|  
|**Bajty wyłączne**|Liczba bajtów pamięci przydzielonych przez tę funkcję, ale nie przez jej funkcji podrzędnych.|  
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były bajty wyłączne tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)



