---
title: IEnumDebugModules2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a78023b8c09139368e736a32ae349c566457035a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928142"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Ten interfejs wylicza listę modułów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę moduły załadowane w programie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugModules2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Pobiera określoną liczbę modułów w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Pomija określoną liczbę modułów w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Pobiera liczbę modułów.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio używa tego interfejsu, głównie w celu aktualizacji **modułów** okna.  
  
 Na potrzeby debugowania w programie Visual Studio program jest logicznej kolejności instrukcji kodu, które mogą między granicami modułów, dlatego potrzebę listę modułów dla pojedynczego [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Moduł pierwszy na liście zazwyczaj zawiera punkt wejścia początkowej dla skojarzonego programu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)