---
title: Przegląd okna właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61887844e06a88cab9eaa8ca8be7a89c124e2340
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725083"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
Okno **Właściwości** służy do wyświetlania właściwości obiektów wybranych w dwóch głównych typach systemu Windows dostępnych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE). Te dwa typy okien są następujące:

- Okna narzędzi, takie jak Eksplorator rozwiązań, Widok klasy i Przeglądarka obiektów

- Okna dokumentów zawierające takie redaktorzy i projektanci jak Projektant formularzy, Edytor XML i Edytor HTML

## <a name="using-the-properties-window"></a>Korzystanie z okna właściwości
 W oknie **Właściwości** są wyświetlane właściwości jednego lub wielu zaznaczonych elementów. Jeśli wybrano wiele elementów, zostanie wyświetlona część wspólna wszystkich właściwości dla wszystkich wybranych obiektów.

 Zdarzenia związane z wybranym obiektem w oknie Projekt formularza lub edytorem HTML przy użyciu metadanych modelu COM+ są wyświetlane w oknie **Właściwości** . Na przykład można wybrać przycisk i wyświetlić skojarzone z nim zdarzenia, takie jak zdarzenie `OnClick`, które można połączyć z tym przyciskiem.

 Zdarzenia wyświetlane w oknie **Właściwości** są używane głównie z obiektami, które są powiązane z kodem. Jeśli edytujesz format pliku, który nie ma niczego do wykonania przy użyciu kodu, nie będziesz mieć żadnych zdarzeń. Zdarzenia są wyświetlane w oknie **Właściwości** tylko wtedy, gdy istnieje powiązanie między uruchomionym kodem a określonymi zdarzeniami związanymi z konkretnymi obiektami. Przykładem może być kod związany z wybranym obiektem, który jest wykonywany po aktywowaniu tego obiektu.

 W poniższej tabeli wymieniono podstawowe interfejsy używane przez okno **Właściwości** .

|Nazwa interfejsu|Opis|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii w oknie **Właściwości** i mapuje każdą właściwość na kategorię.|
|[Interfejs IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Uwidacznia metody i właściwości obiektu dla narzędzi programistycznych i innych aplikacji, które obsługują automatyzację.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Zawiera przyciski wielokropka (...) o nazwie *konstruktory* otwierające modalne okna dialogowe systemu Windows zaimplementowane przez sam obiekt. Używane, gdy wartość nie jest łatwo wpisywana przez użytkownika w polu tekstowym. Na przykład może służyć do otwierania selektora kolorów, który określa wartość RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używanych do aktualizowania informacji wyświetlanych w oknie **Właściwości** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest implementowana przez pakietów VSPackage dla każdego okna, które zawiera obiekty możliwe do wybrania z powiązanymi właściwościami do wyświetlenia.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje na temat typu obiektu, takiego jak metody interfejsu i pola struktury.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia pakietów VSPackage otrzymywanie powiadomień o zdarzeniach wyboru i pobieranie informacji o bieżącej hierarchii projektu, elemencie, wartości elementu i kontekście interfejsu użytkownika poleceń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Zapewnia środowisko z dostępem do wielu zaznaczeń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Służy do udostępniania zlokalizowanych nazw na niektórych właściwościach wyświetlanych w oknie **Właściwości** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowane pakietów VSPackage o zmianach w bieżącym zaznaczeniu, wartości elementu lub kontekście interfejsu użytkownika poleceń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowisko o zmianie w bieżącym zaznaczeniu i zapewnia dostęp do hierarchii i informacji o elemencie odnoszących się do nowego zaznaczenia.|

 Więcej informacji o `IDispatch` można znaleźć w bibliotece MSDN.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
- [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)