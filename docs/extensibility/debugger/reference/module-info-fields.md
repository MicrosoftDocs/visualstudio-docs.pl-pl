---
description: Określa flagi dla informacji modułu debugowania.
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c530caa530a230dc0fc0344a31e0ab7793f336f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079777"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Określa flagi dla informacji modułu debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Pola
 `MIF_NONE`\
 W strukturze nie należy inicjować ani używać żadnych pól.

 `MIF_NAME`\
 Zainicjuj/Użyj `m_bstrName` pola w strukturze [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 `MIF_URL`\
 Zainicjuj/Użyj `m_bstrUrl` pola w `MODULE_INFO` strukturze.

 `MIF_VERSION`\
 Zainicjuj/Użyj `m_bstrVersion` pola w `MODULE_INFO` strukturze.

 `MIF_DEBUGMESSAGE`\
 Zainicjuj/Użyj `m_bstrDebugMessage` pola w `MODULE_INFO` strukturze.

 `MIF_LOADADDRESS`\
 Zainicjuj/Użyj `m_addrLoadAddress` pola w `MODULE_INFO` strukturze.

 `MIF_PREFFEREDADDRESS`\
 Zainicjuj/Użyj `m_addrPreferredLoadAddress` pola w `MODULE_INFO` strukturze.

 `MIF_SIZE`\
 Zainicjuj/Użyj `m_dwSize` pola w `MODULE_INFO` strukturze.

 `MIF_LOADORDER`\
 Zainicjuj/Użyj `m_dwLoadOrder` pola w `MODULE_INFO` strukturze.

 `MIF_TIMESTAMP`\
 Zainicjuj/Użyj `m_TimeStamp` pola w `MODULE_INFO` strukturze.

 `MIF_URLSYMBOLLOCATION`\
 Zainicjuj/Użyj `m_bstrUrlSymbolLocation` pola w `MODULE_INFO` strukturze.

 `MIF_FLAGS`\
 Zainicjuj/Użyj `m_dwModuleFlags` pola w `MODULE_INFO` strukturze.

 `MIF_ALLFIELDS`\
 Zainicjuj/Użyj wszystkich pól w `MODULE_INFO` strukturze.

## <a name="remarks"></a>Uwagi
 Te wartości są przekazywane jako argument do metody [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) , aby wskazać, które pola struktury [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) mają być inicjowane.

 Te wartości są również używane w `MODULE_INFO` strukturze, aby wskazać, które pola są używane i są prawidłowe.

 Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
