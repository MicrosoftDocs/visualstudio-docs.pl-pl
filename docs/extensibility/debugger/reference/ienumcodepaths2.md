---
title: IEnumCodePaths2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e43491c329753e50e7c733afb55ecd4f415d11a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965236"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Ten interfejs reprezentuje listę ścieżek kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę ścieżek kodu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumCodePaths2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Pobiera określoną liczbę ścieżek kodu w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Pomija określoną liczbę ścieżek kodu w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Pobiera liczbę ścieżek kodu w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Ścieżka kodu reprezentuje gałęzi punktu lub wywołania funkcji w programie. Lista ścieżek kodu reprezentuje ścieżkę, przez które zajęło wykonanie kodu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)