---
title: Implementowanie wizualizatorów typów i podglądów niestandardowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b780f2115400fd43e8915a5109c960cab99bf131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835574"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementowanie wizualizatorów typu i przeglądarek niestandardowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wizualizatory typów i niestandardowe osoby przeglądające umożliwiają użytkownikowi wyświetlanie danych określonego typu w sposób bardziej zrozumiały od prostego szesnastkowego zrzutu liczb. Ewaluatora wyrażeń (EE) może kojarzyć niestandardowe podglądy z określonymi typami danych lub zmiennych. Te niestandardowe podglądy są implementowane przez program EE. Na stronie EE można także obsługiwać wizualizacje typu zewnętrznego, które mogą pochodzić od innego dostawcy innych firm, a nawet od użytkownika końcowego.  
  
## <a name="discussion"></a>Dyskusja  
  
### <a name="type-visualizers"></a>Wizualizatory typów  
 Program Visual Studio pyta o listę wizualizatorów typu i niestandardowe podglądy dla każdego obiektu, który ma być wyświetlany w oknie czujki. Program Expression ewaluatora (EE) dostarcza takie listy dla każdego typu, dla którego chce obsługiwać Wizualizatory typów i niestandardowe osoby przeglądające. Wywołania funkcji [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) umożliwiają cały proces uzyskiwania dostępu do wizualizatorów typu i niestandardowym użytkownikom (zobacz [wizualizowanie i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md) w celu uzyskania szczegółowych informacji o sekwencji wywoływania).  
  
### <a name="custom-viewers"></a>Niestandardowe osoby przeglądające  
 Niestandardowe przeglądarki są implementowane w EE dla określonego typu danych i są reprezentowane przez interfejs [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Niestandardowa przeglądarka nie jest tak elastyczna jak wizualizator typu, ponieważ jest ona dostępna tylko wtedy, gdy jest wykonywane polecenie EE, które implementuje konkretną niestandardową przeglądarkę. Implementacja niestandardowej przeglądarki jest prostsza niż implementacja obsługi wizualizatorów typów. Jednak Wizualizatory typu wspomagającego zapewniają największą elastyczność użytkownikowi końcowemu do wizualizacji swoich danych. Pozostała część tej dyskusji dotyczy tylko wizualizatorów typu.  
  
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
 [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
