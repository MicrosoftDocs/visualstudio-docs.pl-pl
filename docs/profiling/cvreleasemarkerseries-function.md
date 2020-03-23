---
title: Funkcja CvReleaseMarkerSeries | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62974146"
---
# <a name="cvreleasemarkerseries-function"></a>Funkcja CvReleaseMarkerSeries
Zwalnia serię znaczników. Nie należy używać obiektu serii znaczników po zwolnieniu w przeciwnym razie aplikacja może ulec awarii. Niepowodzenie zwolnienia serii znaczników powoduje przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `pMarkerSeries`Adres zmiennej obiektu dostawcy. Adres nie może być NULL, zmienna może mieć dowolną wartość.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy seria znaczników zostanie pomyślnie wydana lub kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)