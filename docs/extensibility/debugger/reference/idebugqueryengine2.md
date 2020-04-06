---
title: IDebugQueryEngine2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720653"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Ten interfejs umożliwia menedżera debugowania sesji (SDM) pobrać interfejs, który reprezentuje aparat debugowania (DE).

## <a name="syntax"></a>Składnia

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs na obiektach, które implementują najbardziej typowe interfejsy DE (takie jak [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)i [IDebugStackFrame2)](../../../extensibility/debugger/reference/idebugstackframe2.md)w celu umożliwienia dostępu do interfejsu [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) samego DE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na typowy interfejs DE, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugQueryEngine2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Pobiera niestandardowy aparat debugowania (DE) interfejs.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zazwyczaj implementowane w obiekcie, który implementuje interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) w celu obsługi przyczynowości uporządkowane przechodzenie przez funkcje; oznacza to, że gdy debuger jest wyjście z funkcji, następna funkcja do wykonania nie może być poprzednią funkcję na stosie, ale funkcja w innym wątku całkowicie. Aby uzyskać definicję "przyczynowości", zobacz [słowniczek debugera programu Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
