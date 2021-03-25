---
description: Aparat debugowania (DE) może wysłać to zdarzenie opcjonalne do Menedżera debugowania sesji (SDM), gdy program został zatrzymany.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087148"
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
