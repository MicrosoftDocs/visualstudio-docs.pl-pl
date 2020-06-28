---
title: 'IDiaSymbol:: get_countLiveRanges | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 89a6198a73adc5a9f4afec1f3b40302263660a29
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463975"
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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="requirements"></a>Wymagania
 Nagłówek: dia2. h

 Biblioteka: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)