---
title: Memorytypeenum — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a83a37a3aa454885d714be667ca7678ae543ff09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875919"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Określa typ pamięci, aby uzyskać dostęp.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `MemTypeCode`  
 Uzyskuje dostęp do kodu tylko pamięci.  
  
 `MemTypeData`  
 Uzyskuje dostęp do danych lub stosu pamięci.  
  
 `MemTypeStack`  
 Uzyskuje dostęp do tylko stosu pamięci.  
  
 `MemTypeAny`  
 Uzyskuje dostęp do dowolnego rodzaju pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są przekazywane do [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) metodę, aby ograniczyć dostęp do różnych typów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)