---
title: IDebugObject::IsEqual | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b801594c4e3dd1edb04ae0d29dfe6c814fa4a094
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954452"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Porównuje obiekt z tym obiektem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący obiekt do porównania.  
  
 `pfIsEqual`  
 [out] Zwraca wartość różna od zera (`TRUE`) Jeśli wartości obiekty są równe; w przeciwnym razie, zwraca wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj ta metoda może porównać adresy wartości reprezentowanej przez `pObject` parametr i to [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt; Jeśli adresy są takie same, a następnie obiekty mogą być uważane za równe.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)