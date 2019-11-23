---
title: 'IProcessDebugManager:: isapplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateApplication
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5be4c67168a43ec405a6d4ed857b9772fdddd1e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577110"
---
# <a name="iprocessdebugmanagercreateapplication"></a>IProcessDebugManager::CreateApplication
Tworzy nowy obiekt aplikacji debugowania dla tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 określoną Obiekt aplikacji debugowania dla tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt utworzony przez tę metodę nie ma nazwy i nie został dodany do listy uruchomionych aplikacji. Użyj `IProcessDebugManager::AddApplication`, aby dodać aplikację debugowania do listy aplikacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IProcessDebugManager  interfejsu](../../winscript/reference/iprocessdebugmanager-interface.md)  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)