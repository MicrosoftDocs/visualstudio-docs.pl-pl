---
title: IPropertyProxyEESide::CreateReplacementObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c71f87b35915906475ce27971196d540ece39452
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757201"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

