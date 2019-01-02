---
title: IDebugBinder3::GetEEService | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b0739294f5c2b003baa7e221c7e617456fda89e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822045"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Ta metoda zwraca żądanej usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vendor`  
 [in] `GUID` dostawcy (wartość null jest dopuszczalne).  
  
 `language`  
 [in] `GUID` języka (wartość null jest dopuszczalne).  
  
 `iid`  
 [in] `IID` usługi do uzyskania.  
  
 `ppService`  
 [out] Interfejs do żądanej usługi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Przekaż `IID` dla [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interfejsu (`IID_IEEVisualizerServiceProvider`) aby zobaczyć, czy usługa Wizualizator typów jest dostępna. Jeśli tak, można uzyskać Ewaluator wyrażeń [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) wizualizatorów typu obsługiwany przez interfejs. Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)