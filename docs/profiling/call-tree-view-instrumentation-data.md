---
title: Widok drzewa wywołań - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a838a511c5f37a00ed2331d2376b395f399e65d2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638104"
---
# <a name="call-tree-view---instrumentation-data"></a>Widok drzewa wywołań - dane Instrumentacji
Wartości dla funkcji w drzewie wywołań wskazują godzinę dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpień funkcji łączny całkowity czas, który upłynął, wszystkich funkcji w trakcie uruchomienia profilowania.

## <a name="general"></a>Ogólne
 Ogólne kolumn identyfikować ich funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba wywołań**|Całkowita liczba wywołań, które zostały wprowadzone do tej funkcji.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Narzut sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, które zostało spowodowane przez Instrumentację. Narzut sondy odjęciu z cały czas wyłączny.|
|**Narzut sondy czasu Włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, które zostało spowodowane przez Instrumentację. Narzut sondy odjęciu z cały czas (włącznie).|
|**Poziom**|Głębokość funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|

## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości
 Upłynęło wartości włącznie wskazują godzinę na stosie wywołań wystąpień tych funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań. Czas obejmuje czas spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję, jak i w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Całkowity czas, który upłynął**|Łączny całkowity czas wszystkie wywołania do tej funkcji, w tym kontekście, który upłynął.|
|**% Całkowitego czasu, który upłynął**|Wartość procentowa całkowity czas całkowity czas uruchomienia profilowania przeznaczony całkowity czas całkowity czas tej funkcji, w tym kontekście.|
|**Średnia liczba upłynęło włącznie czasu**|Średni całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|
|**Maksymalny czas, który upłynął (włącznie)**|Maksymalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|
|**Min upłynęło włącznie czasu**|Minimalny całkowity czas wywołania tej funkcji, w tym kontekście, który upłynął.|

## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości
 Czas wyłączny wartości wskazują czasu wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań zostały wykonywanie kodu w treści funkcji; oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań. Czas obejmuje czas w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia. Jednak podczas nie obejmuje czas spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Suma własny czas wszystkie wywołania do tej funkcji, w tym kontekście, który upłynął.|
|**% Wyłącznego czasu, który upłynął**|Łączny czas wyłączny czas tej funkcji, w tym kontekście przeznaczony procent całkowity czas własny czas uruchomienia profilowania.|
|**Średnia liczba upłynęło wyłącznie czasu**|Średni własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|
|**Min upłynęło wyłącznie czasu**|Minimalny własny czas wywołania tej funkcji, w tym kontekście, który upłynął.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Aplikacji wartości włącznie wskazują czas wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań znajdowały się w stosie wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia, jednak czas uwzględnia czas spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Całkowity czas aplikacji**|Łączny całkowity czas aplikacji dla wszystkich wywołań tej funkcji, w tym kontekście.|
|**% Całkowitego czasu aplikacji**|Wartość procentowa całkowity czas całkowity czas uruchomienia profilowania był poświęcony w kompletnej aplikacji, całkowity czas tej funkcji, w tym kontekście.|
|**Średni całkowity czas aplikacji**|Średni całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|
|**Maksymalny całkowity czas aplikacji**|Maksymalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|
|**Minimalny całkowity czas aplikacji**|Minimalny całkowity czas aplikacji wywołania tej funkcji, w tym kontekście.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Aplikacja wyłączne wartości wskazują czasu, że wystąpień funkcji, które zostały wywołane przez funkcję nadrzędnego w drzewie wywołań bezpośrednio wykonywały kod w treści funkcji; oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań. Czas nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia. Ponadto nie obejmuje czas spędzony w funkcji podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Własny czas aplikacji**|Łączna liczba własny czas aplikacji dla wszystkich wywołań tej funkcji, w tym kontekście.|
|**% Własnego czasu aplikacji**|Wartość procentowa całkowity czas własny czas uruchomienia profilowania przeznaczony własny czas aplikacji całkowita tej funkcji, w tym kontekście.|
|**Średni własny czas aplikacji**|Średni własny czas aplikacji wywołania tej funkcji, w tym kontekście.|
|**Maksymalny własny czas aplikacji**|Maksymalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|
|**Minimalny własny czas aplikacji**|Minimalny własny czas aplikacji wywołania tej funkcji, w tym kontekście.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok drzewa wywołań](../profiling/call-tree-view-sampling-data.md)
- [Widok drzewa wywołań - Instrumentacja](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Drzewo wywołań view - próbkowanie](../profiling/call-tree-view-dotnet-memory-sampling-data.md)