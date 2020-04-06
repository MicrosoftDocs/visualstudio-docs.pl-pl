---
title: IDebugProcess3::Kontynuuj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723779"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Kontynuuje uruchamianie tego procesu ze stanu zatrzymanego. Każdy poprzedni stan wykonywania (na przykład krok) jest zachowywany, a proces rozpoczyna wykonywanie ponownie.

> [!NOTE]
> Ta metoda powinna być używana zamiast [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
[w] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt reprezentujący wątek, który ma być kontynuowany.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana w tym procesie, niezależnie od tego, ile procesów są debugowane lub który proces wygenerował zdarzenie zatrzymania. Implementacja musi zachować poprzedni stan wykonywania (na przykład krok) i kontynuować wykonywanie tak, jakby nigdy nie zatrzymał się przed zakończeniem jego wcześniejszego wykonania. Oznacza to, że jeśli wątek w tym procesie robi operację step-over `Continue` i został zatrzymany, ponieważ niektóre inne procesy zatrzymane, a następnie został wywołany, określony wątek musi zakończyć oryginalną operację step-over.

 **Ostrzeżenie** Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
