---
title: Informacje o wartościach danych próbkowania | Microsoft Docs
description: Dowiedz się, jak Metoda profilowania próbkowania w programie Visual Studio narzędzia profilowania przerywa procesor komputera w ustalonych odstępach czasu i zbiera stos wywołań funkcji.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 40902746e1dd1a4c68c9e1aa54ed4e72030a8fff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886031"
---
# <a name="understand-sampling-data-values"></a>Omówienie wartości danych próbkowania

Metoda profilowania *próbkowania* w programie Visual Studio narzędzia profilowania przerywa procesor komputera w ustalonych odstępach czasu i zbiera stos wywołań funkcji. *Stos wywołań* jest strukturą dynamiczną, która przechowuje informacje o funkcjach wykonywanych na procesorze.

Analiza profilera określa, czy procesor wykonuje kod w procesie docelowym. Jeśli procesor nie wykonuje kodu w procesie docelowym, przykład zostanie odrzucony.

Jeśli procesor wykonuje kod docelowy, profiler zwiększa liczbę próbek dla każdej funkcji na stosie wywołań. W czasie, gdy pobierana jest próbka, tylko jedna funkcja na stosie wywołań wykonuje obecnie kod. Inne funkcje na stosie są elementami nadrzędnymi w hierarchii wywołań funkcji, które oczekują na zwrócenie przez nich elementów podrzędnych.

W przypadku przykładowego zdarzenia Profiler *zwiększa losową* liczbę funkcji, która wykonuje obecnie instrukcje. Ze względu na to, że próbka wyłączna jest również częścią łącznej (*włącznie*) próbek funkcji, jest również zwiększana liczba włączonych próbek dla obecnie aktywnej funkcji.

 Profiler zwiększa liczbę włączonych próbek wszystkich innych funkcji na stosie wywołań.

## <a name="inclusive-samples"></a>Próbki włączne

Całkowita liczba próbek zbieranych podczas wykonywania funkcji docelowej.

Obejmuje to próbki, które są zbierane podczas bezpośredniego wykonywania kodu funkcji i próbek, które są zbierane podczas wykonywania funkcji podrzędnych, które są wywoływane przez funkcję docelową.

## <a name="exclusive-samples"></a>Próbki wyłączne

Liczba próbek zbieranych podczas bezpośredniego wykonywania instrukcji funkcji docelowej.

Próbki wyłączne nie obejmują próbek, które są zbierane podczas wykonywania funkcji, które są wywoływane przez funkcję docelową.

## <a name="inclusive-percent"></a>Łączny procent

Wartość procentowa łącznej liczby próbek włącznie w przebiegu profilowania, które obejmują próbki funkcji lub zakresu danych.

## <a name="exclusive-percent"></a>Procent wyłączny

Procent całkowitej liczby próbek wyłącznych w przebiegu profilowania, które są wyłącznymi próbkami funkcji lub zakresu danych.

## <a name="see-also"></a>Zobacz też

[Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md) 
 [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)
