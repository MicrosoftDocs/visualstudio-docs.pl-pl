---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c24edcd5ef47408cd4c11b3d0548ad34516702a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326504"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Ten interfejs wylicza porty dostawcy maszynowo lub port.

## <a name="syntax"></a>Składnia

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs reprezentujący listę portów tworzone przez dostawcę. Program Visual Studio implementuje ten interfejs, w odniesieniu do własnego dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) uzyskać ten interfejs reprezentujący listę portów tworzone przez dostawcę portu. Wywołaj [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) uzyskać ten interfejs reprezentujący listę portów, które zostały zapisane na dysku.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugPorts2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Pobiera określoną liczbę portów w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Pomija określoną liczbę portów w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Pobiera liczbę portów w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu, aby pomóc, wypełnić listę portów używanych do dołączanie do procesu.

 Aparat debugowania zwykle nie korzysta z tego interfejsu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)