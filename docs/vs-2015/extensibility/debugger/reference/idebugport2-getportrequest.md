---
title: IDebugPort2::GetPortRequest | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b41106cc4e7cdfc04bcd1934b5959089d078206
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782881"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera opis portu, który został wcześniej użyty do utworzenia portu (jeśli jest dostępny).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRequest`  
 [out] Zwraca [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) obiekt reprezentujący żądanie, które zostało użyte do utworzenia portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  Zwraca `E_PORT_NO_REQUEST` Jeśli port nie został utworzony przy użyciu [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) port żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
