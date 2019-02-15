---
title: DiaAddressMapEntry | Microsoft Docs
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
ms.openlocfilehash: b472c52934353e6324d72077f8ea878467159cbd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318644"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
W tym artykule opisano wpis z mapy adresów.

## <a name="syntax"></a>Składnia

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementy
`rva`  
Względny adres wirtualny (RVA) obraz A.

`rvaTo`  
Względny adres wirtualny `rva` jest mapowany na obrazie B.

## <a name="remarks"></a>Uwagi
Mapa adres udostępnia tłumaczenia z jednego obrazu układu (A) do innego (B). Tablica `DiaAddressMapEntry` struktur, posortowane według `rva` definiuje mapę adresu.

Do translacji adresów `addrA`, na ilustracji A adres `addrB`, na ilustracji B, wykonaj następujące czynności:

1. Wyszukaj mapy dla wpisu, `e`, za pomocą największej `rva` mniejsze niż lub równe `addrA`.

2. Ustaw `delta = addrA - e.rva`.

3. Ustaw `addrB = e.rvaTo + delta`.

    Tablica `DiaAddressMapEntry` struktury jest przekazywany do [idiaaddressmap::set_addressmap —](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: dia2.h

## <a name="see-also"></a>Zobacz też
[Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
