---
title: DiaAddressMapEntry — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745263"
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
`rva` względny adres wirtualny (RVA) w obrazie A.

`rvaTo` względny adres wirtualny `rva` jest mapowany na obraz B.

## <a name="remarks"></a>Uwagi
Mapa adresów zapewnia tłumaczenie z jednego układu obrazu (A) na inny (B). Tablica struktur `DiaAddressMapEntry` posortowanych przez `rva` definiuje mapę adresów.

Aby przetłumaczyć adres, `addrA`, w obraz A na adres, `addrB`, w obrazie B, wykonaj następujące czynności:

1. Przeszukaj mapę dla wpisu, `e`, z największą `rva` mniejszą lub równą `addrA`.

2. Ustaw `delta = addrA - e.rva`.

3. Ustaw `addrB = e.rvaTo + delta`.

    Tablica struktur `DiaAddressMapEntry` jest przenoszona do metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: dia2. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
