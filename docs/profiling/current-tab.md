---
title: Bieżąca karta | Microsoft Docs
description: Wybierz bieżącą kartę widoku wątki, aby wyświetlić stos wywołań dla segmentu wątku procesora lub segmentu blokującego. Informacje o segmentach DirectX są również dostępne.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 65261d6304ead5ade7c28f40495fa68afb0c2171
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686222"
---
# <a name="current-tab"></a>Bieżąca karta
Klikając **bieżącą** kartę, w przypadku wybrania segmentu wątku procesora można zobaczyć stos wywołań (jeśli jest dostępny) znajdujący się najbliżej bieżącego punktu zaznaczenia na osi czasu.  W takim przypadku punkt wyboru jest reprezentowany przez czarną strzałkę lub karetkę powyżej osi czasu. Gdy zaznaczony jest segment blokujący, karetka nie jest wyświetlana, ponieważ nie było żadnego wykonania. Jednak segment jest nadal wyróżniony i zostanie wyświetlony stos wywołań.

 **Bieżąca** karta zawiera również informacje o segmentach aktywności DirectX, znacznikach i dostępie we/wy.  W przypadku segmentów aktywności DirectX informacje o sposobie przetwarzania pakietów DMA przez kolejkę sprzętu są wyświetlane.  Dla znaczników są wyświetlane informacje o opisie i typie znacznika.  W przypadku dostępu we/wy zostanie wyświetlona informacja o pliku i liczbie bajtów odczytywanych lub zapisywana.

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)