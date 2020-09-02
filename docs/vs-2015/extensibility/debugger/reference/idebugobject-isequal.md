---
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159121"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porównuje obiekt z tym obiektem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 podczas Obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący obiekt, do którego ma zostać wykonane porównanie.  
  
 `pfIsEqual`  
 określoną Zwraca wartość różną od zera ( `TRUE` ), jeśli wartości obiektów są równe; w przeciwnym razie zwraca zero ( `FALSE` ).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj ta metoda umożliwia porównanie adresów wartości reprezentowanych przez `pObject` parametr i ten obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; Jeśli adresy są równe, obiekty można traktować jako równe.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
