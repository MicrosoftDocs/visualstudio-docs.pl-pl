---
description: Wylicza prawidłowe wartości flag opcjonalnych.
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2203a6fa2a5f84f422eafd28706c54065f752e2e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165621"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Wylicza prawidłowe wartości flag opcjonalnych. Opcjonalne flagi mogą służyć do określania dodatkowych informacji podczas ustawiania punktu przerwania. To Wyliczenie rozszerza [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Wyliczenie.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Pola
`BP90_FLAG_NONE`\
Określa brak flagi punktu przerwania.

`BP90_FLAG_MAP_DOCPOSITION`\
Określa, że aparat debugowania (DE) powinien mapować punkt przerwania przy użyciu pozycji dokumentu. Ma to zastosowanie tylko do punktów przerwania ustawionych w plikach źródłowych zorientowanych na skrypty, takich jak strony Active Server (ASP).

`BP90_FLAG_DONT_STOP`\
Określa, że punkt przerwania powinien być przetwarzany przez aparat debugowania, ale aparat debugowania ostatecznie nie powinien go zatrzymać; oznacza to, że obiekt zdarzenia [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) nie powinien być wysyłany. Ta flaga jest przeznaczona do użycia głównie z punktami śledzenia.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Używane przez natywny aparat debugowania do określenia, czy stan krokowe powinien zostać wyczyszczony. Różni się od BP90_FLAG_DONT_STOP, ponieważ BP90_FLAG_DONT_STOP nie jest ustawiona, jeśli punkt śledzenia wykonuje makro.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
