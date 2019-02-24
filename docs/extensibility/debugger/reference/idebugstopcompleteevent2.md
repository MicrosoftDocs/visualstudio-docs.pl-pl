---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3ec59d6e9a6008f195cab40fe5c1998aff24a50
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705284"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Aparat debugowania (DE) można wysłać zdarzenie to opcjonalne Menedżer debugowania sesji (SDM), po zatrzymaniu program.

## <a name="syntax"></a>Składnia

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji

Ten interfejs został wprowadzony w programie Visual Studio 2005. Wcześniejsze wersje nie obsługują zatrzymywanie asynchronicznego.

- [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowe lub wielu programów. Gdy jeden program wysyła zdarzenia zatrzymywanie SDM, SDM żądań inne programy, aby zatrzymać zbyt.

Zatrzymaj jest używany do asynchronicznie powiadamia SDM, który programu została zatrzymana. Informowanie SDM przydaje się do aparatu debugowania interpreter, gdzie czasami uruchomiony żaden kod w debugowanym programu, więc [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie może zostać ukończona synchronicznie. Jeśli aparat debugowania chce używać tego asynchronicznego powiadomienia, aplikacja musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Wymagania

Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll