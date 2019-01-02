---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39da50c17d4d4b8b02390e0d2960d5696b93b1f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932899"
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

Nagłówek: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll