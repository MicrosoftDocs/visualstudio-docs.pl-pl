---
title: CONTEXT_COMPARE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737601"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Określa kryteria porównywania dwóch kontekstów pamięci.

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

## <a name="fields"></a>Pola
`CONTEXT_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest równy kontekstowi pamięci docelowej.

`CONTEXT_LESS_THAN`\
Znajdź pierwszy kontekst pamięci na liście, który jest mniejszy niż kontekst pamięci docelowej.

`CONTEXT_GREATER_THAN`\
Znajdź pierwszy kontekst pamięci na liście, który jest większy niż kontekst pamięci docelowej.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest mniejszy lub równy kontekstowi pamięci docelowej.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest większy lub równy kontekstowi pamięci docelowej.

`CONTEXT_SAME_SCOPE`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tym samym zakresie co kontekst pamięci docelowej.

`CONTEXT_SAME_FUNCTION`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tej samej funkcji co zakres pamięci docelowej.

`CONTEXT_SAME_MODULE`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tym samym module co kontekst pamięci docelowej.

`CONTEXT_SAME_PROCESS`\
Znajdź pierwszy kontekst pamięci na liście, który jest w tym samym procesie co kontekst pamięci docelowej.

## <a name="remarks"></a>Uwagi
Przekazany jako argument do [Metody Porównania.](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

Wartości te są używane do znajdowania pierwszego kontekstu pamięci na liście, która spełnia określone kryteria porównania. Kontekst pamięci otrzymuje listę kontekstów pamięci, aby porównać się za pośrednictwem `IDebugMemoryContext2::Compare` metody. Pierwszy kontekst pamięci na liście, dla `true` którego jest zwracany operator porównania.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porównanie](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
