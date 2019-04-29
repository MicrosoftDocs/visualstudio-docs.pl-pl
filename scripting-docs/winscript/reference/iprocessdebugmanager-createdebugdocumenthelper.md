---
title: IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs
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
ms.openlocfilehash: 38de1e828ccd1715fb83cc76c06ba837818d2af0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002360"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Tworzy nowy Pomocnik dokumentu debugowania dla tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punkOuter`  
 [in] Jeśli zwracany obiekt jest zagregowany, `punkOuter` jest wskaźnik interfejsu do sterowania `IUnknown`. W przeciwnym razie jest wskaźnikiem wartości null.  
  
 `pddh`  
 [out] Obiekt pomocnika dokumentu debugowania dla tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy nowy Pomocnik dokumentu debugowania dla tej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IProcessDebugManager, interfejs](../../winscript/reference/iprocessdebugmanager-interface.md)