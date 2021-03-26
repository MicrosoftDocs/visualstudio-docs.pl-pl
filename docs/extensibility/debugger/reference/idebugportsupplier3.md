---
description: Ten interfejs umożliwia obiektowi wywołującemu określenie, czy dostawca portu może zachować porty (pisząc je na dysku) między wywołaniami debugera, a następnie uzyskać listę tych zachowanych portów.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa17984c9b7f3e87d4a7118188ecc6ca79c5deef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071938"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Ten interfejs umożliwia obiektowi wywołującemu określenie, czy dostawca portu może zachować porty (pisząc je na dysku) między wywołaniami debugera, a następnie uzyskać listę tych zachowanych portów.

## <a name="syntax"></a>Składnia

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs, aby zapewnić obsługę utrwalania lub zapisywania informacji o portach na dysku. Ten interfejs musi być zaimplementowany w tym samym obiekcie co Interfejs [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na `IDebugPortSupplier2` interfejsie, aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z interfejsu [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , ten interfejs obsługuje następujące elementy:

|Metoda|Opis|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Zwraca informację o tym, czy dostawca portu może utrwalać porty (pisząc je na dysku) między wywołaniami debugera.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Zwraca obiekt, którego można użyć do wyliczenia przez wszystkie porty, które zostały zapisaną na dysku przez tego dostawcę portu.|

## <a name="remarks"></a>Uwagi
 Jeśli dostawca portu może utrzymywać porty w wywołaniach, powinien implementować ten interfejs. Porty powinny być ładowane w przypadku wystąpienia dostawcy portów i zapisywane na dysku w przypadku zniszczenia dostawcy portów.

 Aparat debugowania zwykle nie współdziała z dostawcą portu i nie będzie miał zastosowania do tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
