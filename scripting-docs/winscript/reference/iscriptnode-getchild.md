---
title: IScriptNode::GetChild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086596"
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