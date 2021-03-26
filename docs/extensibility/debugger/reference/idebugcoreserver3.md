---
description: Ten interfejs zapewnia dostęp do informacji o serwerze, na którym jest uruchomiony proces.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab605db6a49b8b7cc9893692ff1bb9e6da15171f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088149"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Ten interfejs zapewnia dostęp do informacji o serwerze, na którym jest uruchomiony proces.

## <a name="syntax"></a>Składnia

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z interfejsu [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) . Wywołanie metody [getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) może również zwrócić ten interfejs. Ten interfejs jest najczęściej używany przez niestandardowego dostawcę portu do uruchamiania programów na serwerze (lokalna lub zdalna).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod interfejsu [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Pobiera nazwę serwera.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Pobiera przyjazną wersję nazwy serwera|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Instruuje określone aparaty debugowania, aby automatycznie dołączać do procesów, gdy te procesy zostały uruchomione.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Pobiera określony kod błędu, jeśli automatyczne dołączanie nie powiedzie się.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Tworzy wystąpienie aparatu debugowania na serwerze.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Pobiera flagę wskazującą, czy serwer znajduje się na tym samym komputerze co obiekt wywołujący.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Pobiera wartość wskazującą protokół używany do komunikacji z serwerem.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Wyłącza wszystkie ustawienia automatyczne dołączania dla wszystkich aparatów debugowania, o których wie ten serwer.|

## <a name="remarks"></a>Uwagi
 Dostawca portu niestandardowego odbiera Interfejs [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) w wywołaniu [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3`Interfejs można uzyskać z tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
