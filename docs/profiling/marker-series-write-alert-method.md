---
title: 'marker_series:: write_alert Metoda | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency, diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5e79bab25885c8759ea5726b037771a4943c563
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329639"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series:: write_alert, Metoda
Zapisuje alert do pliku śledzenia Concurrency Visualizer.

## <a name="syntax"></a>Składnia

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format` Ciąg formatu złożonego, który zawiera tekst, który jest przemieszany z zerem lub więcej elementów formatu, który odpowiada obiektom na liście argumentów.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Klasa marker_series](../profiling/marker-series-class.md)