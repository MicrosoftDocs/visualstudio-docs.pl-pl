---
title: IDebugDynamicField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53e4bd31833ad5cf3441638c3735230b89a16cf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938470"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Ten interfejs reprezentuje typ zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawców symbol jako klasę bazową dla dowolnego typu, który może być ustalony w czasie wykonywania. Te informacje dotyczą tylko kodu zarządzanego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs reprezentuje klasę bazową, z którego mogą być uzyskane bardziej wyspecjalizowane interfejsy.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Ten interfejs nie dostarcza żadnych metod innych niż odziedziczone z `IDebugField`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)