---
title: 'IDebugApplicationNode:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574783"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Dodaje ten węzeł aplikacji do określonego drzewa projektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdanParent`  
 podczas Drzewo projektu, do którego ma zostać dodany ten węzeł aplikacji.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda dodaje ten węzeł aplikacji do drzewa projektu przy użyciu `pdanParent` jako elementu nadrzędnego. Jeśli `pdanParent` jest `NULL`, ten węzeł aplikacji będzie węzłem najwyższego poziomu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)