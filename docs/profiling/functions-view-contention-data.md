---
title: Widok funkcji - dane Kontencji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dcea1097b33c612094c4a7eb35b240c28f8bde0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969748"
---
# <a name="functions-view---contention-data"></a>Widok funkcji — dane rywalizacji
Raport funkcji widoku list danych rywalizacji o zasoby funkcji w trakcie uruchomienia profilowania, które zostały zablokowane z wykonanie w trakcie uruchomienia profilowania.

 W poniższej tabeli przedstawiono wartości, które są wyświetlane w widoku funkcji w pliku danych profilowania, które zostały zebrane za pomocą metody współbieżności.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|Ilość czasu, w którym ta funkcja został zablokowany wykonywanie kodu w treści funkcji. Czas blokowania w funkcjach, które zostały wywołane przez funkcję nie jest włączony.|
|**% Własnego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, który był wyłączny czas blokowania w tej funkcji.|
|**Rywalizacje wyłączne**|Liczba przypadków, które tej funkcji został zablokowany wykonywanie kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.|
|**% Rywalizacji wyłącznych**|Wartość procentowa rywalizacji wszystkich podczas uruchomienia profilowania były rywalizacji wyłącznych tej funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Całkowity czas blokowania**|Czas, jaki ta funkcja lub funkcja, która została wywołana przez tę funkcję zablokowano wykonywania.|
|**% Całkowitego czasu blokowania**|Procent wszystkich czas blokowania podczas uruchomienia profilowania, który był całkowity czas blokowania w tej funkcji lub modułu.|
|**Rywalizacje włączne**|Ile razy ta funkcja lub funkcja, która została wywołana przez tę funkcję zablokowano wykonywania.|
|**% Rywalizacji włącznych**|Wartość procentowa wszystkie rywalizacje w uruchomienia profilowania były rywalizacji włącznych tej funkcji lub modułu.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wykonywania funkcji.|
|**Nazwa procesu**|Nazwa procesu.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji](../profiling/functions-view.md)
- [Widok funkcji - Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji - próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)