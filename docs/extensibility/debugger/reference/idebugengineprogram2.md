---
title: IDebugEngineProgram2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730301"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Ten interfejs zapewnia obsługę debugowania w wielu wątkach.

## <a name="syntax"></a>Składnia

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs do obsługi jednoczesnego debugowania wielu wątków. Ten interfejs jest zaimplementowany na tym samym obiekcie, który implementuje interfejs [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać `IDebugProgram2` ten interfejs z interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugEngineProgram2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Zatrzymuje wszystkie wątki uruchomione w tym programie.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Zegarki do wykonania (lub zatrzymać oglądanie do wykonania) występuje na danym wątku.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Umożliwia (lub nie zezwala) na ocenę wyrażenia w danym wątku, nawet jeśli program jest zatrzymany.|

## <a name="remarks"></a>Uwagi
 Visual Studio wywołuje ten interfejs w odpowiedzi na [zdarzenie IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i ustawić "Watch for Thread Step" i "Watch for Expression Evaluation on Thread" stanu programu. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana za każdym razem, gdy program ma zostać zatrzymany; ta metoda daje programowi szansę zakończenia wszystkich wątków.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
