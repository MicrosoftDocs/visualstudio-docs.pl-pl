---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 032e7f05ebb1ba8367ffaa7ef1ffbfb974aa0df1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933571"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Zwraca kontekst kodu reprezentujący lokalizację, w przypadku operacji rozwijania stosu wystąpił.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCodeContext`  
 [out] Zwraca [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który reprezentuje lokalizacji kontekst kodu, jeśli wystąpił podczas odwijania stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Mimo że ta metoda może zwrócić kontekst kodu w lokalizacji po odwijania stosu, go nie musi oznaczać, że odwijania stosu faktycznie mogą występować w bieżącej ramki stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)