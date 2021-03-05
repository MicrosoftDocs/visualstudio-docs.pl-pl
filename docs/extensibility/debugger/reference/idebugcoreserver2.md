---
description: Ten interfejs służy do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 871f7ea5671fa4f3c615d84e0591bd331f945ccc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163138"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Ten interfejs służy do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.

## <a name="syntax"></a>Składnia

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs, aby reprezentować serwer. Każde wystąpienie programu Visual Studio tworzy wystąpienie tego interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Dostawca portu niestandardowego odbiera ten interfejs w wywołaniu [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Aparat debugowania może uzyskać ten interfejs pośrednio za pośrednictwem wywołania metody [getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (która zwraca [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), interfejs, który jest pochodną `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugCoreServer2` .

|Metoda|Opis|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Pobiera nazwę i atrybuty maszyny.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Pobiera nazwę komputera.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Pobiera dostawcę portu, który istnieje na komputerze.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Pobiera port, który już istnieje na maszynie.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tworzy moduł wyliczający dla wszystkich portów na komputerze.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tworzy moduł wyliczający dla wszystkich dostawców portów na komputerze.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Pobiera narzędzia maszyny dla komputera.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest również używany przez program Visual Studio do przeglądania procesów uruchomionych na maszynach w sieci.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
