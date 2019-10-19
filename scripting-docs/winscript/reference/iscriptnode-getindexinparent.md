---
title: 'IScriptNode:: GetIndexInParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9251f65414a5ebd48ce56dae6a7dbfeec4e514e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575045"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Zwraca indeks obiektu znajdującego się na liście elementów podrzędnych elementu nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pisn`  
 określoną Zwraca indeks obiektu znajdującego się na liście elementów podrzędnych elementu nadrzędnego.  
  
 Jeśli ta metoda jest wywoływana przez obiekt `IScriptNode`, który reprezentuje stronę sieci Web, ten parametr zwraca wartość 0.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)