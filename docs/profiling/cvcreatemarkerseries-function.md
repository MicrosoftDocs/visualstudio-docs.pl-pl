---
title: Funkcja CvCreateMarkerSeries | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności CvCreateMarkerSeries (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8915724c39a656917d6565c60ddc7dfbb0737564
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941037"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries, funkcja
Tworzy serię znaczników dla danego dostawcy.

## <a name="syntax"></a>Składnia

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>Parametry
 `pProvider` Obiekt dostawcy został wcześniej zainicjowany przez CvInitProvider —. Nie może mieć wartości NULL.

 `pSeriesName` Nazwa serii znaczników. Nie może mieć wartości NULL, ale jest dozwolony pusty ciąg.

 `ppMarkerSeries` Adres zmiennej wyjściowej, w której będzie przechowywany kontekst serii znaczników. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy seria znaczników zostanie pomyślnie utworzona lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)