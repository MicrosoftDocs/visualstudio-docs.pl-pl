---
title: IDebugProgram2::Step | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f841960eec9274139307f5fcc1bcaea9bb9fb8e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412861"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Wykonuje krok.

> [!NOTE]
> Ta metoda jest przestarzała. Użyj [kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody zamiast tego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

#### <a name="parameters"></a>Parametry
 `pThread`

 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek jest zmieniana.

 `sk`

 [in] Wartość z zakresu od [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) wyliczenie, które określa rodzaj kroku.

 `step`

 [in] Wartość z zakresu od [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) wyliczenie, które określa jednostki kroku (na przykład za pomocą instrukcji lub instrukcji).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku synchronizacji wątków ani komunikacji między wątkami, inne wątki w programie należy uruchomić, gdy przechodzenie krok po kroku określonego wątku.

> [!WARNING]
> Nie wysyłaj zdarzeń zatrzymywania lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)