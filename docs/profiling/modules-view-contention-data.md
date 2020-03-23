---
title: Widok modułów — dane rywalizacji | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780016"
---
# <a name="modules-view---contention-data"></a>Widok modułów — dane rywalizacji
Widok Moduły danych rywalizacji wyświetla dane współbieżności pogrupowane według modułów, które zostały pobrane próbkowane w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Funkcje modułu, w którym wystąpiły zdarzenia rywalizacji są wymienione w węźle modułu.

 Jeśli funkcja była wykonywanie własnego kodu, gdy wystąpiło zdarzenie rywalizacji, oznacza to, że funkcja była w górnej części stosu wywołań, wiersze źródłowe i adresy instrukcji, które były wykonywane są wymienione w węźle funkcji. Ponieważ dane są zbierane dla wiersza źródłowego lub wskaźnika instrukcji, gdy linia lub instrukcja jest wykonywana, wartości włączające i wyłączne są zawsze takie same dla danych wiersza i danych instrukcji.

 W poniższej tabeli opisano wartości kolumn w widoku Moduły danych rywalizacji.

|Kolumna|Opis|
|------------|-----------------|
|**Ekskluzywny zablokowany czas**|- Dla funkcji, czas, że ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję nie jest uwzględniony.<br />- Dla modułu suma wyłącznego zablokowanego czasu funkcji w module.<br />- W przypadku wiersza lub instrukcji czas, w której ta linia lub instrukcja została zablokowana przed wykonaniem.|
|**Ekskluzywny zablokowany czas %**|- Dla funkcji lub modułu procent wszystkich zablokowanych czasów w przebiegu profilowania, który był wyłącznym zablokowanym czasem tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich zablokowany czas w profilu uruchomić, w którym ten wiersz lub instrukcja została zablokowana z wykonywania.|
|**Ekskluzywne twierdzenia**|- Dla funkcji, ile razy ta funkcja została zablokowana z wykonywania kodu w treści funkcji. Rywalizacje w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.<br />- Dla modułu, suma wyłącznych rywalizacji funkcji w module.<br />- W przypadku wiersza lub instrukcji, ile razy ten wiersz lub instrukcja została zablokowana w wykonywaniu.|
|**Ekskluzywne rywalizacje %**|- Dla funkcji lub modułu procent wszystkich rywalizacji w przebiegu profilowania, które były wyłącznymi twierdzeniami tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich rywalizacji w przebiegu profilowania, które były rywalizacje, które zablokowały ten wiersz lub instrukcji z wykonywania.|
|**Włącznie zablokowany czas**|- Dla funkcji czas, że ta funkcja lub funkcja, która została wywołana przez tę funkcję został zablokowany wykonywania.<br />- Dla modułu, suma zablokowanego czasu, w którym co najmniej jedna funkcja z tego modułu była na stosie.<br />- W przypadku wiersza lub instrukcji czas, w której ta linia lub instrukcja została zablokowana przed wykonaniem.|
|**Włącznie zablokowany czas %**|- Dla funkcji lub modułu procent wszystkich zablokowany czas w przebiegu profilowania, który był włącznie zablokowany czas tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich zablokowany czas w profilu uruchomić, w którym ten wiersz lub instrukcja była wykonywana.|
|**Rywalizacje włączające**|- Dla funkcji, liczba razy, że ta funkcja lub funkcja, która została wywołana przez tę funkcję została zablokowana wykonywanie.<br />- W przypadku modułu liczba rywalizacji, w których co najmniej jedna funkcja z tego modułu znajdowała się na stosie.<br />- W przypadku wiersza lub instrukcji, ile razy ten wiersz lub instrukcja została zablokowana w wykonywaniu.|
|**Rywalizacja włączająca %**|- Dla funkcji lub modułu procent wszystkich rywalizacji w przebiegu profilowania, które były włącznie rywalizacji tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich zablokowany czas w profilu uruchomić, w którym ten wiersz lub instrukcja była wykonywana.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu zawierającego funkcję, wiersz lub wskaźnik instrukcji.|
|**Ścieżka modułu**|Ścieżka modułu zawierającego moduł, funkcję, linię lub wskaźnik instrukcji.|
|**Nazwa**|Nazwa modułu lub funkcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok modułów](../profiling/modules-view.md)
- [Widok modułów - oprzyrządowanie](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-sampling-data.md)
