---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b45db093a451331de20b3f38bdf58f2669f0577
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223667"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Ta metoda tworzy usługę wizualizatora.

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

## <a name="parameters"></a>Parametry
 `binder`\

 [in] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiekt przekazany do [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

 `pSymProv`\

 [in] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) obiekt przekazany do `IDebugParsedExpression::EvaluateSync`.

 `pAddress`\

 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt przekazany do `IDebugParsedExression::EvaluateSync`.

 `dataProvider`\

 [in] Implementowanie obiektu [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejsu (dostarczonych przez ewaluatora wyrażeń).

 `ppService`\

 [out] Utworzono usługę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `binder`, `pSymProv`, I `pAddress` parametry zostały przekazane do `IDebugParsedExpression::EvaluateSync` metody. `CreateVisualizerService` jest wywoływane tylko z `IDebugParsedExpression::EvaluateSync` jako część ewaluatora wyrażeń obsługę wizualizatorów typu.

## <a name="see-also"></a>Zobacz także
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)