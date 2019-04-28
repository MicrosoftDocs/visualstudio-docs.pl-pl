---
title: IActiveScriptSiteDebug32::GetApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992496"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Zwraca obiekt aplikacji debugowania, które są skojarzone z tą lokacją skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 [out] Wskaźnik do obiektu aplikacji debugowania, które są skojarzone z lokacją skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie obsługuje bezpośrednio debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 `GetApplication` Metoda oferuje hosta inteligentnego zdefiniować obiekt aplikacji, do której należy każdego skryptu. Aparaty skryptów powinien próbować wywołać tę metodę w celu ich zawierającego aplikacji i zastosuje poważniejsze `IProcessDebugManager::GetDefaultApplication` w przypadku niepowodzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteDebug32 Interface](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)