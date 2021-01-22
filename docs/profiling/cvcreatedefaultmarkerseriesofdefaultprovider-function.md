---
title: Funkcja Cvcreatedefaultmarkerseriesofdefaultprovider — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności Cvcreatedefaultmarkerseriesofdefaultprovider — (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 0802b91bb9cbbbe31cb156104bb7b5df3fda1282
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686184"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Cvcreatedefaultmarkerseriesofdefaultprovider —, funkcja
Tworzy domyślną serię znaczników domyślnego dostawcy.

## <a name="syntax"></a>Składnia

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `ppProvider` Adres zmiennej obiektu dostawcy. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.

 `ppMarkerSeries` Adres zmiennej obiektu serii znaczników. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy zarówno dostawca, jak i seria znaczników zostały pomyślnie utworzone lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)