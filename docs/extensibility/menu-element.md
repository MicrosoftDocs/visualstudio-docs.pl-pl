---
title: Menu Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c3d2e874a414efd546e3d6841cfaaf9fdd70da5c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951394"
---
# <a name="menu-element"></a>Menu element
Definiuje jeden element menu. Są to sześć menu: Kontekst, Menu, MenuController, MenuControllerLatched, narzędzi i ToolWindowToolbar.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator GUID identyfikatora polecenia identyfikator GUID/ID.|  
|identyfikator|Wymagana. Identyfikator GUID/ID identyfikator polecenia.|  
|priority|Opcjonalna. Wartość liczbowa, która określa względne położenie menu w grupie menu.|  
|ToolbarPriorityInBand|Opcjonalna. Wartość liczbowa, który określa względne położenie paska narzędzi w przedziale, gdy okno jest zadokowany.|  
|— typ|Opcjonalna. Wartość wyliczana, który określa typ elementu.<br /><br /> Jeśli nie istnieje, domyślnym typem jest Menu.<br /><br /> Kontekst<br /> Menu skrótów, która jest wyświetlana, gdy użytkownik kliknie prawym przyciskiem myszy okno. Menu skrótów ma następującą charakterystykę:<br /><br /> -Nie używa **nadrzędnego** i **priorytet** pola, gdy menu ma być wyświetlany jako menu podręczne.<br />-Może służyć jako podmenu, a także jako menu podręczne. W takim przypadku zarówno **identyfikator grupy** i **priorytet** pola są przestrzegane.<br />— To nie jest zawsze dostępna.<br /><br /> Menu podręczne jest wyświetlana tylko wtedy, gdy są spełnione następujące warunki:<br /><br /> Zostanie wyświetlone okno, udostępniającym go.<br />-Obsługi myszy w pakietu VSPackage wykrywa, kliknij prawym przyciskiem myszy w oknie, a następnie wywołuje metodę, która obsługuje polecenie.<br />-Menu skrótów wyświetlony po wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> — metoda (podejście zalecane) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metody.<br /><br /> Menu<br /> Zawiera menu rozwijane. Menu rozwijane ma następującą charakterystykę:<br /><br /> -Względem elementu nadrzędnego w ich definicji.<br />-Musi mieć grupę nadrzędną lub CommandPlacement do grupy.<br />— Może być podmenu w każdego rodzaju menu.<br />-Jest automatycznie wyświetlana zawsze wtedy, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wykonania dowolnego kodu VSPackage, aby był wyświetlany.<br /><br /> MenuController<br /> Zawiera menu rozwijane przycisku podziału, która zwykle jest używana na paskach narzędzi. MenuController menu ma następującą charakterystykę:<br /><br /> -Musi być zawarty w innym menu przez nadrzędne lub CommandPlacement.<br />-Względem elementu nadrzędnego w ich definicji.<br />— Może mieć wszelkiego rodzaju menu jako klasy nadrzędnej.<br />-Jest automatycznie udostępniane w każdym przypadku, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wsparcia programowego się z wyświetlonego menu.<br /><br /> Polecenia menu przycisku podziału jest wyświetlany na przycisku menu. Polecenia wyświetlane ma jedną z następujących właściwości:<br /><br /> -Jest ostatnie polecenie, który został użyty, jeśli polecenie jest nadal wyświetlany.<br />-Jest pierwsze polecenie wyświetlane.<br /><br /> MenuControllerLatched<br /> Zawiera menu rozwijane przycisku podziału, dla którego polecenie może być określona jako ustawienie domyślne, oznaczając polecenie jako zablokowane.<br /><br /> Polecenie zatrzaśnięcia to polecenie oznaczonej w menu wybierany, zwykle za pomocą wyświetlania znacznik wyboru. Polecenia można oznaczyć jako zablokowane, jeśli ma on OLECMDF_LATCHED Flaga go w celu wykonania `QueryStatus` metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. MenuControllerLatched menu ma następującą charakterystykę:<br /><br /> -Musi być zawarty w innym menu przy użyciu grupy nadrzędnej lub CommandPlacement.<br />-Względem elementu nadrzędnego w ich definicji.<br />— Może mieć wszelkiego rodzaju menu jako klasy nadrzędnej.<br />-Staje się dostępny zawsze, gdy zostanie wyświetlone menu jej nadrzędnej.<br />— Nie wymaga wsparcia programowego się z wyświetlonego menu.<br /><br /> Polecenia menu przycisku podziału jest wyświetlany na przycisku menu. Polecenia wyświetlane ma jedną z następujących właściwości:<br /><br /> -Jest pierwsze polecenie wyświetlany jest zablokowane.<br />-Jest pierwsze polecenie wyświetlane.<br /><br /> Pasek narzędzi<br /> Zawiera pasek narzędzi. Pasek narzędzi ma następującą charakterystykę:<br /><br /> -Ignoruje element nadrzędny w ich definicji.<br />-Nie można wprowadzać podmenu żadnej grupy nie nawet przy użyciu CommandPlacement.<br />— Zawsze można wyświetlić, klikając pozycję **pasków narzędzi** na **widoku** menu.<br />— Można wyświetlić za pomocą [VisibilityItem](../extensibility/visibilityitem-element.md).<br />— Nie wymaga żadnego kodu, aby go utworzyć. Na przykład o sposobach tworzenia paska narzędzi, zobacz [dodać pasek narzędzi](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Zawiera pasek narzędzi, który jest dołączony do okna narzędzi określonych, tak samo, jak pasek narzędzi jest dołączony do środowiska deweloperskiego.<br /><br /> -Ignoruje element nadrzędny w ich definicji.<br />-Nie można wprowadzać podmenu żadnej grupy nie nawet przy użyciu CommandPlacement.<br />-Jest wyświetlana tylko wtedy, gdy okna narzędzi, które hostuje pasku jest wyświetlane i pakietu VSPackage jawnie dodaje pasek narzędzi okna narzędzia. Zazwyczaj jest to wykonywane podczas tworzenia okna narzędzi, uzyskując właściwości hosta paska narzędzi (reprezentowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfejsu) z ramki okna narzędzi i następnie wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalna. Element nadrzędny elementu menu.|  
|CommandFlag|Wymagana. Zobacz [Command flag, element](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag Menu są następujące:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **DontCache**<br />-   **DynamicVisibility** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Ciągi|Wymagana. Zobacz [Strings, element](../extensibility/strings-element.md). Element podrzędny `ButtonText` element musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli poleceń w usłudze Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)