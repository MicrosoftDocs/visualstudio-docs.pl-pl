---
title: BP_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f18d21485084351e639405dad946dff8be4c767a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315979"
---
# <a name="bptype"></a>BP_TYPE
Określa, czy punkt przerwania znajduje się w lokalizacji kodu, jest lokalizacja danych lub inny typ punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="members"></a>Elementy członkowskie
BPT_NONE  
Określa żadnego typu punktu przerwania.

BPT_CODE  
Określa punkt przerwania w kodzie.

BPT_DATA  
Określa punkt przerwania danych.

BPT_SPECIAL  
Określa punkt przerwania, który nie jest ani kodu ani typu danych. Ten typ jest przestarzały i nie powinna być używana.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) i [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)  
[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
