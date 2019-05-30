---
title: Implementowanie Wizualizatorów typu i przeglądarek niestandardowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f7e977df6236ea8c3310312114ba4fa30d5003a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344199"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementowanie wizualizatorów typu i przeglądarek niestandardowych
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wizualizatorów typu i przeglądarek niestandardowych umożliwia użytkownikowi wyświetlanie danych określonego typu w sposób, który jest bardziej opisowe niż proste zrzut szesnastkowy liczb. Ewaluatora wyrażeń (EE) można skojarzyć przeglądarek niestandardowych za pomocą określonych rodzajów danych lub zmienne. Te przeglądarek niestandardowych są implementowane przez EE. EE może również obsługiwać wizualizatorów typu zewnętrznego, które mogą pochodzić z innego dostawcy lub nawet użytkownika końcowego.

## <a name="discussion"></a>Dyskusja

### <a name="type-visualizers"></a>Wizualizatorów typu
 Visual Studio Wyświetla prośbę o listę wizualizatorów typu i przeglądarek niestandardowych dla każdego obiektu, które mają być wyświetlane w oknie czujki. Ewaluatora wyrażeń (EE) dostarcza listę dla każdego typu, którego chce obsługiwać wizualizatorów typu i przeglądarek niestandardowych. Wywołania [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) rozpoczęcia całego procesu uzyskiwania dostępu do wizualizatorów typu i przeglądarek niestandardowych (zobacz [Visualizing i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)szczegółowe informacje na temat sekwencja wywoływania).

### <a name="custom-viewers"></a>Przeglądarek niestandardowych
 Przeglądarek niestandardowych są implementowane w EE dla określonego typu danych i są reprezentowane przez [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejsu. Przeglądarka niestandardowa nie jest tak elastyczna jak Wizualizator typów, ponieważ jest dostępna tylko wtedy, gdy jest wykonywany EE, który implementuje tego konkretnego podglądu niestandardowego. Implementowanie Przeglądarka niestandardowa jest prostsze niż Implementowanie wizualizatorów typu obsługi. Jednak obsługa wizualizatorów typu zapewnia maksymalną elastyczność dla użytkownika końcowego do wizualizacji danych. W pozostałej części tej dyskusji dotyczy tylko wizualizatorów typu.

## <a name="interfaces"></a>Interfejsy
 EE implementuje następujące interfejsy do obsługi wizualizatorów typu, być używane przez program Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE wykorzystuje następujące interfejsy do obsługi wizualizatorów typu:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Zobacz także
- [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)