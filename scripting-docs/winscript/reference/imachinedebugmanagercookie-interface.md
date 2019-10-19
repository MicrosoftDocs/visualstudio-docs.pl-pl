---
title: Interfejs IMachineDebugManagerCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573882"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfejs IMachineDebugManagerCookie
Podobnie jak interfejs `IMachineDebugManager`, interfejs `IMachineDebugManagerCookie` obsługuje debugowanie plików cookie.  
  
 Ten interfejs (wraz z interfejsem `IDebugCookie`) umożliwia uruchamianie skryptów w procesie debugera skryptów bez konieczności, aby debuger śledzi te skrypty.  
  
 Debuger skryptów wywołuje metodę `IDebugCookie::SetDebugCookie` w Menedżerze debugowania procesów (PDM). Następnie PDM wysyła ten plik cookie wraz z dowolnym żądaniem dodania lub usunięcia aplikacji skryptowej do lub z Menedżera debugowania maszyn (MDM) przy użyciu metod interfejsu `IMachineDebugManagerCookie`. Usługa MDM powiadamia następnie każdy debuger zmiany, z wyjątkiem tego, który ma ten plik cookie.  
  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `IMachineDebugManagerCookie` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Dodaje aplikację do listy uruchomionych aplikacji.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Zwraca moduł wyliczający bieżącej listy uruchomionych aplikacji.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Usuwa aplikację z listy uruchomionych aplikacji.|  
  
## <a name="see-also"></a>Zobacz także  
 [IMachineDebugManager   interfejsu](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IDebugCookie, interfejs](../../winscript/reference/idebugcookie-interface.md)