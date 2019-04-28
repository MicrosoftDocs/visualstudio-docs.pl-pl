---
title: IDebugEngine3::SetEngineGuid | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14c1ad0e659df29c462d145e8c98166079857275
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875254"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda ustawia aparat debugowania (DE) `GUID`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidEngine`  
 [in] `GUID` silnika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
