---
title: 'IMachineDebugManager:: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87951e55a7cfcfef1a366f79c380948c7651ed12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573936"
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
Usuwa aplikację z listy uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppCookie`  
 podczas Plik cookie podany, gdy aplikacja została dodana do listy aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez Menedżera debugowania procesów za każdym razem, gdy `IProcessDebugManager::RemoveApplication` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także  
 [IMachineDebugManager:: addapplication](../../winscript/reference/imachinedebugmanager-addapplication.md)   
 [IMachineDebugManager  interfejsu](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)