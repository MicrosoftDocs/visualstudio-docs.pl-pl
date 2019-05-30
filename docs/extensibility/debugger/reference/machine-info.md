---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e50fe4901ebcbf008bf191226502ccac8ec4cf5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339227"
---
# <a name="machineinfo"></a>MACHINE_INFO
W tym artykule opisano określonego komputera.

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
 Kombinacja flag z [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) wyliczenie określające, które pola struktury są inicjowane.

 `bstrName`\
 Nazwa komputera. Równoważne z wywoływaniem [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Kombinacja flag z [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) wyliczenie opisujące atrybuty maszyny.

## <a name="remarks"></a>Uwagi
 Ta struktura jest zwracany przez wywołanie [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metody.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)