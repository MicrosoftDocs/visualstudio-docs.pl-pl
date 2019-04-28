---
title: Funkcja CvCreateMarkerSeries | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb3ef4d928aaac57f39a48e5be212c1148ef58eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62552684"
---
# <a name="cvcreatemarkerseries-function"></a>Cvcreatemarkerseries — funkcja
Tworzy serię znacznika dla danego dostawcy.

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
 `pProvider` Poprzednio inicjowany przez cvinitprovider — obiekt dostawcy. Nie może mieć wartości NULL.

 `pSeriesName` Nazwa serii znacznika. Nie może mieć wartości NULL, ale dozwolone jest pustym ciągiem.

 `ppMarkerSeries` Adres zmiennej danych wyjściowych, który będzie przechowywał znaczników serii kontekstu. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK znaczników serii został pomyślnie utworzony lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Zobacz także
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)