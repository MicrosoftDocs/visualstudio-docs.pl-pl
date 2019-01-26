---
title: IEnumDebugObjects::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c2bb11f09edbc854a021bb917971b38df605dc8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956665"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Ta metoda powoduje zresetowanie wyliczenia do pierwszego elementu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po ta metoda jest wywoływana, następnym wywołaniu [dalej](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) zwraca pierwszy element wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)