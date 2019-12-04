---
title: Reguły wydajności pamięci i stronicowania | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778560"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności w kategorii pamięć i stronicowanie identyfikują aktywność stronicowania w przebiegu profilowania, który może mieć wpływ na wydajność aplikacji i czas odpowiedzi.

|||
|-|-|
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoki wskaźnik stronicowania aktywnej pamięci na i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci. Ta zasada jest wyzwalana, gdy ilość aktywności stronicowania przekroczy górny próg reguły D0017.|
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Relatywnie wysoki współczynnik stronicowania aktywnej pamięci do i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci.|
