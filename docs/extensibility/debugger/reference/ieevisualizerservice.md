---
title: IEEVisualizerSługa | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717942"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs implementuje kluczowe metody, które dostarczają funkcje do interfejsów [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) i [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="syntax"></a>Składnia

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio implementuje ten interfejs, aby umożliwić oceniający wyrażenie (EE) do obsługi wizualizatorów typów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 EE wywołuje [CreateVisualizerService,](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) aby uzyskać ten interfejs jako część jego obsługi wizualizatorów typu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable

|Metoda|Opis|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Pobiera liczbę niestandardowych widzów, o których ta usługa wie.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Pobiera listę niestandardowych widzów.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Zwraca obiekt proxy dla właściwości.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Pobiera liczbę ciągów wartości do wyświetlenia dla określonej właściwości lub pola.|

## <a name="remarks"></a>Uwagi
 IDE używa interfejsu [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) aby ustalić, czy istnieją jakieś niestandardowe przeglądarki lub wizualizatory typu dla właściwości. Tworząc usługę wizualizatora (z [CreateVisualizerService),](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)EE może `IDebugProperty3` dostarczyć funkcje do i [IPropertyProxyEEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (który obsługuje wyświetlanie i zmienianie wartości właściwości) interfejsów, a tym samym obsługi wizualizatorów typu.

 Jeśli EE ma niestandardowe przeglądarki, które samodzielnie implementuje, EE może dołączyć `CLSID`s tych niestandardowych widzów na końcu listy zwróconej przez [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Dzięki temu EE do obsługi zarówno wizualizatorów typu i własnych niestandardowych widzów. Upewnij się tylko, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla dodanie dowolnych niestandardowych widzów.

 Zobacz [Wizualizator typów i Przeglądarka niestandardowa, aby](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) zapoznać się z omówieniam różnicy między wizualizatorami a przeglądarkami.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
