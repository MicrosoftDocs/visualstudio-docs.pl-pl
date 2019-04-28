---
title: Widok modułów — dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0b4870a17988c4f926e04aca24e50419c4a27165
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829960"
---
# <a name="modules-view---net-memory-sampling-data"></a>Widok modułów — dane próbkowania pamięci platformy .NET
Widok modułów danych alokacji pamięci .NET, które są zbierane przy użyciu metody próbkowania grupuje dane pamięci przez moduły, które zostały wykonane w trakcie uruchomienia profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcji modułu są wyświetlane poniżej tego węzła modułu.

 Numery wierszy pliku źródłowego w instrukcji, które przydzielają pamięć są wymienione poniżej tego węzła funkcji, a adresy instrukcji, które wykonują alokacji są wymienione pod węzeł wiersza. Wartości włączne i wyłączne są zawsze takie same dla wiersza danych i danych instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa modułu, funkcji, numer wiersza lub adres instrukcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka do modułu.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Przydziały włączne**|— Dla funkcji, całkowita liczba obiektów, które zostały utworzone przez funkcję. Numer obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu powodowała liczba przydzielonych podczas co najmniej jedna funkcja w module obiektów podczas uruchomienia profilowania. Numer obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcje modułu.<br />— Aby wiersz lub instrukcji, całkowita liczba obiektów, które zostały przydzielone wiersza lub instrukcji.|
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów włącznych modułu, funkcji, wiersza lub instrukcji.|
|**Przydziały wyłączne**|— W przypadku funkcji bieżącej liczby obiektów, które zostały utworzone podczas wykonywania funkcji kodu w treści funkcji (oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu, sumę przydziałów wyłącznych funkcje w module.<br />— Aby wiersz lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez tego wiersza lub instrukcji.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w uruchomienia profilowania były przydziałów wyłącznych modułu, funkcji, wiersza lub instrukcji.|
|**Bajty włączne**|— W przypadku funkcji liczba bajtów przydzielonych przez funkcję. Liczba uwzględnia przydzielonych bajtów w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu liczba przydzielonych bajtów w przebiegu profilowania przydzielonych podczas co najmniej jedna funkcja w module wykonywania. Liczba uwzględnia obiekty, które zostały utworzone we wszystkich funkcji, które zostały wywołane przez funkcje modułu.<br />— Aby wiersz lub instrukcji, całkowita liczba obiektów, które zostały utworzone przez wiersz lub instrukcji.|
|**% Bajtów włącznych**|Procent wszystkich bajtów przydzielonych w uruchomienia profilowania były bajty włączne modułu, funkcji, wiersza lub instrukcji.|
|**Bajty wyłączne**|— Dla funkcji, całkowita liczba bajtów przydzielonych przez funkcję. Liczba nie ma przydzielonych bajtów w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla modułu, Suma bajtów wyłącznych, przydzielone przez funkcje w module.<br />— Aby wiersz lub instrukcji, całkowita liczba obiektów, które zostały przydzielone przez ten wiersz lub instrukcji.|
|**% Bajtów wyłącznych**|Procent wszystkich bajtów przydzielonych w uruchomienia profilowania były bajty wyłączne modułu, funkcji, wiersza lub instrukcji.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)