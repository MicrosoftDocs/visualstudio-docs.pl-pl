---
title: IDebugProgram2::Krok | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722757"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Wykonuje krok.

> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj [metody Krok.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

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

## <a name="parameters"></a>Parametry
`pThread`\
[w] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek jest stopniowane.

`sk`\
[w] Wartość z wyliczenia [STEPKIND,](../../../extensibility/debugger/reference/stepkind.md) która określa rodzaj kroku.

`step`\
[w] Wartość z wyliczenia [STEPUNIT,](../../../extensibility/debugger/reference/stepunit.md) która określa jednostkę kroku (na przykład według instrukcji lub instrukcji).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku, gdy istnieje synchronizacja wątku lub komunikacji między wątkami, inne wątki w programie powinny działać, gdy określony wątek jest stepping.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
