---
description: Ten interfejs jest wysyłany przez aparat debugowania (DE), aby wskazać, że symbole debugowania dla debugowanego modułu zostały załadowane.
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ef2d315568b78e567d682728c4cbc989c5a4ed2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145745"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE), aby wskazać, że symbole debugowania dla debugowanego modułu zostały załadowane.

## <a name="syntax"></a>Składnia

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Element DE implementuje ten interfejs, aby zgłosić, że symbole modułu zostały załadowane. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, aby zgłosić, że symbole modułu zostały załadowane. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 `IDebugSymbolSearchEvent2`Interfejs uwidacznia poniższą metodę.

|Metoda|Opis|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Pobiera informacje o wynikach wyszukiwania symboli.|

## <a name="remarks"></a>Uwagi
 To zdarzenie zostanie wysłane, nawet jeśli nie udało się załadować symboli. Wywołanie `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` zezwala programowi obsługi tego zdarzenia w celu ustalenia, czy moduł rzeczywiście ma symbole.

 Program Visual Studio zwykle używa tego zdarzenia do aktualizowania stanu załadowanych symboli w oknie **moduły** .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
