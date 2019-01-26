---
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9638256c3aaf3d025b59b7fba89cf33e72a47a1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006427"
---
# <a name="bpstate"></a>BP_STATE
Określa istnienie powiązany punkt przerwania i określa, czy jest włączony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPS_NONE  
 Określa, czy istnieje nie punktu przerwania.  
  
 BPS_DELETED  
 Określa, że punkt przerwania został usunięty.  
  
 BPS_DISABLED  
 Określa, że punkt przerwania jest wyłączona.  
  
 BPS_ENABLED  
 Określa, że punkt przerwania jest włączony.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócone w wyniku [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)