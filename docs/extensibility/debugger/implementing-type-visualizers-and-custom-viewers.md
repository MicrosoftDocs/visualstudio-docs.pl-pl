---
title: Implementowanie wizualizatorów typów i niestandardowych przejasków | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738504"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementowanie wizualizatorów typów i niestandardowych przejańsków
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wizualizatory typu i przeglądarki niestandardowe umożliwiają użytkownikowi wyświetlanie danych określonego typu w sposób, który jest bardziej znaczący niż prosty szesnastkowy zrzut liczb. Oceniający wyrażenie (EE) może skojarzyć przeglądarki niestandardowe z określonymi typami danych lub zmiennych. Te niestandardowe przeglądarki są implementowane przez EE. EE może również obsługiwać wizualizatory typów zewnętrznych, które mogą pochodzić od innego dostawcy zewnętrznego lub nawet użytkownika końcowego.

## <a name="discussion"></a>Dyskusji

### <a name="type-visualizers"></a>Wizualizatory typów
 Visual Studio prosi o listę wizualizatorów typu i niestandardowych widzów dla każdego obiektu, które mają być wyświetlane w oknie czujki. Oceniający wyrażenie (EE) dostarcza taką listę dla każdego typu, dla którego chce obsługiwać wizualizatory typów i przeglądarki niestandardowe. Wywołania [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) rozpocząć cały proces uzyskiwania dostępu do wizualizatorów typu i niestandardowych przeglądarek (zobacz [Wizualizacja i wyświetlanie danych, aby](../../extensibility/debugger/visualizing-and-viewing-data.md) uzyskać szczegółowe informacje na temat sekwencji wywołującej).

### <a name="custom-viewers"></a>Przeglądarki niestandardowe
 Przeglądarki niestandardowe są implementowane w EE dla określonego typu danych i są reprezentowane przez interfejs [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Przeglądarka niestandardowa nie jest tak elastyczna jak wizualizator typu, ponieważ jest dostępna tylko wtedy, gdy ee, który implementuje tej konkretnej przeglądarki niestandardowej jest wykonywany. Implementowanie przeglądarki niestandardowej jest prostsze niż implementowanie obsługi wizualizatorów typów. Jednak obsługa wizualizatorów typów zapewnia użytkownikom końcowym maksymalną elastyczność w zakresie wizualizacji ich danych. Pozostała część tej dyskusji dotyczy tylko wizualizatorów typu.

## <a name="interfaces"></a>Interfejsy
 EE implementuje następujące interfejsy do obsługi wizualizatorów typu, które mają być używane przez program Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE zużywa następujące interfejsy do obsługi wizualizatorów typów:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
