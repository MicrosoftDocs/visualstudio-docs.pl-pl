---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148638"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wykonuje program debugera. Wątek jest zwracany w celu udostępnienia informacji debugera, na których wątku użytkownik przegląda podczas wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy różne sposoby, aby debuger mógł wznowić wykonywanie po zatrzymywaniu:  
  
- Wykonaj: anuluje wszystkie poprzednie kroki i uruchamiaj do następnego punktu przerwania i tak dalej.  
  
- Krok: Anuluj dowolny stary krok i uruchom do momentu zakończenia nowego kroku.  
  
- Kontynuuj: ponownie uruchom i pozostaw wszystkie starsze, aktywne.  
  
  Wątek przeszedł do `ExecuteOnThread` jest przydatny podczas wybierania kroku do anulowania. Jeśli nie znasz wątku, uruchomienie polecenie Execute powoduje anulowanie wszystkich kroków. Mając wiedzę na temat wątku, wystarczy anulować krok w aktywnym wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonana](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
