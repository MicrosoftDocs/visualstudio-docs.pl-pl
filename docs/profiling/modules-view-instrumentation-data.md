---
title: Widok modułów — dane Instrumentacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6449ad30edf11d3d315532cc33db2a79c14f90b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778534"
---
# <a name="modules-view---instrumentation-data"></a>Widok modułów — dane Instrumentacji
Widok moduły przedstawia dane wydajności pogrupowane według modułów, które znajdowały się w danych profilowania. Funkcje modułu są wymienione poniżej węzła modułu.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji lub modułu.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba wywołań**|Całkowita liczba wywołań wykonanych dla tej funkcji lub modułu.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu, w którym uruchomiono moduł lub funkcję.|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji lub modułu ze względu na instrumentację.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji lub modułu oraz jej funkcji podrzędnych z powodu Instrumentacji.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|-Dla funkcji, czas spędzony w funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />-Dla modułu, czas, w którym co najmniej jedna funkcja w module znajdowała się na stosie wywołań.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania w łącznym czasie trwania tego modułu lub funkcji.|
|**Średni łączny czas, który upłynął**|-Dla funkcji — średni czas włączny, który upłynął w przypadku wywołania tej funkcji.<br />— Dla modułu, średni czas włączny, który upłynął dla wszystkich wywołań funkcji w module.|
|**Maksymalny łączny czas, który upłynął**|-Dla funkcji — maksymalny czas, który upłynął, włącznie wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas, który upłynął włącznie, dla wszystkich wywołań funkcji w module.|
|**Minimalny łączny czas, który upłynął**|-Dla funkcji — minimalny czas, który upłynął, włącznie wywołania tego modułu lub funkcji.<br />-Dla modułu, minimalny czas, który upłynął włącznie dla wszystkich wywołań funkcji w module.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|-Dla funkcji, czas spędzony w module lub funkcji. Obejmuje to wywołania systemu operacyjnego, takie jak przełączenia kontekstu i operacje wejścia/wyjścia, ale wyklucza czas spędzony w funkcjach podrzędnych.<br />-Dla modułu, suma czasu wyłącznego dla funkcji w module.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa łącznego czasu trwania uruchomienia profilowania, która nastąpiła w łącznym czasie trwania tego modułu lub funkcji.|
|**Średni czas wyłączny, który upłynął**|— Dla funkcji — średni czas, który upłynął w przypadku wywołania tej funkcji.<br />— Dla modułu, średni czas wyłączny wszystkich wywołań funkcji w module.|
|**Maksymalny czas wyłączny, który upłynął**|— Dla funkcji, maksymalny czas wyłączny wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas, który upłynął, przez wszystkie wywołania funkcji w module.|
|**Minimalny czas, który upłynął**|— Dla funkcji — minimalny czas, który upłynął podczas wywołania tego modułu lub funkcji.<br />— W przypadku modułu minimalny czas, który upłynął, w przypadku wszystkich wywołań funkcji w module.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia. Jednak ten czas obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|-Dla funkcji, czas spędzony w wywołaniach funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych, ale wyklucza wywołania systemu operacyjnego, takie jak operacje przełączania kontekstu i operacji wejścia/wyjścia.<br />-Dla modułu, czas, w którym co najmniej jedna funkcja w module znajdowała się na stosie wywołań. Wyklucza to czas spędzony w wywołaniach systemu operacyjnego.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która została wykorzystana w czasie trwania tego modułu lub funkcji przez aplikację.|
|**Średni czas włączny aplikacji**|-Dla funkcji — średni czas włączny aplikacji wywołania tej funkcji.<br />-Dla modułu, średni czas włączania wszystkich wywołań funkcji w module.|
|**Maksymalny czas włączny aplikacji**|-Dla funkcji — maksymalny czas włączny aplikacji wywołania tej funkcji.<br />— W przypadku modułu maksymalny czas trwania wszystkich wywołań funkcji w module.|
|**Minimalny czas włączny aplikacji**|-Dla funkcji, minimalna godzina włącznego wywołania do tego modułu lub funkcji.<br />— W przypadku modułu minimalna dołączenia do funkcji w module (włącznie).|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas spędzony w module lub funkcji. Wyklucza to czas spędzony w funkcjach podrzędnych, a także wyklucza wywołania systemu operacyjnego, takie jak operacje przełączania kontekstu i operacji wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|Łączny czas wyłączny aplikacji wszystkich wywołań tego modułu lub funkcji.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został wykorzystany w niepełnym czasie aplikacji tego modułu lub funkcji.|
|**Średni czas wyłączny aplikacji**|-Dla funkcji — średni czas wyłączny aplikacji wywołania tej funkcji.<br />— Dla modułu, średni czas wyłączny aplikacji dla wszystkich wywołań funkcji w module.|
|**Maksymalny czas wyłączny aplikacji**|— W przypadku funkcji maksymalny czas wyłączny aplikacji wywołania tej funkcji.<br />— W przypadku modułu maksymalna, wyłączny czas aplikacji dla wszystkich wywołań funkcji w module.|
|**Minimalny czas wyłączny aplikacji**|— W przypadku funkcji jest to minimalny czas wyłączny aplikacji wywołania tego modułu lub funkcji.<br />— W przypadku modułu minimalna, wyłączny czas wszystkich wywołań funkcji w module.|

## <a name="see-also"></a>Zobacz także
- [Widok modułów](../profiling/modules-view-sampling-data.md)
- [Widok modułów-Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów-próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
