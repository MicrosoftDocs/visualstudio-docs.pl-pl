---
description: 'IDebugProgram2:: Continue kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są zachowywane, a program ponownie uruchamia wykonywanie.'
title: 'IDebugProgram2:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60f3cb4764a53d359e971020df8261d064c62e81
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076124"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Kontynuuje działanie tego programu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są zachowywane, a program ponownie uruchamia wykonywanie.

> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj metody [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .

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
`pThread` podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w tym programie niezależnie od tego, ile programów jest debugowanych lub który program wygenerował zdarzenie zatrzymania. Implementacja musi zachować poprzedni stan wykonania (na przykład krok) i kontynuować wykonywanie, tak jakby nigdy nie zostało zatrzymane przed ukończeniem jego wcześniejszego wykonania. Oznacza to, że jeśli wątek w tym programie wykonywał operację krok po kroku i został zatrzymany, ponieważ inny program został zatrzymany, a następnie ta metoda została wywołana, program musi wykonać pierwotną operację krok po kroku.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
