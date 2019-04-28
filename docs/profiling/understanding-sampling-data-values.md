---
title: Opis wartościami danych próbkowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2668d5b60fba429613975cc24e751dbe07f87b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830874"
---
# <a name="understand-sampling-data-values"></a>Informacje z wartościami danych próbkowania

*Próbkowania* profilowanie metody Visual Studio Profiling Tools przerywa działanie procesora komputera w ustalonych odstępach czasu i gromadzi stos wywołań funkcji. A *stos wywołań* jest dynamiczne struktury, która przechowuje informacje dotyczące funkcji, które są wykonywane na procesorze.

Analiza profiler Określa, czy procesor jest wykonywanie kodu w procesie docelowym. Jeśli procesor nie wykonuje kod w procesie docelowym, plik zostanie odrzucony.

Jeśli procesor, jest wykonywany kod docelowy, program profilujący zwiększa liczby próbek dla każdej funkcji na stosie wywołań. W tym czasie jest próbka tylko jednej funkcji — na stosie wywołań aktualnie wykonuje kod. Innych funkcji na stosie są elementów nadrzędnych w hierarchii wywołań funkcji, które oczekują na ich elementy podrzędne do zwrócenia.

Zdarzenia przykładowe przyrosty profiler *wyłączne* liczba funkcji, która jest w trakcie wykonywania instrukcji próbek. Ponieważ próbek wyłącznych wchodzi w skład całości (*włącznie*) przykłady funkcji liczność próbki włączne aktualnie aktywnych funkcji również jest zwiększany.

 Program profilujący zwiększa liczność próbki włączne wszystkich funkcji w stosie wywołań.

## <a name="inclusive-samples"></a>Próbki włączne

Łączna liczba próbek, które są zbierane podczas wykonywania funkcji docelowej.

Obejmuje to przykłady, które są zbierane podczas bezpośredniego wykonywania kodu funkcji i przykłady, które są zbierane podczas wykonywania funkcji podrzędnych, które są wywoływane przez funkcję docelowego.

## <a name="exclusive-samples"></a>Próbki wyłączne

Liczba próbek, które są zbierane podczas bezpośredniego wykonywania instrukcji docelowej funkcji.

Próbki wyłączne nie zawierają przykłady, które są zbierane podczas wykonywania funkcji wywołanych przez funkcję docelowego.

## <a name="inclusive-percent"></a>Procent (włącznie)

Procent całkowitej liczby włącznych próbek podczas uruchomienia profilowania, które są włącznych próbek zakresu funkcję lub dane.

## <a name="exclusive-percent"></a>% Wyłącznych

Procent całkowitej liczby próbek wyłącznych podczas uruchomienia profilowania, które są wyłącznych próbek zakres funkcji lub danych.

## <a name="see-also"></a>Zobacz także

[Instrukcje: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)
[narzędzi wydajności analizy danych](../profiling/analyzing-performance-tools-data.md)