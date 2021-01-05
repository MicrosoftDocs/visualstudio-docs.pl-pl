---
title: Basictype | Microsoft Docs
description: Znajdź informacje referencyjne na temat wyliczenia Basictype, które określa typ podstawowy symbolu w zestawie SDK dostępu do interfejsu debugowania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 27fd166b094f74cfbf9b6a37a87804031dedcbc7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728880"
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

Typ podstawowy btVoid to `void` .

Typ podstawowy btChar to `char` Typ (C/C++).

Typ podstawowy btWChar jest znakiem szeroki (Unicode) ( `WCHAR` ).

Typ podstawowy btInt to `signed int` (typ C/C++).

Typ podstawowy btUInt to `unsigned int` (typ C/C++).

Typ podstawowy btFloat to liczba zmiennoprzecinkowa ( `FLOAT` ).

Typ podstawowy btBCD jest kodowane binarnie ( `BCD` ).

Typ podstawowy btBool jest wartością logiczną ( `BOOL` ).

Typ podstawowy btLong to `long int` Typ (C/C++).

Typ podstawowy btULong to `unsigned long int` Typ (C/C++).

Typ podstawowy btCurrency jest walutą.

Typ podstawowy btDate to data/godzina ( `DATE` ).

Typ podstawowy btVariant jest strukturą typu zmiennej ( `VARIANT` ).

Typ podstawowy btComplex jest liczbą zespoloną.

Typ podstawowy btBit jest bitowy.

Typ podstawowy btBSTR jest ciągiem Basic lub binary ( `BSTR` ).

Typ podstawowy btHresult to `HRESULT` .

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez metodę [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
