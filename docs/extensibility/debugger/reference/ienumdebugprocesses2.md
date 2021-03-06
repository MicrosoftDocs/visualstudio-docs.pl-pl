---
description: Ten interfejs wylicza procesy działające na porcie debugowania.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 75778ea0f02c0e7dcca1f7d2eb0ea8ace82c9b9c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224385"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Ten interfejs wylicza procesy działające na porcie debugowania.

## <a name="syntax"></a>Składnia

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs, aby zapewnić listę procesów uruchomionych na porcie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Program Visual Studio wywołuje [EnumProcesses —](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) , aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugProcesses2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Pobiera określoną liczbę procesów w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Pomija określoną liczbę procesów w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Pobiera liczbę procesów w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu do wypełniania okna **procesy** .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
