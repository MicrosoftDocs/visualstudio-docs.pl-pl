---
title: 'IActiveScriptSiteDebug:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570126"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie obsługuje bezpośrednio debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetApplication` umożliwia inteligentnemu hostowi zdefiniowanie obiektu aplikacji, do którego należy każdy skrypt. Aparaty skryptów powinni próbować wywołać tę metodę, aby dokończyć aplikacje i `IProcessDebugManager::GetDefaultApplication`, jeśli to się nie powiedzie.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteDebug  interfejsu](../../winscript/reference/iactivescriptsitedebug-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)