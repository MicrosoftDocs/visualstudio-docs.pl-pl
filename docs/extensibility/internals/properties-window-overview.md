---
title: Przegląd okna właściwości | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706028"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
Okno **Właściwości** służy do wyświetlania właściwości obiektów wybranych w dwóch głównych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] typach okien dostępnych w zintegrowanym środowisku programistycznym (IDE). Te dwa typy okien to:

- Okna narzędzi, takie jak Eksplorator rozwiązań, Widok klasy i przeglądarka obiektów

- Okna dokumentów zawierające takich edytorów i projektantów, jak projektant formularzy, edytor XML i edytor HTML

## <a name="using-the-properties-window"></a>Korzystanie z okna Właściwości
 Okno **Właściwości** wyświetla właściwości pojedynczych lub wielu zaznaczonych elementów. Jeśli zaznaczono wiele elementów, zostanie wyświetlone przecięcie wszystkich właściwości wszystkich zaznaczonych obiektów.

 Zdarzenia związane z zaznaczonym obiektem w oknie projektu formularza lub edytorze HTML przy użyciu metadanych COM+ są wyświetlane w oknie **Właściwości.** Na przykład można wybrać przycisk i wyświetlić skojarzone `OnClick` z nim zdarzenia, takie jak zdarzenie, które można połączyć z tym przyciskiem.

 Zdarzenia wyświetlane w oknie Właściwości są używane głównie z **obiektami,** które są powiązane z kodem. Jeśli edytujesz format pliku, który nie ma nic wspólnego z kodem, nie będziesz mieć żadnych zdarzeń. Zdarzenia są wyświetlane tylko w oknie **Właściwości,** gdy istnieje powiązanie między uruchomionym kodem a niektórymi zdarzeniami skojarzonymi z określonymi obiektami. Przykładem tego może być kod za wybrany obiekt, który jest wykonywany, gdy ten obiekt jest aktywowany.

 W poniższej tabeli wymieniono interfejsy podstawowe używane przez okno **Właściwości.**

|Nazwa interfejsu|Opis|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii do **właściwości** okna i mapuje każdą właściwość do kategorii.|
|[Interfejs IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Udostępnia metody i właściwości obiektu do programowania narzędzi i innych aplikacji, które obsługują automatyzację.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Zawiera wielokropek (...) przyciski zwane *konstruktorami,* które otwierają modalne okna dialogowe zaimplementowane przez sam obiekt. Używane, gdy wartość nie jest łatwo wpisywane przez użytkownika w polu tekstowym. Na przykład może służyć do otwierania selektora kolorów, który określa wartość RGB dla Ciebie.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używanych do aktualizowania informacji wyświetlanych w oknie **Właściwości.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>jest implementowany przez VSPackages dla każdego okna, które zawiera wybieralne obiekty z powiązanych właściwości, które mają być wyświetlane.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje o typie obiektu, takie jak metody interfejsu i pola struktury.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia vspackages otrzymywać powiadomienia o zdarzeniach wyboru i pobrać informacje o bieżącej hierarchii projektu, element, wartość elementu i kontekst interfejsu użytkownika polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Zapewnia środowisku dostęp do wielu wyborów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Służy do dostarczania zlokalizowanych nazw w niektórych właściwościach wyświetlanych w oknie **Właściwości.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowane vspackages zmian w bieżącym zaznaczeniu, wartość elementu lub kontekstu interfejsu użytkownika polecenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowisko o zmianie w bieżącym zaznaczeniu i zapewnia dostęp do hierarchii i informacji o elemencie związanych z nowym wyborem.|

 Aby uzyskać `IDispatch`więcej informacji na temat , zobacz bibliotekę MSDN.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
- [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)
