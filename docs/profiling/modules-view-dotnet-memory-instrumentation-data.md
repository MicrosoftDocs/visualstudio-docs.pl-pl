---
title: Widok modułów — dane instrumentacji pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 521c884a0a25d7fa975a4039e6ec3e36ff4dc020
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778547"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Widok modułów — dane instrumentacji pamięci .NET
Widok Moduły danych alokacji pamięci .NET zebranych przy użyciu metody instrumentacji grupuje dane pamięci i chronometrażu przez moduły, które zostały wykonane w przebiegu profilowania. Dane profilowania dla funkcji modułu są wymienione pod węzłem modułu.

## <a name="general"></a>Ogólne

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

## <a name="net-memory-values"></a>Wartości pamięci .NET
 Wartości pamięci .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (bajty) obiektów, które zostały utworzone przez funkcję i jej funkcje podrzędne.

 Wartości pamięci wyłączności wskazują liczbę i rozmiar obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcje podrzędne.

 Wartości pamięci włączającej i wyłącznej modułu są sumą wartości pamięci włączającej i wyłącznej funkcji w module.

|Kolumna|Opis|
|------------|-----------------|
|**Alokacje włącznie**|- Dla funkcji całkowita liczba obiektów, które zostały utworzone przez funkcję. Liczba ta obejmuje obiekty, które zostały utworzone przez funkcje, które były wywoływane przez funkcję.<br />- Dla modułu liczba obiektów w przebiegu profilowania, które zostały przydzielone, gdy co najmniej jedna funkcja z modułu była wykonywana. Liczba ta obejmuje obiekty, które zostały przydzielone w funkcjach, które zostały wygenerowane przez wywołania z funkcji modułu.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie modułu lub funkcji.|
|**Alokacje wyłączne**|- Dla funkcji liczba obiektów, które zostały utworzone, gdy funkcja była wykonywanie kodu w treści funkcji (czyli gdy funkcja była w górnej części stosu wywołań). Liczba ta nie obejmuje obiektów, które zostały utworzone w funkcjach, które były wywoływane przez funkcję.<br />- Dla modułu suma wyłącznych alokacji funkcji w module.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje modułu lub funkcji.|
|**Bajty wyłączne**|- Dla funkcji całkowita liczba bajtów pamięci, które zostały przydzielone, gdy funkcja była wykonywanie kodu w treści funkcji (czyli, gdy funkcja była w górnej części stosu wywołań). Liczba ta nie obejmuje bajtów, które zostały przydzielone w funkcjach, które były wywoływane przez funkcję.<br />- Dla modułu suma bajtów wyłącznych, które zostały przydzielone przez funkcje w module.|
|**Bajty wyłączności %**|Procent wszystkich bajtów, które zostały przydzielone w przebiegu profilowania, które były wyłącznymi bajtami modułu, funkcji, wiersza lub instrukcji.|
|**Bajty włącznie**|- Dla funkcji liczba bajtów, które zostały przydzielone przez funkcję. Liczba ta obejmuje bajty, które zostały przydzielone w funkcjach, które były wywoływane przez funkcję.<br />- Dla modułu liczba bajtów, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone, gdy co najmniej jedna funkcja z modułu był wykonywany. Liczba ta obejmuje obiekty, które zostały utworzone we wszystkich funkcjach, które były wywoływane przez funkcje modułu.|
|**Bajty włącznie %**|Procent wszystkich bajtów, które zostały przydzielone w przebiegu profilowania, które były bajtami włącznie modułu lub funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|- Dla funkcji, czas spędzony w funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla modułu, okres, w którym co najmniej jedna funkcja w module był na stosie wywołań.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie tego modułu lub funkcji.|
|**Średni czas włącznie, który upłynął**|- Dla funkcji, średni czas włącznie wywołania tej funkcji.<br />- W przypadku modułu średni czas włącznie wszystkich wywołań funkcji w module.|
|**Maksymalny czas włącznie, który upłynął**|- Dla funkcji maksymalny czas włącznie wywołania tej funkcji.<br />- Dla modułu maksymalny czas włącznie wszystkich wywołań funkcji w module.|
|**Min. Czas włącznie, który upłynął**|- Dla funkcji, minimalny czas włącznie wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas włącznie wszystkich wywołań funkcji w module.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|- Dla funkcji, czas spędzony w module lub funkcji. Obejmuje to wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.<br />- Dla modułu, suma czasu wyłączności funkcji w module.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności tego modułu lub funkcji.|
|**Średni czas wyłączny, który upłynął**|- Dla funkcji, średni czas wyłączny wywołania tej funkcji.<br />- W przypadku modułu średni czas wyłączności wszystkich wywołań do funkcji w module.|
|**Maksymalny czas wyłączny**|- Dla funkcji maksymalny czas wyłączny wywołania tej funkcji.<br />- Dla modułu maksymalny czas wyłączny wszystkich wywołań do funkcji w module.|
|**Min Upłynął czas wyłączny**|- Dla funkcji, minimalny czas wyłączny wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas wyłączny wszystkich wywołań do funkcji w module.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|- Dla funkcji, czas spędzony w wywołaniach funkcji. Obejmuje to czas spędzony w funkcjach podrzędnych, ale wyklucza wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla modułu, okres, w którym co najmniej jedna funkcja w module był na stosie wywołań, z wyłączeniem czasu spędzonego w wywołaniach systemu operacyjnego.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie aplikacji tego modułu lub funkcji.|
|**Średni czas włącznie aplikacji**|- Dla funkcji, średni czas włącznie aplikacji wywołania tej funkcji.<br />- Dla modułu, średni czas włącznie aplikacji wszystkich wywołań funkcji w module.|
|**Maksymalny czas włącznie aplikacji**|- Dla funkcji maksymalny czas włącznie aplikacji wywołania tej funkcji.<br />- Dla modułu maksymalny czas włączania aplikacji wszystkich wywołań funkcji w module.|
|**Min. czas włącznie aplikacji**|- Dla funkcji, minimalny czas włącznie aplikacji wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas włącznie aplikacji wszystkich wywołań funkcji w module.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas spędzony w module lub funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych. Wskazany czas wyklucza również wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|- Dla funkcji, całkowity czas wyłączności aplikacji wywołania tej funkcji.<br />- Dla modułu, całkowity czas wyłączności aplikacji wszystkich wywołań do funkcji w module.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego uruchomienia profilowania, który został spędzony w wyłącznym czasie aplikacji tego modułu lub funkcji.|
|**Średni czas wyłączny aplikacji**|- Dla funkcji, średni czas wyłączności aplikacji wywołania tej funkcji.<br />- Dla modułu, średni czas wyłączności aplikacji wszystkich wywołań do funkcji w module.|
|**Maksymalny czas wyłączności aplikacji**|- Dla funkcji, maksymalny czas wyłączności aplikacji wywołania tej funkcji.<br />- Dla modułu maksymalny czas wyłączności aplikacji wszystkich wywołań funkcji w module.|
|**Minimalny czas wyłączności aplikacji**|- Dla funkcji, minimalny czas wyłączności aplikacji wywołania tego modułu lub funkcji.<br />- Dla modułu, minimalny czas wyłączności aplikacji wszystkich wywołań do funkcji w module.|

## <a name="see-also"></a>Zobacz też
- [Widok modułów - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
