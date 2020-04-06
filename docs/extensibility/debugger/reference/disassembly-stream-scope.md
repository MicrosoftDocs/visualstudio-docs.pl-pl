---
title: DISASSEMBLY_STREAM_SCOPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737274"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Określa zakres strumienia demontażu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Pola
`DSS_HUGE`\
Określa, że demontaż kontekstu kodu wygenerowałby więcej danych wyjściowych niż klient zazwyczaj chce pobrać w jednym wywołaniu.

`DSS_FUNCTION`\
Określa, że funkcja zawarta w kontekście kodu powinna zostać zdemontowana. Określa, że strumień demontażu reprezentuje funkcję, po zwróceniu przez [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.

`DSS_MODULE`\
Po zwróceniu `IDebugDisassemblyStream2::GetScope` przez metodę, określa, że strumień demontażu reprezentuje moduł.

`DSS_ALL`\
Określa demontaż dla całej przestrzeni adresowej.

## <a name="remarks"></a>Uwagi
Przekazany jako argument do [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metody i zwrócony przez [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
