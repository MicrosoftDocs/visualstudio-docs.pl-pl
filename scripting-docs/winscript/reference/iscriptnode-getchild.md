---
title: IScriptNode::GetChild | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787133"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Zwraca element podrzędny, który jest umieszczony pod określonym indeksem w węźle.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `ppsn`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptNode` interfejsu, wystąpienia podrzędne.  
  
 Aby uzyskać `IScriptNode` obiektów, które reprezentują strony sieci Web, ten parametr zwraca obiekt, który zawiera blok skryptu.  
  
 Aby uzyskać `IScriptEntry` obiektów, które określają blok skryptu, ten parametr zwraca obiekt, który określa funkcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Dla `IScriptEntry` obiekty, które określają obiektu funkcyjnego i `IScriptScriptlet` obiektów, ta metoda nie powiedzie się, ponieważ nie ma żadnych wpisów podrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)