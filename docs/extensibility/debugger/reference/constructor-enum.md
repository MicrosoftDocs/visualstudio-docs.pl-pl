---
title: CONSTRUCTOR_ENUM | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 199201037889dbcb1b3019ef7632fc81e9c88db4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958660"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Zaznacza różne rodzaje konstruktorów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 crAll  
 Wybiera wszystkie konstruktory.  
  
 crNonStatic  
 Wybiera niestatycznych konstruktorów.  
  
 crStatic  
 Wybiera konstruktorów statycznych.  
  
## <a name="remarks"></a>Uwagi  
 Przekazywany jako argument do [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)