---
title: Funkcja Cvreleaseprovider — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności Cvreleaseprovider — (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948234"
---
# <a name="cvreleaseprovider-function"></a>Cvreleaseprovider —, funkcja
Dostawca znaczników wydań. Zwolnienie dostawcy znaczników nie będzie miało wpływu na wcześniej utworzoną serię znaczników tego dostawcy. Seria znaczników musi być wykorzystana oddzielnie przez wywołanie CvReleaseMarkerSeries —. Niepowodzenie zwolnienia dostawcy powoduje przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametry
 `pProvider` Kontekst dostawcy. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy dostawca został pomyślnie wydzierżawiony lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)