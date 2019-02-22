---
title: marker_series, klasa | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613911"
---
# <a name="markerseries-class"></a>marker_series, klasa
Reprezentuje serial kanał zdarzeń generowanych przez jednego dostawcę.

## <a name="syntax"></a>Składnia

```cpp
class marker_series;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inicjuje nowe wystąpienie klasy `marker_series` klasy.|
|[marker_series:: ~ marker_series — destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Niszczy obiekt marker_series i zwalnia wszystkie zasoby przydzielone.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[marker_series::is_enabled — metoda](../profiling/marker-series-is-enabled-method.md)|Określa, czy dowolnej sesji ma włączone dostawcy.|
|[marker_series::write_alert — metoda](../profiling/marker-series-write-alert-method.md)|Zapisuje plik śledzenia Concurrency Visualizer alertu.|
|[marker_series::write_flag — metoda](../profiling/marker-series-write-flag-method.md)|Zapisuje plik śledzenia Concurrency Visualizer flagę.|
|[marker_series::write_message — metoda](../profiling/marker-series-write-message-method.md)|Zapisuje komunikat do pliku śledzenia w Wizualizatorze współbieżności.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia
 `marker_series`

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Namespace:** CONCURRENCY::Diagnostic —

## <a name="see-also"></a>Zobacz także
- [Diagnostic — przestrzeń nazw](../profiling/diagnostic-namespace.md)