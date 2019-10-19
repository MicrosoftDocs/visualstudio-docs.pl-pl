---
title: 'IJsDebugFrame:: GetDocumentPositionWithId — Metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573860"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId — Metoda
Zwraca bieżącą pozycję ramki stosu w dokumencie na poziomie użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentId`  
 określoną Unikatowy identyfikator dokumentu źródłowego (wskaźnik do IDebugDocumentText).  
  
 `pCharacterOffset`  
 określoną Przesunięcie znaku na podstawie zera od początku skryptu.  
  
 `pStatementCharCount`  
 określoną Wyrażona w znakach długość bieżącej instrukcji, która zaczyna się od znaku * pCharacterOffset.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Jscript9diag. h  
  
## <a name="see-also"></a>Zobacz także  
 [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)