---
title: EVENTATTRIBUTES | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737060"
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
Wskazuje, że zdarzenie jest asynchroniczne i nie jest wymagana żadna odpowiedź na zdarzenie.

`EVENT_SYNCHRONOUS`\
Wskazuje, że zdarzenie jest synchroniczne; odpowiedź za pomocą [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Wskazuje, że jest to zdarzenie zatrzymania. Muszą być połączone `EVENT_ASYNCHRONOUS` z `EVENT_SYNCHRONOUS`jednym lub .

`EVENT_ASYNC_STOP`\
Wskazuje zdarzenie zatrzymania asynchroniiowego. Obecnie nie ma takiego zdarzenia. Ta flaga jest tylko symbolem zastępczym.

`EVENT_SYNC_STOP`\
Wskazuje zdarzenie zatrzymania synchronicznego `EVENT_SYNCHRONOUS` (kombinacja `EVENT_STOPPING`i ). Ta wartość jest używana przez aparat debugowania (DE) podczas wysyła zdarzenie zatrzymania. Odpowiedź jest dokonywana za pomocą wywołania [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)lub [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Wskazuje zdarzenie, które jest wysyłane natychmiast i synchronicznie do IDE. Ta flaga jest łączona `EVENT_SYNCHRONOUS`z `EVENT_SYNC_STOP` innymi flagami, takimi jak `EVENT_ASYNCHRONOUS`, lub w celu wskazania typu zdarzenia i faktu, że mechanizm odpowiedzi (jeśli istnieje) jest znany.

`EVENT_EXPRESSION_EVALUATION`\
Zdarzenie jest wynikiem oceny wyrażenia.

## <a name="remarks"></a>Uwagi
Te wartości są `dwAttrib` przekazywane w parametrze [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
