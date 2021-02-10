---
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7c1e2b8b537607f6dc57d807d276c5b72ccb144
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968570"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Zawiera informacje o stanie punktu przerwania, który jest gotowy do powiązania z lokalizacją w kodzie.

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
 `state`\
 Wartość z wyliczenia [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) , która określa stan oczekującego punktu przerwania.

 `flags`\
 Kombinacja flag z wyliczenia [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) , która określa, czy punkt przerwania jest zwirtualizowany.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przenoszona do metody [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) , w której jest wypełniana.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
