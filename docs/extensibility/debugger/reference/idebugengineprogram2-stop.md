---
title: IDebugEngineProgram2::Stop | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3cb9627ba11bdec5729383bd6a31e4a338f3ef9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920328"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Zatrzymuje wszystkie wątki uruchomione w tym programie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, gdy ten program jest debugowany w środowisku wielu programów. Po odebraniu zdarzenia zatrzymywanie inny program, ta metoda jest wywoływana dla tego programu. Implementacja tej metody powinna być asynchroniczne; oznacza to, że nie wszystkie wątki powinny będzie musiał być zatrzymana zanim ta metoda zwraca wartość. Implementacja tej metody może być proste co wywołanie metody [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metody dla tego programu.

 Nie zdarzeń debugowania jest wysyłany w odpowiedzi na tę metodę.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)