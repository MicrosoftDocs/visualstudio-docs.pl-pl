---
title: IJsDebugProcess::CreateBreakPoint, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557975"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint — Metoda
Ustawia punkt przerwania w położeniu określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `documentId`  
 [in] Wskaźnik IDebugDocumentText.  
  
 `characterOffset`  
 [in] Znak przesunięcia od początku pliku.  
  
 `characterCount`  
 [in] Długość tekstu dokumentu, w którym można wstawić punkt przerwania.  
  
 `isEnabled`  
 [in] Określa, czy punkt przerwania jest włączony.  
  
 `ppDebugBreakPoint`  
 [out] Obiekt reprezentujący punkt przerwania, który został utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugProcess, interfejs](../../winscript/reference/ijsdebugprocess-interface.md)