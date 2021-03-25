---
description: Zapewnia opcjonalne flagi, które mogą być używane do określania dodatkowych informacji podczas ustawiania punktu przerwania.
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e35e0b219bb77ce722f2e06a260de7ecc837dfb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085328"
---
# <a name="bp_flags"></a>BP_FLAGS
Zapewnia opcjonalne flagi, które mogą być używane do określania dodatkowych informacji podczas ustawiania punktu przerwania.

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
Określa, że aparat debugowania (DE) powinien mapować punkt przerwania przy użyciu pozycji dokumentu. Ma to zastosowanie tylko do punktów przerwania ustawionych w plikach źródłowych zorientowanych na skrypty, takich jak strony Active Server (ASP).

`BP_FLAG_DONT_STOP`\
Określa, że punkt przerwania powinien być przetwarzany przez aparat debugowania, ale aparat debugowania ostatecznie nie powinien go zatrzymać (to oznacza, że obiekt zdarzenia [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) nie powinien być wysyłany). Ta flaga jest przeznaczona do użycia głównie z punkty śledzenia.

## <a name="remarks"></a>Uwagi
Używane dla `dwFlags` elementu członkowskiego struktur [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
