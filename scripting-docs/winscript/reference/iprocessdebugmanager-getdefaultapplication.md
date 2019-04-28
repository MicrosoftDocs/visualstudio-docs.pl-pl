---
title: IProcessDebugManager::GetDefaultApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fec84a60863b426f2f65c26e2375262b109d635
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953975"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Zwraca domyślny obiekt aplikacji dla bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDefaultApplication(  
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
 Ta metoda tworzy nowy obiekt debugowania aplikacji i dodaje go do uruchamiania listę aplikacji, jeśli to konieczne.  
  
 Aparaty języka należy używać aplikacji określonej przez `GetDefaultApplication` metody, jeśli są uruchomione na hoście, który nie zapewnia aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IProcessDebugManager, interfejs](../../winscript/reference/iprocessdebugmanager-interface.md)