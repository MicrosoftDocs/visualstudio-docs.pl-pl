---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aafc62f5920db70bd881bd3a541cfcfabfac360
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862347"
---
# <a name="locationtype"></a>LocationType
Wskazuje rodzaj informacji o lokalizacji zawartych w symbolu.

## <a name="syntax"></a>Składnia

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elementy
`LocIsNull` Informacje o lokalizacji są niedostępne.

`LocIsStatic` Lokalizacja jest statyczna.

`LocIsTLS` Lokalizacja znajduje się w lokalnym magazynie wątków.

`LocIsRegRel` Lokalizacja jest zależna od rejestru.

`LocIsThisRel` Lokalizacja jest `this` względna.

`LocIsEnregistered` Lokalizacja znajduje się w rejestrze.

`LocIsBitField` Lokalizacja znajduje się w polu bitowym.

`LocIsSlot` Lokalizacja jest miejscem języka pośredniego firmy Microsoft (MSIL).

`LocIsIlRel` Lokalizacja jest zależna od języka MSIL.

`LocInMetaData` Lokalizacja znajduje się w metadanych.

`LocIsConstant` Lokalizacja jest w stałej wartości.

`LocTypeMax` Liczba typów lokalizacji w tym wyliczeniu.

## <a name="remarks"></a>Uwagi
Właściwości dostępne dla interfejsu [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) zależą od lokalizacji symbolu w pliku obrazu. Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md).

Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)
