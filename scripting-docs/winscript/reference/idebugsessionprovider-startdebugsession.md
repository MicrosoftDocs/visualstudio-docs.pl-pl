---
title: 'IDebugSessionProvider:: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProvider.StartDebugSession
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugSessionProvider::StartDebugSession
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fc4bdade94401d5fc7b5756eb61fddd166fe49b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574906"
---
# <a name="idebugsessionproviderstartdebugsession"></a>IDebugSessionProvider::StartDebugSession
Inicjuje sesję debugowania z określoną aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Określa aplikację do debugowania.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje sesję debugowania z określoną aplikacją. Debuger powinien wywołać `IRemoteDebugApplication::ConnectDebugger` przed powrotem z tego wywołania.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugSessionProvider  interfejsu](../../winscript/reference/idebugsessionprovider-interface.md)  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)