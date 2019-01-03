---
title: Idiastackframe::get_registervalue — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0bb8f3a10bebbdaff489b2b628af2e1228fdf40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985803"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Pobiera wartość określonego rejestru, ponieważ przechowywane w ramce stosu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `registerIndex`  
 [in] Jedną z [cv_hreg_e — wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md) wartości wyliczenia.  
  
 `pRetVal`  
 [out] Wartość przechowywana w rejestrze.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e, wyliczenie](../../debugger/debug-interface-access/cv-hreg-e.md)