---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
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
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572198"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32:: GetApplication
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
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie obsługuje bezpośrednio debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetApplication` umożliwia inteligentnemu hostowi zdefiniowanie obiektu aplikacji, do którego należy każdy skrypt. Aparaty skryptów powinni próbować wywołać tę metodę, aby dokończyć aplikacje i `IProcessDebugManager::GetDefaultApplication`, jeśli to się nie powiedzie.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteDebug32   interfejsu](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)