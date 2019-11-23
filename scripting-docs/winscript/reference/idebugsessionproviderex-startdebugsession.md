---
title: 'IDebugSessionProviderEx: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfe26265d56b2179feeac2a9802940258074b1c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574295"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Inicjuje sesję debugowania z określoną aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 podczas Określa aplikację do debugowania.  
  
 `fQuery`  
 podczas Wartość true wskazuje zapytanie.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje sesję debugowania z określoną aplikacją. Debuger powinien wywołać `IRemoteDebugApplication::ConnectDebugger` przed powrotem z tego wywołania.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugSessionProviderEx  interfejsu](../../winscript/reference/idebugsessionproviderex-interface.md)  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)