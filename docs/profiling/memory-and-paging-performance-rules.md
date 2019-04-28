---
title: Reguły wydajności pamięci i stronicowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f779a050c334e8f61d6d3711ed2be2a7b087e72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896689"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności pamięci i stronicowania kategorii zidentyfikować działania stronicowania w przebiegu profilowania, która może mieć wpływ na wydajność aplikacji i czasu odpowiedzi.

|||
|-|-|
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoki stopień stronicowania aktywnej pamięci na i z dysku wystąpił w całym uruchomienia profilowania. Stronicowanie kursy na ten poziom zwykle wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowanie na komputerze, który ma więcej pamięci. Ta reguła jest uruchamiana, gdy zmniejszenia liczby działań stronicowania przekroczy próg górny reguły D0017.|
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoki stopień stronicowania aktywnej pamięci na i z dysku wystąpił w całym uruchomienia profilowania. Stronicowanie kursy na ten poziom zwykle wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowanie na komputerze, który ma więcej pamięci.|