---
title: IDebugProcess3::Step | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 686e8dfbd94fc3fddbc5e696fc6e943184357c02
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711530"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Powoduje, że proces krok jednej instrukcji lub instrukcji.

> [!NOTE]
>  Ta metoda powinna być używana zamiast [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Składnia

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

#### <a name="parameters"></a>Parametry
 `pThread`

 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątku jest zmieniana.

 `sk`

 [in] Jedną z [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) wartości.

 `step`

 [in] Jedną z [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) wartości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku synchronizacji wątków ani komunikacji między wątkami, inne wątki w procesie należy uruchomić, gdy przechodzenie krok po kroku określonego wątku.

 **Ostrzeżenie** nie będą wysyłane zdarzenia zatrzymywania lub natychmiastowego zdarzeń (synchroniczne) [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)