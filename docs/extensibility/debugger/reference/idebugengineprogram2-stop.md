---
title: IDebugEngineProgram2::Stop | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730485"
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
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, gdy ten program jest debugowany w środowisku wieloprogramowym. Po odebraniu zdarzenia zatrzymania z innego programu ta metoda jest wywoływana w tym programie. Implementacja tej metody powinna być asynchroniczne; oznacza to, że nie wszystkie wątki powinny być wymagane do zatrzymania przed tej metody zwraca. Implementacja tej metody może być tak proste, jak wywołanie [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metody w tym programie.

 Implementerzy powinni wysłać [IDebugStopCompleteEVent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) po zatrzymaniu programu.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
