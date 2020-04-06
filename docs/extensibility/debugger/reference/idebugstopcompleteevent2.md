---
title: IDebugStopCompleteEvent2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719443"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Aparat debugowania (DE) może wysłać to opcjonalne zdarzenie do menedżera debugowania sesji (SDM) po zatrzymaniu programu.

## <a name="syntax"></a>Składnia

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji

Ten interfejs został wprowadzony w programie Visual Studio 2005. Wcześniejsze wersje nie obsługiwały zatrzymania asynchronii.

- [Zatrzymanie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływane przez SDM w scenariuszach wieloprocesowych lub wieloprogramowych. Gdy jeden program wysyła zdarzenie zatrzymania do SDM, SDM żąda innych programów, aby zatrzymać, zbyt.

Stop służy do asynchronicznie poinformować SDM, że program został zatrzymany. Informowanie SDM jest przydatne dla aparatu debugowania interpretera, gdzie czasami żaden kod nie jest uruchomiony wewnątrz debugowanego programu, więc [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie można ukończyć synchronicznie. Jeśli aparat debugowania chce zastosować to powiadomienie asynchroniczne, musi zwrócić `S_ASYNC_STOP` z [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Wymagania

Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
