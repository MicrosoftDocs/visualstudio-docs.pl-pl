---
title: IDebugBreakpointErrorEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735044"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Ten interfejs informuje menedżera debugowania sesji (SDM), że oczekujący punkt przerwania nie może być powiązany z załadowanym programem z powodu ostrzeżenia lub błędu.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs jako część jego obsługi punktów przerwania. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten `IDebugEvent2` interfejs (SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia, gdy oczekujące punktu przerwania nie mogą być powiązane z programem debugowane. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez SDM po podłączeniu do programu, który jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugBreakpointErrorEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Pobiera [interfejs IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) który opisuje ostrzeżenie lub błąd.|

## <a name="remarks"></a>Uwagi
 Zawsze, gdy punkt przerwania jest powiązany, zdarzenie jest wysyłane do SDM. Jeśli nie można wiązać `IDebugBreakpointErrorEvent2` punktu przerwania, jest wysyłany; w przeciwnym razie zostanie wysłana [iDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

 Na przykład gdy warunek skojarzony z oczekującym punktem przerwania nie może przeanalizować lub ocenić, zostanie wysłane ostrzeżenie, że oczekujący punkt przerwania nie może być powiązany w tej chwili. Taka liczba może wystąpić, jeśli kod punktu przerwania nie został jeszcze załadowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
