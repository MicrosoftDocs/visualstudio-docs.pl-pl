---
title: Reguły wydajności pamięci i stronicowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf868164a8768b01793e6c5ec69b90c89cab34bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547969"
---
# <a name="memory-and-paging-performance-rules"></a>Reguły wydajności pamięci i stronicowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reguły wydajności w kategorii pamięć i stronicowanie identyfikują aktywność stronicowania w przebiegu profilowania, który może mieć wpływ na wydajność aplikacji i czas odpowiedzi.  
  
|Reguła|Opis|  
|-|-|  
|[DA0014: Skrajnie intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Bardzo wysoki wskaźnik stronicowania aktywnej pamięci na i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci. Ta zasada jest wyzwalana, gdy ilość aktywności stronicowania przekroczy górny próg reguły D0017.|  
|[DA0017: Intensywne stronicowanie aktywnej pamięci na dysk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Relatywnie wysoki współczynnik stronicowania aktywnej pamięci do i z dysku wystąpił w trakcie przebiegu profilowania. Stawki stronicowania na tym poziomie mają zwykle wpływ na wydajność aplikacji i czas odpowiedzi. Rozważ zmniejszenie alokacji pamięci przez skorygowanie algorytmów. Może być również konieczne uwzględnienie wymagań dotyczących pamięci aplikacji. Spróbuj ponownie uruchomić profilowanie na komputerze z większą ilością pamięci.|
