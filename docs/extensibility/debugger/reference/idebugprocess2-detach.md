---
title: IDebugProcess2::Detach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 747430b837cf682e35f5973ea35d36e72484fb3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988071"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Odłącza debuger z tego procesu przez odłączenie wszystkich programów w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie programy i proces nadal działa, ale nie są już częścią sesji debugowania. Operacja odłączenia po pełne, nie ma więcej debugowania, który będą wysyłane zdarzenia dla tego procesu (i jego programów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)