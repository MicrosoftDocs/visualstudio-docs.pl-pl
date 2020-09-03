---
title: Element menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79a8fafc748274015dac7f8f0938bba37ba5a8bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194351"
---
# <a name="menu-element"></a>Menu, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje jeden element menu. Oto sześć rodzajów menu: Context, menu, MenuController, MenuControllerLatched, Toolbar i ToolWindowToolbar.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
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
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|  
|identyfikator|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|  
|priority|Opcjonalny. Wartość liczbowa, która określa względne położenie menu w grupie menu.|  
|ToolbarPriorityInBand|Opcjonalny. Wartość liczbowa określająca względną pozycję paska narzędzi w paśmie, gdy okno jest zadokowane.|  
|typ|Opcjonalny. Wartość wyliczana, która określa rodzaj elementu.<br /><br /> Jeśli nie istnieje, domyślny typ to menu.<br /><br /> Kontekst<br /> Menu skrótów, które jest wyświetlane, gdy użytkownik kliknie okno prawym przyciskiem myszy. Menu skrótów ma następującą charakterystykę:<br /><br /> -Nie używa pól nadrzędnych i priorytetowych, gdy menu ma być wyświetlane jako menu skrótów.<br />— Może służyć jako podmenu, a także jako menu skrótów. W takim przypadku przestrzegane są pola Identyfikator grupy i priorytet.<br />-Nie zawsze jest dostępna.<br /><br /> Menu skrótów jest wyświetlane tylko wtedy, gdy są spełnione następujące warunki:<br /><br /> -Zostanie wyświetlone okno obsługujące tę wartość.<br />-Procedura obsługi myszy w pakietu VSPackage wykrywa kliknięcie prawym przyciskiem myszy okna, a następnie wywołuje metodę, która obsługuje polecenie.<br />— Menu skrótów jest wyświetlane przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> metody (zalecane podejście) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metodę.<br /><br /> Menu<br /> Udostępnia menu rozwijane. Menu rozwijane ma następującą charakterystykę:<br /><br /> — Szanuje element nadrzędny w jego definicji.<br />-Musi mieć grupę nadrzędną lub CommandPlacement do grupy.<br />-Może być podmenu w dowolnym innym rodzaju menu.<br />-Jest automatycznie wyświetlana za każdym razem, gdy zostanie wyświetlone menu nadrzędne.<br />-Nie wymaga implementacji żadnego kodu pakietu VSPackage, aby był wyświetlany.<br /><br /> MenuController<br /> Udostępnia menu rozwijane przycisk z podziałem, które jest zwykle używane w paskach narzędzi. Menu MenuController ma następującą charakterystykę:<br /><br /> -Musi być zawarte w innym menu za poorednictwem elementu Parent lub CommandPlacement.<br />— Szanuje element nadrzędny w jego definicji.<br />— Może mieć dowolny rodzaj menu jako element nadrzędny.<br />-Jest automatycznie udostępniana za każdym razem, gdy zostanie wyświetlone menu nadrzędne.<br />-Nie wymaga wsparcia programistycznego, aby wyświetlić menu.<br /><br /> Polecenie z menu podzielonego przycisku jest wyświetlane na przycisku menu. Wyświetlane polecenie ma jedną z następujących cech:<br /><br /> -Ostatnie polecenie, które było używane, jeśli polecenie jest nadal wyświetlane i włączone.<br />— Jest to pierwsze wyświetlane polecenie.<br /><br /> MenuControllerLatched<br /> Udostępnia menu rozwijane przycisk z podziałem, dla którego można określić polecenie jako domyślne zaznaczenie, zaznaczając polecenie jako zatrzask.<br /><br /> Zatrzask polecenia to polecenie, które jest oznaczone w menu jako wybrane, zazwyczaj przez wyświetlenie znacznika wyboru. Polecenie może być oznaczone jako zatrzaskowe, jeśli ma ustawioną flagę OLECMDF_LATCHED w implementacji `QueryStatus` metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Menu MenuControllerLatched ma następującą charakterystykę:<br /><br /> -Musi być zawarte w innym menu za pomocą grupy nadrzędnej lub CommandPlacement.<br />— Szanuje element nadrzędny w jego definicji.<br />— Może mieć dowolny rodzaj menu jako element nadrzędny.<br />— Jest udostępniana za każdym razem, gdy zostanie wyświetlone menu nadrzędne.<br />-Nie wymaga wsparcia programistycznego, aby wyświetlić menu.<br /><br /> Polecenie z menu podzielonego przycisku jest wyświetlane na przycisku menu. Wyświetlane polecenie ma jedną z następujących cech:<br /><br /> — Jest to pierwsze wyświetlane polecenie, które jest zatrzask.<br />— Jest to pierwsze wyświetlane polecenie.<br /><br /> Pasek narzędzi<br /> Udostępnia pasek narzędzi. Pasek narzędzi ma następującą charakterystykę:<br /><br /> -Ignoruje element nadrzędny w jego definicji.<br />-Nie można nawiązać podmenu żadnej grupy, a nie za pomocą CommandPlacement.<br />-Zawsze można je wyświetlić, klikając pozycję **paski narzędzi** w menu **Widok** .<br />— Może być wyświetlana przy użyciu [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Nie wymaga żadnego kodu, aby go utworzyć. Aby zapoznać się z przykładem dotyczącym tworzenia paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Udostępnia pasek narzędzi, który jest dołączony do określonego okna narzędzi, tak jak pasek narzędzi jest dołączony do środowiska deweloperskiego.<br /><br /> -Ignoruje element nadrzędny w jego definicji.<br />-Nie można nawiązać podmenu żadnej grupy, a nie za pomocą CommandPlacement.<br />-Jest wyświetlana tylko wtedy, gdy jest wyświetlany okno narzędzia, które obsługuje pasek narzędzi, a pakietu VSPackage jawnie dodaje pasek narzędzi do okna narzędzi. Jest to zazwyczaj wykonywane po utworzeniu okna narzędzia przez uzyskanie właściwości hosta Toolbar (reprezentowanej przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfejs) z ramki okna narzędzi, a następnie wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalny. Element nadrzędny elementu menu.|  
|CommandFlag|Wymagany. Zobacz [element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag dla menu są następujące:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **DontCache**<br />-   **DynamicVisibility** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **IconAndText**<br />-   **Nie dostosowywać**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Ciągi|Wymagany. Zobacz [element Strings](../extensibility/strings-element.md). Element podrzędny `ButtonText` musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje pakietu VSPackage.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)