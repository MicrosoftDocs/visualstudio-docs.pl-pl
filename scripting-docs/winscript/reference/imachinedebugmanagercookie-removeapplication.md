---
title: 'IMachineDebugManagerCookie:: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::RemoveApplication
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d829262245c8c14b83ce4016f103ecae68895bd9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576781"
---
# <a name="imachinedebugmanagercookieremoveapplication"></a>IMachineDebugManagerCookie::RemoveApplication
Usuwa aplikację z listy uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwDebugAppCookie`  
 podczas Plik cookie, który identyfikuje aplikację do debugowania.  
  
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
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [IMachineDebugManagerCookie  interfejsu](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)