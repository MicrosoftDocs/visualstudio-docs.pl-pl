---
description: Ten interfejs reprezentuje moduł obsługujący alternatywne lokalizacje symboli i Stanów JustMyCode.
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38ced8edcc97ad4ab8ff4db430cea57a2533cb30
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149886"
---
# <a name="idebugmodule3"></a>IDebugModule3
Ten interfejs reprezentuje moduł obsługujący alternatywne lokalizacje symboli i Stanów JustMyCode.

## <a name="syntax"></a>Składnia

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby obsługiwać alternatywne lokalizacje symboli i współdziałać z Stanami JustMyCode (zobacz [słownik debugera programu Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) , aby zapoznać się z definicją "JustMyCode").

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetSymbolSearchInfo —](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) zwraca ten interfejs. Anuluj wysyła Interfejs [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) do Menedżera debugowania sesji (SDM) przy użyciu metody [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Ponadto wywołanie [polecenia QueryInterface](/cpp/atl/queryinterface) w interfejsie [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod interfejsu [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Zwraca listę ścieżek przeszukanych symboli i wyniki wyszukiwania każdej ścieżki.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Ładuje i inicjuje symbole dla bieżącego modułu.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Zwraca flagę określającą, czy moduł reprezentuje kod użytkownika.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Określa, czy moduł powinien być uznawany za kod użytkownika, czy nie.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio jest typowym konsumentem tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
