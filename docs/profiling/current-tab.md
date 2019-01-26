---
title: Current Tab | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4303336fe12f817bdb2843d03f9e936a5b1736c1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069150"
---
# <a name="current-tab"></a>Aktualna karta
Klikając **bieżącego** karcie, możesz zobaczyć stos wywołań (jeśli jest dostępny) jest najbardziej zbliżony do bieżącego zaznaczenia punktu na osi czasu zaznaczenie segment wątku procesora CPU.  W tym przypadku punktu zaznaczenia jest reprezentowana przez czarną strzałkę lub daszek powyżej osi czasu. Po wybraniu segment blokujący karetkę nie jest wyświetlany, ponieważ nie było żadnych wykonywania. Jednak segmentu nadal jest wyróżniona i stos wywołań jest wyświetlany.  
  
 **Bieżącego** karta zawiera również informacje o segmentów aktywności DirectX, znaczniki i dostępu We/Wy.  Segmentów aktywności DirectX zostaną wyświetlone informacje o sposobie DMA pakiety są przetwarzane przez kolejce sprzętowej.  Dla znaczników zostaną wyświetlone informacje o typ opisu i znacznika.  Na potrzeby dostępu we/wy zostaną wyświetlone informacje o pliku oraz liczbę bajtów odczytywanych lub zapisywanych.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)