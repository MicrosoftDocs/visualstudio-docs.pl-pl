---
title: IDebugProgram2::GetProcess | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148656"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Uzyskaj procesu, który tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProcess`  
 [out] Zwraca [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejs, który reprezentuje proces.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 O ile nie implementuje aparat debugowania (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfejsu, DE implementacja tej metody zawsze powinna zwrócić `E_NOTIMPL` DE nie może ustalić, który proces jest uruchomiony w i dlatego nie może spełnia implementacja tej metody.  
  
 Implementowanie `IDebugEngineLaunch2` interfejs oznacza, że Niemcy musi wiedzieć, jak można utworzyć procesu; w związku z tym, DE implementacji [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu jest w stanie wiedzieć, jakie procesy jest uruchomiony w.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
