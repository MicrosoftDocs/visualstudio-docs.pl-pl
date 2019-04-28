---
title: Metoda marker_series::write_flag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09cca9bd1e3babccb0debc369881a0efa00fa0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830814"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag — metoda
Zapisuje plik śledzenia Concurrency Visualizer flagę.

## <a name="syntax"></a>Składnia

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format` Ciąg formatu złożonego, który zawiera tekst zmieszać z zero lub więcej elementów formatu, które odnoszą się do obiektów na liście argumentów.

 `_Importance` Poziom ważności.

 `_Category` Kategoria.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Namespace:** CONCURRENCY::Diagnostic —

## <a name="see-also"></a>Zobacz także
- [marker_series, klasa](../profiling/marker-series-class.md)