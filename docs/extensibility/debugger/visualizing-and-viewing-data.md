---
title: Wizualizacja i wyświetlanie danych | Microsoft Docs
description: Dowiedz się, jak Wizualizatory typów i podglądy niestandardowe przedstawiają dane deweloperom. Ewaluatora wyrażeń obsługuje Wizualizatory typu innej firmy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61c2094564ea20c1073a198c3da162862c543e65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965359"
---
# <a name="visualizing-and-viewing-data"></a>Wizualizacja i wyświetlanie danych
Wizualizatory typów i podglądy niestandardowe przedstawiają dane w sposób, który jest szybko zrozumiały dla dewelopera. Ewaluatora wyrażeń (EE) może obsługiwać Wizualizatory typu innych firm, a także dostarczać własne przeglądarki niestandardowe.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Określa, ile wizualizatorów typów i przegląda niestandardowych są skojarzone z typem obiektu przez wywołanie metody [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Jeśli jest dostępny co najmniej jeden wizualizator typu lub przeglądarka niestandardowa, program Visual Studio wywołuje metodę [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) , aby pobrać listę wizualizacji i osób przeglądających (w rzeczywistości listę s, która implementuje Wizualizatory i osoby przeglądające), i prezentuje je użytkownikowi.

## <a name="supporting-type-visualizers"></a>Wizualizatory typów pomocniczych
 Istnieje wiele interfejsów, które należy zaimplementować na potrzeby obsługi wizualizatorów typu EE. Te interfejsy można podzielić na dwie szerokie Kategorie: interfejsy, które wyświetlają Wizualizatory typów i interfejsy, które uzyskują dostęp do danych właściwości.

### <a name="listing-type-visualizers"></a>Wizualizacje typów list
 Program EE obsługuje listę wizualizatorów typów w jej implementacji `IDebugProperty3::GetCustomViewerCount` i `IDebugProperty3::GetCustomViewerList` . Te metody przekazują wywołania do odpowiednich metod [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) jest uzyskiwany przez wywołanie [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Ta metoda wymaga interfejsu [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , który jest uzyskiwany z interfejsu [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) przesłanego do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` wymaga również interfejsów [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) i [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) , które zostały przesłane do `IDebugParsedExpression::EvaluateSync` . Ostatnim interfejsem wymaganym do utworzenia `IEEVisualizerService` interfejsu jest interfejs [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , który implementuje polecenie EE. Ten interfejs umożliwia wprowadzanie zmian w wizualizacji właściwości. Wszystkie dane właściwości są hermetyzowane w interfejsie [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , który jest również ZAIMPLEMENTOWANY przez EE.

### <a name="accessing-property-data"></a>Uzyskiwanie dostępu do danych właściwości
 Uzyskiwanie dostępu do danych właściwości odbywa się za pomocą interfejsu [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Aby uzyskać ten interfejs, program Visual Studio wywołuje polecenie [QueryInterface](/cpp/atl/queryinterface) w obiekcie Property, aby uzyskać Interfejs [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (zaimplementowany dla tego samego obiektu, który implementuje interfejs [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ), a następnie wywołuje metodę [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) w celu uzyskania `IPropertyProxyEESide` interfejsu.

 Wszystkie dane przesyłane do i z `IPropertyProxyEESide` interfejsu są hermetyzowane w interfejsie [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) . Ten interfejs reprezentuje tablicę bajtów i jest implementowany przez program Visual Studio i EE. Gdy dane właściwości mają być zmieniane, program Visual Studio tworzy `IEEDataStorage` obiekt przechowujący nowe dane i wywołuje metodę [restąpiobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) z tym obiektem danych w celu uzyskania nowego `IEEDataStorage` obiektu, który z kolei jest przenoszona do [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) w celu zaktualizowania danych właściwości. `IPropertyProxyEESide::CreateReplacementObject` umożliwia programowi EE utworzenie wystąpienia własnej klasy, która implementuje `IEEDataStorage` interfejs.

## <a name="supporting-custom-viewers"></a>Obsługa podglądów niestandardowych
 Flaga `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` jest ustawiana w `dwAttrib` polu struktury [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (zwrócone przez wywołanie [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), aby wskazać, że obiekt ma skojarzoną z nim przeglądarkę niestandardową. Gdy ta flaga jest ustawiona, program Visual Studio uzyskuje Interfejs [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) z interfejsu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) przy użyciu [polecenia QueryInterface](/cpp/atl/queryinterface).

 Jeśli użytkownik wybierze niestandardową przeglądarkę, program Visual Studio tworzy wystąpienie niestandardowej przeglądarki przy użyciu przeglądarki `CLSID` dostarczonej przez `IDebugProperty3::GetCustomViewerList` metodę. Program Visual Studio następnie wywołuje [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) , aby wyświetlić wartość dla użytkownika.

 Zwykle `IDebugCustomViewer::DisplayValue` przedstawia widok danych tylko do odczytu. Aby umożliwić wprowadzanie zmian w danych, na stronie EE musi być zaimplementowany niestandardowy interfejs, który obsługuje zmienianie danych w obiekcie właściwości. `IDebugCustomViewer::DisplayValue`Metoda używa tego interfejsu niestandardowego do obsługi zmiany danych. Metoda szuka niestandardowego interfejsu w interfejsie, który `IDebugProperty2` przeszedł jako `pDebugProperty` argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Obsługa wizualizacji typu i podglądów niestandardowych
 W programie EE można obsługiwać zarówno Wizualizatory typu, jak i niestandardowe osoby przeglądające w metodach [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . Po pierwsze, EE dodaje liczbę niestandardowych podglądów, które są dostarczane do wartości zwracanej przez metodę [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Po drugie, EE dodaje `CLSID` własne niestandardowe podglądy do listy zwracanej przez metodę [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [Wizualizator typów i Podgląd niestandardowy](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
