---
title: IDebugObject::IsNullReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021d7d8b7c1203aab68a93efe8581f66dec698f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975273"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Sprawdza, czy ten obiekt jest odwołanie o wartości null.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsNull`  
 [out] Zwraca wartość różna od zera (`TRUE`) Jeśli ten obiekt jest odwołanie o wartości null; w przeciwnym razie zwraca wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie o wartości null oznacza obiekt, który nie został przypisany do pustego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)