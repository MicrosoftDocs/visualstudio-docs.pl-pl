---
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163812"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do debugowanego programu podczas wznawiania wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca albo `S_OK` (wyjątek można przesłać do programu) lub `S_FALSE` (nie można przesłać wyjątku).  
  
## <a name="remarks"></a>Uwagi  
 Element DE musi mieć domyślną akcję do przekazania do debugowanego obiektu. IDE może odebrać zdarzenie [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) i wywołać metodę [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) bez wywoływania `CanPassToDebuggee` metody. W związku z tym, DE powinien mieć domyślny przypadek do przekazania wyjątku w lub nie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
