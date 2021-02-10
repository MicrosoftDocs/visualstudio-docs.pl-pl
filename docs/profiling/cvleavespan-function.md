---
title: Funkcja Cvleavespan — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności Cvleavespan — (biblioteka C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da049fc5cc96e9eaa6830159db8c60f9469e2ac4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948260"
---
# <a name="cvleavespan-function"></a>Cvleavespan —, funkcja
Oznacza koniec zakresu.

## <a name="syntax"></a>Składnia

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parametry
 `pSpan` Obiekt span zwrócony przez poprzednie wywołanie do CvEnterSpan *. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy komunikat został pomyślnie zapisany. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)