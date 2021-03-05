---
description: Określa kryteria do porównywania dwóch kontekstów pamięci.
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70f4621eaad5e494684e6c227959e13566a22eba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170786"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
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

## <a name="fields"></a>Pola
`CONTEXT_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest równy kontekstowi pamięci docelowej.

`CONTEXT_LESS_THAN`\
Znajdź pierwszy kontekst pamięci na liście, który jest mniejszy niż kontekst pamięci docelowej.

`CONTEXT_GREATER_THAN`\
Znajdź pierwszy kontekst pamięci na liście, który jest większy niż kontekst pamięci docelowej.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest mniejszy niż lub równy kontekstowi pamięci docelowej.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Znajdź pierwszy kontekst pamięci na liście, który jest większy niż lub równy kontekstowi pamięci docelowej.

`CONTEXT_SAME_SCOPE`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tym samym zakresie co kontekst pamięci docelowej.

`CONTEXT_SAME_FUNCTION`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tej samej funkcji co zakres pamięci docelowej.

`CONTEXT_SAME_MODULE`\
Znajdź pierwszy kontekst pamięci na liście, który znajduje się w tym samym module co kontekst pamięci docelowej.

`CONTEXT_SAME_PROCESS`\
Znajdź pierwszy kontekst pamięci na liście, który jest w tym samym procesie co kontekst pamięci docelowej.

## <a name="remarks"></a>Uwagi
Przeszedł jako argument do metody [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .

Te wartości są używane do znajdowania pierwszego kontekstu pamięci na liście, która spełnia określone kryteria porównania. Kontekst pamięci otrzymuje listę kontekstów pamięci, aby porównać siebie z nią za pomocą `IDebugMemoryContext2::Compare` metody. Pierwszy kontekst pamięci na liście, dla którego zwracany jest operator porównania `true` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Porównaj](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
