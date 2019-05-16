---
title: Wizualizacja i wyświetlanie danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696311"
---
# <a name="visualizing-and-viewing-data"></a>Wizualizacja i wyświetlanie danych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wizualizatorów typu i przeglądarek niestandardowych danych obecnych w sposób, który jest szybko zrozumiałe dla dewelopera. Ewaluator wyrażeń (EE) może obsługiwać wizualizatorów typu innych firm także podać swój własny przeglądarek niestandardowych.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Określa, ile wizualizatorów typu i przeglądarek niestandardowych są skojarzone z typem obiektu przez wywołanie metody [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metody. Jeśli istnieje co najmniej jeden typ wizualizatora lub Przeglądarka niestandardowa dostępny, Visual Studio wywołuje [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodę, aby pobrać listę tych wizualizatorów i osoby przeglądające (w rzeczywistości listę `CLSID`s, który implementuje wizualizatory i przeglądarki) i wyświetlane dla użytkownika.  
  
## <a name="supporting-type-visualizers"></a>Obsługa Wizualizatorów typu  
 Istnieje kilka interfejsów, które EE musi implementować do obsługi wizualizatorów typu. Interfejsy te mogą być podzielone na dwie szerokie kategorie: te, które listy wizualizatorów typu i te, które uzyskuje dostęp do danych właściwości.  
  
### <a name="listing-type-visualizers"></a>Wizualizatorów typu listy  
 EE obsługuje wyświetlanie wizualizatorów typu w jego implementacja obiektu `IDebugProperty3::GetCustomViewerCount` i `IDebugProperty3::GetCustomViewerList`. Te metody zakończyły się pomyślnie wywołanie odpowiedniej metody [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) można uzyskać przez wywołanie [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Ta metoda wymaga [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfejs, który jest uzyskiwana z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfejsu przekazany do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` wymaga również [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) i [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfejsów, które zostały przekazane do `IDebugParsedExpression::EvaluateSync`. Końcowy interfejs wymagany do utworzenia `IEEVisualizerService` interfejs [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejs, który implementuje EE. Ten interfejs umożliwia zmiany wprowadzone do właściwości wizualizowanego. Wszystkie dane właściwości są hermetyzowane w [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfejs, który jest również implementowana przez EE.  
  
### <a name="accessing-property-data"></a>Uzyskiwanie dostępu do danych właściwości  
 Uzyskiwanie dostępu do właściwości danych odbywa się za pośrednictwem [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu. Aby uzyskać ten interfejs, wywołuje program Visual Studio [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) w obiekcie właściwości, aby uzyskać [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu (implementowane w ten sam obiekt, który implementuje [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface), a następnie wywołuje [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodę, aby uzyskać `IPropertyProxyEESide` interfejsu.  
  
 Wszystkie dane przekazywane do i z `IPropertyProxyEESide` interfejsu jest hermetyzowany w [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfejsu. Ten interfejs reprezentuje tablicę bajtów i jest implementowany przez Visual Studio i EE. Gdy właściwość data ma zostać zmieniony, program Visual Studio tworzy `IEEDataStorage` obiekt przechowujący nowe dane i wywołuje [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) z tym obiektem danych w celu uzyskania nowego `IEEDataStorage` obiekt, który z kolei jest przekazany do [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) do aktualizacji właściwości danych. `IPropertyProxyEESide::CreateReplacementObject` Umożliwia EE utworzyć własne klasy, która implementuje `IEEDataStorage` interfejsu.  
  
## <a name="supporting-custom-viewers"></a>Obsługa przeglądarek niestandardowych  
 Flagi `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` jest ustawiana w `dwAttrib` pole [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury (zwrócone przez wywołanie [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) do wskazania, że obiekt ma Przeglądarka niestandardowa skojarzone z nim. Gdy ta flaga jest ustawiona, Visual Studio uzyskuje [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfejs z [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, za pomocą [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
 Jeśli użytkownik wybierze podglądu niestandardowego, programu Visual Studio tworzy wystąpienie podglądu niestandardowego za pomocą przeglądarki `CLSID` dostarczonych przez `IDebugProperty3::GetCustomViewerList` metody. Program Visual Studio następnie wywołuje [się pozycje DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) do przedstawienia wartości użytkownika.  
  
 Zwykle `IDebugCustomViewer::DisplayValue` przedstawia widok tylko do odczytu danych. Aby zezwolić na zmiany w danych, EE musi implementować niestandardowe interfejs, który obsługuje zmieniających się danych w obiekcie właściwości. `IDebugCustomViewer::DisplayValue` Metoda używa tego niestandardowego interfejsu do obsługują zmieniającymi się danymi. Metoda szuka niestandardowy interfejs `IDebugProperty2` interfejsu przekazany jako `pDebugProperty` argumentu.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Obsługuje zarówno typ Wizualizatorów i przeglądarek niestandardowych  
 EE może obsługiwać wizualizatorów typu i przeglądarek niestandardowych w [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody. Po pierwsze, EE dodaje do wartości zwracanej przez liczbę przeglądarek niestandardowych, które go udostępnia [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Po drugie, dołącza EE `CLSID`s swój własny niestandardowy oglądającym listy jest zwracana przez [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
