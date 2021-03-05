---
description: Określa stan oczekującego punktu przerwania (punkt przerwania, który nie został jeszcze powiązany).
title: PENDING_BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce0ceedd50fbdf6345b49143c4634f49dec308f7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222123"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Określa stan oczekującego punktu przerwania (punkt przerwania, który nie został jeszcze powiązany).

## <a name="syntax"></a>Składnia

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Pola
 `PBPS_NONE`\
 Symbol zastępczy dla zera. Ta wartość nigdy nie jest zwracana.

 `PBPS_DELETED`\
 Wskazuje, że oczekujący punkt przerwania został usunięty.

 `PBPS_DISABLED`\
 Wskazuje, że oczekujący punkt przerwania jest wyłączony.

 `PBPS_ENABLED`\
 Wskazuje, że oczekujący punkt przerwania jest włączony.

## <a name="remarks"></a>Uwagi
 Użyj jako `state` elementu członkowskiego struktury [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
