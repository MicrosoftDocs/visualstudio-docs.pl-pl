---
title: Reguły wydajności pamięci i stronicowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f491ee766b2f17e14a8d13cc189018adea84903f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778560"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności w kategorii pamięci i stronicowania identyfikują działanie stronicowania w przebiegu profilowania, które może mieć wpływ na wydajność i szybkość reakcji aplikacji.

|||
|-|-|
|[DA0014: Wyjątkowo wysoki stopień stronicowania aktywnej pamięci na dysku](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoka szybkość stronicowania aktywnej pamięci do i z dysku wystąpił w trakcie wykonywania profilowania. Szybkość stronicowania na tym poziomie zwykle wpływa na wydajność aplikacji i szybkość reakcji. Należy rozważyć zmniejszenie alokacji pamięci przez zmianę algorytmów. Może być również należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze, który ma więcej pamięci. Ta reguła jest uruchamiana, gdy ilość aktywności stronicowania przekracza górny próg reguły D0017.|
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoka szybkość stronicowania aktywnej pamięci do i z dysku wystąpiła podczas wykonywania profilowania. Szybkość stronicowania na tym poziomie zwykle wpływa na wydajność aplikacji i szybkość reakcji. Należy rozważyć zmniejszenie alokacji pamięci przez zmianę algorytmów. Może być również należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze, który ma więcej pamięci.|
