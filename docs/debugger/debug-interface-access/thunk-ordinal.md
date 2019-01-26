---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 756a1b9fde9c85ca914b00924cb13191859be78e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952304"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Określa typy thunk.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementy  
 THUNK_ORDINAL_NOTYPE  
 Standardowe wywołanie.  
  
 THUNK_ORDINAL_ADJUSTOR  
 A `this` adjustor thunk.  
  
 THUNK_ORDINAL_VCALL  
 Thunk wywołanie wirtualne.  
  
 THUNK_ORDINAL_PCODE  
 Thunk P-code.  
  
 THUNK_ORDINAL_LOAD  
 Thunk obciążenia opóźnienia.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk trampoline przyrostowej (trampoline sekcją thunk służy do Odbijanie wywołania z miejsca w pamięci z jednego do drugiego).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Thunk trampoline punktu gałęzi.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane z wywołania [idiasymbol::get_thunkordinal —](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)