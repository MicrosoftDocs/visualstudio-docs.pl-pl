---
title: Element menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702602"
---
# <a name="menu-element"></a>Element menu
Definiuje jeden element menu. Są to sześć rodzajów menu: Kontekst, Menu, MenuController, MenuControllerLatched, Pasek narzędzi i ToolWindowToolbar.

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
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|id|Wymagany. Identyfikator polecenia GUID/ID.|
|priority|Element opcjonalny. Wartość liczbowa określająca względne położenie menu w grupie menu.|
|Pasek narzędziPriorityInBand|Element opcjonalny. Wartość liczbowa określająca względną pozycję paska narzędzi w paśmie, gdy okno jest zadokowane.|
|type|Element opcjonalny. Wyliczona wartość, która określa rodzaj elementu.<br /><br /> Jeśli nie jest obecny, domyślnym typem jest Menu.<br /><br /> Kontekst<br /> Menu skrótów wyświetlane po kliknięciu prawym przyciskiem myszy okna przez użytkownika. Menu skrótów ma następujące cechy:<br /><br /> - Nie używa pól **Nadrzędny** i **Priorytet,** gdy menu ma być wyświetlane jako menu skrótów.<br />- Może być używany jako podmenu, a także jako menu skrótów. W takim przypadku przestrzegane są pola **Identyfikator grupy** i **Priorytet.**<br />- Nie zawsze jest dostępny.<br /><br /> Menu skrótów jest wyświetlane tylko wtedy, gdy spełnione są następujące warunki:<br /><br /> - Wyświetlane jest okno, w którym jest ono hostowane.<br />- Obsługi myszy w VSPackage wykrywa kliknięcie prawym przyciskiem myszy w oknie, a następnie wywołuje metodę, która obsługuje polecenia.<br />- Menu skrótów jest wyświetlane <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> (zalecane podejście) lub metody.<br /><br /> Menu<br /> Zawiera menu rozwijane. Menu rozwijane ma następujące cechy:<br /><br /> - Szanuje rodzica w swojej definicji.<br />- Musi mieć grupę nadrzędną lub CommandPlacement do grupy.<br />- Może być podmenu w każdym innym rodzaju menu.<br />- Jest automatycznie wyświetlany za każdym razem, gdy wyświetlane jest jego menu nadrzędne.<br />- Nie wymaga implementacji żadnego kodu VSPackage, aby go wyświetlić.<br /><br /> Kontroler menu<br /> Zawiera menu rozwijane z podziałem przycisków, które jest zwykle używane na paskach narzędzi. Menu MenuController ma następujące cechy:<br /><br /> - Musi być zawarte w innym menu za pośrednictwem nadrzędnego lub CommandPlacement.<br />- Szanuje rodzica w swojej definicji.<br />- Może mieć wszelkiego rodzaju menu jako jego rodzica.<br />- Jest automatycznie udostępniany za każdym razem, gdy wyświetlane jest jego menu nadrzędne.<br />- Nie wymaga obsługi programowej, aby menu było wyświetlane.<br /><br /> Na przycisku menu menu jest wyświetlane polecenie z menu z podzielonym przyciskiem. Wyświetlane polecenie ma jedną z następujących cech:<br /><br /> - Jest to ostatnie polecenie, które zostało użyte, jeśli polecenie jest nadal wyświetlane i włączone.<br />- Jest to pierwsze wyświetlone polecenie.<br /><br /> MenuControllerLatched<br /> Zawiera menu rozwijane z podziałem przycisków, dla którego polecenie można określić jako domyślne, oznaczając polecenie jako zatrzaśnięte.<br /><br /> Zatrzaśnięte polecenie jest poleceniem oznaczonym w menu jako zaznaczone, zazwyczaj przez wyświetlenie znacznika wyboru. Polecenie może być oznaczone jako zatrzaśnięte, jeśli ma ustawioną na `QueryStatus` nim flagę OLECMDF_LATCHED w implementacji metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Menu Menu Menu MenuControllerLatched ma następujące cechy:<br /><br /> - Musi być zawarte w innym menu za pośrednictwem grupy nadrzędnej lub CommandPlacement.<br />- Szanuje rodzica w swojej definicji.<br />- Może mieć wszelkiego rodzaju menu jako jego rodzica.<br />- Jest udostępniany za każdym razem, gdy wyświetlane jest jego menu nadrzędne.<br />- Nie wymaga obsługi programowej, aby menu było wyświetlane.<br /><br /> Na przycisku menu menu jest wyświetlane polecenie z menu z podzielonym przyciskiem. Wyświetlane polecenie ma jedną z następujących cech:<br /><br /> - Jest to pierwsze wyświetlane polecenie, które jest zatrzaśnięte.<br />- Jest to pierwsze wyświetlone polecenie.<br /><br /> Pasek narzędzi<br /> Udostępnia pasek narzędzi. Pasek narzędzi ma następujące właściwości:<br /><br /> - Ignoruje nadrzędnego w jego definicji.<br />- Nie można zrobić podmenu żadnej grupy, nawet za pomocą CommandPlacement.<br />- Zawsze można wyświetlić, klikając **paski narzędzi** w menu **Widok.**<br />- Może być wyświetlany za pomocą [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- Nie wymaga żadnego kodu, aby go utworzyć. Aby uzyskać przykład tworzenia paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).<br /><br /> Pasek narzędzia Narzędzia Do okien<br /> Udostępnia pasek narzędzi, który jest dołączony do okna określonego narzędzia, podobnie jak pasek narzędzi jest dołączony do środowiska programistycznego.<br /><br /> - Ignoruje nadrzędnego w jego definicji.<br />- Nie można zrobić podmenu żadnej grupy, nawet za pomocą CommandPlacement.<br />- Jest wyświetlany tylko wtedy, gdy okno narzędzia, które obsługuje pasek narzędzi jest wyświetlany i VSPackage jawnie dodaje pasek narzędzi do okna narzędzia. Zazwyczaj odbywa się to, gdy okno narzędzia jest tworzony przez uzyskanie właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> hosta paska narzędzi (reprezentowane <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> przez interfejs) z ramki okna narzędzia, a następnie wywołanie metody.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Element opcjonalny. Element nadrzędny elementu menu.|
|CommandFlag (Żużel dowodzenia)|Wymagany. Zobacz [Element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag dla menu są następujące:<br /><br /> -   **ZawszeKrówz**<br />-   **Domyślnieokło**<br />-   **DefaultInvisible** — ta flaga nie wpływa na wyświetlanie pasków narzędzi.<br />-   **DontCache (DontCache)**<br />-   **DynamicVisibility** — ta flaga nie wpływa na wyświetlanie pasków narzędzi.<br />-   **Ikona Itext**<br />-   **NoCustomize (Niezwyklij)**<br />-   **Lista NotInTB**<br />-   **NoToolbarKrówka**<br />-   **Zmiany tekstu**<br />-   **TextIsAnchorCommand (Wychwytyw.**|
|Ciągi|Wymagany. Zobacz [Strings element](../extensibility/strings-element.md). Element `ButtonText` podrzędny musi być zdefiniowany.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Menu](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje VSPackage.|

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
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
