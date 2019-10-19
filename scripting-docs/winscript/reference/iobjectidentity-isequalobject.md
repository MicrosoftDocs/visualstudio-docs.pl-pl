---
title: 'IObjectIdentity:: isequalobject | Microsoft Docs'
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
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571463"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Określa, czy obiekt jest równy bieżącemu obiektowi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `punk`  
 podczas Adres obiektu do porównania z bieżącym obiektem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekty są równe.|  
|`S_FALSE`|Obiekty nie są równe.|  
  
## <a name="remarks"></a>Uwagi  
 Implementacja metody `IsEqualObject` powinna zwracać `S_OK` tylko wtedy, gdy obiekty są identyczne.  
  
## <a name="see-also"></a>Zobacz także  
 [IObjectIdentity, interfejs](../../winscript/reference/iobjectidentity-interface.md)