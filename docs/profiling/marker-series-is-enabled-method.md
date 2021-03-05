---
description: Określa, czy dowolna sesja włączyła dostawcę.
title: 'marker_series:: is_enabled Metoda | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ce01d71b3fac63062a3f823f1862fd199fa39be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223579"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series:: is_enabled, Metoda
Określa, czy dowolna sesja włączyła dostawcę.

## <a name="syntax"></a>Składnia

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parametry
 `_Importance` Poziom ważności.

 `_Category` Kategorii.

## <a name="return-value"></a>Wartość zwracana

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Klasa marker_series](../profiling/marker-series-class.md)
