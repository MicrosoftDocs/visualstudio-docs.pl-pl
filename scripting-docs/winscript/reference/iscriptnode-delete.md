---
title: IScriptNode::D suń | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3522e5543d333443de5b1287c994bf29de51c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576302"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Usuwa to drzewo obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu metody `Delete` Metoda [IScriptNode:: Alive](../../winscript/reference/iscriptnode-alive.md) powinna wskazywać, że węzeł skryptu nie jest aktywny.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)