---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac9b23c40b7481fc7520b109afc7d23864582548
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225694"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Ten interfejs wylicza programów uruchomionych w bieżącej sesji debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby udostępnić listę programów, które jest debugowane DE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołania [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) uzyskać ten interfejs. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) nie jest używany przez program Visual Studio.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugPrograms2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Pobiera określoną liczbę programów w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Pomija określoną liczbę programów w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Pobiera liczbę programów w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu:

- Wypełnij **modułów** okna (przez wywołanie metody [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , a następnie wywołując [enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) na każdy program).

- Wypełnij **dołączyć do procesu** listy (przez wywołanie metody `IDebugProcess2::EnumPrograms` , a następnie wywołując [QueryInterface](/cpp/atl/queryinterface) na każdym [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs do uzyskiwania [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interfejsu).

- Generowanie listy DEs, który można debugować każdy program w procesie (przy użyciu [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Stosowanie aktualizacji Edytuj i Kontynuuj (ENC) do każdego programu (przez wywołanie IDebugProcess2::EnumPrograms, a następnie wywołując [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)