---
title: Funkcja Cvcreatemarkerserieswithcodepagea — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności Cvcreatemarkerserieswithcodepagea — (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 69f4f19df03c4c2f6bb21a5e2262a4a1495adab8
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686158"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Cvcreatemarkerserieswithcodepagea —, funkcja
Tworzy serię znaczników dla danego dostawcy i określonej strony kodowej. Ta funkcja może służyć do określania strony kodowej jawnie dla tekstu pisanego przez funkcje ANSI interfejsu API znaczników. Ustawienie strony kodowej może być przydatne w przypadku, gdy śledzenie jest przechwytywane, a następnie analizowane na różnych maszynach przy użyciu różnych ustawień regionalnych/języków. Domyślnie jest używana strona kodowa zwrócona przez funkcję GetACP ().

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
 `pProvider` Obiekt dostawcy został wcześniej zainicjowany przez CvInitProvider —. Nie może mieć wartości NULL.

 `pSeriesName` Nazwa serii znaczników. Nie może mieć wartości NULL, ale jest dozwolony pusty ciąg.

 `nTextCodePage` Prawidłowa strona kodowa.

 `ppMarkerSeries` Adres zmiennej wyjściowej, w której będzie przechowywany kontekst serii znaczników. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy seria znaczników zostanie pomyślnie utworzona lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)