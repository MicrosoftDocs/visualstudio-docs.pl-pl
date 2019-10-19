---
title: 'IDebugDocumentHelper:: init | Microsoft Docs'
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
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576864"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Metoda `Init` inicjuje pomocnika dokumentu debugowania z nazwą i początkowymi atrybutami.  
  
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
 podczas Aplikacja do debugowania skojarzona z tym dokumentem.  
  
 `pszShortName`  
 podczas Ciąg zakończony znakiem null zawierający krótką nazwę dokumentu.  
  
 `pszLongName`  
 podczas Ciąg zakończony znakiem null zawierający długą nazwę dokumentu.  
  
 `docAttr`  
 podczas Określa atrybuty dokumentu tekstowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje pomocnika dokumentu debugowania z nazwą i początkowymi atrybutami.  
  
 Ten dokument nie jest wyświetlany w drzewie do momentu wywołania `IDebugDocumentHelper::Attach`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)    
 [IDebugDocumentHelper   interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [TEXT_DOC_ATTR, stałe](../../winscript/reference/text-doc-attr-constants.md)