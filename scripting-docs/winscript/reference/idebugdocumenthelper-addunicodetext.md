---
title: 'IDebugDocumentHelper:: AddUnicodeText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5820c380c92f2c3cd95763b440d5f9755db3e717
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577052"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Dołącza ciąg Unicode na końcu tego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszText`  
 podczas Wskaźnik na ciąg zakończony znakiem null zawierający tekst.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie mogła dodać znaków.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda generuje `IDebugDocumentTextEvents` powiadomienia.  
  
> [!NOTE]
> Jeśli ta metoda jest wywoływana po wywołaniu `AddDeferredText`, zwracany jest `E_FAIL`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper  interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents, interfejs](../../winscript/reference/idebugdocumenttextevents-interface.md)