---
title: Funkcja CvReleaseMarkerSeries | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d100b7ff37ea5a3cd224fd420f14e4cb23061903
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974146"
---
# <a name="cvreleasemarkerseries-function"></a>Cvreleasemarkerseries — funkcja
Zwalnia znaczników serii. Nie używaj znaczników serii obiektu po zwalniania w przeciwnym razie aplikacja może ulec awarii. Nie można zwolnić znaczników serii powoduje, że przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `pMarkerSeries` Adres dostawcy zmiennej obiektu. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.

## <a name="return-value"></a>Wartość zwracana
 S_OK znaczników serii jest pomyślnie zwolnione lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz także
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)