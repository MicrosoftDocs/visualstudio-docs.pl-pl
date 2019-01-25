---
title: IDebugThread2::CanSetNextStatement | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3e98603a39d820b5565836bd2620f8a27def76f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752438"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Określa, czy bieżący wskaźnik instrukcji można ustawić ramkę stosu w danym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 Zarezerwowane dla przyszłego użytku; Ustaw wartość null. Jeśli jest to wartość null, należy użyć bieżącej ramki stosu.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który opisuje lokalizacji kodu, który ma zostać wykonany i kontekst.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwraca `S_OK`, następnie wywołać [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) metodę, aby faktycznie Ustaw następną instrukcję.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
