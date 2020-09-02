---
title: BP_UNBOUND_REASON | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153277"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca powód, dla którego nie powiązano punkt przerwania.  
  
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
 Przyczyna jest nieznana.  
  
 BPUR_CODE_UNLOADED  
 Kod, który zawiera punkt przerwania został zwolniony.  
  
 BPUR_BREAKPOINT_REBIND  
 Punkt przerwania został Przewiązany do innej lokalizacji. Może to nastąpić po przejściu operacji Edytuj i Kontynuuj, gdy punkt przerwania jest przenoszony lub gdy punkt przerwania jest powiązany z plikiem o ścieżce, która nie jest już prawidłowa.  
  
 BPUR_ BREAKPOINT_ERROR  
 Punkt przerwania jest określany jako błąd, po którym jest powiązany. Dzieje się tak w przypadku zarządzanych punktów przerwania, których warunki nie są już prawidłowe.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócone przez metodę [getpowód](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
