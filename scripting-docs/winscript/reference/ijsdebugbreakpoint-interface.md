---
title: IJsDebugBreakPoint, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14823baeb999ad24aabef9b2b55b59a7b5d08c71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583109"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint — Interfejs
Reprezentuje punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete, metoda](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Usuwa punkt przerwania.|  
|[IJsDebugBreakPoint::Disable, metoda](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Wyłącza punkt przerwania.|  
|[IJsDebugBreakPoint::Enable, metoda](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Włącza punkt przerwania.|  
|[IJsDebugBreakPoint::GetDocumentPosition, metoda](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Zwraca pozycję instrukcji, w której powiązany został punkt przerwania.|  
|[IJsDebugBreakPoint::IsEnabled, metoda](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Określa, czy punkt przerwania jest włączony.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsów skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)