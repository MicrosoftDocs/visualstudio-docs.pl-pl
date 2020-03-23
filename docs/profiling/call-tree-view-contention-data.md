---
title: Widok drzewa wywołań — dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e91e231f72b006d2020c8b4d5d96c7e24fa1dd9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779782"
---
# <a name="call-tree-view---contention-data"></a>Widok drzewa wywołań — dane rywalizacji
Widok Drzewa wywołań wyświetla ścieżki wykonywania funkcji, które zostały przesuniętych w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywoływał, ile razy funkcja została zablokowana i czas, przez jaki funkcja została zablokowana, ponieważ rywalizowała o zasób z innymi wątkami lub procesami.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z całkowitą liczbą rywalizacji w przebiegu profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnianie ścieżki aktywnej wykonania
 Widok drzewa wywołań można rozwinąć i wyróżnić ścieżkę wykonywania procesu lub funkcji, która utworzyła najwięcej rywalizacji.

- Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku Drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie kliknij polecenie **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Aby zresetować węzeł główny z powrotem do oryginalnego węzła, kliknij prawym przyciskiem myszy widok Drzewo wywołań, a następnie kliknij polecenie **Resetuj katalog główny**.

|Kolumna|Opis|
|------------|-----------------|
|**Ekskluzywny zablokowany czas**|Czas, że wystąpienia tej funkcji w tej ścieżce wykonywania zostały zablokowane przed wykonywaniem w przebiegu profilowania. Czas nie obejmuje zablokowanego czasu funkcji podrzędnych, które zostały wywołane przez funkcję.|
|**Ekskluzywny zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był wyłączny zablokowany czas dla tej funkcji w tej ścieżce wykonywania.|
|**Ekskluzywne twierdzenia**|Liczba rywalizacji, które wystąpiły w wystąpieniach tej funkcji w tej ścieżce wykonywania. Liczba nie zawiera rywalizacji funkcji podrzędnych wywoływanych przez funkcję.|
|**Ekskluzywne rywalizacje %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były wyłączne rywalizacje wystąpień tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.|
|**Adres funkcji**|Adres funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Włącznie zablokowany czas**|Całkowity czas, przez który wystąpienia tej funkcji w tej ścieżce wykonywania zostały zablokowane przed wykonaniem w przebiegu profilowania. Czas obejmuje zablokowany czas funkcji podrzędnych wywoływanych przez funkcję.|
|**Włącznie zablokowany czas %**|Procent wszystkich zablokowany czas w przebiegu profilowania, który był włącznie zablokowany czas dla wystąpień tej funkcji w tej ścieżce wykonywania.|
|**Rywalizacje włączające**|Całkowita liczba rywalizacji, które zablokowały wystąpienia tej funkcji w tej ścieżce wykonywania. Liczba zawiera rywalizacji funkcji podrzędnych wywoływanych przez funkcję.|
|**Rywalizacja włączająca %**|Procent wszystkich rywalizacji w przebiegu profilowania, które były włącznie rywalizacji wystąpień tej funkcji w tej ścieżce wykonywania.|
|**Poziom**|Poziom funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia VSReport. Aby uzyskać więcej informacji, zobacz w [VSPerfReport](../profiling/vsperfreport.md).|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa połączeń](../profiling/call-tree-view.md)
- [Widok drzewa wywołań — instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-instrumentation-data.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-sampling-data.md)
