---
title: 'IJsDebugFrame:: Oceń metodę | Microsoft Docs'
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573494"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate — Metoda
Oceń wyrażenie w kontekście tej ramki stosu.  
  
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
 podczas Wyrażenie, które ma zostać obliczone.  
  
 `ppDebugProperty`  
 określoną Obiekt reprezentujący przeglądarkę właściwości.  
  
 `pError`  
 określoną Komunikat o błędzie, jeśli wystąpi błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca następujące wartości: S_OK: Ocena powiedzie się, * ppDebugProperty zawiera wynik oceny. S_FALSE: Obliczanie zgłasza błąd (lub operacja oceny nie jest obsługiwana), \*pError zawiera komunikat o błędzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)