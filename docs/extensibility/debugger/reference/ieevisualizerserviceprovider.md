---
description: Ten interfejs zapewnia dostęp do metody, która może utworzyć usługę wizualizatora, która jest używana do obsługi zadań wizualizatora typu dla środowiska IDE.
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d4fc53ae13588a0e285e4a62691da4d88a94d5f5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227180"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs zapewnia dostęp do metody, która może utworzyć usługę wizualizatora, która jest używana do obsługi zadań wizualizatora typu dla środowiska IDE.

## <a name="syntax"></a>Składnia

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs, aby utworzyć obiekt usługi wizualizatora, który z kolei służy do dostarczania identyfikatorów klasy `CLSID` wizualizatorów do środowiska IDE programu Visual Studio.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 W celu uzyskania tego interfejsu [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) ewaluatora wyrażeń (EE).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych

|Metoda|Opis|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Tworzy usługę wizualizatora|

## <a name="remarks"></a>Uwagi
 `IEEVisualizerServiceProvider`Interfejs jest uzyskiwany podczas implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Usługa wizualizatora, którą tworzy ten interfejs, służy do dostarczania funkcji do interfejsu [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , który jest odpowiedzialny za wdrożenie. EE jest również odpowiedzialny za implementację interfejsu [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , który umożliwia wizualizatorom typów wyświetlanie i modyfikowanie wartości właściwości.

 Zobacz [wizualizowanie i wyświetlanie danych,](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje na temat sposobu działania tych interfejsów.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
