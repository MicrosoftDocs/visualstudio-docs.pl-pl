---
title: IScriptNode::Delete | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 41bf932b242865b1deac4c61db400f973bd0b00c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787163"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Usuwa drzewa tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Po `Delete` metoda jest wywoływana, [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) — metoda powinna być widoczna w tym węźle skrypt nie jest aktywny.  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)