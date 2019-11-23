---
title: 'IDebugDocumentText:: GetDocumentAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetDocumentAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetDocumentAttributes
ms.assetid: 8c544ca1-8db4-4bca-973e-09315d9a0ee5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3a97c42037e5f7439692e3c3185b4194e63dc2a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572159"
---
# <a name="idebugdocumenttextgetdocumentattributes"></a>IDebugDocumentText::GetDocumentAttributes
Zwraca atrybuty dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocumentAttributes(  
   TEXT_DOC_ATTR*  ptextdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ptextdocattr`  
 określoną Atrybuty tekstu dokumentu.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca atrybuty dokumentu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentText  interfejsu](../../winscript/reference/idebugdocumenttext-interface.md)  
 [TEXT_DOC_ATTR, stałe](../../winscript/reference/text-doc-attr-constants.md)