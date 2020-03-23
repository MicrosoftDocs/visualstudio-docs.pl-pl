---
title: Funkcja cvCreateDefaultMarkerSeriesOfDefaultProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a13174b2991b7c69535a6d1910f761890397818
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552697"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Funkcja CvCreateDefaultMarkerSeriesOfDefaultProvider
Tworzy domyślną serię znaczników domyślnego dostawcy.

## <a name="syntax"></a>Składnia

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `ppProvider`Adres zmiennej obiektu dostawcy. Adres nie może być NULL, zmienna może mieć dowolną wartość.

 `ppMarkerSeries`Adres zmiennej obiektu serii znaczników. Adres nie może być NULL, zmienna może mieć dowolną wartość.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy pomyślnie utworzone są zarówno seria dostawcy, jak i znacznika lub kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)