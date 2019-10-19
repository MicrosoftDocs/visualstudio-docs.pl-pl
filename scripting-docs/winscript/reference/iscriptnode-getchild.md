---
title: 'IScriptNode:: GetChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573565"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Zwraca element podrzędny, który znajduje się w określonym indeksie w węźle.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 podczas Indeks elementu podrzędnego w elemencie nadrzędnym.  
  
 `ppsn`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IScriptNode` wystąpienia podrzędnego.  
  
 W przypadku `IScriptNode` obiektów, które reprezentują stronę sieci Web, ten parametr zwraca obiekt, który zawiera blok skryptu.  
  
 Dla `IScriptEntry` obiektów, które określają blok skryptu, ten parametr zwraca obiekt, który określa funkcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku `IScriptEntry` obiektów, które określają obiekt Function i dla obiektów `IScriptScriptlet`, ta metoda nie powiedzie się, ponieważ nie ma żadnych wpisów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)