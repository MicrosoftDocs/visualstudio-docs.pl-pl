---
description: 'IDiaFrameData:: get_allocatesBasePointer Pobiera flagę wskazującą, czy wskaźnik podstawowy został przydzielony do kodu w tym zakresie adresów.'
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fce5e5dbd12be7bae6ba1937b30c8a5d62de3ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157749"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Pobiera flagę wskazującą, czy wskaźnik podstawowy został przydzielony do kodu w tym zakresie adresów. Ta metoda jest przestarzała.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Zwraca `TRUE` czy jest przydzielony wskaźnik podstawowy; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość, `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta właściwość powinna być używana tylko przez kod, który wcześniej uzyskał dostęp FPO_DATA, lub gdy ciąg programu zwracany przez metodę [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) ma wartość `NULL` . W przeciwnym razie ciąg programu zawiera wszystkie informacje, które są konieczne do obliczenia poprzednich wartości rejestru.

## <a name="see-also"></a>Zobacz też
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
