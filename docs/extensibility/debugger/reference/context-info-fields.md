---
title: CONTEXT_INFO_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737595"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Określa, jakie informacje mają być pobierane o kontekście pamięci.

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

## <a name="fields"></a>Pola
`CIF_MODULEURL`\
Inicjuj/użyj `bstrModuleUrl` pola [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury.

`CIF_FUNCTION`\
Inicjuj/użyj `bstrFunction` `CONTEXT_INFO` pola konstrukcji.

`CIF_FUNCTIONOFFSET`\
Inicjuj/użyj `posFunctionOffset` `CONTEXT_INFO` pola konstrukcji.

`CIF_ADDRESS`\
Inicjuj/użyj `bstrAddress` `CONTEXT_INFO` pola konstrukcji.

`CIF_ADDRESSOFFSET`\
Inicjuj/użyj `bstrAddressOffset` `CONTEXT_INFO` pola konstrukcji.

`CIF_ALLFIELDS`\
Inicjuj/użyj `CONTEXT_INFO` wszystkich pól struktury.

## <a name="remarks"></a>Uwagi
Wartości te są przekazywane parametr do [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metody, aby wskazać, które pola [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struktury mają być inicjowane.

Flagi te są również używane do `CONTEXT_INFO` wskazania, które pola struktury są używane i prawidłowe, gdy struktura jest zwracana.

Wartości te mogą być łączone z bitowym OR.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
