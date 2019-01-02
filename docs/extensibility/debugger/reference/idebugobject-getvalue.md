---
title: IDebugObject::GetValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98dd9208fe28fd433a201e4d59f8dcc0af694b08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914160"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Pobiera wartość obiektu jako serię kolejnych bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pValue`  
 [out w] Tablica, która jest wypełniane serię kolejnych bajtów reprezentujący wartość obiektu.  
  
 `nSize`  
 [in] Maksymalna liczba bajtów do pobrania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Pobierz całkowitą liczbę bajtów wartości, które mogą być pobierane przez wywołanie metody [getsize —](../../../extensibility/debugger/reference/idebugobject-getsize.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)