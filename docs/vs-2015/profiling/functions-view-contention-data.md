---
title: Widok funkcji — dane rywalizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141895"
---
# <a name="functions-view---contention-data"></a>Widok funkcji — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok raport dotyczący danych rywalizacji zawiera funkcje w przebiegu profilowania, które zostały zablokowane przed wykonaniem podczas przebiegu profilowania.  
  
 W poniższej tabeli objaśniono wartości, które są wyświetlane w widoku funkcje w pliku danych profilowania, który został zebrany przy użyciu metody współbieżności.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Wyłączny czas blokowania**|Czas, w którym ta funkcja została zablokowana do wykonywania kodu w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję, nie jest uwzględniany.|  
|**% Wyłącznego czasu blokowania**|Procent całego zablokowanego czasu w przebiegu profilowania, który był wyłącznym czasem blokowania tej funkcji.|  
|**Rywalizacje wyłączne**|Liczba przypadków, w których ta funkcja została zablokowana na podstawie wykonywania kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane.|  
|**Zawartość wyłącznych%**|Procent wszystkich rywalizacji w przebiegu profilowania miał wyłączne rywalizacje tej funkcji.|  
|**Adres funkcji**|Adres funkcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|  
|**Włączny czas blokowania**|Czas, przez który ta funkcja lub funkcja, która została wywołana przez tę funkcję, została zablokowana.|  
|**% Włącznego czasu blokowania**|Wartość procentowa wszystkich zablokowanych godzin w przebiegu profilowania, która była włącznie z zablokowanym czasem dla tej funkcji lub modułu.|  
|**Rywalizacje włączne**|Liczba przypadków, w których ta funkcja lub funkcja, która została wywołana przez tę funkcję, została zablokowana.|  
|**% Rywalizacji włącznych**|Wartość procentowa wszystkich rywalizacji w przebiegu profilowania, które były łącznymi zawartością tej funkcji lub modułu.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym uruchomiono funkcję.|  
|**Nazwa procesu**|Nazwa procesu|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji](../profiling/functions-view.md)   
 [Widok funkcji-Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)   
 [Widok funkcji](../profiling/functions-view-sampling-data.md)
