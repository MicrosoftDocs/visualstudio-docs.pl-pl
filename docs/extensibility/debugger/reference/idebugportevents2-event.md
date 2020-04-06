---
title: IDebugPortEvents2::Wydarzenie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725248"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Ta metoda wysyła zdarzenia, które oznaczają tworzenie i niszczenie procesów i programów w porcie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parametry
`pMachine`\
[w] [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) obiekt, który reprezentuje serwer debugowania (istnieje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]jeden dla każdego wystąpienia), w którym wystąpiło zdarzenie.

`pPort`\
[w] Obiekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) reprezentujący port, w którym wystąpiło zdarzenie.

`pProcess`\
[w] [Obiekt IDebugProcess2 reprezentujący](../../../extensibility/debugger/reference/idebugprocess2.md) proces, w którym wystąpiło zdarzenie.

`pProgram`\
[w] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym wystąpiło zdarzenie.

`pEvent`\
[w] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) obiekt, który identyfikuje zdarzenie. Możliwe zdarzenia są następujące:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
[w] Identyfikator GUID zdarzenia. Ponieważ zdarzenie jest rzutowana na [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) przed wywołaniem tej metody, ten identyfikator ułatwia określenie, które zdarzenie jest wysyłane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
