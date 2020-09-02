---
title: 'IDebugObject:: IsReadOnly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74b55895e440f900e59cd3b517e22dd8a0191414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159095"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, czy ten obiekt jest tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsReadOnly`  
 określoną Zwraca wartość różną od zera ( `TRUE` ), jeśli ten obiekt jest tylko do odczytu; w przeciwnym razie zwraca zero ( `FALSE` ).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu obiektu tylko do odczytu nie można zmienić jego wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
