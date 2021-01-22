---
title: Przestrzeń nazw diagnostyki | Microsoft Docs
description: Użyj przestrzeni nazw diagnostyki, aby emitować znaczniki Concurrency Visualizer. Przestrzeń nazw diagnostyki jest członkiem przestrzeni nazw współbieżności.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686548"
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