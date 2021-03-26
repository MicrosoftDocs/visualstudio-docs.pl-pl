---
description: Określa istnienie powiązanego punktu przerwania, a także określa, czy jest włączony.
title: BP_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 886469727e9a20802f375faac12abbdd0d2b1ff2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089111"
---
# <a name="bp_state"></a>BP_STATE
Określa istnienie powiązanego punktu przerwania, a także określa, czy jest włączony.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="fields"></a>Pola
`BPS_NONE`\
Określa, że punkt przerwania nie istnieje.

`BPS_DELETED`\
Określa, że punkt przerwania został usunięty.

`BPS_DISABLED`\
Określa, że punkt przerwania jest wyłączony.

`BPS_ENABLED`\
Określa, że punkt przerwania jest włączony.

## <a name="remarks"></a>Uwagi
Zwrócone z metody [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
