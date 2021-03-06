---
description: Ten interfejs wylicza porty komputera lub dostawcy portów.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4b93aa34870d05b9a4ec0a9a0aa92f681735dfe3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224463"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Ten interfejs wylicza porty komputera lub dostawcy portów.

## <a name="syntax"></a>Składnia

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs, aby reprezentować listę portów utworzonych przez dostawcę. Program Visual Studio implementuje ten interfejs w celu obsługi własnego dostawcy portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) , aby uzyskać ten interfejs reprezentujący listę portów utworzonych przez dostawcę portu. Wywołaj [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) , aby uzyskać ten interfejs reprezentujący listę portów, które zostały zapisane na dysku.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugPorts2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Pobiera określoną liczbę portów w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Pomija określoną liczbę portów w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Pobiera liczbę portów w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu, aby pomóc wypełnić listę portów używanych do dołączania do procesów.

 Aparat debugowania zwykle nie używa tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
