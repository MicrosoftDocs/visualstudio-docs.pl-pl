---
title: IDebugDocumentHelper::Init | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b399f51fc042aa1ed297ab30a7bf2c9bc4befca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000989"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` Metoda inicjuje pomocnika dokumentu debugowania z nazwą i początkowa atrybuty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 [in] Debugowanie aplikacji skojarzone z tym dokumentem.  
  
 `pszShortName`  
 [in] Ciąg zakończony znakiem null, zawierającego krótką nazwę dokumentu.  
  
 `pszLongName`  
 [in] Ciąg zakończony wartością null zawierający długa nazwa dokumentu.  
  
 `docAttr`  
 [in] Określa atrybuty dokumentu tekstowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje pomocnika dokumentu debugowania z nazwą i początkowa atrybuty.  
  
 Ten dokument nie jest wyświetlana w drzewie, dopóki `IDebugDocumentHelper::Attach` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR, stałe](../../winscript/reference/text-doc-attr-constants.md)