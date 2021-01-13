---
title: Widok drzewa wywołań — dane Instrumentacji | Microsoft Docs
description: Dowiedz się więcej o tym, jak widok drzewa wywołań wyświetla informacje Instrumentacji w drzewie wywołań w Eksplorator wydajności.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9c846910da4dec636c073446ae63cffb7cb2a682
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150798"
---
# <a name="call-tree-view---instrumentation-data"></a>Widok drzewa wywołań — dane Instrumentacji
Wartości funkcji w drzewie wywołania wskazują czas dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpień funkcji z łącznym czasem trwania wszystkich funkcji w przebiegu profilowania.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań wykonanych dla tej funkcji.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, który został spowodowany przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, która została spowodowana przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|
|**Poziomie**|Głębokość funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne, które upłynęły, wskazują na czas w stosie wywołań tych wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych, które zostały wywołane przez funkcję i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|Łączny czas, który upłynął włącznie dla wszystkich wywołań tej funkcji w tym kontekście.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania w łącznym czasie trwania tej funkcji w tym kontekście.|
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął w tym kontekście w przypadku wywołania tej funkcji.|
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wykluczone wartości wskazują czas, przez jaki te wystąpienia funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań, wykonywały kod w treści funkcji. oznacza to, że gdy funkcja znajduje się w górnej części stosu wywołań. Czas obejmuje czas wywołań systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia. Jednak czas nie obejmuje czasu spędzonego w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Łączny czas wyłączny wszystkich wywołań tej funkcji w tym kontekście.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania w łącznym czasie trwania tej funkcji w tym kontekście.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny dla wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny czas wyłączny w wywołaniu tej funkcji w tym kontekście.|
|**Minimalny czas, który upłynął**|Minimalny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez jaki wystąpienia funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań, były na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, jednak czas ten obejmuje czas spędzony w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|Łączny czas (włącznie) wszystkich wywołań tej funkcji w tym kontekście.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która została wykorzystana w łącznym czasie włącznie aplikacji w tym kontekście.|
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji w tym kontekście w przypadku wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas, przez jaki te wystąpienia funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań, były bezpośrednio wykonywane w treści funkcji. oznacza to, że gdy funkcja znajduje się w górnej części stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia. Nie obejmuje to również czasu spędzonego w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|Łączny czas wyłączny aplikacji wszystkich wywołań tej funkcji w tym kontekście.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został spędzony w łącznym czasie trwania tej funkcji aplikacji w tym kontekście.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji w wywołaniu tej funkcji w tym kontekście.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)
- [Widok drzewa wywołań-Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Widok drzewa wywołań — próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
