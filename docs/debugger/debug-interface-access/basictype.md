---
title: BasicType | Microsoft Docs
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
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829735"
---
# <a name="basictype"></a>BasicType
Określa podstawowy typ symbolu.

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
btNoType żaden typ podstawowy jest określona.

btVoid typ podstawowy jest `void`.

btChar typ podstawowy jest `char` (C/C++ typu).

btWChar typ podstawowy jest znakiem dwubajtowym (Unicode) (`WCHAR`).

btInt typ podstawowy jest `signed int` (C/C++ typu).

btUInt typ podstawowy jest `unsigned int` (C/C++ typu).

btFloat typ podstawowy jest liczba zmiennoprzecinkowa (`FLOAT`).

btBCD typ podstawowy jest kodowane dane binarne wartości dziesiętnej (`BCD`).

btBool typ podstawowy jest wartością logiczną (`BOOL`).

btLong typ podstawowy jest `long int` (C/C++ typu).

btULong typ podstawowy jest `unsigned long int` (C/C++ typu).

btCurrency typ podstawowy jest waluta.

btDate typ podstawowy jest daty/godziny (`DATE`).

btVariant typ podstawowy jest strukturą typu zmiennej (`VARIANT`).

btComplex typ podstawowy jest liczbą.

btBit typ podstawowy jest nieco.

btBSTR typ podstawowy jest ciągiem podstawowe lub binarny (`BSTR`).

btHresult typ podstawowy jest `HRESULT`.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_basetype —](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
