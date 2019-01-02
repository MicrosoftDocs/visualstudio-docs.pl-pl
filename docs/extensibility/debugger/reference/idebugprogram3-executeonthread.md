---
title: IDebugProgram3::ExecuteOnThread | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbb2650fc2c001e57de7b1820cff238c8963e8cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889439"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Wykonuje program debugera. Wątek jest zwracany do przedstawienia informacji debugera, na który wątek użytkownika jest wyświetlana podczas wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy różne sposoby wznowić wykonywanie po zatrzymaniu debugera:  
  
- Należy wykonać: Anuluj wszelkie poprzedniego kroku i uruchamianie aż do następnego punktu przerwania i tak dalej.  
  
- Krok: Anuluj którykolwiek z kroków stary i uruchomić do momentu ukończenia nowy krok.  
  
- Kontynuuj: Uruchom ponownie i pozostawianie aktywnej stare którykolwiek z kroków.  
  
  Wątek jest przekazywany do `ExecuteOnThread` jest przydatne w przypadku podejmowania decyzji, który krok, aby anulować. Jeśli nie znasz wątek systemu wykonaj anuluje wszystkie kroki. Przy zachowaniu wiedzy o wątku wystarczy anulować kroku na aktywnym wątkiem.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)