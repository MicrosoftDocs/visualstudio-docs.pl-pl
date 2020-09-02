---
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
podczas Obiekt [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , który reprezentuje aparat debugowania, który wysyła to zdarzenie. Element DE jest wymagany do wypełnienia tego parametru.

`pProcess`\
podczas Obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje proces, w którym występuje zdarzenie. Ten parametr jest wypełniany przez Menedżera debugowania sesji (SDM). Element DE zawsze przekazuje wartość null dla tego parametru.

`pProgram`\
podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program, w którym występuje to zdarzenie. W przypadku większości zdarzeń ten parametr nie jest wartością null.

`pThread`\
podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek, w którym występuje to zdarzenie. W przypadku zdarzeń zatrzymywania ten parametr nie może być wartością null, ponieważ Ramka stosu jest uzyskiwana z tego parametru.

`pEvent`\
podczas Obiekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , który reprezentuje zdarzenie debugowania.

`riidEvent`\
podczas Identyfikator GUID, który identyfikuje interfejs zdarzenia, który ma zostać uzyskany z `pEvent` parametru.

`dwAttrib`\
podczas Kombinacja flag z wyliczenia [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Podczas wywoływania tej metody `dwAttrib` parametr musi być zgodny z wartością zwróconą przez metodę [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) wywoływaną w obiekcie zdarzenia przekazaną w `pEvent` parametrze.

 Wszystkie zdarzenia debugowania są ogłaszane asynchronicznie, bez względu na to, czy samo zdarzenie jest asynchroniczne, czy nie. W przypadku wywołania tej metody zwracana wartość nie wskazuje, czy zdarzenie zostało przetworzone, czy zdarzenie zostało odebrane. W rzeczywistości w większości przypadków zdarzenie nie zostało przetworzone, gdy ta metoda zwraca wartość.

## <a name="see-also"></a>Zobacz też
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
