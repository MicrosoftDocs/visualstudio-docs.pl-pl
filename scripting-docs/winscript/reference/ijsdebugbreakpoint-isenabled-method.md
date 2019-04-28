---
title: IJsDebugBreakPoint::IsEnabled, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99df17f73896b4dd04481315b04e1672a56285a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583096"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled — Metoda
Określa, czy punkt przerwania jest włączony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIsEnabled`  
 [out] Zwraca wartość PRAWDA, jeśli punkt przerwania jest włączony; w przeciwnym razie zwraca wartość false.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość E_UNEXPECTED, jeśli wywołano usunięty punkt przerwania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugBreakPoint, interfejs](../../winscript/reference/ijsdebugbreakpoint-interface.md)