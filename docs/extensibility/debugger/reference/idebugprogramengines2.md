---
title: IDebugProgramEngines2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a5ad34904a2f0bf02e5a2221f1ff73093012a41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916933"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Ten interfejs jest używany przez węzły programu do określenia wszystkich możliwych silniki debugowania (DE), które można debugować ten program.

## <a name="syntax"></a>Składnia

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE lub dostawcy niestandardowego portu implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) umożliwiających ustanawianie określonych DE do użycia dla określonego programu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejsu w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugProgramEngines2`.

|Metoda|Opis|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Wskazuje wszystkie możliwe DEs, który można debugować ten program.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wybiera DE używane do debugowania tego programu.|

## <a name="remarks"></a>Uwagi
 Po DE jest wybierany przez użytkownika, wybór jest zarejestrowany w węźle programu poprzez wywołanie [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Wybrany aparat staje się aparat, który został zwrócony przez [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)