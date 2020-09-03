---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f66587f462e1bbfb60704c5c75dc2299cb9ce36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160970"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs wylicza listę modułów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować listę modułów ładowanych dla programu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Program Visual Studio wywołuje [EnumModules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) , aby uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IEnumDebugModules2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Pobiera określoną liczbę modułów w sekwencji wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Pomija określoną liczbę modułów w sekwencji wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Resetuje sekwencję wyliczenia na początek.|  
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Pobiera liczbę modułów.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio używa tego interfejsu głównie do aktualizowania okna **moduły** .  
  
 Na potrzeby debugowania w programie Visual Studio program jest logiczną sekwencją instrukcji kodu, która może przekroczyć granice modułu, dlatego konieczna jest lista modułów dla jednego interfejsu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Pierwszy moduł na liście zwykle zawiera początkowy punkt wejścia dla skojarzonego programu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
