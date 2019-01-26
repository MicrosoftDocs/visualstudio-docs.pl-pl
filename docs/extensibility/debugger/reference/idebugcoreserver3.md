---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 388c884e77f4367eae1ac90e0390163efa7a7e37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933068"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Ten interfejs zapewnia dostęp do informacji o serwerze, który proces jest uruchomiony w.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu. Wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) może również zwracać ten interfejs. Ten interfejs jest używany przez dostawcę numery portów w większości przypadków można uruchomić programy na serwerze (lokalnego lub zdalnego).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Pobiera nazwę serwera.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Pobiera wersję przyjazną nazwę serwera|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Informuje aparaty debugowania określonych umożliwia automatyczne dołączanie do procesów, po uruchomieniu tych procesów.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Pobiera określonego kodu błędu, gdy automatyczne dołączanie kończy się niepowodzeniem.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Tworzy wystąpienie aparatu debugowania na serwerze.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Pobiera flagę wskazującą, czy serwer znajduje się na tym samym komputerze, co obiekt wywołujący.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Pobiera wartość wskazującą, protokół używany do komunikacji z serwerem.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Wyłącza wszystkie automatyczne dołączanie ustawienia dla wszystkich aparaty debugowania, który zna tego serwera.|  
  
## <a name="remarks"></a>Uwagi  
 Dostawca niestandardowy port otrzymuje [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu w wywołaniu [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3` Interfejsu można uzyskać z interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)