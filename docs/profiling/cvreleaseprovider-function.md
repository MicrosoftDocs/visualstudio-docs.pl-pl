---
title: Funkcja cvreleaseprovider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62974049"
---
# <a name="cvreleaseprovider-function"></a>Funkcja CvReleaseProvider
Zwalnia dostawcę znaczników. Zwolnienie dostawcy znaczników nie wpłynie na poprzednio utworzoną serię znaczników tego dostawcy. Seria markerów musi być wydana oddzielnie przez wywołanie CvReleaseMarkerSeries. Niepowodzenie wydania dostawcy powoduje przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametry
 `pProvider`Kontekst dostawcy. Nie może być null.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy dostawca został pomyślnie zwolniony lub kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)