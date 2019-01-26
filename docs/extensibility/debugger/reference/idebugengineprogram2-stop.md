---
title: IDebugEngineProgram2::Stop | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9e60b328ee13a47df9d7656c992f81e63cbbd2ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983784"
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
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)