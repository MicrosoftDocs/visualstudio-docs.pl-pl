---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ccf980fb3d5b357b6211674ca8b99132d81fae1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041012"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Określa, czy aparat debugowania (DE) obsługuje możliwość przekazywania ten wyjątek do debugowanego po wznowieniu działania wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca albo `S_OK` (wyjątek może być przekazywany do program) lub `S_FALSE` (wyjątek nie mogą być przekazywane).  
  
## <a name="remarks"></a>Uwagi  
 DE musi mieć domyślnej akcji do przekazania do debugowany program. IDE może zostać wyświetlony [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) zdarzenia i wywołania [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody bez wywoływania `CanPassToDebuggee` metody. W związku z tym DE powinien mieć przypadek domyślny, przekazywania wyjątek, czy nie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)