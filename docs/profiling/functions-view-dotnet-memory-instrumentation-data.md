---
title: Widok funkcji — dane Instrumentacji pamięci platformy .NET | Microsoft Docs
description: Uzyskaj informacje o widoku funkcji dla danych profilowania przydziału pamięci platformy .NET zebranych za pomocą metody instrumentacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a26ce757ade9428326e54d3c21050b7df8d9a620
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916570"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Widok funkcji — dane Instrumentacji pamięci platformy .NET
Widok funkcji dla danych profilowania przydziału pamięci platformy .NET zebranych za pomocą metody instrumentacji zawiera listę funkcji, które przydzieliły pamięć podczas przebiegu profilowania. Wiersz funkcji zgłasza rozmiar i liczbę alokacji oraz dane chronometrażu funkcji.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań wykonanych dla tej funkcji.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji ze względu na instrumentację. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych ze względu na instrumentację. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|

## <a name="net-memory-values"></a>Wartości pamięci platformy .NET
 Wartości pamięci platformy .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcję i jej funkcje podrzędne.

 Wartości pamięci wyłącznej wskazują liczbę i rozmiar obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcje podrzędne.

|Kolumna|Opis|
|------------|-----------------|
|**Przydziały włączne**|Całkowita liczba obiektów, które zostały utworzone w tej funkcji oraz w funkcjach, które zostały wywołane przez tę funkcję.|
|**% Przydziałów włącznych**|Wartość procentowa wszystkich obiektów, które zostały przydzielone w ramach uruchomienia profilowania, które były przydzielane przez tę funkcję.|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone, gdy funkcja wykonywała kod w treści funkcji. Ta liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które wystąpiły na wyłączność alokacji tej funkcji.|
|**Bajty włączne**|Liczba bajtów pamięci przydzielonej w tej funkcji oraz w funkcjach, które zostały wywołane przez tę funkcję.|
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci, które zostały przydzieloną w przebiegu profilowania, które były w bajtach tej funkcji.|
|**Bajty wyłączne**|Liczba bajtów pamięci przydzielonej przez tę funkcję, ale nie przez funkcje, które zostały wywołane przez tę funkcję.|
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci, które zostały przydzieloną w ramach uruchomienia profilowania, które były wyłącznych bajtów tej funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|Łączny czas, który upłynął włącznie dla wszystkich wywołań tej funkcji.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która była pobrana w czasie trwania tej funkcji.|
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął dla wywołania tej funkcji.|
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w wywołaniu tej funkcji.|
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w wywołaniu tej funkcji.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas wywołań systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Łączny czas, który upłynął dla wszystkich wywołań tej funkcji.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa łącznego czasu trwania uruchomienia profilowania, która nastąpiła w łącznym czasie trwania tej funkcji.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny, który upłynął w wywołaniu tej funkcji.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny, upłynął czas wyłączny wywołania tej funkcji.|
|**Minimalny czas, który upłynął**|Minimalny czas, który upłynął w przypadku wywołania tej funkcji.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|Łączny czas aplikacji włącznie dla wszystkich wywołań tej funkcji.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która była pobrana w łącznym czasie włącznie aplikacji.|
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji.|
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji.|
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji dla wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ani nie obejmują czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|Łączny czas wyłączny aplikacji wszystkich wywołań tej funkcji.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został spędzony w łącznym czasie trwania tej funkcji przez aplikację.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji.|
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji.|
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji dla wywołania tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
