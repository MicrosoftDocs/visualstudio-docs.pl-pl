---
title: Klasa marker_series | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62575920"
---
# <a name="marker_series-class"></a>klasa marker_series
Reprezentuje kanał szeregowy zdarzeń generowanych przez jednego dostawcę.

## <a name="syntax"></a>Składnia

```cpp
class marker_series;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktorzy publiczni

|Nazwa|Opis|
|----------|-----------------|
|[marker_series::marker_series konstruktor](../profiling/marker-series-marker-series-constructor.md)|Inicjuje nowe wystąpienie klasy `marker_series`.|
|[marker_series::~marker_series destruktor](../profiling/marker-series-tilde-marker-series-destructor.md)|Niszczy marker_series obiekt i uwalnia wszystkie przydzielone zasoby.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[marker_series::metoda is_enabled](../profiling/marker-series-is-enabled-method.md)|Określa, czy którakolwiek sesja włączyła dostawcę.|
|[marker_series::metoda write_alert](../profiling/marker-series-write-alert-method.md)|Zapisuje alert do pliku śledzenia wizualizatora współbieżności.|
|[marker_series::metoda write_flag](../profiling/marker-series-write-flag-method.md)|Zapisuje flagę do pliku śledzenia wizualizatora współbieżności.|
|[marker_series::metoda write_message](../profiling/marker-series-write-message-method.md)|Zapisuje komunikat do pliku śledzenia wizualizatora współbieżności.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia
 `marker_series`

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też
- [diagnostyczna przestrzeń nazw](../profiling/diagnostic-namespace.md)