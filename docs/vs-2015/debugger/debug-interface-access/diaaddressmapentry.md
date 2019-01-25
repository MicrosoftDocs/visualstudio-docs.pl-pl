---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785338"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym artykule opisano wpis z mapy adresów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
2. Ustaw `delta = addrA – e.rva`.  
  
3. Ustaw `addrB = e.rvaTo + delta`.  
  
   Tablica `DiaAddressMapEntry` struktury jest przekazywany do [idiaaddressmap::set_addressmap —](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
