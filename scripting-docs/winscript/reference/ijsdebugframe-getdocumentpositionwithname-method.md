---
title: IJsDebugFrame::GetDocumentPositionWithName, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4d3b909f3a3ebc672bf6d0a014b519de685b1677
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558156"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName — Metoda
Zwraca bieżącą pozycję ramki stosu w obrębie dokumentu poziomie użytkownika.  
  
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
 [out] Dla statycznych skryptów URL do dokumentu. Dla dynamicznych skryptów zwracana jest nazwa zawierająca typ skryptu (na przykład kod ewaluacyjny, kod funkcji itp.).  
  
 `pLine`  
 [out] pozycja 1 na podstawie wiersza w dokumencie.  
  
 `pColumn`  
 [out] pozycja 1 na podstawie wiersza w dokumencie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)