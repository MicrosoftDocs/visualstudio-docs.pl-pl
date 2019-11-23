---
title: 'IMachineDebugManager:: addapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573966"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Dodaje aplikację do listy uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Aplikacja na listę uruchomionych aplikacji.  
  
 `pdwAppCookie`  
 określoną Plik cookie służący do usuwania aplikacji z Menedżera debugowania maszyny.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez Menedżera debugowania procesów za każdym razem, gdy `IProcessDebugManager::AddApplication` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także  
 [IMachineDebugManager  interfejsu](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IMachineDebugManager:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)