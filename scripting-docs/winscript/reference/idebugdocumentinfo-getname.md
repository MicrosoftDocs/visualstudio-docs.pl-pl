---
title: IDebugDocumentInfo::GetName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9975563c27b986190fbd2731c3f36b1e32719c0b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160329"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Zwraca nazwę określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnt`  
 [in] Typ nazwy dokumentu do zwrócenia.  
  
 `pbstrName`  
 [out] Ciąg zawierający nazwę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Określona nazwa dokumentu nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca nazwę określonego dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE, wyliczenie](../../winscript/reference/documentnametype-enumeration.md)