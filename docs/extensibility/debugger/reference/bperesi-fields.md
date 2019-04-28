---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 488c2b1a96d01e0e7dfa9868d2f7e5111adc4e2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924899"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Określa informacje, które mają zostać pobrane dotyczących rozwiązania nie powiodło się punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>Elementy członkowskie
PERESI_BPRESLOCATION zainicjować bądź użyj `bpResLocation` pola (lokalizacji punktu przerwania rozdzielczość) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury.

BPERESI_PROGRAM zainicjować bądź użyj `pProgram` pole `BP_ERROR_RESOLUTION_INFO` struktury.

BPERESI_THREAD zainicjować bądź użyj `pThread` pole `BP_ERROR_RESOLUTION_INFO` struktury.

BPERESI_MESSAGE zainicjować bądź użyj `bstrMessage` pole `BP_ERROR_RESOLUTION_INFO` struktury.

BPERESI_TYPE zainicjować bądź użyj `dwType` pola (typ punktu przerwania) `BP_ERROR_RESOLUTION_INFO` struktury.

BPERESI_ALLFIELDS zainicjować bądź Użyj wszystkich pól `BP_ERROR_RESOLUTION_INFO` struktury.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodę, aby wskazać, które pola [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury, które mają zostać zainicjowane.

Te wartości są również używane do wskazania, które pola w `BP_ERROR_RESOLUTION_INFO` struktury są używane i ważne, gdy tej struktury jest zwracany.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
