---
title: Przegląd okna właściwości | Microsoft Docs
description: Zapoznaj się z interfejsami używanymi do współpracy z okno Właściwości w środowisku IDE programu Visual Studio w tym omówieniu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5f378200072df603817a445a9c3406cf62233c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061007"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
Okno **Właściwości** służy do wyświetlania właściwości obiektów wybranych w dwóch głównych typach systemu Windows dostępnych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku programistycznym (IDE). Te dwa typy okien są następujące:

- Okna narzędzi, takie jak Eksplorator rozwiązań, Widok klasy i Przeglądarka obiektów

- Okna dokumentów zawierające takie redaktorzy i projektanci jak Projektant formularzy, Edytor XML i Edytor HTML

## <a name="using-the-properties-window"></a>Korzystanie z okna właściwości
 W oknie **Właściwości** są wyświetlane właściwości jednego lub wielu zaznaczonych elementów. Jeśli wybrano wiele elementów, zostanie wyświetlona część wspólna wszystkich właściwości dla wszystkich wybranych obiektów.

 Zdarzenia związane z wybranym obiektem w oknie Projekt formularza lub edytorem HTML przy użyciu metadanych modelu COM+ są wyświetlane w oknie **Właściwości** . Na przykład można wybrać przycisk i wyświetlić skojarzone z nim zdarzenia, takie jak `OnClick` zdarzenie, które może być połączone z tym przyciskiem.

 Zdarzenia wyświetlane w oknie **Właściwości** są używane głównie z obiektami, które są powiązane z kodem. Jeśli edytujesz format pliku, który nie ma niczego do wykonania przy użyciu kodu, nie będziesz mieć żadnych zdarzeń. Zdarzenia są wyświetlane w oknie **Właściwości** tylko wtedy, gdy istnieje powiązanie między uruchomionym kodem a określonymi zdarzeniami związanymi z konkretnymi obiektami. Przykładem może być kod związany z wybranym obiektem, który jest wykonywany po aktywowaniu tego obiektu.

 W poniższej tabeli wymieniono podstawowe interfejsy używane przez okno **Właściwości** .

|Nazwa interfejsu|Opis|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii w oknie **Właściwości** i mapuje każdą właściwość na kategorię.|
|[Interfejs IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Uwidacznia metody i właściwości obiektu dla narzędzi programistycznych i innych aplikacji, które obsługują automatyzację.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Zawiera przyciski wielokropka (...) o nazwie *konstruktory* otwierające modalne okna dialogowe systemu Windows zaimplementowane przez sam obiekt. Używane, gdy wartość nie jest łatwo wpisywana przez użytkownika w polu tekstowym. Na przykład może służyć do otwierania selektora kolorów, który określa wartość RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używanych do aktualizowania informacji wyświetlanych w oknie **Właściwości** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Program jest implementowany przez pakietów VSPackage dla każdego okna, które zawiera obiekty możliwe do wybrania z powiązanymi właściwościami do wyświetlenia.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje na temat typu obiektu, takiego jak metody interfejsu i pola struktury.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia pakietów VSPackage otrzymywanie powiadomień o zdarzeniach wyboru i pobieranie informacji o bieżącej hierarchii projektu, elemencie, wartości elementu i kontekście interfejsu użytkownika poleceń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Zapewnia środowisko z dostępem do wielu zaznaczeń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Służy do udostępniania zlokalizowanych nazw na niektórych właściwościach wyświetlanych w oknie **Właściwości** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowane pakietów VSPackage o zmianach w bieżącym zaznaczeniu, wartości elementu lub kontekście interfejsu użytkownika poleceń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowisko o zmianie w bieżącym zaznaczeniu i zapewnia dostęp do hierarchii i informacji o elemencie odnoszących się do nowego zaznaczenia.|

 Aby uzyskać więcej informacji na temat `IDispatch` , zobacz Biblioteka MSDN.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
- [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)
