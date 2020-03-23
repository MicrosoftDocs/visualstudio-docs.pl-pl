---
title: Widok drzewa wywołań — dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 558cef408ceca48a55563ae31f2399da0e951b8e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779756"
---
# <a name="call-tree-view---sampling-data"></a>Widok drzewa wywołań — dane próbkowania
Widok Drzewa wywołań wyświetla ścieżki wykonywania funkcji, które zostały przesuniętych w profilowanej aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywołuje i dane wydajności o tych wywołań funkcji.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z całkowitą liczbą próbek w przebiegu profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnianie ścieżki aktywnej wykonania
 Widok drzewa wywołań można rozwinąć i wyróżnić ścieżkę wykonywania procesu lub funkcji, która była najczęściej próbkowania. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Aby ustawić węzeł początkowy widoku Drzewa wywołań, kliknij prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierz polecenie **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku z wyjątkiem poddrzewa wybranego węzła. Aby zresetować węzeł główny z powrotem do oryginalnego węzła, kliknij prawym przyciskiem myszy okno Widok drzewa wywołań i wybierz polecenie **Resetuj katalog główny**.

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
|**Poziom**|Głębokość tej funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Ekskluzywne próbki**|Liczba próbek, które zostały zebrane w tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań. Liczba ta nie obejmuje próbek, które zostały zebrane w funkcjach, które zostały wywołane przez funkcję.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Próbki włączające**|Liczba próbek, które zostały zebrane w tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań. Liczba ta obejmuje przykłady, które zostały zebrane w funkcjach, które były wywoływane przez funkcję.|
|**Próbki włącznie %**|Procent wszystkich próbek w przebiegu profilowania, które były włącznie próbki tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa wywołań — dane próbkowania profilera](../profiling/call-Tree-view-sampling-data.md)
- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Widok drzewa wywołań — instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-instrumentation-data.md)
