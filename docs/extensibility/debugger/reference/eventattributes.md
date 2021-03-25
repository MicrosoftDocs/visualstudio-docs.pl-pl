---
description: Określa atrybuty zdarzenia.
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 922c60c0bb36c58b88c2422580eeda0db1c02d42
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059486"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Określa atrybuty zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Pola
`EVENT_ASYNCHRONOUS`\
Wskazuje, że zdarzenie jest asynchroniczne i nie są konieczne żadne odpowiedzi na zdarzenie.

`EVENT_SYNCHRONOUS`\
Wskazuje, że zdarzenie jest synchroniczne; Odpowiedz przy użyciu metody [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Wskazuje, że jest to zdarzenie zatrzymywania. Musi być połączony z albo `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Wskazuje asynchroniczne zdarzenie zatrzymywania. Obecnie nie ma takiego zdarzenia. Ta flaga jest tylko symbolem zastępczym.

`EVENT_SYNC_STOP`\
Wskazuje synchroniczne zdarzenie zatrzymania (kombinację `EVENT_SYNCHRONOUS` i `EVENT_STOPPING` ). Ta wartość jest używana przez aparat debugowania (DE), gdy wysyła zdarzenie zatrzymania. Odpowiedź jest podejmowana przez wywołanie do [wykonania](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [krok](../../../extensibility/debugger/reference/idebugprogram2-step.md)lub [kontynuacja](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Wskazuje zdarzenie, które jest wysyłane natychmiast i synchronicznie do IDE. Ta flaga jest połączona z innymi flagami, takimi jak `EVENT_ASYNCHRONOUS` , `EVENT_SYNCHRONOUS` , lub `EVENT_SYNC_STOP` wskazują typ zdarzenia i fakt, że mechanizm odpowiedzi (jeśli istnieje) jest znany.

`EVENT_EXPRESSION_EVALUATION`\
Zdarzenie jest wynikiem obliczenia wyrażenia.

## <a name="remarks"></a>Uwagi
Te wartości są przesyłane w `dwAttrib` parametrze metody [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
