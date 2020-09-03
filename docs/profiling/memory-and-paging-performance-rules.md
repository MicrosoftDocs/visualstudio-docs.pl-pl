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
ms.openlocfilehash: 716bc771310b73c8a0b11a97080184d9868fe91b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535138"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
Reguły wydajności w kategorii pamięć i stronicowanie identyfikują aktywność stronicowania w przebiegu profilowania, który może mieć wpływ na wydajność aplikacji i czas odpowiedzi.

|Reguła|Opis|
|-|-|
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoki wskaźnik stronicowania aktywnej pamięci na i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci. Ta zasada jest wyzwalana, gdy ilość aktywności stronicowania przekroczy górny próg reguły D0017.|
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Relatywnie wysoki współczynnik stronicowania aktywnej pamięci do i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci.|
