---
title: Funkcja CvWriteAlert | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b7cc2316168d14c6c996c4d55065771c85ffdfc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62989771"
---
# <a name="cvwritealert-function"></a>Funkcja CvWriteAlert
Zapisuje alert do pliku śledzenia wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```C
HRESULT CvWriteAlertW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteAlertA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteAlertVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteAlertVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parametry
 `argList`Lista argumentów.

 `pMarkerSeries`Prawidłowy kontekst serii znaczników. Nie może być null.

 `pMessage`Ciąg formatu wiadomości. Nie może być null.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy wiadomość zostanie pomyślnie napisana. Kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

 **Unicode:** CvWriteAlertW, CvWriteAlertVW

 **ANSI:** CvWriteAlertA, CvWriteAlertVA

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)