---
title: 'IJsDebugProcess:: CreateStackWalker — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70f5d4885abba3d891526723d3ca1f174549c348
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573836"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker — Metoda
Metoda fabryki analizatora stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 podczas Identyfikator wątku.  
  
 `ppStackWalker`  
 określoną Nowy obiekt analizatora stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca E_JsDEBUG_UNKNOWN_THREAD, jeśli wątek nie ma w nim języka JavaScript. Tę metodę można wywołać tylko w czasie, gdy proces docelowy został zatrzymany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugProcess, interfejs](../../winscript/reference/ijsdebugprocess-interface.md)