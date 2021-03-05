---
description: Opisuje wpis w mapie adresowej.
title: DiaAddressMapEntry — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdac0233901ac8571bbfb2a5d6659adf69e35298
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149194"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Opisuje wpis w mapie adresowej.

## <a name="syntax"></a>Składnia

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementy
`rva` Względny adres wirtualny (RVA) w obrazie A.

`rvaTo` Względny adres wirtualny `rva` jest mapowany na obraz B.

## <a name="remarks"></a>Uwagi
Mapa adresów zapewnia tłumaczenie z jednego układu obrazu (A) na inny (B). Tablica `DiaAddressMapEntry` struktur posortowana według `rva` definicji mapowania adresów.

Aby przetłumaczyć adres, `addrA` w obrazie A na adres, `addrB` w obrazie B wykonaj następujące czynności:

1. Przeszukaj mapę dla wpisu, `e` z największą `rva` mniejszą lub równą `addrA` .

2. Ustaw `delta = addrA - e.rva` .

3. Ustaw `addrB = e.rvaTo + delta` .

    Tablica `DiaAddressMapEntry` struktur jest przenoszona do metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
