---
title: Diaaddressmapentry — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cadfe96bc0bf0ac0395d93c2ef0b156b9965ed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964088"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
W tym artykule opisano wpis z mapy adresów.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
struct DiaAddressMapEntry {   
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