---
title: PENDING_BP_STATE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69c8dbe1022ee0b1b2ff034d2b83b947c8fb3df6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713994"
---
# <a name="pending_bp_state"></a>PENDING_BP_STATE
Określa stan oczekującego punktu przerwania (punktu przerwania, który nie został jeszcze powiązany).

## <a name="syntax"></a>Składnia

```cpp
enum enum_PENDING_BP_STATE { 
   PBPS_NONE     = 0x0000,
   PBPS_DELETED  = 0x0001,
   PBPS_DISABLED = 0x0002,
   PBPS_ENABLED  = 0x0003
};
typedef DWORD PENDING_BP_STATE;
```

```csharp
public enum enum_PENDING_BP_STATE { 
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
 Użyj jako `state` element członkowski [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struktury.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
