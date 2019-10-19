---
title: 'IDebugDocumentTextEvents:: onUpdateDocumentAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c256d2cc6d826a72eb369cda0ad1e5f108e909bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576043"
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Wskazuje, że atrybuty dokumentu zostały zmienione.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `textdocattr`  
 podczas Atrybuty nowego dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, że atrybuty dokumentu zostały zmienione.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentTextEvents   interfejsu](../../winscript/reference/idebugdocumenttextevents-interface.md)  
 [TEXT_DOC_ATTR, stałe](../../winscript/reference/text-doc-attr-constants.md)