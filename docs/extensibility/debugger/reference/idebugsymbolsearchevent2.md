---
title: IDebugSymbolSearchEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed7108c9e1349b01115bed8a6b2a77a3eaa71f45
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320390"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Ten interfejs są wysyłane przez aparat debugowania (DE) w celu wskazania, czy załadowano symbole debugowania dla debugowanego modułu.

## <a name="syntax"></a>Składnia

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby zgłosić, czy załadowano symbole dla modułu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia do raportowania, czy załadowano symbole dla modułu. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 `IDebugSymbolSearchEvent2` Interfejsu udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Pobiera informacje o wynikach wyszukiwania symboli.|

## <a name="remarks"></a>Uwagi
 To zdarzenie zostanie wysłane, nawet wtedy, gdy nie można załadować symbole. Wywoływanie `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` pozwala procedurze obsługi tego zdarzenia, aby sprawdzić, czy moduł jest faktycznie wszystkie symbole.

 Program Visual Studio zazwyczaj używa tego zdarzenia do aktualizowania stanu załadowano symbole w **modułów** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)