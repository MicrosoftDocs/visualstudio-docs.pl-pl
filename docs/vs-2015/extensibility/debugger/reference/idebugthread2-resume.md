---
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152992"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wznawia wykonywanie wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSuspendCount`  
 określoną Zwraca liczbę wstrzymań po operacji wznawiania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każde wywołanie tej metody zmniejsza liczbę wstrzymania do momentu, aż osiągnie wartość 0, a wykonanie jest ostatecznie wznawiane. Ta liczba wstrzymań zostanie wyświetlona w oknie Debugowanie **wątków** .  
  
 Dla każdego wywołania tej metody musi istnieć poprzednie wywołanie metody [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Liczba wstrzymań określa, ile razy Metoda została wywołana do tej `IDebugThread2::Suspend` pory.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
