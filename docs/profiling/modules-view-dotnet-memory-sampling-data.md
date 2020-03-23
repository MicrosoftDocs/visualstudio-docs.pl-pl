---
title: Widok modułów — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9d0d9b7ab681a266115673b48f2c2604c5ff869c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772730"
---
# <a name="modules-view---net-memory-sampling-data"></a>Widok modułów — dane próbkowania pamięci .NET
Widok Moduły danych alokacji pamięci .NET, które są zbierane przy użyciu metody próbkowania grupuje dane pamięci przez moduły, które zostały wykonane w przebiegu profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcje modułu są wymienione pod węzłem modułu.

 Numery wierszy pliku źródłowego instrukcji, które przydzielają pamięć są wymienione pod węzłem funkcji, a adresy instrukcji, które wykonują alokację, są wyświetlane pod węzłem wiersza. Wartości włączające i wyłączne są zawsze takie same dla danych wiersza i danych instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa modułu, funkcji, numeru wiersza lub adresu instrukcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Alokacje włącznie**|- Dla funkcji całkowita liczba obiektów, które zostały utworzone przez funkcję. Liczba zawiera obiekty, które zostały utworzone w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla modułu liczba obiektów w przebiegu profilowania, które zostały przydzielone podczas wykonywania co najmniej jednej funkcji z modułu. Liczba zawiera obiekty, które zostały utworzone w funkcjach, które były wywoływane przez funkcje modułu.<br />- Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały przydzielone przez wiersz lub instrukcji.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były włącznie alokacje modułu, funkcji, wiersza lub instrukcji.|
|**Alokacje wyłączne**|- Dla bieżącej funkcji liczba obiektów, które zostały utworzone, gdy funkcja była wykonywanie kodu treści funkcji (czyli gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla modułu suma wyłącznych alokacji funkcji w module.<br />- Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez ten wiersz lub instrukcji.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje modułu, funkcji, wiersza lub instrukcji.|
|**Bajty włącznie**|- Dla funkcji liczba bajtów, które zostały przydzielone przez funkcję. Liczba zawiera bajty, które zostały przydzielone w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla modułu liczba bajtów, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone podczas wykonywania co najmniej jednej funkcji z modułu. Liczba zawiera obiekty, które zostały utworzone we wszystkich funkcjach, które były wywoływane przez funkcje modułu.<br />- Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez wiersz lub instrukcji.|
|**Bajty włącznie %**|Procent wszystkich bajtów, które zostały przydzielone w przebiegu profilowania, które były włącznie bajtów modułu, funkcji, wiersza lub instrukcji.|
|**Bajty wyłączne**|- Dla funkcji całkowita liczba bajtów, które zostały przydzielone przez funkcję. Liczba ta nie zawiera bajtów, które zostały przydzielone w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla modułu suma bajtów wyłącznych, które zostały przydzielone przez funkcje w module.<br />- Dla wiersza lub instrukcji, całkowita liczba obiektów, które zostały przydzielone przez ten wiersz lub instrukcji.|
|**Bajty wyłączności %**|Procent wszystkich bajtów, które zostały przydzielone w przebiegu profilowania, które były wyłącznymi bajtami modułu, funkcji, wiersza lub instrukcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok modułów - oprzyrządowanie](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
