---
title: IJsDebugFrame::GetStackRange, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090288"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange — Metoda
Zwraca bezwzględny zakres adresów dla logicznej ramki stosu JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Dolny wskaźnika stosu ramki.  
  
 `pEnd`  
 [out] Najważniejsze górna większa część wskaźnika ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest przydatna do zszywania przeplotem śladów stosu zebranych z wielu modułów wykonawczych. Rozpoczęcia, zakończenia wskaźniki stosu może obejmować wiele ramek stosu maszyn fizycznych (dla interpretowanych ramek środowiska wykonawczego języka JavaScript). Start > kończy gdy stos rośnie od największej do niskiego adresu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)