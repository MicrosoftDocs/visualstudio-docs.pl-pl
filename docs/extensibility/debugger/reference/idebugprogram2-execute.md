---
title: IDebugProgram2::Wykonaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722982"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Kontynuuje uruchamianie tego programu ze stanu zatrzymanego. Każdy poprzedni stan wykonania (na przykład krok) jest czyszczony, a program rozpoczyna wykonywanie ponownie.

> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy użytkownik rozpoczyna wykonywanie ze stanu zatrzymanego w wątku innego programu, ta metoda jest wywoływana w tym programie. Ta metoda jest również wywoływana, gdy użytkownik wybiera polecenie **Start** z menu **debugowania** w IDE. Implementacja tej metody może być tak proste, jak [wywołanie Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody w bieżącym wątku w programie.

> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani natychmiastowego (synchroniczowego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może zawiesić.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
