---
title: IDebugApplicationNode::D etach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Detach
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ffb422bec21bec65f1550368d898608a5f65015
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574808"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Usuwa ten węzeł aplikacji z drzewa projektu.  
  
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
 Ta metoda usuwa ten węzeł aplikacji z drzewa projektu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNode:: Attach](../../winscript/reference/idebugapplicationnode-attach.md)   
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)