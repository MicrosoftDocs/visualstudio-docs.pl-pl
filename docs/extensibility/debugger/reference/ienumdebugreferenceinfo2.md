---
title: IEnumDebugReferenceInfo2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f3b370757516220259c8229b7abffc211bc6405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919463"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Ten interfejs wylicza [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, w ramach wsparcia dla odwołania do obiektów w pamięci. Ten interfejs musi można zaimplementować tylko wtedy, gdy odwołania są obsługiwane.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugReferenceInfo2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Pobiera określoną liczbę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Pomija określoną liczbę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Pobiera liczbę [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie jest zasadniczo typu i adres właściwości jest nazwa, typ i adres. Odwołanie będzie się powtarzać, tak długo, jak określony obiekt istnieje w pamięci. Zobacz [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Aby uzyskać więcej informacji.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)