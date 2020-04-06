---
title: IDebugProcess3::Wykonaj | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723678"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Kontynuuje uruchamianie tego procesu ze stanu zatrzymanego. Każdy poprzedni stan wykonywania (na przykład krok) jest czyszczony i proces rozpoczyna wykonywanie ponownie.

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
[w] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątek do wykonania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy użytkownik rozpoczyna wykonywanie ze stanu zatrzymanego w wątku innego procesu, ta metoda jest wywoływana w tym procesie. Ta metoda jest również wywoływana, gdy użytkownik wybiera polecenie **Start** z menu **debugowania** w IDE. Implementacja tej metody może być tak proste, jak [wywołanie Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody w bieżącym wątku w procesie.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
