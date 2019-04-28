---
title: IScriptNode::Alive | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787176"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Wskazuje, czy obiekt jest nadal aktywne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Ten węzeł skryptu jest nadal aktywne.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt nie jest aktywne, Component Object Model (COM) zwraca błąd z serwera proxy kierowania do wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)