---
title: Funkcja CvLeaveSpan | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776c24777403b9d88de31e11d0c28fe104666600
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974118"
---
# <a name="cvleavespan-function"></a>Cvleavespan — funkcja
Oznacza koniec zakresu.

## <a name="syntax"></a>Składnia

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parametry
 `pSpan` Span obiekt zwrócony przez poprzednie wywołanie CvEnterSpan *. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy komunikat jest pomyślnie zapisane. Kod błędu w przypadku, gdy było żadnych błędów. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz także
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)