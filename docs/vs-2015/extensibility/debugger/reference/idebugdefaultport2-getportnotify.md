---
title: IDebugDefaultPort2::GetPortNotify | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8684b04b401d9b0a6f068a6425e0e82a4e348f2e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800552"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu dla tego portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppPortNotify`  
 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle `QueryInterface` metoda jest wywoływana w implementacji obiektu [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejs w celu uzyskania [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu. Istnieją jednak okoliczności, w których zaimplementowano żądanego interfejsu na inny obiekt. Ta metoda polega na schowaniu tych sytuacji i zwraca `IDebugPortNotify2` interfejs z najbardziej odpowiedniego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)

