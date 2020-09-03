---
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9faacd80b036282a088b006a15eb9500e8606c5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196026"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Informuje aparat debugowania (DE), że określony program został nietypowym zakończony i że DE powinien czyścić wszystkie odwołania do programu i wysyłać zdarzenie zniszczenia programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProgram`  
 podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program, który został nietypowym zakończony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu tej metody, a następnie wysyła zdarzenie [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) z powrotem do Menedżera debugowania sesji (SDM).  
  
 Ta metoda nie jest zaimplementowana (zwraca `E_NOTIMPL` ), jeśli nie działa w tym samym procesie co debugowany program. Ta metoda jest implementowana tylko wtedy, gdy nie działa w tym samym procesie co model SDM.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
