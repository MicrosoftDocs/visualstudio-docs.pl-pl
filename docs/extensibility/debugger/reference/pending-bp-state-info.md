---
title: PENDING_BP_STATE_INFO | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93b1278c9f0bc11ce4a79e10750f4f7952fba81f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896048"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Zawiera informacje o stanie punktu przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 state  
 Wartość z zakresu od [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) wyliczenie, który określa stan oczekujący punkt przerwania.  
  
 flagi  
 Kombinacja flag z [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) wyliczenia, która określa, czy punkt przerwania zostaje zwirtualizowany.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywany do [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) metody, gdzie jest wypełnione.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)