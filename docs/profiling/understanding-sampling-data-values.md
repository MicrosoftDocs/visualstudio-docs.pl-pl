---
title: Opis wartości danych próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 289f92deaceca32a44249ed77c17187743a34fa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778053"
---
# <a name="understand-sampling-data-values"></a>Zrozumienie wartości danych próbkowania

Metoda profilowania *próbkowania* narzędzi profilowania programu Visual Studio przerywa procesor komputera w ustalonych odstępach czasu i zbiera stos wywołań funkcji. *Stos wywołań* to struktura dynamiczna, która przechowuje informacje o funkcjach wykonywanych na procesorze.

Analiza profilera określa, czy procesor wykonuje kod w procesie docelowym. Jeśli procesor nie wykonuje kodu w procesie docelowym, próbka zostanie odrzucona.

Jeśli procesor wykonuje kod docelowy, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. W czasie, gdy próbka jest pobierana, tylko jedna funkcja na stosie wywołań jest obecnie wykonywania kodu. Inne funkcje na stosie są elementów ami w hierarchii wywołań funkcji, które czekają na ich dzieci do powrotu.

W przypadku zdarzenia przykładowego profiler zwiększa *liczbę próbek wyłącznych* funkcji, która jest obecnie wykonywanie jego instrukcje. Ponieważ próbka wyłączna jest również częścią całkowitych *(włącznie)* próbek funkcji, zwiększa się również liczba próbek włącznie aktualnie aktywnej funkcji.

 Profiler zwiększa włącznie liczba próbek wszystkich innych funkcji na stosie wywołań.

## <a name="inclusive-samples"></a>Próbki włączające

Całkowita liczba próbek, które są zbierane podczas wykonywania funkcji docelowej.

Obejmuje to przykłady, które są zbierane podczas bezpośredniego wykonywania kodu funkcji i przykłady, które są zbierane podczas wykonywania funkcji podrzędnych, które są wywoływane przez funkcję docelową.

## <a name="exclusive-samples"></a>Ekskluzywne próbki

Liczba próbek, które są zbierane podczas bezpośredniego wykonywania instrukcji funkcji docelowej.

Wyłączne próbki nie obejmują przykłady, które są zbierane podczas wykonywania funkcji, które są wywoływane przez funkcję docelową.

## <a name="inclusive-percent"></a>Procent włącznie

Procent całkowitej liczby próbek włącznie w przebiegu profilowania, które są włącznie próbki funkcji lub zakresu danych.

## <a name="exclusive-percent"></a>Ekskluzywny procent

Procent całkowitej liczby próbek wyłącznych w przebiegu profilowania, które są wyłącznymi próbkami funkcji lub zakresu danych.

## <a name="see-also"></a>Zobacz też

[Jak: Wybierz metody](../profiling/how-to-choose-collection-methods.md)
zbierania[Analizuj dane narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)
