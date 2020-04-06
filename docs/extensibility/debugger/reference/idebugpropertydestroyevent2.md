---
title: IDebugPropertyDestroyEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce15f389f22513e08b06c0d097cdac4aec3c35bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720908"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do menedżera debugowania sesji (SDM), gdy właściwość skojarzona z określonym dokumentem ma zostać zniszczona.

## <a name="syntax"></a>Składnia

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do raportu, że właściwość została zniszczona. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu. Ten interfejs jest implementowany, jeśli DE wcześniej utworzył właściwość skojarzoną ze skryptem; zniszczenie właściwości usuwa skojarzony skrypt z IDE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia do raportu właściwość została zniszczona. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączony do programu jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPropertyDestroyEvent2`przedstawiono metodę .

|Metoda|Opis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Pobiera właściwość do zniszczenia.|

## <a name="remarks"></a>Uwagi
 Zobacz Uwagi dla [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) szczegółowe informacje na temat dlaczego te zdarzenia są używane.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
