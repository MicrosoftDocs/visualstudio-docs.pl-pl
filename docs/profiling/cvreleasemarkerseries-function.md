---
title: Funkcja CvReleaseMarkerSeries — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności CvReleaseMarkerSeries — (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a69f60a991b9d88e6969992edbfe8eabdb7bd116
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686457"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries —, funkcja
Zwalnia serię znaczników. Nie używaj obiektu serii znaczników po zwolnieniu w przeciwnym razie aplikacja może ulec awarii. Niepowodzenie zwolnienia serii znaczników powoduje przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `pMarkerSeries` Adres zmiennej obiektu dostawcy. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy seria znaczników zostanie pomyślnie wydana lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)