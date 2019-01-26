---
title: IDebugExceptionEvent2::GetExceptionDescription | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3182ab0da9c03027a2a884f7eaa6ed9713e9744
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54915886"
---
# <a name="idebugexceptionevent2getexceptiondescription"></a>IDebugExceptionEvent2::GetExceptionDescription
Pobiera zawiera opis wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```csharp  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrDescription`  
 [out] Zwraca zawiera opis wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ciąg zwracany przez tę metodę jest zazwyczaj nazwą wyjątek i jest widoczny w **dane wyjściowe** okna, gdy wystąpi wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)