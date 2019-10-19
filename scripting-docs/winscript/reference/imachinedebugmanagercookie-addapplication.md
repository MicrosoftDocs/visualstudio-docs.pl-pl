---
title: 'IMachineDebugManagerCookie:: addapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da436308c71a66d3070d42128d8da03ae88d2935
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573913"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Dodaje aplikację do listy uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Aplikacja na listę uruchomionych aplikacji.  
  
 `dwDebugAppCookie`  
 podczas Plik cookie, który identyfikuje aplikację do debugowania.  
  
 `pdwAppCookie`  
 określoną Plik cookie służący do usuwania aplikacji z Menedżera debugowania maszyny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez Menedżera debugowania procesów za każdym razem, gdy `IProcessDebugManager::AddApplication` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także  
 [IMachineDebugManagerCookie   interfejsu](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
 [IMachineDebugManagerCookie:: RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)