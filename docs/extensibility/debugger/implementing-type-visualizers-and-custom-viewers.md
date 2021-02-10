---
title: Implementowanie wizualizatorów typów i podglądów niestandardowych | Microsoft Docs
description: Dowiedz się więcej na temat implementowania wizualizatorów typów i niestandardowych recenzentów, które umożliwiają użytkownikom wyświetlanie danych w sposób bardziej zrozumiały niż zrzut liczby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8cf456dca27a45a2674f7138a6c0b21b12750c81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945971"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementowanie wizualizatorów typów i podglądów niestandardowych
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wizualizatory typów i podglądy niestandardowe pozwalają użytkownikom na wyświetlanie danych określonego typu w sposób bardziej zrozumiały od prostego zrzutu szesnastkowego liczb. Ewaluatora wyrażeń (EE) może kojarzyć niestandardowe podglądy z określonymi typami danych lub zmiennych. Te niestandardowe podglądy są implementowane przez program EE. Na stronie EE można także obsługiwać wizualizacje typu zewnętrznego, które mogą pochodzić od innego dostawcy innych firm, a nawet od użytkownika końcowego.

## <a name="discussion"></a>Dyskusja

### <a name="type-visualizers"></a>Wizualizatory typów
 Program Visual Studio pyta o listę wizualizatorów typu i niestandardowe podglądy dla każdego obiektu, który ma być wyświetlany w oknie czujki. Program Expression ewaluatora (EE) dostarcza takie listy dla każdego typu, dla którego chce obsługiwać Wizualizatory typów i niestandardowe osoby przeglądające. Wywołania funkcji [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) umożliwiają cały proces uzyskiwania dostępu do wizualizatorów typu i niestandardowym użytkownikom (zobacz [wizualizowanie i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md) w celu uzyskania szczegółowych informacji o sekwencji wywoływania).

### <a name="custom-viewers"></a>Niestandardowe osoby przeglądające
 Niestandardowe przeglądarki są implementowane w EE dla określonego typu danych i są reprezentowane przez interfejs [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Niestandardowa przeglądarka nie jest tak elastyczna jak wizualizator typu, ponieważ jest ona dostępna tylko wtedy, gdy jest wykonywane polecenie EE, które implementuje konkretną niestandardową przeglądarkę. Implementacja niestandardowej przeglądarki jest prostsza niż implementacja obsługi wizualizatorów typów. Jednak Wizualizatory typu wspomagającego zapewniają największą elastyczność użytkownikowi końcowemu do wizualizacji danych. Pozostała część tej dyskusji dotyczy tylko wizualizatorów typu.

## <a name="interfaces"></a>Interfejsy
 Na stronie EE zaimplementowane są następujące interfejsy do obsługi wizualizatorów typów, które mają być używane przez program Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  Na stronie EE są używane następujące interfejsy do obsługi wizualizatorów typów:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
