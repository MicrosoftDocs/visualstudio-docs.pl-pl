---
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155083"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda służy do tworzenia usługi wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `binder`  
 podczas Obiekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) przeszedł do [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 podczas Obiekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) przeszedł do `IDebugParsedExpression::EvaluateSync` .  
  
 `pAddress`  
 podczas Obiekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) przeszedł do `IDebugParsedExression::EvaluateSync` .  
  
 `dataProvider`  
 podczas Obiekt implementujący interfejs [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (dostarczany przez ewaluatora wyrażeń).  
  
 `ppService`  
 określoną Utworzona usługa.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `binder`Parametry, `pSymProv` i `pAddress` zostały przesłane do `IDebugParsedExpression::EvaluateSync` metody. `CreateVisualizerService` ma być wywoływana tylko z `IDebugParsedExpression::EvaluateSync` jako część obsługi ewaluatora wyrażeń dla wizualizatorów typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
