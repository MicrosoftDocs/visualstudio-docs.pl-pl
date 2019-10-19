---
title: 'IJsDebugFrame:: GetDocumentPositionWithName — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575122"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName — Metoda
Zwraca bieżącą pozycję ramki stosu w dokumencie na poziomie użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentName`  
 określoną Dla skryptów statycznych, adres URL do dokumentu. W przypadku skryptów dynamicznych jest zwracana nazwa zawierająca typ skryptu (na przykład kod oceny, kod funkcji itp.).  
  
 `pLine`  
 [out] 1 pozycja wiersza w dokumencie.  
  
 `pColumn`  
 [out] 1 pozycja wiersza w dokumencie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)