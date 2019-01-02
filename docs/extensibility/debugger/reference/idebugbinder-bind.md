---
title: IDebugBinder::Bind | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72beca1ede38b310e34edfaabce0ee02e8fb52cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865209"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Ta metoda pobiera kontekst pamięci lub obiekt, który zawiera bieżącą wartość symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pContainer`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zawierający odwołuje się element podrzędny `pField`.  
  
 `pField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący symbol.  
  
 `ppObject`  
 [out] Zwraca `IDebugObject` reprezentujący wystąpienie symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)