---
title: Porty IEnumDebugPorts2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716104"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Ten interfejs wylicza porty dostawcy maszyny lub portu.

## <a name="syntax"></a>Składnia

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs do reprezentowania listy portów utworzonych przez dostawcę. Visual Studio implementuje ten interfejs w celu obsługi własnego dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [EnumPorts,](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) aby uzyskać ten interfejs reprezentujący listę portów utworzonych przez dostawcę portu. Wywołanie [EnumPersistedPorts,](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) aby uzyskać ten interfejs reprezentujący listę portów, które zostały zapisane na dysku.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugPorts2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Pobiera określoną liczbę portów w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Pomija określoną liczbę portów w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Pobiera liczbę portów w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Visual Studio używa tego interfejsu, aby pomóc wypełnić listę portów używanych do dołączania do procesów.

 Aparat debugowania zazwyczaj nie używa tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
