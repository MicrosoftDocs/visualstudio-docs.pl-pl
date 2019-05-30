---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b32d2469c42931fa3dead4c5078e7d5b44b5d60
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334938"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Ten interfejs wylicza procesów uruchomionych na porcie debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs, aby udostępnić listę procesów uruchomionych na porcie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołania [enumprocesses —](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugProcesses2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Pobiera określoną liczbę procesów w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Pomija określoną liczbę procesów w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Pobiera liczbę procesów w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu do wypełniania **procesy** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)