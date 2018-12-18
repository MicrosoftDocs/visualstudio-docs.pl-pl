---
title: IDebugCoreServer3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f732492a3730a9071fd08aab4fe925f4e6bf2cd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735843"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs zapewnia dostęp do informacji o serwerze, który proces jest uruchomiony w.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) uzyskać ten interfejs z [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu. Wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) może również zwracać ten interfejs. Ten interfejs jest używany przez dostawcę numery portów w większości przypadków można uruchomić programy na serwerze (lokalnego lub zdalnego).  
  
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
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)

