---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4f36431ef7a190e98d35e795ffd8213781553dfc
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036122"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Zezwala (lub nie zezwala) na Obliczanie wyrażenia w danym wątku, nawet jeśli program został zatrzymany.

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
podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) reprezentujący program oceniający wyrażenie.

`dwTid`\
podczas Określa identyfikator wątku.

`dwEvalFlags`\
podczas Kombinacja flag z wyliczenia [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , która określa, w jaki sposób ma być przeprowadzana Ocena.

`pExprCallback`\
podczas Obiekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który ma być używany do wysyłania zdarzeń debugowania, które wystąpiły podczas obliczania wyrażenia.

`fWatch`\
podczas Jeśli wartość jest różna od zera ( `TRUE` ), umożliwia Obliczanie wyrażenia w wątku identyfikowanym przez `dwTid` ; w przeciwnym razie zero ( `FALSE` ) nie zezwala na Obliczanie wyrażenia w tym wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy Menedżer debugowania sesji zażąda programu identyfikowanego przez `pOriginatingProgram` parametr w celu obliczenia wyrażenia, powiadamia wszystkie inne dołączone programy przez wywołanie tej metody.

 Obliczanie wyrażeń w jednym programie może spowodować, że kod będzie działać w innym, z powodu oceny funkcji lub oceny wszelkich `IDispatch` właściwości. W związku z tym ta metoda umożliwia uruchamianie i kończenie obliczania wyrażeń, nawet jeśli wątek może zostać zatrzymany w tym programie.

## <a name="see-also"></a>Zobacz także
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
