---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba419d0b10174e375cd15313fbc0770bf9d8cc0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311376"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Określa flagi dla informacji debugowania w module.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MODULE_INFO_FIELDS { 
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
public enum enum_MODULE_INFO_FIELDS { 
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
 Inicjowanie/użycie żadnego z pól w strukturze.

 `MIF_NAME`\
 Inicjowanie bądź użyj `m_bstrName` pole [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.

 `MIF_URL`\
 Inicjowanie bądź użyj `m_bstrUrl` pole `MODULE_INFO` struktury.

 `MIF_VERSION`\
 Inicjowanie bądź użyj `m_bstrVersion` pole `MODULE_INFO` struktury.

 `MIF_DEBUGMESSAGE`\
 Inicjowanie bądź użyj `m_bstrDebugMessage` pole `MODULE_INFO` struktury.

 `MIF_LOADADDRESS`\
 Inicjowanie bądź użyj `m_addrLoadAddress` pole `MODULE_INFO` struktury.

 `MIF_PREFFEREDADDRESS`\
 Inicjowanie bądź użyj `m_addrPreferredLoadAddress` pole `MODULE_INFO` struktury.

 `MIF_SIZE`\
 Inicjowanie bądź użyj `m_dwSize` pole `MODULE_INFO` struktury.

 `MIF_LOADORDER`\
 Inicjowanie bądź użyj `m_dwLoadOrder` pole `MODULE_INFO` struktury.

 `MIF_TIMESTAMP`\
 Inicjowanie bądź użyj `m_TimeStamp` pole `MODULE_INFO` struktury.

 `MIF_URLSYMBOLLOCATION`\
 Inicjowanie bądź użyj `m_bstrUrlSymbolLocation` pole `MODULE_INFO` struktury.

 `MIF_FLAGS`\
 Inicjowanie bądź użyj `m_dwModuleFlags` pole `MODULE_INFO` struktury.

 `MIF_ALLFIELDS`\
 Inicjowanie bądź Użyj wszystkich pól w `MODULE_INFO` struktury.

## <a name="remarks"></a>Uwagi
 Te wartości są przekazywane jako argument do [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodę, aby wskazać, które pola [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury, które mają zostać zainicjowane.

 Te wartości są również używane w `MODULE_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)