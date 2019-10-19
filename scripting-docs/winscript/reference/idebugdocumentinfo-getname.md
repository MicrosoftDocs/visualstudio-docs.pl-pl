---
title: 'IDebugDocumentInfo:: GetName | Microsoft Docs'
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
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570958"
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
 podczas Typ nazwy dokumentu do zwrócenia.  
  
 `pbstrName`  
 określoną Ciąg zawierający nazwę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Określona nazwa dokumentu jest nieznana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca określoną nazwę dokumentu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentInfo   interfejsu](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [DOCUMENTNAMETYPE, wyliczenie](../../winscript/reference/documentnametype-enumeration.md)