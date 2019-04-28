---
title: IDebugDocumentHelper::AddDBCSText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d346f3877574c45aaff6dcef8ca99f699a42552
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446651"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Dołącza ciąg znaków Dwubajtowych na końcu tego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszText`  
 [in] Wskaźnik na ciąg zakończony wartością null zawierający tekst.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie może dodać znaków.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda generuje `IDebugDocumentTextEvents` powiadomienia.  
  
> [!NOTE]
> Jeśli ta metoda jest wywoływana po `IDebugDocumentHelper::AddDeferredText` została wywołana, `E_FAIL` jest zwracana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents, interfejs](../../winscript/reference/idebugdocumenttextevents-interface.md)