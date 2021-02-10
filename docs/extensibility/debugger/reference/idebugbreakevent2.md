---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61fb53c1fc83f06c200b50b5fcf55f950a00ead6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943437"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Ten interfejs informuje Menedżera debugowania sesji (SDM) o tym, że przerwa asynchroniczna została pomyślnie ukończona.

## <a name="syntax"></a>Składnia

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby obsługiwać przerwy użytkownika w programie. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Model SDM wywołuje [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) , gdy użytkownik zażądał wstrzymania działania programu. Po pomyślnym wstrzymaniu program wysyła `IDebugBreakEvent2` zdarzenie. To zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="remarks"></a>Uwagi
 Na przykład użytkownik może wybrać polecenie **Przerwij wszystko** w menu **debugowanie** , aby przerwać działanie programu, w którym działa nieskończona pętla. Model SDM informuje program, aby zatrzymał się przez wywołanie [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). ANULUJe, `IDebugBreakEvent2` gdy program zakończy pracę.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
