---
title: CONTEXT_INFO_FIELDS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13501c86eabd249e0e47137099862cd6db654415
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62878244"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Określa, jakie informacje należy pobrać o kontekście pamięci.

## <a name="syntax"></a>Składnia

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="members"></a>Elementy członkowskie
CIF_MODULEURL zainicjować bądź użyj `bstrModuleUrl` pole [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury.

CIF_FUNCTION zainicjować bądź użyj `bstrFunction` pole `CONTEXT_INFO` struktury.

CIF_FUNCTIONOFFSET zainicjować bądź użyj `posFunctionOffset` pole `CONTEXT_INFO` struktury.

CIF_ADDRESS zainicjować bądź użyj `bstrAddress` pole `CONTEXT_INFO` struktury.

CIF_ADDRESSOFFSET zainicjować bądź użyj `bstrAddressOffset` pole `CONTEXT_INFO` struktury.

CIF_ALLFIELDS zainicjować bądź Użyj wszystkich pól `CONTEXT_INFO` struktury.

## <a name="remarks"></a>Uwagi
Te wartości są przekazywane parametr [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metodę, aby wskazać, które pola [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury, które mają zostać zainicjowane.

Te flagi są również używane w celu wskazania, które pola `CONTEXT_INFO` struktury są używane i ważne, gdy struktura jest zwracany.

Te wartości mogą być łączone z bitowe OR.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
