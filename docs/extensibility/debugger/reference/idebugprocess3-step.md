---
title: IDebugProcess3::Krok | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723550"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Powoduje, że proces krok jeden instrukcji lub instrukcji.

> [!NOTE]
> Ta metoda powinna być używana zamiast [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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

## <a name="parameters"></a>Parametry
`pThread`\
[w] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątek jest stopniowane.

`sk`\
[w] Jedna z wartości [STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[w] Jedna z wartości [STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W przypadku, gdy istnieje synchronizacja wątku lub komunikacji między wątkami, inne wątki w procesie należy uruchomić, gdy określony wątek jest stepping.

 **Ostrzeżenie** Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
