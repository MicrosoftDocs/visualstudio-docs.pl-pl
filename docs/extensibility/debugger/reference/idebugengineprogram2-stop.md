---
description: Przerywa wszystkie wątki działające w tym programie.
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3867e4e3f119e69734495d5c545d53348755af3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153459"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Przerywa wszystkie wątki działające w tym programie.

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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, gdy ten program jest debugowany w środowisku z obsługą kilku programów. Po odebraniu zdarzenia zatrzymania z innego programu Metoda ta jest wywoływana w tym programie. Implementacja tej metody powinna być asynchroniczna; oznacza to, że nie wszystkie wątki powinny być wymagane do zatrzymania przed zwróceniem tej metody. Implementacja tej metody może być prosta jako wywołanie metody [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) w tym programie.

 Implementacje powinny wysyłać [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) , gdy program zostanie zatrzymany.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
