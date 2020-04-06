---
title: IDebugCoreServer3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732809"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Ten interfejs daje dostęp do informacji o serwerze, na który działa proces.

## <a name="syntax"></a>Składnia

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) można również zwrócić ten interfejs. Ten interfejs jest najczęściej używany przez niestandardowego dostawcę portu do uruchamiania programów na serwerze (lokalnym lub zdalnym).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na interfejsie [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Pobiera nazwę serwera.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Pobiera przyjazną wersję nazwy serwera|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Informuje określone aparaty debugowania, aby automatycznie dołączane do procesów podczas uruchamiania tych procesów.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Pobiera określony kod błędu, gdy automatyczne dołączanie nie powiedzie się.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Tworzy wystąpienie aparatu debugowania na serwerze.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Pobiera flagę wskazującą, czy serwer znajduje się na tym samym komputerze co wywołujący.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Pobiera wartość wskazującą protokół używany do komunikowania się z serwerem.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Wyłącza wszystkie ustawienia automatycznego dołączania dla wszystkich aparatów debugowania, o których wie ten serwer.|

## <a name="remarks"></a>Uwagi
 Niestandardowy dostawca portu odbiera interfejs [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) podczas wywołania [zdarzenia.](../../../extensibility/debugger/reference/idebugportevents2-event.md) Interfejs `IDebugCoreServer3` można uzyskać z tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
