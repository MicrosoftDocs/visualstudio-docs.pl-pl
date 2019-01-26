---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67796e647bd59fbf0d6f6bcca076d12154d08b78
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917903"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Ta metoda pobiera informacje żądania punktu przerwania, opisujący tego żądania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinacja flag z [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) wyliczenie, które określają, które pola `pBPRequestInfo` mają być wypełnione.  
  
 `bBPRequestInfo`  
 [out] [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury do wypełnienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Więcej informacji można znaleźć w tym żądaniu nie jest zwracana z [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)