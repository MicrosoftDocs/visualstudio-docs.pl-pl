---
title: IDebugBeforeSymbolSearchEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736111"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Aparat debugowania (DE) wysyła ten interfejs do menedżera debugowania sesji (SDM), aby ustawić komunikat paska stanu podczas ładowania symbolu.

## <a name="syntax"></a>Składnia

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, gdy musi ustawić komunikat paska stanu podczas ładowania symbolu. Ten interfejs jest implementowany tylko przez aparaty debugowania, które współpracują z interpreterami skryptów lub są ich częścią. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs (SDM używa **QueryInterface,** aby uzyskać dostęp do interfejsu **IDebugEvent2).**

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia, gdy musi ustawić komunikat paska stanu podczas ładowania symbolu. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez SDM po podłączeniu do programu, który jest debugowany.

## <a name="methods"></a>Metody
 W poniższej tabeli `IDebugBeforeSymbolSearchEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Pobiera nazwę modułu aktualnie debugowanego.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
