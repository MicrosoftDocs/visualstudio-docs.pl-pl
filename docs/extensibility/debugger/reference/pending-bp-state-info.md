---
title: PENDING_BP_STATE_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d66ecc63e133a75148f06b59b8f1ccf61fe2658d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714080"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Zawiera informacje o stanie punktu przerwania, który jest gotowy do powiązania z lokalizacją kodu.

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
 Wartość z [wyliczenia PENDING_BP_STATE,](../../../extensibility/debugger/reference/pending-bp-state.md) która określa stan oczekującego punktu przerwania.

 `flags`\
 Kombinacja flag z wyliczenia [PENDING_BP_STATE_FLAGS,](../../../extensibility/debugger/reference/pending-bp-state-flags.md) która określa, czy punkt przerwania jest zwirtualizowany.

## <a name="remarks"></a>Uwagi
 Ta struktura jest przekazywana do [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) metody, gdzie jest wypełniona.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
