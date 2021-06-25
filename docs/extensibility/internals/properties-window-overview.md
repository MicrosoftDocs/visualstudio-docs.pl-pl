---
title: Omówienie okna właściwości | Microsoft Docs
description: Dowiedz się więcej o interfejsach używanych do interakcji z okno Właściwości w Visual Studio IDE w tym przeglądzie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0b775cbc96303f53bcd795b2121d10af83714e6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899670"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
Okno **Właściwości** służy do wyświetlania właściwości obiektów wybranych w dwóch głównych typach okien dostępnych w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanym środowisku projektowym (IDE). Te dwa typy okien to:

- Okna narzędzi, takie jak Eksplorator rozwiązań, Widok klasy i przeglądarka obiektów

- Okna dokumentów zawierające takie edytory i projektantów jak projektant formularzy, edytor XML i edytor HTML

## <a name="using-the-properties-window"></a>Korzystanie z okna właściwości
 W **oknie** Właściwości są wyświetlane właściwości pojedynczych lub wielu wybranych elementów. Jeśli wybrano wiele elementów, zostanie wyświetlony przecięcie wszystkich właściwości dla wszystkich wybranych obiektów.

 Zdarzenia związane z wybranym obiektem w oknie projektowania formularza lub edytorze HTML przy użyciu metadanych COM+ są wyświetlane w **oknie** Właściwości. Możesz na przykład wybrać przycisk i wyświetlić skojarzone z nim zdarzenia, takie jak zdarzenie, które można `OnClick` połączyć z tym przyciskiem.

 Zdarzenia wyświetlane w **oknie Właściwości** są używane głównie z obiektami powiązanymi z kodem. Jeśli edytujesz format pliku, który nie ma nic z kodem, nie będziesz mieć żadnych zdarzeń. Zdarzenia są wyświetlane w oknie **Właściwości** tylko wtedy, gdy istnieje powiązanie między uruchomionym kodem i pewnymi zdarzeniami skojarzonymi z określonymi obiektami. Przykładem może być kod za wybranym obiektem, który jest wykonywany po aktywowaniu tego obiektu.

 W poniższej tabeli wymieniono podstawowe interfejsy używane przez **okno** Właściwości.

|Nazwa interfejsu|Opis|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii w oknie **Właściwości** i mapuje każdą właściwość na kategorię.|
|[IDispatch, interfejs](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Uwidacznia metody i właściwości obiektu dla narzędzi programistycznych i innych aplikacji, które obsługują automatyzację.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Udostępnia przyciski wielokropka (...) nazywane *konstruktorami,* które otwierają modalne okna dialogowe implementowane przez sam obiekt. Używana, gdy użytkownik nie może łatwo wpisać wartości w polu tekstowym. Na przykład może służyć do otwierania s wyboru kolorów, który określa wartość RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używanych do aktualizowania informacji wyświetlanych w **oknie** Właściwości. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Jest implementowany przez pakiet VSPackages dla każdego okna zawierającego obiekty, które można wybrać, z powiązanymi właściwościami do wyświetlania.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje o typie obiektu, takie jak metody interfejsu i pola struktury.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia pakietom VSPackage odbieranie powiadomień o zdarzeniach wyboru i pobieranie informacji o bieżącej hierarchii projektu, elemencie, wartości elementu i kontekście interfejsu użytkownika polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Zapewnia środowisku dostęp do wielu wyborów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Służy do podania zlokalizowanych nazw niektórych właściwości wyświetlanych w **oknie** Właściwości.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowanych pakietów VSPackage o zmianach do bieżącego zaznaczenia, wartości elementu lub kontekstu interfejsu użytkownika polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowisko o zmianie bieżącego zaznaczenia i zapewnia dostęp do informacji o hierarchii i elementach związanych z nowym wyborem.|

 Aby uzyskać więcej informacji `IDispatch` na temat programu , zobacz bibliotekę MSDN.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
- [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)
