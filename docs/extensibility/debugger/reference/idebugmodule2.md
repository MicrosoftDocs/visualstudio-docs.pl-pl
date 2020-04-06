---
title: IDebugModule2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726904"
---
# <a name="idebugmodule2"></a>IDebugModule2
Ten interfejs reprezentuje moduł — czyli jednostkę wykonywalną programu — taką jak biblioteka DLL.

## <a name="syntax"></a>Składnia

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania modułu i zapewnienia dostępu do informacji o tym module.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) zwraca ten interfejs. DE wysyła interfejs [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) do menedżera debugowania sesji (SDM) przy użyciu [event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.

 Ten interfejs można również zwrócić w strukturze [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (która jest zwracana przez wywołanie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) zwraca również ten interfejs ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) zwraca interfejs [IEnumDebugModules2).](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugModule2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Pobiera [MODULE_INFO,](../../../extensibility/debugger/reference/module-info.md) który opisuje ten moduł.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|Przestarzałe. NIE UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.|

## <a name="remarks"></a>Uwagi
 Informacje o module mogą być wyświetlane w oknie **Moduły** IDE.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
