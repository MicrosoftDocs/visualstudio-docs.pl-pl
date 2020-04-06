---
title: IDebugProgram2::Kontynuuj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723077"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Kontynuuje uruchamianie tego programu ze stanu zatrzymanego. Każdy poprzedni stan wykonania (na przykład krok) jest zachowywany, a program rozpoczyna wykonywanie ponownie.

> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody.

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
`pThread`[w] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w tym programie, niezależnie od tego, ile programów są debugowane lub który program wygenerował zdarzenie zatrzymania. Implementacja musi zachować poprzedni stan wykonywania (na przykład krok) i kontynuować wykonywanie tak, jakby nigdy nie zatrzymał się przed zakończeniem jego wcześniejszego wykonania. Oznacza to, że jeśli wątek w tym programie robi operację step-over i został zatrzymany, ponieważ jakiś inny program został zatrzymany, a następnie ta metoda została wywołana, program musi zakończyć oryginalną operację step-over.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
