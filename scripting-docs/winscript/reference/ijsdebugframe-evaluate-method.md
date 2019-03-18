---
title: IJsDebugFrame::Evaluate, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157818"
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