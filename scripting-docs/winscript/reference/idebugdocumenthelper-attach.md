---
title: 'IDebugDocumentHelper:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577033"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Dodaje ten dokument do drzewa dokumentów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddhParent`  
 podczas Drzewo dokumentu, do którego zostanie dodany ten dokument. Może mieć wartość NULL.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda dodaje ten dokument do drzewa dokumentów przy użyciu `pddhParent` jako elementu nadrzędnego. Jeśli `pddhParent` jest `NULL`, dokument ten będzie dokumentem najwyższego poziomu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper::D etach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper, interfejs](../../winscript/reference/idebugdocumenthelper-interface.md)