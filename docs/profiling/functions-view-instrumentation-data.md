---
title: Widok funkcji — dane Instrumentacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 423b6d61af93c37e6fa83549ed3fa5d422128165
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779223"
---
# <a name="functions-view---instrumentation-data"></a>Widok funkcji — dane Instrumentacji
Widok raport funkcji zawiera listę danych profilowania według nazwy funkcji.

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
|**Nazwa procesu**|Nazwa procesu|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, który jest spowodowany przez instrumentację. Nie obejmuje to obciążeń w funkcjach, które zostały wywołane przez funkcję. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, która jest spowodowana przez instrumentację. Obejmuje to narzuty w funkcje, które zostały wywołane przez funkcję. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas polega na uwzględnieniu czasu spędzonego w funkcjach, które zostały wywołane przez funkcję i czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|Łączny czas, który upłynął włącznie dla wszystkich wywołań tej funkcji.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która była pobrana w czasie trwania tej funkcji.|
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął dla wywołania tej funkcji.|
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w wywołaniu tej funkcji.|
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w wywołaniu tej funkcji.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartość wyłączność wskazuje czas, przez który funkcja wykonywała kod w treści funkcji, czyli gdy funkcja była w górnej części stosu wywołań. Czas polega na uwzględnieniu czasu, który był poświęcony na wywołania systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Łączny czas, który upłynął dla wszystkich wywołań tej funkcji.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa łącznego czasu trwania uruchomienia profilowania, która nastąpiła w łącznym czasie trwania tej funkcji.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny, który upłynął w wywołaniu tej funkcji.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny, upłynął czas wyłączny wywołania tej funkcji.|
|**Minimalny czas, który upłynął**|Minimalny czas, który upłynął w przypadku wywołania tej funkcji.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale obejmuje on czas spędzony w funkcjach, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|Łączny czas aplikacji włącznie dla wszystkich wywołań tej funkcji.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która była pobrana w łącznym czasie włącznie aplikacji.|
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji.|
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji.|
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji dla wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia i nie obejmują czasu spędzonego w funkcjach, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|Łączny czas wyłączny aplikacji wszystkich wywołań tej funkcji.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został spędzony w łącznym czasie trwania tej funkcji przez aplikację.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji.|
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji.|
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji dla wywołania tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji-Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
