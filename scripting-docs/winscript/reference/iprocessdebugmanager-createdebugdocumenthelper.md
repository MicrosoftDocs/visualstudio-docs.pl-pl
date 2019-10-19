---
title: 'IProcessDebugManager:: CreateDebugDocumentHelper | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a009fa5174ab897116c02b91e376e2dc41d67600
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577095"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Tworzy nowego pomocnika dokumentu debugowania dla tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punkOuter`  
 podczas Jeśli zwracany obiekt ma być zagregowany, `punkOuter` jest wskaźnikiem interfejsu do kontrolki `IUnknown`. W przeciwnym razie jest wskaźnikiem o wartości null.  
  
 `pddh`  
 określoną Obiekt pomocnika dokumentu debugowania dla tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia utworzenie nowego pomocnika dokumentu debugowania dla tej aplikacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IProcessDebugManager, interfejs](../../winscript/reference/iprocessdebugmanager-interface.md)