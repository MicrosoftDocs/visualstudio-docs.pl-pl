---
title: Przegląd okna właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700739"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **Właściwości** służy do wyświetlania właściwości obiektów wybranych w dwóch głównych typach systemu Windows dostępnych w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE). Te dwa typy okien są następujące:  
  
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
|[Interfejs IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Uwidacznia metody i właściwości obiektu dla narzędzi programistycznych i innych aplikacji, które obsługują automatyzację.|  
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
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)   
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)
