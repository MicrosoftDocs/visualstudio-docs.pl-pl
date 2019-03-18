---
title: IJsDebugDataTarget::GetThreadContext, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154689"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext — Metoda
Pobiera kontekst dla podanego wątku.  
  
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
 [in] Wątek działający w procesie docelowym.  
  
 `contextFlags`  
 [in] Określa flagi kontekstu. Jest tak samo jak w przypadku pola ContextFlags KONTEKSTU (Aby uzyskać więcej informacji, zobacz plik winnt.h, Szukaj CONTEXT_ALL).  
  
 `contextSize`  
 [in] Rozmiar buforu określony przez pContext.  
  
 `pContext`  
 [out] Odbiera strukturę CONTEXT specyficzną dla platformy do buforu określonego przez pContext.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)