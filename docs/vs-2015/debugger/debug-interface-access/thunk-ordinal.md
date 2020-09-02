---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576411"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyznacza typy thunk.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Standardowa thunk.  
  
 THUNK_ORDINAL_ADJUSTOR  
 `this`Thunk korygowania.  
  
 THUNK_ORDINAL_VCALL  
 Thunk wywołania wirtualnego.  
  
 THUNK_ORDINAL_PCODE  
 P-Code thunk.  
  
 THUNK_ORDINAL_LOAD  
 Opóźnij thunk ładowania.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Przyrostowe Trampoline thunk (Trampoline thunk służy do odbijania wywołań z jednego miejsca w pamięci do innej).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Punkt rozgałęzienia Trampoline thunk.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane z wywołania metody [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
