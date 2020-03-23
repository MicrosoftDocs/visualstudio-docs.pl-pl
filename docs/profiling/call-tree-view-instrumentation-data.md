---
title: Widok drzewa wywołań - Dane oprzyrządowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7497f455ad3868f53758555aa28d305b6068e30d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773514"
---
# <a name="call-tree-view---instrumentation-data"></a>Widok drzewa wywołań — dane instrumentacji
Wartości funkcji w drzewie wywołań wskazują czas dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpień funkcji z całkowitym czasem włącznie wszystkich funkcji w przebiegu profilowania.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań, które zostały wykonane do tej funkcji.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji, które było spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych, które zostały spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od czasów all inclusive.|
|**Poziom**|Głębokość funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas na stosie wywołań tych wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych, które były wywoływane przez funkcję i w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|Całkowity czas włącznie wszystkich wywołań tej funkcji w tym kontekście.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został wydany w całkowitym czasie włącznie tej funkcji w tym kontekście.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji w tym kontekście.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji w tym kontekście.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który te wystąpienia funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań, były wykonywane kodu w treści funkcji; oznacza to, gdy funkcja była w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia. Jednak czas nie obejmuje czasu spędzonego w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Całkowity czas wyłączny wszystkich wywołań tej funkcji w tym kontekście.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został wydany w całkowitym czasie wyłącznym tej funkcji w tym kontekście.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji w tym kontekście.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że wystąpienia funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań były na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, Jednak czas obejmuje czas spędzony w funkcjach podrzędnych, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|Całkowita aplikacja włącznie czas wszystkich wywołań tej funkcji w tym kontekście.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie aplikacji tej funkcji w tym kontekście.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas, przez który te wystąpienia funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań, bezpośrednio wykonywały kod w treści funkcji; oznacza to, gdy funkcja była w górnej części stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia. Nie obejmuje również czasu spędzonego w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|Całkowity czas wyłączności aplikacji wszystkich wywołań tej funkcji w tym kontekście.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji w tym kontekście.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa połączeń](../profiling/call-tree-view-sampling-data.md)
- [Widok drzewa wywołań — instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
