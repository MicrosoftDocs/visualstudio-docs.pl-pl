---
title: IEnumDebugCustomAttributes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebf7250f0845eb666b910b5ddcce266be1ea9361
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990649"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Wylicza atrybutów niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symboli implementuje ten interfejs do obsługi atrybuty niestandardowe (za pośrednictwem [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [Enumcustomattributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugCustomAttributes`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Pobiera określoną liczbę atrybutów niestandardowych, w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Pomija określoną liczbę atrybutów niestandardowych, w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Pobiera moduł wyliczający liczba atrybutów niestandardowych.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy dostawca symboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Enumcustomattributes —](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)