---
description: Opisuje konkretną maszynę.
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 796b6c95016708d3c179a8428b7f32aff9ccfe88
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224086"
---
# <a name="machine_info"></a>MACHINE_INFO
Opisuje konkretną maszynę.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>Elementy członkowskie
 `Fields`\
 Kombinacja flag z wyliczenia [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) , która określa, które pola struktury są inicjowane.

 `bstrName`\
 Nazwa maszyny. Równoważne z wywołaniem metody [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Kombinacja flag z wyliczenia [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) opisującego atrybuty maszyny.

## <a name="remarks"></a>Uwagi
 Ta struktura jest zwracana przez wywołanie metody [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
