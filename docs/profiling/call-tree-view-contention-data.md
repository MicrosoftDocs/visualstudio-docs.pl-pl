---
title: Widok drzewa wywołań — dane rywalizacji | Microsoft Docs
description: Przejrzyj widok drzewa wywołań, który pokazuje dane rywalizacji o ścieżki wykonywania funkcji przenoszone w profilowanej aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d6c444bba23ca216b058544d0ceae0d3d312fd4d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892375"
---
# <a name="call-tree-view---contention-data"></a>Widok drzewa wywołań — dane rywalizacji
W widoku drzewa wywołań są wyświetlane ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich wywoływanych przez nią funkcji, liczbę przedziałów czasu, przez jaką funkcja została zablokowana i ilość czasu, przez który funkcja została zablokowana, ponieważ była dla zasobu z innymi wątkami lub procesami.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji do całkowitej liczby rywalizacji w przebiegu profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnij gorącą ścieżkę wykonywania
 Widok drzewa wywołań może rozwinąć i wyróżnić ścieżkę wykonywania procesu lub funkcji, która utworzyła najwięcej rywalizacji.

- Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustaw węzeł główny drzewa wywołań
 Każdy proces w przebiegu profilowania pojawia się jako węzeł główny. Aby ustawić węzeł początkowy widoku drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie kliknij pozycję **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Aby przywrócić węzeł główny z powrotem do oryginalnego węzła, kliknij prawym przyciskiem myszy w widoku drzewa wywołań, a następnie kliknij polecenie **Zresetuj katalog główny**.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|Czas blokowania wykonywania wystąpień tej funkcji w tej ścieżce wykonywania w przebiegu profilowania. Czas nie obejmuje blokowania czasu funkcji podrzędnych, które zostały wywołane przez funkcję.|
|**% Wyłącznego czasu blokowania**|Procent całego zablokowanego czasu w przebiegu profilowania, który miał wyłączny czas zablokowany dla tej funkcji w tej ścieżce wykonania.|
|**Rywalizacje wyłączne**|Liczba rywalizacji, które wystąpiły w wystąpieniach tej funkcji w tej ścieżce wykonania. Liczba nie obejmuje rywalizacji o funkcje podrzędne wywoływane przez funkcję.|
|**Zawartość wyłącznych%**|Procent wszystkich rywalizacji w przebiegu profilowania, który miał wyłuskane rywalizacje wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.|
|**Adres funkcji**|Adres funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Włączny czas blokowania**|Łączny czas, w którym wystąpienia tej funkcji w tej ścieżce wykonania zostały zablokowane w przebiegu profilowania. Czas obejmuje zablokowany czas funkcji podrzędnych wywoływanych przez funkcję.|
|**% Włącznego czasu blokowania**|Wartość procentowa wszystkich zablokowanych godzin w przebiegu profilowania, która była włącznie czasowo zablokowanym dla wystąpień tej funkcji w tej ścieżce wykonania.|
|**Rywalizacje włączne**|Całkowita liczba rywalizacji, które zablokowały wystąpienia tej funkcji w tej ścieżce wykonania. Liczba zawiera zawartość funkcji podrzędnych wywoływanych przez funkcję.|
|**% Rywalizacji włącznych**|Wartość procentowa wszystkich rywalizacji w przebiegu profilowania, które były łącznymi rywalizacjami wystąpień tej funkcji w tej ścieżce wykonania.|
|**Poziomie**|Poziom funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia VSReport. Aby uzyskać więcej informacji, zobacz w [VSPerfReport](../profiling/vsperfreport.md).|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa wywołań](../profiling/call-tree-view.md)
- [Widok drzewa wywołań-Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Widok drzewa wywołań](../profiling/call-tree-view-instrumentation-data.md)
- [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)
