---
title: IDebugThread2::SetThreadName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6a427eaa8677cdf1cdf1ba9b89c6bee98a2e1b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752943"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa nazwę wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```csharp  
int SetThreadName (   
   string pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [in] Nazwa wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać nazwę wątku, należy wywołać [getname —](../../../extensibility/debugger/reference/idebugthread2-getname.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)
