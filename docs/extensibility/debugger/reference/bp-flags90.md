---
title: BP_FLAGS90 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738047"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Wylicza prawidłowe wartości dla flag opcjonalnych. Opcjonalne flagi mogą służyć do określania dodatkowych informacji podczas ustawiania punktu przerwania. To wyliczenie rozszerza wyliczenie [BP_FLAGS.](../../../extensibility/debugger/reference/bp-flags.md)

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
Określa, że aparat debugowania (DE) powinien mapować punkt przerwania przy użyciu położenia dokumentu. Dotyczy to tylko punktów przerwania ustawionych w plikach źródłowych zorientowanych na skrypty, takich jak Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Określa, że punkt przerwania powinny być przetwarzane przez aparat debugowania, ale aparat debugowania ostatecznie nie powinien zatrzymać się tam; oznacza to, że obiekt zdarzenia [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) nie powinien być wysyłany. Ta flaga jest przeznaczona do użycia głównie z punktami śledzenia.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Używany przez natywnego aparatu debugowania, aby ustalić, czy stan stepping powinny być wyczyszczone. Różni się od BP90_FLAG_DONT_STOP, ponieważ BP90_FLAG_DONT_STOP nie jest ustawiona, jeśli punkt śledzenia wykonuje makro.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
