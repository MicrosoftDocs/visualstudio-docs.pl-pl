---
title: BP_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738063"
---
# <a name="bp_flags"></a>BP_FLAGS
Zawiera opcjonalne flagi, które mogą służyć do określania dodatkowych informacji podczas ustawiania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Pola
`BP_FLAG_NONE`\
Określa brak flagi punktu przerwania.

`BP_FLAG_MAP_DOCPOSITION`\
Określa, że aparat debugowania (DE) powinien mapować punkt przerwania przy użyciu położenia dokumentu. Dotyczy to tylko punktów przerwania ustawionych w plikach źródłowych zorientowanych na skrypty, takich jak Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Określa, że punkt przerwania powinny być przetwarzane przez aparat debugowania, ale aparat debugowania ostatecznie nie powinien zatrzymać tam (oznacza to, że [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) obiekt zdarzenia nie powinny być wysyłane). Ta flaga jest przeznaczona do użycia głównie z punktami śledzenia.

## <a name="remarks"></a>Uwagi
Używany dla `dwFlags` członków [struktur BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
