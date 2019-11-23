---
title: IDebugDocumentHelper::D etach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Detach
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 876e23d3466352cb244cc445b2435f556bb88160
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576963"
---
# <a name="idebugdocumenthelperdetach"></a>IDebugDocumentHelper::Detach
Usuwa ten dokument z drzewa dokumentów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda usuwa ten dokument z drzewa dokumentów.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper, interfejs](../../winscript/reference/idebugdocumenthelper-interface.md)