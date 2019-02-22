---
title: IDebugProgram2::Continue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ca9d7841671c44702b883cc8efcc23e803ea8fe
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693688"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Nadal uruchomiony ten program w stanie zatrzymania. Dowolnego poprzedniego stanu wykonywania (np. krok) są zachowywane, i ponownym wykonaniem uruchamiania programu.

> [!NOTE]
>  Ta metoda jest przestarzała. Użyj [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody zamiast tego.

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

#### <a name="parameters"></a>Parametry
 `pThread`

 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana dla tego programu, niezależnie od tego, ile programy są debugowane lub program, który wygenerował zdarzenie zatrzymywania. Wdrożenie musi zachować poprzedni stan wykonania (np. krok) i kontynuować wykonywanie, tak, jakby nigdy nie przestała się przed wykonaniem jego wcześniejszego wykonania. Oznacza to jeśli wątek w tym programie wykonywanych operacji przejścia, zostało zatrzymane, ponieważ inny program, zatrzymana, a następnie wywołania tej metody program, należy wykonać operację przejścia.

> [!WARNING]
>  Nie wysyłaj zdarzeń zatrzymywania lub natychmiastowego zdarzenia (synchroniczne) w celu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może się zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)