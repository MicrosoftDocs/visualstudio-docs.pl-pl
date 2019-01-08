---
title: IJsDebugFrame::Evaluate, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091926"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate — Metoda
Ocena wyrażenia w kontekście tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExpressionText`  
 [in] Wyrażenie do oceny.  
  
 `ppDebugProperty`  
 [out] Obiekt reprezentujący przeglądarkę właściwości.  
  
 `pError`  
 [out] Komunikat o błędzie, jeśli wystąpi błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca następujące czynności: S_OK: Oceny zakończy się powodzeniem, * ppDebugProperty zawiera wynik oceny. S_FALSE: Ocena zgłasza błąd (lub operacja oceny nie jest obsługiwana) \*pError zawiera komunikat o błędzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)