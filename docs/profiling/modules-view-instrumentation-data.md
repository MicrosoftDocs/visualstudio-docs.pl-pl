---
title: Widok modułów - Dane oprzyrządowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778534"
---
# <a name="modules-view---instrumentation-data"></a>Widok modułów - dane oprzyrządowania
W widoku Moduły są wyświetlane dane dotyczące wydajności pogrupowane według modułów, które znajdowały się w danych profilowania. Funkcje modułu są wymienione poniżej węzła modułu.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji lub modułu.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań, które zostały wykonane do tej funkcji lub modułu.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu, w którym moduł lub funkcja była wykonywana.|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji lub modułu z powodu instrumentacji.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji lub modułu i jego funkcji podrzędnych z powodu instrumentacji.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|- Dla funkcji, czas spędzony w funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla modułu, czas, w którym co najmniej jedna funkcja w module był na stosie wywołań.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie tego modułu lub funkcji.|
|**Średni czas włącznie, który upłynął**|- Dla funkcji, średni czas włącznie wywołania tej funkcji.<br />- W przypadku modułu średni czas włącznie wszystkich wywołań funkcji w module.|
|**Maksymalny czas włącznie, który upłynął**|- Dla funkcji maksymalny czas włącznie wywołania tej funkcji.<br />- Dla modułu maksymalny czas włącznie wszystkich wywołań funkcji w module.|
|**Min. Czas włącznie, który upłynął**|- Dla funkcji, minimalny czas włącznie wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas włącznie wszystkich wywołań funkcji w module.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|- Dla funkcji, czas spędzony w module lub funkcji. Obejmuje to wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.<br />- Dla modułu, suma czasu wyłączności funkcji w module.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności tego modułu lub funkcji.|
|**Średni czas wyłączny, który upłynął**|- Dla funkcji, średni czas wyłączny wywołania tej funkcji.<br />- W przypadku modułu średni czas wyłączności wszystkich wywołań do funkcji w module.|
|**Maksymalny czas wyłączny**|- Dla funkcji maksymalny czas wyłączny wywołania tej funkcji.<br />- Dla modułu maksymalny czas wyłączny wszystkich wywołań do funkcji w module.|
|**Min Upłynął czas wyłączny**|- Dla funkcji, minimalny czas wyłączny wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas wyłączny wszystkich wywołań do funkcji w module.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia. Jednak czas obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|- Dla funkcji, czas spędzony w wywołaniach funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych, ale wyklucza wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla modułu, czas, w którym co najmniej jedna funkcja w module był na stosie wywołań. Nie obejmuje to czasu spędzonego na wywołaniach systemu operacyjnego.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie aplikacji tego modułu lub funkcji.|
|**Średni czas włącznie aplikacji**|- Dla funkcji, średni czas włącznie aplikacji wywołania tej funkcji.<br />- Dla modułu, średni czas włącznie aplikacji wszystkich wywołań funkcji w module.|
|**Maksymalny czas włącznie aplikacji**|- Dla funkcji maksymalny czas włącznie aplikacji wywołania tej funkcji.<br />- Dla modułu maksymalny czas włączania aplikacji wszystkich wywołań funkcji w module.|
|**Min. czas włącznie aplikacji**|- Dla funkcji, minimalny czas włącznie aplikacji wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas włącznie aplikacji wszystkich wywołań funkcji w module.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas spędzony w module lub funkcji. Nie obejmuje to czasu spędzonego w funkcjach podrzędnych, a także wyklucza wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|Całkowity czas wyłączności aplikacji wszystkich wywołań tego modułu lub funkcji.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego uruchomienia profilowania, który został spędzony w wyłącznym czasie aplikacji tego modułu lub funkcji.|
|**Średni czas wyłączny aplikacji**|- Dla funkcji, średni czas wyłączności aplikacji wywołania tej funkcji.<br />- Dla modułu, średni czas wyłączności aplikacji wszystkich wywołań do funkcji w module.|
|**Maksymalny czas wyłączności aplikacji**|- Dla funkcji, maksymalny czas wyłączności aplikacji wywołania tej funkcji.<br />- Dla modułu maksymalny czas wyłączności aplikacji wszystkich wywołań funkcji w module.|
|**Minimalny czas wyłączności aplikacji**|- Dla funkcji, minimalny czas wyłączności aplikacji wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas wyłączności aplikacji wszystkich wywołań do funkcji w module.|

## <a name="see-also"></a>Zobacz też
- [Widok modułów](../profiling/modules-view-sampling-data.md)
- [Widok modułów - oprzyrządowanie](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
