---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33272f87ae30832588a998ebea2fc46e9adaae50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984239"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Aparat debugowania (DE) można wysłać zdarzenie to opcjonalne Menedżer debugowania sesji (SDM), po zatrzymaniu program.

## <a name="syntax"></a>Składnia

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji

Ten interfejs został wprowadzony w programie Visual Studio 2005. Wcześniejsze wersje nie obsługują zatrzymywanie asynchronicznego.

[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowe lub wielu programów. Gdy jeden program wysyła zdarzenia zatrzymywanie SDM, SDM żądań inne programy, aby zatrzymać zbyt.

Zatrzymaj jest używany do asynchronicznie powiadamia SDM, który programu została zatrzymana. Informowanie SDM przydaje się do aparatu debugowania interpreter, gdzie czasami uruchomiony żaden kod w debugowanym programu, więc [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie może zostać ukończona synchronicznie. Jeśli aparat debugowania chce używać tego asynchronicznego powiadomienia, aplikacja musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Wymagania

Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll