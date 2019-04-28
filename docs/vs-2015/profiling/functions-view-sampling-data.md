---
title: Widok funkcji - dane próbkowania | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432940"
---
# <a name="functions-view---sampling-data"></a>Widok funkcji — dane próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok raportu funkcji dla pożądana metoda profilowania próbkowania Wyświetla listę funkcji, które zostały poddane próbkowaniu podczas uruchomienia profilowania.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Próbki włączne**|Łączna liczba próbek, które zostały zebrane podczas wykonywania tej funkcji; oznacza to, że liczba próbek, które zostały zebrane podczas tej funkcji na stosie wywołań. Liczba przykłady, które zostały zebrane podczas wykonywania zostały funkcje, które zostały wywołane przez tę funkcję.|  
|**% Włącznych próbek**|Wartość procentowa wszystkie przykłady w uruchomienia profilowania były włącznych próbek w tej funkcji.|  
|**Próbki wyłączne**|Łączna liczba próbek, które zostały zebrane podczas wykonywania kodu w treści tej funkcji; oznacza to, gdy ta funkcja została szczycie stosu wywołań. Przykłady, które zostały zebrane w funkcjach, które były wywoływane przez tę funkcję, nie są uwzględniane.|  
|**% Wyłącznych próbek**|Wartość procentowa wszystkie przykłady w uruchomienia profilowania były wyłącznych próbek w tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
