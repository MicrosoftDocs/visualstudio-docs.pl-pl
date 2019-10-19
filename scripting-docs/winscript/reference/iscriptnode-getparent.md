---
title: 'IScriptNode:: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572560"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Zwraca obiekt `IScriptNode`, który jest elementem nadrzędnym obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppsnParent`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IScriptNode` wystąpienia nadrzędnego.  
  
 Jeśli klasa implementuje `IScriptEntry` lub `IScriptScriptlet`, zwracany jest obiekt `IScriptNode`.  
  
 Jeśli klasa implementuje `IScriptNode` (reprezentującą stronę sieci Web), zwracana jest wartość NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)