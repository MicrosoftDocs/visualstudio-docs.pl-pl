---
title: IScriptNode::GetIndexInParent | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 92f5ae074d65d2360bcfb3dda03903aa3c59209e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786979"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Zwraca indeks obiektu w liście elementów podrzędnych elementu nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pisn`  
 [out] Zwraca indeks obiektu w liście elementów podrzędnych elementu nadrzędnego.  
  
 Jeśli ta metoda jest wywoływana `IScriptNode` obiektu, że reprezentuje strony sieci Web, ten parametr zwraca wartość 0.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)