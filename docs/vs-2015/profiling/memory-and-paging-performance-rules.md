---
title: Reguły wydajności pamięci i stronicowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d10d423c544a1117a56a954bacfa00f0ce439b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808651"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reguły wydajności pamięci i stronicowania kategorii zidentyfikować działania stronicowania w przebiegu profilowania, która może mieć wpływ na wydajność aplikacji i czasu odpowiedzi.  
  
|||  
|-|-|  
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoki stopień stronicowania aktywnej pamięci na i z dysku wystąpił w całym uruchomienia profilowania. Stronicowanie kursy na ten poziom zwykle wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowanie na komputerze, który ma więcej pamięci. Ta reguła jest uruchamiana, gdy zmniejszenia liczby działań stronicowania przekroczy próg górny reguły D0017.|  
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Stosunkowo wysoki stopień stronicowania aktywnej pamięci na i z dysku wystąpił w całym uruchomienia profilowania. Stronicowanie kursy na ten poziom zwykle wpływ na wydajność aplikacji i czasu odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez modyfikowanie algorytmów. Może być również konieczne należy wziąć pod uwagę wymagania dotyczące pamięci aplikacji. Spróbuj uruchomić ponownie profilowanie na komputerze, który ma więcej pamięci.|



