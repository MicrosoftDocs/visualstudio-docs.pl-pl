---
title: 'IDebugDocumentHelper:: SetDebugDocumentHost | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDebugDocumentHost
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDebugDocumentHost
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b32d14f3a7d65bee7bdb587a35dfe05bb06f5e1e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574657"
---
# <a name="idebugdocumenthelpersetdebugdocumenthost"></a>IDebugDocumentHelper::SetDebugDocumentHost
Ustawia `IDebugDocumentHost` dla tego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddh`  
 podczas Host dokumentu debugowania.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `IDebugDocumentHost` służy do kolorowania składni inteligentnego hosta, pobierania odroczonego tekstu i zwracania obiektów kontrolujących nowo utworzonych kontekstów dokumentów.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper  interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)