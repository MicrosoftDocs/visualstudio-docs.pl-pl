---
title: MODULE_INFO_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714326"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Określa flagi dla informacji o module debugowania.

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
 Inicjuj/nie używaj żadnego z pól w strukturze.

 `MIF_NAME`\
 Inicjuj/użyj `m_bstrName` pola w strukturze [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Inicjowanie/używanie `m_bstrUrl` pola `MODULE_INFO` w strukturze.

 `MIF_VERSION`\
 Inicjowanie/używanie `m_bstrVersion` pola `MODULE_INFO` w strukturze.

 `MIF_DEBUGMESSAGE`\
 Inicjowanie/używanie `m_bstrDebugMessage` pola `MODULE_INFO` w strukturze.

 `MIF_LOADADDRESS`\
 Inicjowanie/używanie `m_addrLoadAddress` pola `MODULE_INFO` w strukturze.

 `MIF_PREFFEREDADDRESS`\
 Inicjowanie/używanie `m_addrPreferredLoadAddress` pola `MODULE_INFO` w strukturze.

 `MIF_SIZE`\
 Inicjowanie/używanie `m_dwSize` pola `MODULE_INFO` w strukturze.

 `MIF_LOADORDER`\
 Inicjowanie/używanie `m_dwLoadOrder` pola `MODULE_INFO` w strukturze.

 `MIF_TIMESTAMP`\
 Inicjowanie/używanie `m_TimeStamp` pola `MODULE_INFO` w strukturze.

 `MIF_URLSYMBOLLOCATION`\
 Inicjowanie/używanie `m_bstrUrlSymbolLocation` pola `MODULE_INFO` w strukturze.

 `MIF_FLAGS`\
 Inicjowanie/używanie `m_dwModuleFlags` pola `MODULE_INFO` w strukturze.

 `MIF_ALLFIELDS`\
 Inicjuj/użyj wszystkich `MODULE_INFO` pól w strukturze.

## <a name="remarks"></a>Uwagi
 Wartości te są przekazywane jako argument do [Metody GetInfo,](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) aby wskazać, które pola [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury mają zostać zainicjowane.

 Wartości te są również `MODULE_INFO` używane w strukturze, aby wskazać, które pola są używane i prawidłowe.

 Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
