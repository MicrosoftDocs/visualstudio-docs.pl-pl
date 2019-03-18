---
title: IDebugDocumentText::GetPositionOfLine | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4cfcfc771c49abbf837f4db898936e478cda2194
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159351"
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
Zwraca pozycję znaku odpowiadający pierwszego znaku wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cLineNumber`  
 [in] Numer wiersza.  
  
 `pcCharacterPosition`  
 [out] Pozycja znaku w dokumencie początku wiersza `cLineNumber`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pozycję znaku, w pierwszym znaku, linii.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)