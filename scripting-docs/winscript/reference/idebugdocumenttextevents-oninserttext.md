---
title: 'IDebugDocumentTextEvents:: onInsertText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onInsertText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onInsertText
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c926caf8ff99cf183e41b2caf825aa828fb60de4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572910"
---
# <a name="idebugdocumenttexteventsoninserttext"></a>IDebugDocumentTextEvents::onInsertText
Wskazuje, że nowy tekst został dodany do dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 podczas Pozycja znaku, w której został wstawiony nowy tekst.  
  
 `cNumToInsert`  
 podczas Liczba wstawionych znaków.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana przez hosta, który stopniowo ładuje zawartość, taką jak przeglądarka sieci Web.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentTextEvents  interfejsu](../../winscript/reference/idebugdocumenttextevents-interface.md)  
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)