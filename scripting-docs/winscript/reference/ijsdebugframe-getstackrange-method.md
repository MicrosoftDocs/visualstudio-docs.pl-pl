---
title: 'IJsDebugFrame:: GetStackRange — — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574039"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange — Metoda
Zwraca bezwzględny zakres adresów logicznej ramki stosu JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 określoną Najbardziej dolny Wskaźnik stosu ramki.  
  
 `pEnd`  
 określoną Największa Górna wartość wskaźnika układarki ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest przydatna w przypadku zszywania ze sobą zebranych śladów stosu z wielu środowisk uruchomieniowych. Wskaźniki Start i End stosu mogą obejmować wiele ramek stosu maszyn fizycznych (dla interpretowanych ramek środowiska uruchomieniowego JavaScript). Rozpocznij > zakończy się, ponieważ stos powiększa się od wysokiego do niskiego adresu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)