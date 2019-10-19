---
title: 'IJsDebugDataTarget:: GetThreadContext — — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577655"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext — Metoda
Pobiera kontekst dla danego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 podczas Wątek działający w procesie docelowym.  
  
 `contextFlags`  
 podczas Określa flagi kontekstu. Jest to takie samo jak pole ContextFlags kontekstu (Aby uzyskać więcej informacji, zobacz Winnt. h, Search for CONTEXT_ALL).  
  
 `contextSize`  
 podczas Rozmiar buforu określony przez pContext.  
  
 `pContext`  
 określoną Odbiera strukturę kontekstu specyficzną dla platformy do buforu określonego przez pContext.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)