---
title: Metoda marker_series::write_message | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be6194936264d6038c4dc1e26b5d05f539f0dc6a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830905"
---
# <a name="markerserieswritemessage-method"></a>marker_series::write_message — metoda
Zapisuje komunikat do pliku śledzenia w Wizualizatorze współbieżności.

## <a name="syntax"></a>Składnia

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format` Ciąg formatu złożonego, który zawiera tekst zmieszać z zero lub więcej elementów formatu, które odnoszą się do obiektów na liście argumentów.

 `_Importance` Poziom ważności.

 `_Category` Poziom Category.Importance.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Namespace:** CONCURRENCY::Diagnostic —

## <a name="see-also"></a>Zobacz także
- [marker_series, klasa](../profiling/marker-series-class.md)