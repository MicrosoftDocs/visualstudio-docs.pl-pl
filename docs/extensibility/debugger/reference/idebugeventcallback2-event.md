---
title: IDebugEventCallback2::Zdarzenie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729893"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Wysyła powiadomienie o zdarzeniach debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Parametry
`pEngine`\
[w] [Obiekt IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) reprezentujący aparat debugowania (DE), który wysyła to zdarzenie. De jest wymagane do wypełnienia tego parametru.

`pProcess`\
[w] [Obiekt IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) który reprezentuje proces, w którym występuje zdarzenie. Ten parametr jest wypełniany przez menedżera debugowania sesji (SDM). De zawsze przekazuje wartość null dla tego parametru.

`pProgram`\
[w] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym występuje to zdarzenie. W przypadku większości zdarzeń ten parametr nie jest wartością null.

`pThread`\
[w] [Obiekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) który reprezentuje wątek, w którym występuje to zdarzenie. W przypadku zatrzymywania zdarzeń ten parametr nie może być wartością null, ponieważ ramka stosu jest uzyskiwana z tego parametru.

`pEvent`\
[w] [Obiekt IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) reprezentujący zdarzenie debugowania.

`riidEvent`\
[w] Identyfikator GUID identyfikujący interfejs zdarzenia, który ma być uzyskiany z parametru. `pEvent`

`dwAttrib`\
[w] Kombinacja flag z wyliczenia [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Podczas wywoływania tej `dwAttrib` metody, parametr musi odpowiadać wartości zwróconej z [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) metody, jak wywołano na obiekt zdarzenia przekazywane w parametrze. `pEvent`

 Wszystkie zdarzenia debugowania są księgowane asynchronicznie, niezależnie od tego, czy samo zdarzenie jest asynchroniczne, czy nie. Gdy DE wywołuje tę metodę, zwracana wartość nie wskazuje, czy zdarzenie zostało przetworzone, tylko czy zdarzenie zostało odebrane. W rzeczywistości w większości przypadków zdarzenie nie zostało przetworzone, gdy ta metoda zwraca.

## <a name="see-also"></a>Zobacz też
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
