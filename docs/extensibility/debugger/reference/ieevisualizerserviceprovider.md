---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84ed3f81bed9c413e322e5a906df9d2dd1f60db9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412554"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs zapewnia dostęp do metody, która może utworzyć usługi visualizer, który jest używany do obsługi zadań Wizualizator typu dla środowiska IDE.

## <a name="syntax"></a>Składnia

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio implementuje ten interfejs, aby utworzyć wizualizatora obiektu usługi, która z kolei służą do określania identyfikatorów klas (`CLSID`s) z wizualizatorów typu środowiska IDE programu Visual Studio.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ewaluator wyrażeń (EE) wywołuje [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności

|Metoda|Opis|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Tworzy usługę wizualizatora|

## <a name="remarks"></a>Uwagi
 `IEEVisualizerServiceProvider` Interfejsu są uzyskiwane podczas realizacji [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Usługa wizualizatora, która tworzy tego interfejsu służą do określania funkcji [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs, czyli EE odpowiedzialnych za wdrażanie. EE jest również odpowiedzialny za wdrażanie [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejsu, który umożliwia wizualizatorów typu wyświetlić i zmodyfikować wartości właściwości.

 Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) szczegółowe informacje dotyczące sposobu interakcji tych interfejsów.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)