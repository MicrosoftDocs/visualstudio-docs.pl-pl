---
title: 'IDebugDocumentTextEvents:: onRemoveText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onRemoveText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onRemoveText
ms.assetid: c5dfe674-c42f-4e57-9d48-8380d5aa206b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c302a3b1850db42824f35a306e7e94eaa8a6aa41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576259"
---
# <a name="idebugdocumenttexteventsonremovetext"></a>IDebugDocumentTextEvents::onRemoveText
Wskazuje, że tekst został usunięty z dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onRemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 podczas Pozycja znaku pierwszego znaku, który został usunięty.  
  
 `cNumToRemove`  
 podczas Liczba usuniętych znaków.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, że tekst został usunięty z dokumentu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentTextEvents  interfejsu](../../winscript/reference/idebugdocumenttextevents-interface.md)  
 [IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)