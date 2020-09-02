---
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a610cd5c947d77048e86b31c92298f6cc18607d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193420"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Niszczy unikatowy identyfikator skojarzony z tą właściwością, co oznacza, że obiekt wywołujący nie dba już identyfikować tej właściwości jednoznacznie ze wszystkich innych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat debugowania nie musi obsługiwać unikatowych identyfikatorów dla właściwości (ponieważ już jednoznacznie śledzi je wewnętrznie), może po prostu zwrócić się `E_NOTIMPL` do tej metody.  
  
 Unikatowe identyfikatory są tworzone za pomocą wywołania metody " [Xmlobjectid](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) ", gdy obiekt wywołujący chce, aby upewnić się, że ta właściwość została jednoznacznie zidentyfikowana wśród wszystkich innych właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
