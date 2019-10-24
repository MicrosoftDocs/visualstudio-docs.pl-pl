---
title: 'IDiaSymbol:: get_isStripped | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12fac0c26c53695dcc9b42794337a7feaea6b0fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740023"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
Pobiera flagę wskazującą, czy symbole prywatne zostały usunięte z pliku symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isStripped(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE`, jeśli usunięto symbole prywatne z pliku symboli; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest dostępna z poziomu typu symbolu `SymTagExe` (zobacz [exe](../../debugger/debug-interface-access/exe.md)).

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)