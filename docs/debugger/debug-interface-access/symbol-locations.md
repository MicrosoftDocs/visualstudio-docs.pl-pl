---
title: Lokalizacje symboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f972d0d072aa36cab608c85305588f6bbd5d47d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738540"
---
# <a name="symbol-locations"></a>Lokalizacje symboli
Większość symboli ma zdefiniowaną lokalizację w pliku obrazu. Lokalizacja symbolu jest określana z wartością z wyliczenia elementu [LocationType](../../debugger/debug-interface-access/locationtype.md) . Symbol może obsługiwać dodatkowe właściwości w zależności od jego lokalizacji.

 W poniższej tabeli przedstawiono najczęściej używane typy lokalizacji i ich dodatkowe właściwości.

|Typ lokalizacji|Dodatkowe właściwości|
|-------------------|---------------------------|
|`LocIsNull`|brak|
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (jeśli są włączone względne adresy wirtualne)<br /><br /> [IDiaSymbol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (Jeśli baza obrazu ma ustawioną wartość różną od zera)|
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)
- [IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)
- [IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)
- [IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)
- [IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)
- [IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)
- [IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)
- [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)