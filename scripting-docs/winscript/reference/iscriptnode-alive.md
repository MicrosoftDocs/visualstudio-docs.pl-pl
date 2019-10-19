---
title: 'IScriptNode:: Alive | Microsoft Docs'
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573631"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Wskazuje, czy obiekt jest nadal aktywny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Węzeł skryptu jest nadal aktywny.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt nie jest aktywny, Component Object Model (COM) zwraca błąd z Marshaling proxy dla wywołań do tej metody.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)