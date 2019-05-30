---
title: IDebugModule2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b621ae3b1408bc4af371243a1c34909117d40576
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323935"
---
# <a name="idebugmodule2"></a>IDebugModule2
Ten interfejs reprezentuje moduł — czyli jednostkę pliku wykonywalnego programu — takich jak biblioteki DLL.

## <a name="syntax"></a>Składnia

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania modułu i zapewnić dostęp do informacji na temat tego modułu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [getmodule —](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) zwraca ten interfejs. Wysyła DE [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) współpracować w celu Menedżer debugowania sesji (SDM) przy użyciu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.

 Ten interfejs, również mogą być zwracane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury (który jest zwracany przez wywołanie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Następny](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) zwraca również wartość tego interfejsu ([enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) zwraca [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfejsu).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugModule2`.

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Pobiera [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) opisujący tego modułu.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NIE NALEŻY UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.|

## <a name="remarks"></a>Uwagi
 Informacje o module mogą być wyświetlane w **modułów** okna środowiska IDE.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)