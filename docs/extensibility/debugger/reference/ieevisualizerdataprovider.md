---
title: IEEVisualizerDataProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718056"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs umożliwia zmianę wartości obiektu za pomocą wizualizatora typu.

## <a name="syntax"></a>Składnia

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs do obsługi modyfikowania danych na obiekt właściwości za pośrednictwem wizualizatora typu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest używany do tworzenia [obiektu IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) za pośrednictwem wywołania [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Aby uzyskać więcej informacji, zobacz [Wizualizacja i wyświetlanie danych.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable

|Metoda|Opis|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Określa, czy jest możliwe, aby zaktualizować obiekt (a następnie jego wartość), który reprezentuje ten wizualizator.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Wymusza ponowną ocenę obiektu dla tego wizualizatora.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Pobiera istniejący obiekt dla tego wizualizatora (nie jest wykonywana żadna ocena).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualizuje obiekt dla tego wizualizatora, zmieniając w ten sposób wartość, która prezentuje wizualizator.|

## <a name="remarks"></a>Uwagi
 Usługa wizualizatora (reprezentowana przez interfejs [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) i zwrócona przez [CreateVisualizerService)](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)zachowuje odwołanie do obiektu implementującego `IEEVisualizerDataProvider` interfejs. W rezultacie `IEEVisualizerDataProvider` interfejs nie powinny być implementowane na tym samym obiekcie, który implementuje [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) jeśli ten obiekt utrzymuje odwołanie do `IEEVisualizerService` obiektu: wyniki odwołania cyklicznego i zakleszczenie występuje, gdy obiekty są niszczone. Zalecane podejście jest `IEEVisualizerDataProvider` do zaimplementowania `IDebugProperty2` na oddzielny `IUnknown::AddRef` obiekt, do którego obiekt delegatów bez wywoływania na niego.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
