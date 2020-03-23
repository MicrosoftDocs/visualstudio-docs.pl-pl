---
title: Widok modułów - Dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ead219ddf482af5917842118d386c6fefe67973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772717"
---
# <a name="modules-view---sampling-data"></a>Widok modułów — dane próbkowania
Widok Moduły próbkowania danych wyświetla dane wydajności, które są pogrupowane według modułów, które zostały próbkowane w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznego. Przykładowe funkcje modułu są wymienione pod węzłem modułu.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Jeśli funkcja była wykonywana podczas pobierania próbek (oznacza to, że funkcja znajdowała się w górnej części stosu wywołań), wiersze źródłowe i adresy instrukcji, które były wykonywane są wymienione pod węzłem funkcji. Ponieważ dane są zbierane dla wiersza źródłowego lub wskaźnika instrukcji, gdy linia lub instrukcja jest wykonywana, wartości włączające i wyłączne są zawsze takie same dla danych wiersza i danych instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa modułu, funkcji, numeru wiersza lub adresu wskaźnika instrukcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu zawierającego funkcję, wiersz lub wskaźnik instrukcji.|
|**Ścieżka modułu**|Ścieżka modułu zawierającego moduł, funkcję, linię lub wskaźnik instrukcji.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Próbki włączające**|- Dla funkcji, liczba próbek, w których ta funkcja lub funkcja, która została wywołana przez tę funkcję, była wykonywana; oznacza to, że liczba próbek stosu wywołań, które zawierały tę funkcję.<br />- W przypadku modułu liczba próbek, w których wykonywana była co najmniej jedna funkcja z modułu.<br />- W przypadku wiersza lub instrukcji liczba próbek, w których ta linia lub instrukcja była wykonywana.|
|**Próbki włącznie %**|- Dla funkcji lub modułu procent wszystkich próbek w przebiegu profilowania, które były włącznie próbki tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich próbek w przebiegu profilowania, w którym ten wiersz lub instrukcja była wykonywana.|
|**Ekskluzywne próbki**|- Dla funkcji, liczba próbek stosu wywołań, w których ta funkcja była bezpośrednio wykonywana; oznacza to, że liczba próbek, w których ta funkcja była w górnej części stosu wywołań.<br />- Dla modułu, suma ekskluzywnych próbek funkcji w module.<br />- W przypadku wiersza lub instrukcji liczba próbek, w których ta linia lub instrukcja była wykonywana.|
|**Próbki na wyłączność %**|- Dla funkcji lub modułu procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji lub modułu.<br />- Dla wiersza lub instrukcji, procent wszystkich próbek w przebiegu profilowania, w którym ten wiersz lub instrukcja była wykonywana.|

## <a name="see-also"></a>Zobacz też
- [Widok modułów - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Widok modułów - oprzyrządowanie](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Widok modułów](../profiling/modules-view-instrumentation-data.md)
