---
title: IProcessDebugManager::CreateApplication | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 10d7f2246b327393a810170f5b133f2885186c3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944806"
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
 [out] Obiekt aplikacji debugowania dla tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt utworzony przez tę metodę nie ma nazwy i nie jest dodawany do uruchamiania listy aplikacji. Użyj `IProcessDebugManager::AddApplication` dodania aplikacji debugowania do listy aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IProcessDebugManager Interface](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)