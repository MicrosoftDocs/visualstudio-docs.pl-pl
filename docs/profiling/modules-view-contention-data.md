---
title: Widok modułów — dane rywalizacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2de844867e9c0a8d95abdaa13f860a6487254bfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74780016"
---
# <a name="modules-view---contention-data"></a>Widok modułów — dane rywalizacji
Widok modułów danych rywalizacji zawiera dane współbieżności pogrupowane według modułów, które zostały próbkowane w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcje modułu, w którym wystąpiły zdarzenia rywalizacji, są wyświetlane w węźle modułu.

 Jeśli funkcja wykonywała własny kod w momencie wystąpienia zdarzenia rywalizacji, to oznacza, że funkcja była w górnej części stosu wywołań, wiersze źródłowe i wprowadzone instrukcje są wyświetlane w węźle funkcji. Ponieważ dane są zbierane dla linii źródłowej lub wskaźnika instrukcji podczas wykonywania wiersza lub instrukcji, Włączne i wyłączne wartości są zawsze takie same dla danych wierszowych i danych instrukcji.

 W poniższej tabeli opisano wartości kolumn w widoku moduły danych rywalizacji.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|-Dla funkcji — czas, przez który ta funkcja została zablokowana do wykonywania kodu w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję, nie jest uwzględniany.<br />-Dla modułu, suma wyłącznego czasu blokowania funkcji w module.<br />— W przypadku linii lub instrukcji, czas blokowania wykonywania tego wiersza lub instrukcji.|
|**% Wyłącznego czasu blokowania**|— Dla funkcji lub modułu, procent całego zablokowanego czasu w przebiegu profilowania, który był wyłącznym czasem blokowania tej funkcji lub tego modułu.<br />— W przypadku linii lub instrukcji, procent całego zablokowanego czasu w profilowania, w którym ten wiersz lub instrukcje zostały zablokowane do wykonania.|
|**Rywalizacje wyłączne**|-Dla funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane.<br />-Dla modułu, suma wyłącznych zawartości funkcji w module.<br />— Dla wiersza lub instrukcji, ile razy można zablokować wykonywanie tego wiersza lub instrukcji.|
|**Zawartość wyłącznych%**|— Dla funkcji lub modułu, procent wszystkich rywalizacji w przebiegu profilowania, które były wyłuskanymi zawartości tej funkcji lub modułu.<br />— W przypadku linii lub instrukcji, procent wszystkich rywalizacji w przebiegu profilowania, które były rywalizacjami, które blokują wykonywanie tego wiersza lub instrukcji.|
|**Włączny czas blokowania**|-Dla funkcji, czas blokowania wykonywania tej funkcji lub funkcji, która została wywołana przez tę funkcję.<br />-Dla modułu, suma zablokowanego czasu, w którym co najmniej jedna funkcja z tego modułu znajdowała się na stosie.<br />— W przypadku linii lub instrukcji, czas blokowania wykonywania tego wiersza lub instrukcji.|
|**% Włącznego czasu blokowania**|— Dla funkcji lub modułu, procent całego zablokowanego czasu w przebiegu profilowania, który był włącznie czas zablokowany tej funkcji lub tego modułu.<br />— Dla linii lub instrukcji, procent całego zablokowanego czasu w profilowania, w którym uruchomiono ten wiersz lub instrukcję.|
|**Rywalizacje włączne**|-Dla funkcji, ile razy ta funkcja lub funkcja, która została wywołana przez tę funkcję, została zablokowana do wykonania.<br />-Dla modułu liczba rywalizacji, w których co najmniej jedna funkcja z tego modułu znajdowała się na stosie.<br />— Dla wiersza lub instrukcji, ile razy można zablokować wykonywanie tego wiersza lub instrukcji.|
|**% Rywalizacji włącznych**|— Dla funkcji lub modułu, procent wszystkich rywalizacji w przebiegu profilowania, które były oparte na rywalizacjach tej funkcji lub modułu.<br />— Dla linii lub instrukcji, procent całego zablokowanego czasu w profilowania, w którym uruchomiono ten wiersz lub instrukcję.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję, linię lub wskaźnik instrukcji.|
|**Ścieżka modułu**|Ścieżka modułu zawierającego moduł, funkcję, wiersz lub wskaźnik instrukcji.|
|**Nazwa**|Nazwa modułu lub funkcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok modułów](../profiling/modules-view.md)
- [Widok modułów-Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów-próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
