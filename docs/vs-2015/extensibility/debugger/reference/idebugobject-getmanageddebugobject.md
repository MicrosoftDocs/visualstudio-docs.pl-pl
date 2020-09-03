---
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162471"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy kopię zarządzanego obiektu w przestrzeni adresowej aparatu debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 określoną Zwraca obiekt [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) reprezentujący nowo utworzony obiekt zarządzany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nie reprezentuje wystąpienia klasy wartości zarządzanej.  
  
## <a name="remarks"></a>Uwagi  
 Ten obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) musi reprezentować wystąpienie klasy wartości zarządzanej, takie jak `System.Decimal` wystąpienie. Posiadanie kopii lokalnej powoduje wyeliminowanie narzutu na wywołanie funkcji [szacowania](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
