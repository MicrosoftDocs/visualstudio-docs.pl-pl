---
title: IDebugProcess3::Execute | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2870a50f4ab8bb0358e2e38529e996b143b7ae
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202381"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Kontynuuje, uruchomienie tego procesu w stanie zatrzymania. Jest wyczyszczone wszelkie poprzedni stan wykonania (np. krok) i uruchamiania procesu wykonywania ponownie.

> [!NOTE]
> Ta metoda powinna być używana zamiast [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Składnia

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący na wykonanie wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy użytkownik rozpoczyna wykonywanie w stanie zatrzymania wątku jakiś inny proces, ta metoda jest wywoływana na temat tego procesu. Ta metoda również jest wywoływana, gdy użytkownik wybierze **Start** polecenia **debugowania** menu w środowisku IDE. Implementacja tej metody może być proste co wywołanie metody [Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody na bieżący wątek w procesie.

> [!WARNING]
> Nie wysyłaj zdarzeń zatrzymywania lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.

## <a name="see-also"></a>Zobacz także
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)