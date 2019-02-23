---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c0572bfa8ebe1b70548483b17c58d08c8a0f9ca
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686954"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Zezwala lub nie zezwala na Obliczanie wyrażenia wystąpić w danym wątku, nawet jeśli zostało zatrzymane.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

#### <a name="parameters"></a>Parametry
 `pOriginatingProgram`

 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt reprezentujący program, który jest obliczenia wyrażenia.

 `dwTid`

 [in] Określa identyfikator wątku.

 `dwEvalFlags`

 [in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie określające sposób oceny ma zostać wykonane.

 `pExprCallback`

 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt ma być używany do wysyłania zdarzenia debugowania, które wystąpiły podczas obliczania wyrażenia.

 `fWatch`

 [in] Jeśli wartość od zera (`TRUE`), umożliwia oceny wyrażenia w wątku identyfikowane przez `dwTid`; w przeciwnym razie zero (`FALSE`) nie zezwalają na obliczenia wyrażenia dla tego wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy Menedżer debugowania sesji (SDM) prosi programu identyfikowane przez `pOriginatingProgram` parametru, aby szacować wyrażenia, powiadomi użytkownika wszystkie inne programy dołączone przez wywołanie tej metody.

 Ocena wyrażeń w jeden program może spowodować, że kod uruchomiony w innym, ze względu na obliczanie funkcji lub oceny dowolnego `IDispatch` właściwości. W związku z tym ta metoda umożliwia obliczanie wyrażenia zostać uruchomione i ukończone, nawet jeśli wątek może być zatrzymana w tym programie.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)