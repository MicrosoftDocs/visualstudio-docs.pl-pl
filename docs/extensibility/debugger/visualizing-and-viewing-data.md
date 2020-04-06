---
title: Wizualizacja i wyświetlanie danych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712377"
---
# <a name="visualizing-and-viewing-data"></a>Wizualizacja i wyświetlanie danych
Wizualizatory typu i przeglądarki niestandardowe prezentują dane w sposób, który szybko ma znaczenie dla dewelopera. Oceniający wyrażenie (EE) może obsługiwać wizualizatory typów innych firm, a także dostarczać własne przeglądarki niestandardowe.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]określa, ile typów wizualizatorów i niestandardowych przeglądarek są skojarzone z typem obiektu, wywołując [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metody. Jeśli istnieje co najmniej jeden typ wizualizatora lub przeglądarki niestandardowej dostępne, Visual Studio wywołuje [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody, aby pobrać listę tych wizualizatorów i przeglądarek (w rzeczywistości lista s, która implementuje wizualizatorów i przeglądarek) i przedstawia je do użytkownika.

## <a name="supporting-type-visualizers"></a>Obsługa wizualizatorów typów
 Istnieje wiele interfejsów, które EE musi zaimplementować do obsługi wizualizatorów typów. Interfejsy te można podzielić na dwie szerokie kategorie: interfejsy, które lista wizualizatorów typu i interfejsów, które uzyskują dostęp do danych właściwości.

### <a name="listing-type-visualizers"></a>Wizualizatory typów aukcji
 EE obsługuje listę wizualizacji typu w `IDebugProperty3::GetCustomViewerCount` jego `IDebugProperty3::GetCustomViewerList`realizacji i . Te metody przechodzą wywołanie do odpowiednich metod [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) uzyskuje się przez [wywołanie CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Ta metoda wymaga interfejsu [IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) który jest uzyskiwany z interfejsu [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) przekazywane do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`wymaga również interfejsów [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) i [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) które zostały przekazane do `IDebugParsedExpression::EvaluateSync`. Ostatnim interfejsem wymaganym `IEEVisualizerService` do utworzenia interfejsu jest interfejs [IEEVisualizerDataProvider,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) który implementuje EE. Ten interfejs umożliwia wprowadzenie zmian do właściwości są wizualizowane. Wszystkie dane właściwości są hermetyzowane w interfejsie [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) który jest również implementowany przez EE.

### <a name="accessing-property-data"></a>Uzyskiwanie dostępu do danych właściwości
 Uzyskiwanie dostępu do danych właściwości odbywa się za pośrednictwem interfejsu [IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Aby uzyskać ten interfejs, Visual Studio wywołuje [QueryInterface](/cpp/atl/queryinterface) na obiekt właściwości, aby uzyskać [interfejs IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (zaimplementowane na tym samym obiekcie, który implementuje `IPropertyProxyEESide` interfejs [IDebugProperty3),](../../extensibility/debugger/reference/idebugproperty3.md) a następnie wywołuje [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metody w celu uzyskania interfejsu.

 Wszystkie dane przekazywane do `IPropertyProxyEESide` i z interfejsu są hermetyzowane w interfejsie [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Ten interfejs reprezentuje tablicę bajtów i jest implementowany przez program Visual Studio i EE. Gdy dane właściwości ma zostać zmieniona, Visual `IEEDataStorage` Studio tworzy obiekt zawierający nowe dane i wywołuje [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) z tym obiektem danych w celu uzyskania nowego `IEEDataStorage` obiektu, który z kolei jest przekazywany do [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) w celu zaktualizowania danych właściwości. `IPropertyProxyEESide::CreateReplacementObject`umożliwia EE do wystąpienia własnej klasy, która `IEEDataStorage` implementuje interfejs.

## <a name="supporting-custom-viewers"></a>Wspieranie niestandardowych widzów
 Flaga `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` jest ustawiona w `dwAttrib` polu [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury (zwrócona przez wywołanie [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), aby wskazać, że obiekt ma niestandardową przeglądarkę skojarzoną z nim. Po ustawieniu tej flagi program Visual Studio uzyskuje interfejs [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) z interfejsu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) przy użyciu [queryinterface](/cpp/atl/queryinterface).

 Jeśli użytkownik wybierze niestandardową przeglądarkę, program Visual Studio wystąpienia `CLSID` przeglądarki niestandardowej przy użyciu przeglądarki dostarczone przez `IDebugProperty3::GetCustomViewerList` metodę. Visual Studio następnie wywołuje [DisplayValue,](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) aby wyświetlić wartość dla użytkownika.

 Zwykle `IDebugCustomViewer::DisplayValue` przedstawia widok tylko do odczytu danych. Aby zezwolić na zmiany danych, EE należy zaimplementować interfejs niestandardowy, który obsługuje zmiany danych na obiekcie właściwości. Metoda `IDebugCustomViewer::DisplayValue` używa tego interfejsu niestandardowego do obsługi zmiany danych. Metoda szuka interfejsu niestandardowego `IDebugProperty2` w interfejsie `pDebugProperty` przekazywane jako argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Obsługa zarówno wizualizatorów typów, jak i niestandardowych widzów
 EE może obsługiwać zarówno wizualizatorów typu i niestandardowych widzów w [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody. Po pierwsze EE dodaje liczbę niestandardowych przeglądarek, które jest dostarczanie do wartości zwracanej przez [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Po drugie, EE dołącza `CLSID`s własnych niestandardowych widzów do listy zwróconej przez [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody.

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [Wizualizator typu i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
