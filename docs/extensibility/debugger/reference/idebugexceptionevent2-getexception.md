---
title: IDebugExceptionEvent2::GetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6184a6283b6a93143132afdecb737f011794e96c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998173"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Pobiera szczegółowy opis wyjątku, która wywołała zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExceptionInfo`  
 [out w] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) strukturę, która jest wypełniane opis wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [Tylko w języku C++] Obiekt wywołujący jest odpowiedzialny za zwalnianie wszystkie ciągi w [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, a także udostępnia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiektu w strukturze.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)