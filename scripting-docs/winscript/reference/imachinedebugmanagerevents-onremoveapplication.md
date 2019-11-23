---
title: 'IMachineDebugManagerEvents:: onRemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onRemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onRemoveApplication
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b50d91a75a8f251ad04b456b179fdd0ba0d1dc32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571475"
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Obsługuje zdarzenie po usunięciu aplikacji z listy uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Aplikacja, która została usunięta z listy uruchomionych aplikacji.  
  
 `dwAppCookie`  
 podczas Plik cookie podany podczas dodawania aplikacji z listy aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda oznacza, że aplikacja została usunięta z listy uruchomionych aplikacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IMachineDebugManagerEvents  interfejsu](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)