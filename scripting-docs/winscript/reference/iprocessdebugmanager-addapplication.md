---
title: 'IProcessDebugManager:: addapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ad8132b9b51efa5f5c2f260e48441e5da64c42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576812"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Dodaje aplikację do listy uruchomionych aplikacji Menedżera debugowania maszyny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Aplikacja do debugowania do dodania do listy uruchomionych aplikacji.  
  
 `pdwAppCookie`  
 określoną Plik cookie służący do usuwania aplikacji z Menedżera debugowania maszyny.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda dodaje aplikację do listy uruchomionych aplikacji w Menedżerze debugowania maszyny.  
  
## <a name="see-also"></a>Zobacz także  
 [IProcessDebugManager  interfejsu](../../winscript/reference/iprocessdebugmanager-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)