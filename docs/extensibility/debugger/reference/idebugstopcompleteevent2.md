---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719443"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Aparat debugowania (DE) może wysłać to zdarzenie opcjonalne do Menedżera debugowania sesji (SDM), gdy program został zatrzymany.

## <a name="syntax"></a>Składnia

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji

Ten interfejs został wprowadzony w programie Visual Studio 2005. Wcześniejsze wersje nie obsługują asynchronicznego zatrzymywania.

- Wartość [stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez model SDM w scenariuszach obejmujących wiele procesów lub wiele programów. Gdy jeden program wysyła zdarzenie zatrzymania do modelu SDM, model SDM żąda również innych programów.

Wartość Stop umożliwia asynchroniczne informowanie modelu SDM o zatrzymaniu programu. Informowanie modelu SDM jest przydatne w przypadku aparatu debugowania interpretera, gdzie czasami żaden kod nie działa w debugowanym programie, więc nie można wykonać operacji [zatrzymania](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) synchronicznie. Jeśli aparat debugowania chce użyć tego powiadomienia asynchronicznego, musi zwrócić `S_ASYNC_STOP` z [Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Wymagania

Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
