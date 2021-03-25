---
description: Ta metoda wysyła zdarzenia, które oznaczają tworzenie i niszczenie procesów i programów na porcie.
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 314c31c426300c31f90813e2b73b150678578437
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058342"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Ta metoda wysyła zdarzenia, które oznaczają tworzenie i niszczenie procesów i programów na porcie.

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
podczas Obiekt [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , który reprezentuje serwer debugowania (istnieje jeden dla każdego wystąpienia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ), w którym wystąpiło zdarzenie.

`pPort`\
podczas Obiekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , który reprezentuje port, w którym wystąpiło zdarzenie.

`pProcess`\
podczas Obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje proces, w którym wystąpiło zdarzenie.

`pProgram`\
podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program, w którym wystąpiło zdarzenie.

`pEvent`\
podczas Obiekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , który identyfikuje zdarzenie. Możliwe są następujące zdarzenia:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
podczas Identyfikator GUID zdarzenia. Ponieważ zdarzenie jest rzutowane do [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) przed wywołaniem tej metody, ten identyfikator ułatwia ustalenie, które zdarzenie jest wysyłane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
