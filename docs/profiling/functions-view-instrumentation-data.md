---
title: Widok funkcji - Dane oprzyrządowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779223"
---
# <a name="functions-view---instrumentation-data"></a>Widok funkcji — dane oprzyrządowania
Widok raportu Funkcje zawiera listę danych profilowania według nazwy funkcji.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań, które są wykonane do tej funkcji.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji, które jest spowodowane przez instrumentację. Nie obejmuje narzutów w funkcjach, które były wywoływane przez funkcję. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych, które są spowodowane przez instrumentację. Zawiera obciążenie w funkcjach, które były wywoływane przez funkcję. Obciążenie sondy zostało odjęte od czasów all inclusive.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach, które były wywoływane przez funkcję i czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|Całkowity czas włącznie wszystkich wywołań tej funkcji.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie tej funkcji.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja wykonywała kod w treści funkcji, czyli gdy funkcja znajdowała się u góry stosu wywołań. Czas obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Całkowity czas wyłączny wszystkich wywołań tej funkcji.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności tej funkcji.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny wywołania tej funkcji.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|Całkowita liczba włącznie aplikacji wszystkich wywołań tej funkcji.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie aplikacji tej funkcji.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołania tej funkcji.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołania tej funkcji.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, i nie obejmuje czasu spędzonego w funkcjach, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|Całkowity czas wyłączności aplikacji wszystkich wywołań tej funkcji.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji - instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
