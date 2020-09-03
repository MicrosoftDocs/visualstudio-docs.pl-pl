---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717444"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Ten interfejs wylicza powiązane punkty przerwania skojarzone z oczekującym zdarzeniem punktu przerwania lub przerwaniem.

## <a name="syntax"></a>Składnia

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi punktów przerwania. Ten interfejs musi być zaimplementowany, jeśli są obsługiwane punkty przerwania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania programu Visual Studio:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby uzyskać ten interfejs reprezentujący listę wszystkich wyzwolonych punktów przerwania.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) , aby uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które zostały powiązane.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) , aby uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania powiązanych z tym oczekującym punktem przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugBoundBreakpoints2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Pobiera określoną liczbę powiązanych punktów przerwania w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Pomija określoną liczbę powiązanych punktów przerwania w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Pobiera liczbę powiązanych punktów przerwania w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa powiązanych punktów przerwania reprezentowanych przez ten interfejs do aktualizowania wyświetlania punktów przerwania w IDE.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
