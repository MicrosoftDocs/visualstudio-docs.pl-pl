---
title: 'IRemoteDebugApplication:: ConnectDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed0ddeffd55475e1be4c9fab1e567d61a4b6654
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572320"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Łączy debuger z tą aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pad`  
 podczas Debuger do dołączenia do tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Debuger jest już połączony z tą aplikacją.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja może mieć tylko jeden debuger połączony w danym momencie. Ta metoda kończy się niepowodzeniem, Jeśli debuger jest już połączony.  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [IRemoteDebugApplication, interfejs](../../winscript/reference/iremotedebugapplication-interface.md)