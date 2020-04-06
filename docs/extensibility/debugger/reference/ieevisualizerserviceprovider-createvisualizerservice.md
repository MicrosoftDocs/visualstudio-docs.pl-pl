---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717908"
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
[w] [Obiekt IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) przeszedł do [programu EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[w] [Obiekt IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) przeszedł `IDebugParsedExpression::EvaluateSync`do pliku .

`pAddress`\
[w] [Obiekt IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) przeszedł `IDebugParsedExression::EvaluateSync`do .

`dataProvider`\
[w] Obiekt implementujący interfejs [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (dostarczany przez oceniającego wyrażenie).

`ppService`\
[na zewnątrz] Utworzona usługa.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `pSymProv`, `binder`i `pAddress` parametry zostały przekazane `IDebugParsedExpression::EvaluateSync` do metody. `CreateVisualizerService`jest wywoływana tylko `IDebugParsedExpression::EvaluateSync` w ramach obsługi oceniającego wyrażenie dla wizualizatorów typów.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
