---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730360"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Umożliwia (lub nie zezwala) na ocenę wyrażenia w danym wątku, nawet jeśli program został zatrzymany.

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

## <a name="parameters"></a>Parametry
`pOriginatingProgram`\
[w] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt reprezentujący program, który ocenia wyrażenie.

`dwTid`\
[w] Określa identyfikator wątku.

`dwEvalFlags`\
[w] Kombinacja flag z [wyliczenia EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) które określają sposób wykonywania oceny.

`pExprCallback`\
[w] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który ma służyć do wysyłania zdarzeń debugowania, które występują podczas oceny wyrażenia.

`fWatch`\
[w] Jeśli niezerowa`TRUE`( ), umożliwia ocenę wyrażenia `dwTid`w wątku identyfikowanym przez ; w przeciwnym`FALSE`razie zero ( ) nie zezwala na ocenę wyrażenia w tym wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy menedżer debugowania sesji (SDM) prosi program, identyfikowany przez `pOriginatingProgram` parametr, aby ocenić wyrażenie, powiadamia wszystkie inne dołączone programy, wywołując tę metodę.

 Ocena wyrażenia w jednym programie może spowodować, że kod będzie `IDispatch` uruchamiany w innym, ze względu na ocenę funkcji lub ocenę dowolnych właściwości. Z tego powodu ta metoda umożliwia ocenę wyrażenia do uruchomienia i ukończenia, nawet jeśli wątek może zostać zatrzymany w tym programie.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
