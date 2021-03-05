---
description: Ten interfejs jest wysyłany, gdy proces zostaje zakończony, kończy się nietypowo lub jest odłączony od.
title: IDebugProcessDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessDestroyEvent2
helpviewer_keywords:
- IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91d2e3afc2292f7a180b1dcce0cc015fea640a86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169161"
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Ten interfejs jest wysyłany, gdy proces zostaje zakończony, kończy się nietypowo lub jest odłączony od.

## <a name="syntax"></a>Składnia

```
IDebugProcessDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) lub dostawca portu niestandardowego Implementuj ten interfejs, aby zgłosić, że proces został zakończony. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Niestandardowa dostawca portu tworzy i wysyła ten obiekt zdarzenia w celu zgłoszenia zakończenia procesu. Po wysłaniu tego zdarzenia za pomocą funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest on dołączony do debugowanego programu. Dostawca portu niestandardowego wysyła to zdarzenie przy użyciu interfejsu [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
