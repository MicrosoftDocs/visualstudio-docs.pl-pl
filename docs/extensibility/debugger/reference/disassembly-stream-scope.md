---
title: DISASSEMBLY_STREAM_SCOPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 724e32f83cfec31c2bacdab661407983af87efe6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318244"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Określa zakres strumienia dezasemblacji.

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
Określa, że deasemblowanie kontekst kodu będzie generować więcej danych wyjściowych niż klient będzie zazwyczaj ma zostać pobrane w jednym wywołaniu.

`DSS_FUNCTION`\
Określa funkcję zawarte w kontekście kod powinien zostać zdezasemblowany. Określa, że strumienia dezasemblacji reprezentuje funkcji, gdy zwracany przez [getscope —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.

`DSS_MODULE`\
Po zwróceniu przez `IDebugDisassemblyStream2::GetScope` metody Określa, że strumień dezasemblacji reprezentuje moduł.

`DSS_ALL`\
Określa dezasemblację dla całą przestrzenią adresową.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metody i zwrócone przez [getscope —](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
