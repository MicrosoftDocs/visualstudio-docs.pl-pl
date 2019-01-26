---
title: IPropertyProxyEESide::CreateReplacementObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb1c2c5478bb24f80646dcaacf64a9e6efb2e425
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988327"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Tworzy kopię obiektu danych specyficznych dla Ewaluator wyrażeń (EE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt zawierający dane do skopiowania.  
  
 `dataOut`  
 [out] Zwraca nowy `IEEDataStorage` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda otrzymuje [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt reprezentujący tablicę bajtów. Zazwyczaj ten przychodzących obiekt danych nie jest zaimplementowana przez EE. Jednak obiekt zwracany przez tę metodę zawsze jest implementowany przez EE, która umożliwia Implementowanie EE `IEEDataStorage` interfejsu na pożądana jest klasa niezależnie od.  
  
 Należy pamiętać, że dane dostarczone przez przychodzący `IEEDataStorage` obiekt musi być te same dane w wychodzącej `IEEDataStorage` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)