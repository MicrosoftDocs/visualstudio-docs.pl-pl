---
title: Przestrzeń nazw diagnostyki | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d304a8e4d21365d82f654265ae2f34582b636
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330255"
---
# <a name="diagnostic-namespace"></a>Przestrzeń nazw diagnostyki
`diagnostics`Przestrzeń nazw zapewnia funkcję emitującą znaczniki wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```cpp
namespace diagnostic;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[marker_series — Klasa](../profiling/marker-series-class.md)|Reprezentuje kanał szeregowy zdarzeń generowanych przez jednego dostawcę.|
|[span — Klasa](../profiling/span-class.md)|Definiuje fazę aplikacji.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[marker_importance — Wyliczenie](../profiling/marker-importance-enumeration.md)|Reprezentuje poziom ważności znacznika Concurrency Visualizer.|

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżności

## <a name="see-also"></a>Zobacz też
- [Przestrzeń nazw współbieżności (Concurrency Visualizer)](../profiling/concurrency-namespace-concurrency-visualizer.md)