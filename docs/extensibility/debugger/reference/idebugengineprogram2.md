---
description: Ten interfejs zapewnia obsługę debugowania wielowątkowego.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea46ccad8f357cb868a445a8836280abf7c224e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153381"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Ten interfejs zapewnia obsługę debugowania wielowątkowego.

## <a name="syntax"></a>Składnia

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs do obsługi jednoczesnego debugowania wielu wątków. Ten interfejs jest zaimplementowany dla tego samego obiektu, który implementuje interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z `IDebugProgram2` interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugEngineProgram2` .

|Metoda|Opis|
|------------|-----------------|
|[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Przerywa wszystkie wątki działające w tym programie.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Czujki do wykonania (lub zatrzymania oglądania pod kątem wykonania) mogą wystąpić w danym wątku.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Zezwala (lub nie zezwala) na Obliczanie wyrażenia w danym wątku, nawet jeśli program został zatrzymany.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio wywołuje ten interfejs w odpowiedzi na zdarzenie [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i ustawia wartość "Watch dla kroku wątku" i "Watch for Expression Evaluation" w przypadku programu. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana za każdym razem, gdy program ma zostać zatrzymany; Ta metoda umożliwia programowi zakończenie wszystkich wątków.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
