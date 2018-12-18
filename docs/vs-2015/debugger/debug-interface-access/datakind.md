---
title: Datakind — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93c67b0199524072bf45558dc1713c760567495c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760472"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wskazuje zakresu określonej wartości danych.  
  
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
 Nie można ustalić symbol danych.  
  
 DataIsLocal  
 Element danych jest zmienną lokalną.  
  
 DataIsStaticLocal  
 Element danych jest statyczna zmienna lokalna.  
  
 DataIsParam  
 Element danych jest parametrów formalnych.  
  
 DataIsObjectPtr  
 Element danych jest wskaźnikiem obiektu (`this`).  
  
 DataIsFileStatic  
 Element danych jest zmienną o zakresie pliku.  
  
 DataIsGlobal  
 Element danych jest zmienną globalną.  
  
 DataIsMember  
 Element danych jest zmienną elementu członkowskiego obiektu.  
  
 DataIsStaticMember  
 Element danych jest zmienna statyczna klasy.  
  
 DataIsConstant  
 Element danych jest wartością stałą.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_datakind —](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)



