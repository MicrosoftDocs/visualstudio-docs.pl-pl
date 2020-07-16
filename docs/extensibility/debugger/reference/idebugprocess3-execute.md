---
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: baa607e62732cdf0e04413e07966658bb6a0b8f4
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386514"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Kontynuuje wykonywanie tego procesu ze stanu zatrzymanego. Wszystkie poprzednie Stany wykonania (takie jak krok) są wyczyszczone, a proces zostanie uruchomiony ponownie.

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
podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) reprezentujący wątek do wykonania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy użytkownik uruchamia wykonywanie z stanu zatrzymanego w innym wątku procesu, ta metoda jest wywoływana w tym procesie. Ta metoda jest również wywoływana, gdy użytkownik wybierze polecenie **Uruchom** z menu **DEBUGUJ** w środowisku IDE. Implementacja tej metody może być prosta jako wywołanie metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) w bieżącym wątku w procesie.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Wznawianie](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
