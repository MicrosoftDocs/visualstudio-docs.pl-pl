---
title: Typ datakind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197633"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wskazuje konkretny zakres wartości danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementy  
 DataIsUnknown  
 Nie można określić symbolu danych.  
  
 DataIsLocal  
 Element danych jest zmienną lokalną.  
  
 DataIsStaticLocal  
 Element danych jest statyczną zmienną lokalną.  
  
 DataIsParam  
 Element danych jest parametrem formalnym.  
  
 DataIsObjectPtr  
 Element danych jest wskaźnikiem obiektu ( `this` ).  
  
 DataIsFileStatic  
 Element danych jest zmienną o zakresie pliku.  
  
 DataIsGlobal  
 Element danych jest zmienną globalną.  
  
 DataIsMember  
 Element danych jest zmienną elementu członkowskiego obiektu.  
  
 DataIsStaticMember  
 Element danych jest zmienną statyczną klasy.  
  
 DataIsConstant  
 Element danych jest stałą wartością.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez metodę [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst. h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
