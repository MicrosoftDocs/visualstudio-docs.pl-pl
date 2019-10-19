---
title: 'ISimpleConnectionPoint:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571749"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Kończy połączenie doradcze utworzone wcześniej za `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 podczas Token połączenia do przerwania, który został zwrócony z `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Po przerwaniu połączenia Doradczego punkt połączenia wywołuje metodę `Release` na wskaźniku zapisanym dla połączenia podczas `ISimpleConnectionPoint::Advise` metody. To wywołanie odwraca `AddRef`, który został wykonany podczas `ISimpleConnectionPoint::Advise`, gdy punkt połączenia wywoła `QueryInterface`ego ujścia doradcy.  
  
## <a name="see-also"></a>Zobacz także  
 [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)