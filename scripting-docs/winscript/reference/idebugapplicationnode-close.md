---
title: IDebugApplicationNode::Close | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Close
ms.assetid: ea8db480-2344-4c7b-960c-4fa97fa6c1b7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c634fd154c2470b1a154e5d1c9e97419a2e2e2b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990515"
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Powoduje, że ta aplikacja jest zwolnienie wszystkich odwołań, a następnie wprowadź nieaktywny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle właściciel aplikacji wywołuje tę metodę, gdy aplikacja kończy działanie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)