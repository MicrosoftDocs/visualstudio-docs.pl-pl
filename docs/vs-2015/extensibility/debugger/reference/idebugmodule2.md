---
title: IDebugModule2 | Dokumentacja firmy Microsoft
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
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92e11532019caf5aa7af3c84f7222fdfabcfa45d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768542"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje moduł — czyli jednostkę pliku wykonywalnego programu — takich jak biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania modułu i zapewnić dostęp do informacji na temat tego modułu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [getmodule —](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) zwraca ten interfejs. Wysyła DE [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) współpracować w celu Menedżer debugowania sesji (SDM) przy użyciu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.  
  
 Ten interfejs, również mogą być zwracane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury (który jest zwracany przez wywołanie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Następny](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) zwraca również wartość tego interfejsu ([enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) zwraca [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfejsu).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugModule2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Pobiera [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) opisujący tego modułu.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NIE NALEŻY UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o module mogą być wyświetlane w **modułów** okna środowiska IDE.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [Getmodule —](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

