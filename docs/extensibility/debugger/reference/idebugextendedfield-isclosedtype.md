---
title: IDebugExtendedField::IsClosedType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b3c1badda9933c97761d3bf209380ba0c822b7f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002798"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Określa, czy pole reprezentuje zamkniętego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to pole jest zamkniętego typu, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)