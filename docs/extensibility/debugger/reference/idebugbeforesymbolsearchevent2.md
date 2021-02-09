---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb185e098d76184d3a74df380eb8a5e66bc699df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869963"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Aparat debugowania (DE) wysyła ten interfejs do Menedżera debugowania sesji (SDM), aby ustawić komunikat paska stanu podczas ładowania symboli.

## <a name="syntax"></a>Składnia

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Element DE implementuje ten interfejs, gdy musi ustawić komunikat paska stanu podczas ładowania symboli. Ten interfejs jest implementowany tylko przez aparaty debugowania, które działają z lub są częścią interpreterów skryptów. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa **metody QueryInterface** do uzyskiwania dostępu do interfejsu **IDebugEvent2** ).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, gdy musi ustawić komunikat paska stanu podczas ładowania symboli. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody `IDebugBeforeSymbolSearchEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Pobiera nazwę aktualnie debugowanego modułu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
