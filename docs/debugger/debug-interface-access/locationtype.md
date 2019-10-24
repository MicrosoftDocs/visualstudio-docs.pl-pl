---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738647"
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
Informacje o lokalizacji `LocIsNull` są niedostępne.

Lokalizacja `LocIsStatic` jest statyczna.

Lokalizacja `LocIsTLS` znajduje się w lokalnym magazynie wątków.

Lokalizacja `LocIsRegRel` jest zależna od rejestru.

Lokalizacja `LocIsThisRel` jest `this` względem.

Lokalizacja `LocIsEnregistered` jest w rejestrze.

`LocIsBitField` lokalizacja znajduje się w polu bitowym.

Lokalizacja `LocIsSlot` to gniazdo języka pośredniego firmy Microsoft (MSIL).

Lokalizacja `LocIsIlRel` jest zależna od języka MSIL.

Lokalizacja `LocInMetaData` jest w metadanych.

Lokalizacja `LocIsConstant` jest w stałej wartości.

`LocTypeMax` liczbę typów lokalizacji w tym wyliczeniu.

## <a name="remarks"></a>Uwagi
Właściwości dostępne dla interfejsu [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) zależą od lokalizacji symbolu w pliku obrazu. Aby uzyskać więcej informacji, zobacz [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md).

Wartości w tym wyliczeniu są zwracane przez wywołanie metody [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)
