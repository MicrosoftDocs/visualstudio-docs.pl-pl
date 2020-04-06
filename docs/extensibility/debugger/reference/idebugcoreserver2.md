---
title: IDebugCoreServer2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733035"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Ten interfejs służy do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.

## <a name="syntax"></a>Składnia

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs do reprezentowania serwera. Każde wystąpienie programu Visual Studio tworzy wystąpienie tego interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Dostawca portu niestandardowego odbiera ten interfejs w wywołaniu [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Aparat debugowania można uzyskać ten interfejs pośrednio za pośrednictwem wywołania [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (który zwraca [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), interfejs, który pochodzi od `IDebugCoreServer2`).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugCoreServer2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Pobiera nazwę i atrybuty maszyny.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Pobiera nazwę komputera.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Pobiera dostawcy portu, który istnieje na komputerze.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Pobiera port, który już istnieje na komputerze.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tworzy wyliczenie dla wszystkich portów na komputerze.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tworzy wyliczenie dla wszystkich dostawców portów na komputerze.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Pobiera narzędzia maszyny dla maszyny.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest również używany przez program Visual Studio do przeglądania procesów uruchomionych na komputerach w sieci.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
