---
title: CONTEXT_COMPARE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21628bda9dc0437672b0b755bb64f1c882b0acbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62878320"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Określa kryteria do porównywania dwóch kontekstów pamięci.

## <a name="syntax"></a>Składnia

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="members"></a>Elementy członkowskie
CONTEXT_EQUAL odszukać pierwszy kontekst pamięci na liście, która jest równa docelowej kontekstu pamięci.

CONTEXT_LESS_THAN odszukać pierwszy kontekst pamięci na liście, która jest mniejsza niż docelowy kontekstu pamięci.

CONTEXT_GREATER_THAN odszukać pierwszy kontekst pamięci na liście, która jest większa niż docelowy kontekstu pamięci.

CONTEXT_LESS_THAN_OR_EQUAL odszukać pierwszy kontekst pamięci na liście, która jest mniejsza niż docelowy kontekstu pamięci.

CONTEXT_GREATER_THAN_OR_EQUAL odszukać pierwszy kontekst pamięci na liście, która jest większa lub równa docelowej kontekstu pamięci.

CONTEXT_SAME_SCOPE odszukać pierwszy kontekst pamięci na liście znajduje się w taki sam zakres jak kontekstu pamięci docelowego.

CONTEXT_SAME_FUNCTION odszukać pierwszy kontekst pamięci na liście znajduje się w taką samą funkcję jak zakres docelowy w pamięci.

CONTEXT_SAME_MODULE odszukać pierwszy kontekst pamięci na liście znajduje się w tym samym modułem kontekstu pamięci docelowego.

CONTEXT_SAME_PROCESS odszukać pierwszy kontekst pamięci na liście znajduje się w tym samym procesie co kontekstu pamięci docelowego.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [porównania](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metody.

Te wartości są używane do odszukać pierwszy kontekst pamięci na liście, który spełnia kryteria porównania określony. Kontekst pamięci podano listę konteksty pamięci do porównania sam względem za pośrednictwem `IDebugMemoryContext2::Compare` metody. Kontekst pamięci pierwszy na liście, dla którego operator porównania jest `true` jest zwracana.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
