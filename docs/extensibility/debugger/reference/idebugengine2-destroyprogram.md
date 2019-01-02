---
title: IDebugEngine2::DestroyProgram | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b026155fb6aa514621dd2da0f9a037ded066e808
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967670"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informuje aparat debugowania (DE) program określony został zakończony nietypowo i DE należy wyczyścić wszystkie odwołania do programu i zdarzenie niszczenia send programem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, który ma nietypowo została przerwana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po ta metoda jest wywoływana, DE kliencka wysyła [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Menedżer debugowania sesji (SDM) zdarzenia.  
  
 Ta metoda nie jest zaimplementowana (zwraca `E_NOTIMPL`) Jeśli DE działa w tym samym procesie co debugowanego programu. Ta metoda jest implementowana tylko wtedy, gdy DE działa w tym samym procesie co SDM.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)