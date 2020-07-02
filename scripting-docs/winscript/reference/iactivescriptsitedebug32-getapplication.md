---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835631"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Zwraca obiekt aplikacji debugowania skojarzony z tą lokacją skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 określoną Wskaźnik do obiektu aplikacji debugowania skojarzonego z witryną skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT` . Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie obsługuje bezpośrednio debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 `GetApplication`Metoda umożliwia inteligentnemu hostowi zdefiniowanie obiektu aplikacji, do którego należy każdy skrypt. Aparaty skryptów powinni próbować wywołać tę metodę w celu uzyskania aplikacji zawierających aplikacje i dołączenia do `IProcessDebugManager::GetDefaultApplication` tego, czy to się nie powiedzie.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteDebug32, interfejs](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)