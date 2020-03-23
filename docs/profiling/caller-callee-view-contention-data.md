---
title: Rozmówca - Callee View - Dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 083386a808f7b91a18b3ea685ae657118c723978
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779743"
---
# <a name="callercallee-view----contention-data"></a>Widok wywołujący/wywoływany — dane rywalizacji
W widoku Wywołujący/Wywoływany są wyświetlane informacje o rywalizacji dla wybranej funkcji oraz jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje o rywalizacji dla wybranej funkcji. Wartości obejmują wszystkie rywalizacje blokowania dla funkcji.

 **Funkcje, które wywoływały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują poszczególne wkłady funkcji wywołującego (nadrzędnego) do wartości wybranej (bieżącej) funkcji.

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje informacje rywalizacji dla wywoływane (podrzędne) funkcje wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** - bieżąca funkcja<br />-   **1** - funkcja, która wywołuje bieżącą funkcję<br />-   **2** - funkcja wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Ekskluzywny zablokowany czas**|- Dla bieżącej funkcji czas, że ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Zablokowany czas w funkcjach wywoływanych przez funkcję nie jest uwzględniony.<br />- Dla funkcji wywołującego, część wyłącznego zablokowanego czasu bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywała bieżącą funkcję.<br />- Dla funkcji wywoływanego czas, że ta funkcja została zablokowana wykonywanie własnego kodu, gdy ta funkcja została wywołana przez bieżącą funkcję. Zablokowany czas w funkcjach podrzędnych wywoływanych przez funkcję wywoływana nie jest uwzględniony.|
|**Ekskluzywny zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był wyłączny zablokowany czas dla tej funkcji w tym kontekście.|
|**Ekskluzywne twierdzenia**|- Dla bieżącej funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Twierdzenia, które wystąpiły w funkcjach, które były wywoływane przez funkcję nie są uwzględniane.<br />- Dla funkcji wywołującego liczba wyłącznych rywalizacji bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywała się bieżącą funkcją.<br />- Dla funkcji wywoływanej, liczba razy, że ta funkcja została zablokowana z wykonywania kodu w treści funkcji, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacje, które wystąpiły w funkcjach wywoływanych przez funkcję wywoływana nie są uwzględniane.|
|**Ekskluzywne rywalizacje %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były wyłączne rywalizacji dla tej funkcji w tym kontekście.|
|**Adres funkcji**|Adres funkcji lub token.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Włącznie zablokowany czas**|- Dla bieżącej funkcji czas, że ta funkcja lub jedna z funkcji, które zostały wywołane przez tę funkcję został zablokowany z wykonywania. Zablokowany czas w funkcjach, które były wywoływane przez bieżącą funkcję jest uwzględniony.<br />- Dla funkcji wywołującego, część włącznie zablokowany czas bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywa bieżącą funkcję.<br />- Dla funkcji wywoływanej czas, że ta funkcja lub jedna z funkcji, która została wywołana przez funkcję została zablokowana wykonywanie, gdy ta funkcja została wywołana przez bieżącą funkcję. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję wywoływana jest uwzględniony.|
|**Włącznie zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był włącznie zablokowany czas dla tej funkcji w tym kontekście.|
|**Rywalizacje włączające**|- Dla bieżącej funkcji, liczba razy, że ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję została zablokowana wykonywanie. Rywalizacje, które wystąpiły w funkcjach, które były wywoływane przez funkcję są uwzględniane.<br />- Dla funkcji wywołującego liczba włącznie rywalizacji bieżącej funkcji, która wystąpiła, gdy ta funkcja nazywa się bieżącą funkcję.<br />- Dla funkcji wywoływanej, liczba razy, że ta funkcja lub jedna z funkcji, które zostały wywołane przez funkcję została zablokowana wykonywanie, gdy ta funkcja została wywołana przez bieżącą funkcję. Rywalizacje, które wystąpiły w funkcjach wywoływanych przez funkcję wywoływana są uwzględniane.|
|**Rywalizacja włączająca %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były wyłączne rywalizacji dla tej funkcji w tym kontekście.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wystąpiły rywalizacje.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok rozmówca/wywoływany](../profiling/caller-callee-view.md)
- [Widok wywołujący/wywoływany — dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany — dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok rozmówcy/wywoływania — dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)
