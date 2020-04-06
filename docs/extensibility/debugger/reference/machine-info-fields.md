---
title: MACHINE_INFO_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714523"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Określa, jakiego rodzaju informacje mają być pobierane dla określonego komputera.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Pola
 `MCIF_NAME`\
 Inicjowanie/używanie `bstrName` pola w strukturze.

 `MCIF_FLAGS`\
 Inicjowanie/używanie `Flags` pola w strukturze.

 `MIF_ALL`\
 Inicjuj/użyj wszystkich pól w strukturze.

## <a name="remarks"></a>Uwagi
 Te wartości są przekazywane do [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metody, aby wskazać, które elementy członkowskie [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury mają zostać zainicjowane.

 Używany również `Fields` w człońoszu struktury, `MACHINE_INFO` aby wskazać, które pola są używane i prawidłowe.

 Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
