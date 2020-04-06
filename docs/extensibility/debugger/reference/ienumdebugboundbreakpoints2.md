---
title: IEnumDebugBoundBreakpoints2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717444"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Ten interfejs wylicza powiązane punkty przerwania skojarzone z oczekującym zdarzeniem związanym z punktem przerwania lub punktem przerwania.

## <a name="syntax"></a>Składnia

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługi punktów przerwania. Ten interfejs musi być zaimplementowany, jeśli punkty przerwania są obsługiwane.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania programu Visual Studio:

- [EnumBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) aby uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które zostały wyzwolone.

- [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) aby uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które były powiązane.

- [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) aby uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania powiązanych z tym oczekującym punktem przerwania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugBoundBreakpoints2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Pobiera określoną liczbę powiązanych punktów przerwania w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Pomija określoną liczbę powiązanych punktów przerwania w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Pobiera liczbę powiązanych punktów przerwania w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Visual Studio używa powiązanych punktów przerwania reprezentowanych przez ten interfejs, aby zaktualizować wyświetlanie punktów przerwania w IDE.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
