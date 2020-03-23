---
title: Widok funkcji — dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780055"
---
# <a name="functions-view---contention-data"></a>Widok funkcji — dane rywalizacji
Widok raportu funkcje danych rywalizacji zawiera listę funkcji w przebiegu profilowania, które zostały zablokowane przed wykonaniem podczas przebiegu profilowania.

 W poniższej tabeli wyjaśniono wartości, które są wyświetlane w widoku Funkcje pliku danych profilowania, który został zebrany przy użyciu metody współbieżności.

|Kolumna|Opis|
|------------|-----------------|
|**Ekskluzywny zablokowany czas**|Czas, w którym ta funkcja została zablokowana przed wykonywaniem kodu w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję nie jest uwzględniony.|
|**Ekskluzywny zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był wyłącznym zablokowany czas tej funkcji.|
|**Ekskluzywne twierdzenia**|Liczba, ile ta funkcja została zablokowana przed wykonywaniem kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.|
|**Ekskluzywne rywalizacje %**|Procent wszystkich rywalizacji w przebiegu profilowania były wyłączne twierdzenia tej funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Włącznie zablokowany czas**|Czas, przez który ta funkcja lub funkcja, która została wywołana przez tę funkcję, został zablokowany przed wykonaniem.|
|**Włącznie zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był włącznie zablokowany czas tej funkcji lub modułu.|
|**Rywalizacje włączające**|Liczba zablokowanych wykonywania tej funkcji lub funkcji wywoływanej przez tę funkcję.|
|**Rywalizacja włączająca %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były włącznie rywalizacji tej funkcji lub modułu.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym funkcja była wykonywana.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji](../profiling/functions-view.md)
- [Widok funkcji - instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
