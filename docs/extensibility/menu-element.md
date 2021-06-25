---
title: Menu, element | Microsoft Docs
description: 'Element Menu definiuje jeden element menu. Rodzaje menu to: Context (Kontekst), Menu (Menu), MenuController (MenuController), MenuControllerLatched (MenuControllerLatched), Toolbar (Pasek narzędzi) i ToolWindowToolbar (NarzędzieWindowToolbar).'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2ffa029dd05e7fe3d32a9df4a1d06c90c8b9c6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901542"
---
# <a name="menu-element"></a>Menu, element
Definiuje jeden element menu. Są to sześć rodzajów menu: Kontekst, Menu, MenuController, MenuControllerLatched, Pasek narzędzi i NarzędzieWindowToolbar.

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
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.|
|identyfikator|Wymagane. Identyfikator identyfikatora GUID/ID polecenia.|
|priority|Opcjonalny. Wartość liczbowa określająca względną pozycję menu w grupie menu.|
|ToolbarPriorityInBand|Opcjonalny. Wartość liczbowa określająca względną pozycję paska narzędzi w pasmie, gdy okno jest zadokowane.|
|typ|Opcjonalny. Wartość wyliczana określająca rodzaj elementu.<br /><br /> Jeśli nie ma, domyślnym typem jest Menu.<br /><br /> Kontekst<br /> Menu skrótów, które jest wyświetlane, gdy użytkownik kliknie okno prawym przyciskiem myszy. Menu skrótów ma następujące cechy:<br /><br /> - Nie używa pola **Nadrzędne i** **Priorytet,** gdy menu ma być wyświetlane jako menu skrótów.<br />- Może służyć jako podmenu, a także jako menu skrótów. W takim przypadku są przestrzegane zarówno **pola Identyfikator** **grupy, jak i** Priorytet.<br />— Nie zawsze jest dostępna.<br /><br /> Menu skrótów jest wyświetlane tylko wtedy, gdy spełnione są następujące warunki:<br /><br /> — Zostanie wyświetlone okno, które go hostuje.<br />- Program obsługi myszy w pakietach VSPackage wykrywa kliknięcie prawym przyciskiem myszy w oknie, a następnie wywołuje metodę, która obsługuje polecenie .<br />- Menu skrótów jest wyświetlane przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> metody (zalecane podejście) lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metody .<br /><br /> Menu<br /> Udostępnia menu rozwijane. Menu rozwijane ma następujące cechy:<br /><br /> - Respektuje element nadrzędny w swojej definicji.<br />- Musi mieć grupę nadrzędną lub CommandPlacement do grupy.<br />- Może być podmenu w dowolnym innym rodzaju menu.<br />— jest automatycznie wyświetlany za każdym razem, gdy zostanie wyświetlone jego menu nadrzędne.<br />- Nie wymaga implementacji żadnego kodu VSPackage, aby go wyświetlić.<br /><br /> MenuController<br /> Udostępnia menu rozwijane z podzielonym przyciskiem, które jest zwykle używane na paskach narzędzi. Menu MenuController ma następujące cechy:<br /><br /> - Musi znajdować się w innym menu za pośrednictwem elementu nadrzędnego lub CommandPlacement.<br />- Respektuje element nadrzędny w swojej definicji.<br />- Może mieć menu dowolnego rodzaju jako jego element nadrzędny.<br />— jest automatycznie udostępniane za każdym razem, gdy zostanie wyświetlone jego menu nadrzędne.<br />- Nie wymaga obsługi programowej do wyświetlania menu.<br /><br /> Polecenie z menu przycisku podziału jest wyświetlane na przycisku menu. Wyświetlone polecenie ma jedną z następujących cech:<br /><br /> - Jest to ostatnie polecenie, które zostało użyte, jeśli polecenie jest nadal wyświetlane i włączone.<br />- Jest to pierwsze wyświetlone polecenie.<br /><br /> MenuControllerLatched<br /> Udostępnia menu rozwijane z podzielonym przyciskiem, dla którego można określić polecenie jako wybór domyślny, oznaczając polecenie jako zatrzaśowane.<br /><br /> Zatrzaśczone polecenie jest poleceniem, które jest oznaczone w menu jako wybrane, zwykle wyświetlając znacznik wyboru. Polecenie może być oznaczone jako zatrzaśowane, jeśli ma OLECMDF_LATCHED flagę ustawioną na nim w implementacji `QueryStatus` metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Menu MenuControllerLatched ma następujące cechy:<br /><br /> - Musi znajdować się w innym menu za pośrednictwem grupy nadrzędnej lub CommandPlacement.<br />- Respektuje element nadrzędny w swojej definicji.<br />- Może mieć menu dowolnego rodzaju jako jego element nadrzędny.<br />— jest udostępniane za każdym razem, gdy zostanie wyświetlone jego menu nadrzędne.<br />- Nie wymaga obsługi programowej do wyświetlania menu.<br /><br /> Polecenie z menu przycisku podziału jest wyświetlane na przycisku menu. Wyświetlone polecenie ma jedną z następujących cech:<br /><br /> - Jest to pierwsze wyświetlone polecenie, które jest zatrzaśne.<br />- Jest to pierwsze wyświetlone polecenie.<br /><br /> Pasek narzędzi<br /> Udostępnia pasek narzędzi. Pasek narzędzi ma następujące cechy:<br /><br /> - Ignoruje element nadrzędny w swojej definicji.<br />- Nie można stać się podmenu żadnej grupy, nawet przy użyciu CommandPlacement.<br />— Zawsze można wyświetlić, klikając pozycję **Paski narzędzi** w menu **Widok.**<br />- Można wyświetlić za pomocą [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- Nie wymaga żadnego kodu, aby go utworzyć. Aby uzyskać przykład sposobu tworzenia paska narzędzi, zobacz [Dodawanie paska narzędzi](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Udostępnia pasek narzędzi dołączony do określonego okna narzędzi, tak jak pasek narzędzi jest dołączony do środowiska programowego.<br /><br /> - Ignoruje element nadrzędny w swojej definicji.<br />- Nie można stać się podmenu żadnej grupy, nawet przy użyciu CommandPlacement.<br />- Jest wyświetlana tylko wtedy, gdy zostanie wyświetlone okno narzędzi, które hostuje pasek narzędzi, a pakiet VSPackage jawnie doda pasek narzędzi do okna narzędzi. Zwykle jest to wykonywane, gdy okno narzędzia jest tworzone przez uzyskanie właściwości hosta paska narzędzi (reprezentowanej przez interfejs) z ramki okna narzędzia, a następnie wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metody .|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Opcjonalny. Element nadrzędny elementu menu.|
|CommandFlag|Wymagane. Zobacz [element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag menu są następujące:<br /><br /> -   **Zawsze tworzeć**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **DontCache**<br />-   **DynamicVisibility** — ta flaga nie ma wpływu na wyświetlanie pasków narzędzi.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|Ciągi|Wymagane. Zobacz [ciągi, element](../extensibility/strings-element.md). Element `ButtonText` podrzędny musi być zdefiniowany.|
|Adnotacja|Opcjonalny komentarz.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu implementowanych przez pakiet VSPackage.|

## <a name="example"></a>Przykład

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Zobacz także
- [Visual Studio polecenia tabeli (pliki vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
