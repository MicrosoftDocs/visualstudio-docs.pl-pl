---
title: IObjectIdentity::IsEqualObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944888"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Określa, jeśli obiekt jest taki sam jak bieżący obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punk`  
 [in] Adres obiekt do porównania z bieżącym obiektem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekty są równe.|  
|`S_FALSE`|Obiekty nie są równe.|  
  
## <a name="remarks"></a>Uwagi  
 Implementacja `IsEqualObject` metoda powinna zwrócić `S_OK` tylko wtedy, gdy obiekty są takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [IObjectIdentity, interfejs](../../winscript/reference/iobjectidentity-interface.md)