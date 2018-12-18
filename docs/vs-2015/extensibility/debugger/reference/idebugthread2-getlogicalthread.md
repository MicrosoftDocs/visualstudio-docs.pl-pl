---
title: IDebugThread2::GetLogicalThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e157ab220972579aa1a8a78e8094b5589de8ff28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810207"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aparaty debugowania nie należy implementować tej metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 [in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt, który reprezentuje ramkę stosu.  
  
 `ppLogicalThread`  
 [out] Zwraca `IDebugLogicalThread2` interfejs, który reprezentuje skojarzony wątek logiczne. Implementacja aparatu debugowania, należy Ustaw tę opcję na wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Debuguj aparat implementacje zwracana zawsze `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

