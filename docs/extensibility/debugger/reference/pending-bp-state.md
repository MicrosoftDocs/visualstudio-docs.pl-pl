---
title: PENDING_BP_STATE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6707c09e409e2a04d7afec0322b575a70cea33cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349873"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Określa stan oczekujący punkt przerwania (punkt przerwania, która nie została jeszcze powiązana).

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
 Symbol zastępczy zera. Nigdy nie zostanie zwrócona ta wartość.

 `PBPS_DELETED`\
 Wskazuje, że oczekujący punkt przerwania został usunięty.

 `PBPS_DISABLED`\
 Wskazuje, czy oczekujący punkt przerwania jest wyłączona.

 `PBPS_ENABLED`\
 Wskazuje, że oczekujący punkt przerwania jest włączony.

## <a name="remarks"></a>Uwagi
 Użyj jako `state` członkiem [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struktury.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)