---
description: Reprezentuje kanał szeregowy zdarzeń generowanych przez jednego dostawcę.
title: Klasa marker_series | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4df579ff4eb43dfca4c386716c49f12dae04e9fa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223618"
---
# <a name="marker_series-class"></a>Klasa marker_series
Reprezentuje kanał szeregowy zdarzeń generowanych przez jednego dostawcę.

## <a name="syntax"></a>Składnia

```cpp
class marker_series;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[marker_series:: marker_series, Konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicjuje nowe wystąpienie klasy `marker_series`.|
|[marker_series:: ~ marker_series, destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Niszczy obiekt marker_series i zwalnia wszystkie przydzieloną zasoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[marker_series:: is_enabled, Metoda](../profiling/marker-series-is-enabled-method.md)|Określa, czy dowolna sesja włączyła dostawcę.|
|[marker_series:: write_alert, Metoda](../profiling/marker-series-write-alert-method.md)|Zapisuje alert do pliku śledzenia Concurrency Visualizer.|
|[marker_series:: write_flag, Metoda](../profiling/marker-series-write-flag-method.md)|Zapisuje flagę w pliku śledzenia Concurrency Visualizer.|
|[marker_series:: write_message, Metoda](../profiling/marker-series-write-message-method.md)|Zapisuje komunikat do pliku śledzenia Concurrency Visualizer.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia
 `marker_series`

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Przestrzeń nazw diagnostyki](../profiling/diagnostic-namespace.md)
