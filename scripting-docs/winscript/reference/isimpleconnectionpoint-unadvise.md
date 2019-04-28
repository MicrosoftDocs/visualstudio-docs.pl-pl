---
title: ISimpleConnectionPoint::Unadvise | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 189c07c10e93df9a61218b6a94a0b317999676d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001494"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Przerywa połączenie doradztwa technicznego dotyczącego wcześniej ustanowione przez `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 [in] Token połączenia, aby zakończyć w postaci zwracanej przez `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Poradnik połączenie zostanie przerwane, połączenie punkcie wywołania `Release` metodę we wskaźniku, który został zapisany dla połączenia podczas `ISimpleConnectionPoint::Advise` metody. Odwrócona, które wywołują `AddRef` który zostało wykonane podczas `ISimpleConnectionPoint::Advise` gdy punkt połączenia z wywołuje doradztwa technicznego dotyczącego obiektu sink `QueryInterface`.  
  
## <a name="see-also"></a>Zobacz też  
 [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)