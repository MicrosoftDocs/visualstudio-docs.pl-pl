---
title: diagnostyka Obszar nazw | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970086"
---
# <a name="diagnostic-namespace"></a>diagnostyczna przestrzeń nazw
Obszar `diagnostics` nazw udostępnia funkcje emitowania znaczników wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```cpp
namespace diagnostic;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[marker_series, klasa](../profiling/marker-series-class.md)|Reprezentuje kanał szeregowy zdarzeń generowanych przez jednego dostawcę.|
|[span, klasa](../profiling/span-class.md)|Definiuje fazę aplikacji.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[Wyliczenie marker_importance](../profiling/marker-importance-enumeration.md)|Reprezentuje poziom ważności znacznika wizualizatora współbieżności.|

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżności

## <a name="see-also"></a>Zobacz też
- [Obszar nazw współbieżności (wizualizator współbieżności)](../profiling/concurrency-namespace-concurrency-visualizer.md)