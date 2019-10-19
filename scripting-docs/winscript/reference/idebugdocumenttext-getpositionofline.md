---
title: 'IDebugDocumentText:: GetPositionOfLine | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfLine
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf4add99ac41440e6f4daa491b72166e97b5ba5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572102"
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
Zwraca pozycję znaku odpowiadającą pierwszemu znakowi wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cLineNumber`  
 podczas Numer wiersza.  
  
 `pcCharacterPosition`  
 określoną Pozycja znaku w dokumencie początku wiersza `cLineNumber`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pozycję znaku odpowiadającą pierwszemu znakowi wiersza.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)