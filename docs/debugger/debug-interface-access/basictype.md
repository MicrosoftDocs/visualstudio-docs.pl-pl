---
title: Basictype | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745482"
---
# <a name="basictype"></a>BasicType
Określa typ podstawowy symbolu.

## <a name="syntax"></a>Składnia

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementy
btNoType nie jest określony typ podstawowy.

Typ podstawowy btVoid jest `void`.

Typ podstawowy btChar to `char` (C/C++ typ).

Typ podstawowy btWChar jest znakiem szerokim (Unicode) (`WCHAR`).

Typ podstawowy btInt to `signed int` (C/C++ typ).

Typ podstawowy btUInt to `unsigned int` (C/C++ typ).

Typ podstawowy btFloat jest liczbą zmiennoprzecinkową (`FLOAT`).

Typ podstawowy btBCD jest kodowany binarnie cyfrą dziesiętną (`BCD`).

Typ podstawowy btBool jest wartością logiczną (`BOOL`).

Typ podstawowy btLong to `long int` (C/C++ typ).

Typ podstawowy btULong to `unsigned long int` (C/C++ typ).

Typ podstawowy btCurrency jest walutą.

Typ podstawowy btDate to data/godzina (`DATE`).

Typ podstawowy btVariant jest strukturą typu zmiennej (`VARIANT`).

Typ podstawowy btComplex jest liczbą zespoloną.

Typ podstawowy btBit jest bitowy.

Typ podstawowy btBSTR to podstawowy lub binarny ciąg (`BSTR`).

Typ podstawowy btHresult jest `HRESULT`.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez metodę [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
