---
title: Widok funkcji — dane instrumentacji pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: eba1f0d1434d253aaca698d3ae582e3c507c2d23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779236"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Widok funkcji — dane instrumentacji pamięci .NET
Widok Funkcje alokacji pamięci .NET profilowania danych, które zostały zebrane przy użyciu metody instrumentacji wyświetla funkcje, które przydzielone pamięci podczas przebiegu profilowania. Wiersz funkcji raportuje rozmiar i liczbę alokacji oraz dane chronometrażu dla funkcji.

## <a name="general"></a>Ogólne

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
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji z powodu instrumentacji. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Obciążenie sondy zostało odjęte od czasów all inclusive.|

## <a name="net-memory-values"></a>Wartości pamięci .NET
 Wartości pamięci .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (bajty) obiektów, które zostały utworzone przez funkcję i jej funkcje podrzędne.

 Wartości pamięci wyłączności wskazują liczbę i rozmiar obiektów, które zostały utworzone przez funkcję, a nie przez jej funkcje podrzędne.

|Kolumna|Opis|
|------------|-----------------|
|**Alokacje włącznie**|Całkowita liczba obiektów, które zostały utworzone w tej funkcji i w funkcjach, które były wywoływane przez tę funkcję.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone podczas wykonywania kodu przez funkcję w treści funkcji. Liczba ta nie obejmuje obiektów, które zostały utworzone w funkcjach, które były wywoływane przez tę funkcję.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|
|**Bajty włącznie**|Liczba bajtów pamięci, które zostały przydzielone w tej funkcji i w funkcjach, które były wywoływane przez tę funkcję.|
|**Bajty włącznie %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były włącznie bajtów tej funkcji.|
|**Bajty wyłączne**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję, ale nie przez funkcje, które były wywoływane przez tę funkcję.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były wyłączne bajty tej funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|Całkowity czas włącznie wszystkich wywołań tej funkcji.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie tej funkcji.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Całkowity czas wyłączny wszystkich wywołań tej funkcji.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności tej funkcji.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny wywołania tej funkcji.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|Całkowita liczba włącznie aplikacji wszystkich wywołań tej funkcji.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie aplikacji tej funkcji.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołania tej funkcji.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołania tej funkcji.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ani nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|Całkowity czas wyłączności aplikacji wszystkich wywołań tej funkcji.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
