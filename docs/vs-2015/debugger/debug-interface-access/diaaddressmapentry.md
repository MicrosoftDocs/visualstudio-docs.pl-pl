---
title: DiaAddressMapEntry — | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164354"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Opisuje wpis w mapie adresowej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementy  
 `rva`  
 Względny adres wirtualny (RVA) w obrazie A.  
  
 `rvaTo`  
 Względny adres wirtualny `rva` jest mapowany na obraz B.  
  
## <a name="remarks"></a>Uwagi  
 Mapa adresów zapewnia tłumaczenie z jednego układu obrazu (A) na inny (B). Tablica `DiaAddressMapEntry` struktur posortowana według `rva` definicji mapowania adresów.  
  
 Aby przetłumaczyć adres, `addrA` w obrazie A na adres, `addrB` w obrazie B wykonaj następujące czynności:  
  
1. Przeszukaj mapę dla wpisu, `e` z największą `rva` mniejszą lub równą `addrA` .  
  
2. Ustaw `delta = addrA – e.rva` .  
  
3. Ustaw `addrB = e.rvaTo + delta` .  
  
   Tablica `DiaAddressMapEntry` struktur jest przenoszona do metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
