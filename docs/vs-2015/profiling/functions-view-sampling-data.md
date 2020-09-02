---
title: Widok funkcji — dane próbkowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5aace03631cd768566dca8e314f280e20d9de77f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808228"
---
# <a name="functions-view---sampling-data"></a>Widok funkcji — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok raport funkcji dla metody profilu próbkowania zawiera listę funkcji, które były próbkowane podczas przebiegu profilowania.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Próbki włączne**|Całkowita liczba próbek zebranych podczas wykonywania tej funkcji; oznacza to, że liczba próbek zebranych, gdy ta funkcja była w stosie wywołań. Liczba zawiera próbki, które zostały zebrane, gdy funkcje, które zostały wywołane przez tę funkcję, były wykonywane.|  
|**Próbki włączne%**|Procent wszystkich próbek w przebiegu profilowania, który był włączonych próbek tej funkcji.|  
|**Próbki wyłączne**|Całkowita liczba próbek zebranych podczas wykonywania kodu w treści tej funkcji; oznacza to, że gdy ta funkcja znajduje się w górnej części stosu wywołań. Próbki, które zostały zebrane w funkcjach, które zostały wywołane przez tę funkcję, nie są uwzględniane.|  
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji-Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
