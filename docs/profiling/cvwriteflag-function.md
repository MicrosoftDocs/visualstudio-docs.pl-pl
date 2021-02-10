---
title: Funkcja CvWriteFlag | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności CvWriteFlag (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e24782f38ec3512349efa123f5aed5a068c6b59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948169"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag, funkcja
Zapisuje flagę w pliku śledzenia Concurrency Visualizer.

## <a name="syntax"></a>Składnia

```C
HRESULT CvWriteFlagExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteFlagExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteFlagExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteFlagExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parametry
 `argList` Lista argumentów.

 `category` Kategorii.

 `level` Poziom ważności.

 `pMarkerSeries` Prawidłowy kontekst serii znaczników. Nie może mieć wartości NULL.

 `pMessage` Ciąg formatu komunikatu. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy komunikat został pomyślnie zapisany. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

 **Unicode:** CvWriteFlagExW, CvWriteFlagExVW

 <strong>ANSI:</strong> CvWriteFlagExA, CvWriteFlagExVA

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)