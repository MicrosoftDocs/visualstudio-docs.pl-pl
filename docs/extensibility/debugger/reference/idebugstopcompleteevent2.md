---
description: Aparat debugowania (DE) może wysłać to zdarzenie opcjonalne do Menedżera debugowania sesji (SDM), gdy program został zatrzymany.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d96aa335c8951b9dfc80517bf797338cd590b48
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159748"
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
