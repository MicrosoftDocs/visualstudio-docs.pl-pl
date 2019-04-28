---
title: IDebugApplication::RemoveStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1462ff1382f3ccb844ccc98c6e6eec676a86c669
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990775"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Usuwa dostawcę moduł wyliczający ramek stosu z tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 [in] Zwrócone przez plik cookie `AddStackFrameSniffer` metody podczas dodawania dostawcy moduł wyliczający ramek stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `RemoveStackFrameSniffer` Metoda usuwa dostawcę moduł wyliczający ramek stosu z tej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugStackFrameSniffer, interfejs](../../winscript/reference/idebugstackframesniffer-interface.md)