---
title: Omówienie okna właściwości | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 224fb081f21701433a84121985f90351225036e5
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834768"
---
# <a name="properties-window-overview"></a>Omówienie okna właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Właściwości** okno służy do wyświetlania właściwości obiektów wybranych w dwa główne typy dostępnych w systemie windows [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Te dwa rodzaje systemu windows są:  
  
-   Okna narzędzi, takich jak przeglądarki w Eksploratorze rozwiązań, widoku klas i obiektów  
  
-   Okna dokumentów zawierających takie edytorach i projektantach jako projektant formularzy, edytora XML i edytora HTML  
  
## <a name="using-the-properties-window"></a>W oknie właściwości  
 **Właściwości** oknie zostaną wyświetlone właściwości jednego lub wielu wybranych elementów. Jeśli zaznaczono wiele elementów jest wyświetlany przecięcia wszystkie właściwości dla wszystkich wybranych obiektów.  
  
 Zdarzenia związane z wybranym obiektem w oknie projektowania formularza lub edytora HTML przy użyciu metadanych modelu COM + są wyświetlane w **właściwości** okna. Na przykład, można wybrać przycisk i wyświetlić jego skojarzonego zdarzenia, takie jak `OnClick` zdarzenie, które mogą być połączone z tego przycisku.  
  
 Zdarzenia wyświetlane w **właściwości** okna są używane przede wszystkim z obiektami, które są powiązane z kodu. Jeśli edytujesz format pliku, który nie ma nic wspólnego z kodu nie będą mieć żadnych zdarzeń. Zdarzenia są wyświetlane tylko w **właściwości** okna, jeśli jest powiązaniem między systemem kodu i określonych zdarzeń skojarzone z określonymi obiektami. Na przykład będzie kod związany z wybranego obiektu, który jest wykonywany, gdy ten obiekt jest aktywny.  
  
 W poniższej tabeli wymieniono podstawowe interfejsy używane przez **właściwości** okna.  
  
|Nazwa interfejsu|Opis|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii, aby **właściwości** okna i mapuje każdej właściwości w kategorii.|  
|[IDispatch — interfejs](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Udostępnia metody i właściwości do programowania, narzędzia i inne aplikacje obsługujące automatyzację obiektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Zawiera przyciski wielokropek (...) o nazwie *Konstruktorzy* , Otwórz program windows modalne okno dialogowe implementowany przez sam obiekt. Używane, gdy wartość nie jest łatwo wpisana przez użytkownika w polu tekstowym. Na przykład może być używane otworzyć selektor kolorów, który określa wartość RGB dla Ciebie.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używane do aktualizowania informacji wyświetlanych w **właściwości** okna. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest implementowana przez pakietów VSPackage dla każdego okna, który zawiera obiekty można wybierać z powiązanych właściwości, które mają być wyświetlane.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje o typie obiektu, takiego jak metody interfejsu i pola struktury.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia pakietów VSPackage do otrzymywania powiadomień o zdarzeniach wybór i pobrać informacje o bieżącej hierarchii projektu, element, wartość elementu i kontekstu interfejsu użytkownika polecenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Zapewnia środowisko z dostępem do wielokrotny wybór.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Używane do zapewnienia zlokalizowanych nazw na niektórych właściwości wyświetlane w **właściwości** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowanych pakietów VSPackage zmian w bieżącym zaznaczeniu, wartość elementu lub kontekstu interfejsu użytkownika polecenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowiska zmiany w bieżącym zaznaczeniu i zapewnia dostęp do informacji o hierarchii i elementów odnoszących się do wyboru nowego.|  
  
 Więcej informacji na temat `IDispatch`, zobacz: Biblioteka MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)   
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)
