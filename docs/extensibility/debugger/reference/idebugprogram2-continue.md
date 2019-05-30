---
title: IDebugProgram2::Continue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c7ea051c9753f6149802c9e92534dd9ee1d8735
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319388"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Nadal uruchomiony ten program w stanie zatrzymania. Dowolnego poprzedniego stanu wykonywania (np. krok) są zachowywane, i ponownym wykonaniem uruchamiania programu.

> [!NOTE]
> Ta metoda jest przestarzała. Użyj [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody zamiast tego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread` [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana dla tego programu, niezależnie od tego, ile programy są debugowane lub program, który wygenerował zdarzenie zatrzymywania. Wdrożenie musi zachować poprzedni stan wykonania (np. krok) i kontynuować wykonywanie, tak, jakby nigdy nie przestała się przed wykonaniem jego wcześniejszego wykonania. Oznacza to jeśli wątek w tym programie wykonywanych operacji przejścia, zostało zatrzymane, ponieważ inny program, zatrzymana, a następnie wywołania tej metody program, należy wykonać operację przejścia.

> [!WARNING]
> Nie wysyłaj zdarzeń zatrzymywania lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.

## <a name="see-also"></a>Zobacz także
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)