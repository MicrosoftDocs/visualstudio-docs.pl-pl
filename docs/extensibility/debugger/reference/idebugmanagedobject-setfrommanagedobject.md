---
title: IDebugManagedObject::SetFromManagedObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a760bb14ea1749e359b5f9deacb6e5918a42423f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974399"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Ustawia wartość wystąpienia obiektu klasy wartości z instancji klasy wartości podać jako parametr.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pManagedObject`  
 [in] Interfejs, który reprezentuje zarządzanego obiektu zawierającego nowe wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda służy do zmiany obiektu zarządzanego, reprezentowane przez [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)