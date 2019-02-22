---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fac4c65047c51d1213d8be4352c1b8e6efc35c8e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680571"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Określa informacje, które mają zostać pobrane informacje pomyślnego rozwiązania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="members"></a>Elementy członkowskie
BPRESI_BPRESLOCATION zainicjować bądź użyj `bpResLocation` pola (lokalizacji punktu przerwania rozdzielczość) [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury.

BPRESI_PROGRAM zainicjować bądź użyj `pProgram` pole `BP_RESOLUTION_INFO` struktury.

BPRESI_THREAD zainicjować bądź użyj `pThread` pole `BP_RESOLUTION_INFO` struktury.

BPRESI_ALLFIELDS określa wszystkie pola.

## <a name="remarks"></a>Uwagi
Przekazany do [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metodę, aby wskazać, które pola [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktury, które mają zostać zainicjowane.

Te flagi są również używane w celu wskazania, które pola `BP_RESOLUTION_INFO` struktury są używane i ważne, gdy tej struktury jest zwracany.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
