---
title: Widok drzewa wywołań — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76ea78f37cbc8c5e2b6df900aa0e3f320346300a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779769"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Widok drzewa wywołań — dane próbkowania pamięci .NET
Widok Drzewa wywołań wyświetla ścieżki wykonywania funkcji, które zostały przesuniętych w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywołuje i .NET danych alokacji pamięci o tych wywołaniach funkcji.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z całkowitą liczbą lub rozmiarem alokacji w przebiegu profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnianie ścieżki aktywnej wykonania
 Widok drzewa wywołań można rozwinąć i wyróżnić ścieżkę wykonywania procesu lub funkcji, która utworzyła największe lub większość obiektów pamięci. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku Drzewa wywołań na inny węzeł, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz polecenie **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku z wyjątkiem poddrzewa wybranego węzła. Węzeł główny można zresetować z powrotem do węzła, który był oglądany; kliknij prawym przyciskiem myszy okno Widok drzewa wywołań i wybierz polecenie **Resetuj katalog główny**.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Poziom**|Głębokość funkcji w drzewie wywołań.|
|**Alokacje włącznie**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta obejmuje alokacje, które zostały wykonane przez funkcje podrzędne.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Alokacje wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta nie obejmuje alokacji, które zostały wykonane przez funkcje podrzędne.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były wyłączne alokacje wystąpień funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań.|
|**Bajty włącznie**|Liczba bajtów w pamięci, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta obejmuje alokacje, które zostały wykonane przez funkcje podrzędne.|
|**Bajty włącznie %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Bajty wyłączne**|Liczba bajtów w pamięci, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta nie obejmuje alokacji, które zostały wykonane przez funkcje podrzędne.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Widok drzewa wywołań — instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-sampling-data.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-instrumentation-data.md)
