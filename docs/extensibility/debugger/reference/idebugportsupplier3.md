---
title: IDebugPortSupplier3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724435"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Ten interfejs umożliwia obiektowi wywołującemu ustalenie, czy dostawca portu może zachować porty (zapisując je na dysku) między wywołaniami debugera, a następnie uzyskać listę tych zachowanych portów.

## <a name="syntax"></a>Składnia

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs do obsługi utrwalania lub zapisywania informacji o porcie na dysku. Ten interfejs musi być zaimplementowany na tym samym obiekcie co interfejs [IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) w interfejsie, `IDebugPortSupplier2` aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z interfejsu [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) ten interfejs obsługuje następujące elementy:

|Metoda|Opis|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Zwraca, czy dostawca portu może utrwalać porty (zapisując je na dysku) między wywołaniami debugera.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Zwraca obiekt, który może służyć do wyliczenia przez wszystkie porty, które zostały zapisane na dysku przez tego dostawcę portu.|

## <a name="remarks"></a>Uwagi
 Jeśli dostawca portu może utrwalać porty w wywołaniach, należy zaimplementować ten interfejs. Porty powinny być ładowane, gdy dostawca portu jest sukany i zapisywane na dysku, gdy dostawca portu jest niszczony.

 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu i nie będzie miał zastosowania dla tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
