---
title: IPropertyProxyEESide::InPlaceUpdateObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 940f0b2eb711057cdfbae306028849cf015ed6e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862890"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje dane obiektu z obiektu danych i zwraca obiekt danych reprezentujący danych nowego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu zawierającego nowe dane.  
  
 `dataOut`  
 [out] Zwraca nowy `IEEDataStorage` obiekt zawierający dane zastąpione.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda faktycznie aktualizuje dane obiektu. Dane w zwróconym elemencie [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu nie musi być taka sama, jak dane w przychodzącej `IEEDataStorage` obiekt, ale zwracany obiekt muszą odzwierciedlać bieżącą wartość właściwości.  
  
 Przychodzące obiektu danych nie jest zwykle implementowany przez EE. Jednak obiekt zwracany przez tę metodę zawsze jest implementowany przez EE, która umożliwia Implementowanie EE `IEEDataStorage` interfejsu na pożądana jest klasa niezależnie od.  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metoda tworzy obiekt danych na podstawie przychodzącego obiektu danych, ale nie ma wpływu na właściwości oryginalnych danych.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)