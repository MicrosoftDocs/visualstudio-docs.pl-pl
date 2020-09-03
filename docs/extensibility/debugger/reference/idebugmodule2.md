---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726904"
---
# <a name="idebugmodule2"></a>IDebugModule2
Ten interfejs reprezentuje moduł — czyli jednostkę wykonywalną programu, na przykład bibliotekę DLL.

## <a name="syntax"></a>Składnia

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania modułu i zapewnienia dostępu do informacji na temat tego modułu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie metody [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) zwraca ten interfejs. Anuluj wysyła Interfejs [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) do Menedżera debugowania sesji (SDM) przy użyciu metody [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

 Ten interfejs może być również zwracany w strukturze [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (który jest zwracany przez wywołanie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) zwraca również ten interfejs ([EnumModules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) zwraca interfejs [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugModule2` .

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Pobiera [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , który opisuje ten moduł.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Zbędn. NIE NALEŻY UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.|

## <a name="remarks"></a>Uwagi
 Informacje o module można wyświetlić w oknie **moduły** środowiska IDE.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
