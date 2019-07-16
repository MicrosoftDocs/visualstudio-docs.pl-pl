---
title: BP_UNBOUND_REASON | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddff6130e2243d10c00cefec160d057516d60932
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153277"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zapewnia powodów, dla którego punkt przerwania został niepowiązanej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPUR_UNKNOWN  
 Przyczyną jest nieznany.  
  
 BPUR_CODE_UNLOADED  
 Kod, który zawiera punkt przerwania został zwolniony.  
  
 BPUR_BREAKPOINT_REBIND  
 Punkt przerwania ma zostało odbitych do innej lokalizacji. To jest wykonywane podczas edycji i kontynuowania działania w przypadku, gdy punkt przerwania lub gdy punkt przerwania jest powiązana z pliku ze ścieżką, która nie jest już prawidłowy.  
  
 BPUR_ BREAKPOINT_ERROR  
 Punkt przerwania jest określana jest błędny po jest powiązany. Dzieje się to do zarządzanego punktów przerwania, którego warunki nie są już prawidłowe.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócone przez [getreason —](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
