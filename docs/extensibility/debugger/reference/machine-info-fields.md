---
description: Określa, jakiego rodzaju informacje mają być pobierane dla konkretnej maszyny.
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb07f679027c37ebc74343ba17051a7e7980c1c7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222565"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Określa, jakiego rodzaju informacje mają być pobierane dla konkretnej maszyny.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Pola
 `MCIF_NAME`\
 Zainicjuj/Użyj `bstrName` pola w strukturze.

 `MCIF_FLAGS`\
 Zainicjuj/Użyj `Flags` pola w strukturze.

 `MIF_ALL`\
 Zainicjuj/Użyj wszystkich pól w strukturze.

## <a name="remarks"></a>Uwagi
 Te wartości są przesyłane do metody [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) , aby wskazać, które składowe struktury [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) mają być inicjowane.

 Używany również w `Fields` składowej struktury, `MACHINE_INFO` Aby wskazać, które pola są używane i są prawidłowe.

 Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
