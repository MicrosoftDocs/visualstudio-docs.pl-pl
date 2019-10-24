---
title: 'IDiaSymbol:: get_countLiveRanges | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 990673afdb01b1471ad75d65036610c486e735c4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740748"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
Pobiera liczbę prawidłowych zakresów adresów skojarzonych z symbolem lokalnym.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_countLiveRanges ( 
   DWORD* count
);
```

#### <a name="parameters"></a>Parametry
 `count`

określoną Zwraca liczbę zakresów adresów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100. dll

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)