---
title: IMachineDebugManagerCookie Interface | Microsoft Docs
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
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151053"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfejs IMachineDebugManagerCookie
Podobnie jak `IMachineDebugManager` interfejsu `IMachineDebugManagerCookie` interfejs obsługuje pliki cookie debugowania.  
  
 Ten interfejs (wraz z `IDebugCookie` interfejsu) Zezwalaj na uruchamianie skryptów w procesie debugera skryptów bez konieczności zachować informacje o tych skryptów debugera.  
  
 Wywołuje debugera skryptów `IDebugCookie::SetDebugCookie` metody na proces debugowania Menedżera (menedżerów PDM). Menedżerów PDM wysyła następnie ten plik cookie wraz z każdego żądania, aby dodać lub usunąć aplikację skryptu do lub z maszyny debugowania Manager (MDM), przy użyciu metody `IMachineDebugManagerCookie` interfejsu. Zarządzania urządzeniami Przenośnymi następnie powiadamia użytkownika co debuger zmian, z wyjątkiem jednego, który ma tego pliku cookie.  
  
 Oprócz metod odziedziczone `IUnknown`, `IMachineDebugManagerCookie` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Dodaje aplikację do uruchamiania listy aplikacji.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Zwraca moduł wyliczający bieżącą listę uruchomionych aplikacji.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Usuwa aplikację z uruchomionych listy aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie, interfejs](../../winscript/reference/idebugcookie-interface.md)