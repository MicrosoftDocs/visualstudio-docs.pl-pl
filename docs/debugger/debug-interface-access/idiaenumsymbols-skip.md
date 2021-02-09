---
title: 'IDiaEnumSymbols:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2ec6c696268e069e26eeaf55139debbeac47054
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865154"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Pomija określoną liczbę symboli w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba symboli w sekwencji wyliczenia do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` czy nie ma więcej symboli do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)