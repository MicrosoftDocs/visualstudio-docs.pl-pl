---
title: Funkcja CvCreateMarkerSeriesWithCodePageA | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7e540e56ce0e97ac2c6aa2e42012569f9e4f272
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553074"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA, funkcja
Tworzy serię znaczników dla danego dostawcy i określoną stronę kodową. Ta funkcja może służyć do określenia strony kodowej jawnie dla tekstu zapisanego przez funkcje INTERFEJSU API znacznika ANSI. Ustawienie strony kodowej może być przydatne w przypadku, gdy śledzenie jest przechwytywane, a następnie analizowane na różnych komputerach z różnymi ustawieniami/językami. Domyślnie używana jest strona kodowa zwrócona przez funkcję GetACP().

## <a name="syntax"></a>Składnia

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parametry
 `pProvider`Obiekt dostawcy zainicjowany wcześniej przez CvInitProvider. Nie może być null.

 `pSeriesName`Nazwa serii znaczników. Nie może być null, ale pusty ciąg jest dozwolone.

 `nTextCodePage`Prawidłowa strona kodowa.

 `ppMarkerSeries`Adres zmiennej wyjściowej, która będzie przechowywać kontekst serii znaczników. Nie może być null.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy seria znaczników jest pomyślnie utworzona lub kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)