---
title: IEEVisualizerServiceProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717887"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs daje dostęp do metody, która może utworzyć usługę wizualizatora, który jest używany do obsługi zadań wizualizatora typu dla IDE.

## <a name="syntax"></a>Składnia

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs, aby utworzyć obiekt usługi wizualizatora,`CLSID`który z kolei jest używany do dostarczania identyfikatorów klas (identyfikatorów) wizualizatorów typu do środowiska IDE programu Visual Studio.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Oceniający wyrażenie (EE) wywołuje [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable

|Metoda|Opis|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Tworzy usługę wizualizatora|

## <a name="remarks"></a>Uwagi
 Interfejs `IEEVisualizerServiceProvider` uzyskuje się podczas implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Usługa wizualizatora, który tworzy ten interfejs jest używany do dostarczania funkcji do interfejsu [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) który EE jest odpowiedzialny za implementowanie. EE jest również odpowiedzialny za implementowanie interfejsu [IEEVisualizerDataProvider,](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) który umożliwia wizualizatorów typu do wyświetlania i modyfikowania wartości właściwości.

 Zobacz [Wizualizacja i wyświetlanie danych, aby](../../../extensibility/debugger/visualizing-and-viewing-data.md) uzyskać szczegółowe informacje na temat interakcji tych interfejsów.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
