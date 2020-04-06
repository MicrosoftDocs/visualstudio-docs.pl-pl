---
title: Udostępnianie poleceń | Dokumenty firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707331"
---
# <a name="making-commands-available"></a>Udostępnianie poleceń

Gdy wiele vspackages są dodawane do programu Visual Studio, interfejs użytkownika (UI) może stać się przepełnione polecenia. Pakiet można zaprogramować w celu zmniejszenia tego problemu w następujący sposób:

- Zaprogramuj pakiet tak, aby był ładowany tylko wtedy, gdy użytkownik tego wymaga.

- Program pakietu tak, aby jego polecenia są wyświetlane tylko wtedy, gdy mogą być wymagane w kontekście bieżącego stanu zintegrowanego środowiska programistycznego (IDE).

## <a name="delayed-loading"></a>Opóźniony załadunek

Typowym sposobem włączenia opóźnionego ładowania jest zaprojektowanie vspackage tak, aby jego polecenia były wyświetlane w interfejsie użytkownika, ale sam pakiet nie jest ładowany, dopóki użytkownik nie kliknie jednego z poleceń. Aby to osiągnąć, w pliku vsct należy utworzyć polecenia, które nie mają flag poleceń.

W poniższym przykładzie przedstawiono definicję polecenia menu z pliku vsct. Jest to polecenie generowane przez szablon pakietu programu Visual Studio po wybraniu opcji **Polecenie menu** w szablonie.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

W przykładzie, jeśli grupa `MyMenuGroup`nadrzędna , jest elementem podrzędnym menu najwyższego poziomu, takiego jak menu **Narzędzia,** polecenie będzie widoczne w tym menu, ale pakiet, który wykonuje polecenie, nie zostanie załadowany, dopóki polecenie nie zostanie kliknięty przez użytkownika. Jednak programowanie polecenia do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zaimplementowania interfejsu, można włączyć pakiet do załadowania, gdy menu, które zawiera polecenie jest po raz pierwszy rozwinięta.

Należy zauważyć, że opóźnione ładowanie może również poprawić wydajność uruchamiania.

## <a name="current-context-and-the-visibility-of-commands"></a>Bieżący kontekst i widoczność poleceń

Polecenia VSPackage można zaprogramować jako widoczne lub ukryte, w zależności od bieżącego stanu danych VSPackage lub akcji, które są obecnie istotne. Można włączyć VSPackage ustawić stan jego poleceń, zazwyczaj przy użyciu <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> metody z interfejsu, ale wymaga vsPackage do załadowania, zanim będzie można wykonać kod. Zamiast tego zaleca się włączenie IDE do zarządzania widocznością poleceń bez ładowania pakietu. Aby to zrobić, w pliku vsct skojarz polecenia z co najmniej jednym kontekstem specjalnych interfejsu użytkownika. Te konteksty interfejsu użytkownika są identyfikowane przez identyfikator GUID znany jako *identyfikator GUID kontekstu polecenia*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitoruje zmiany wynikające z działań użytkownika, takich jak ładowanie projektu lub przechodzenie od edycji do budynku. W miarę pojawiania się zmian wygląd IDE jest automatycznie modyfikowany. W poniższej tabeli przedstawiono cztery [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] główne konteksty zmiany IDE, który monitoruje.

| Typ kontekstu | Opis |
|-------------------------| - |
| Aktywny typ projektu | W przypadku większości `GUID` typów projektów ta wartość jest taka sama jak identyfikator GUID vspackage, który implementuje projekt. Jednak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty używają typu `GUID` projektu jako wartości. |
| Aktywne okno | Zazwyczaj jest to ostatnie aktywne okno dokumentu, które ustanawia bieżący kontekst interfejsu użytkownika dla powiązań kluczy. Jednak może to być również okno narzędzia, które ma tabelę powiązania kluczy, która przypomina wewnętrzna przeglądarka sieci Web. W przypadku okien dokumentów z wieloma kartami, takich jak `GUID`edytor HTML, każda karta ma inny kontekst poleceń . |
| Usługa aktywnego języka | Usługa języka skojarzona z plikiem, który jest obecnie wyświetlany w edytorze tekstu. |
| Aktywne okno narzędzia | Okno narzędzia, które jest otwarte i ma fokus. |

Piątym głównym obszarem kontekstu jest stan interfejsu użytkownika IDE. Konteksty interfejsu użytkownika są identyfikowane przez aktywny kontekst `GUID`polecenia s, w następujący sposób:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Te identyfikatory GUID są oznaczone jako aktywne lub nieaktywne, w zależności od bieżącego stanu IDE. Wiele kontekstów interfejsu użytkownika może być aktywnych w tym samym czasie.

### <a name="hide-and-display-commands-based-on-context"></a>Ukrywanie i wyświetlanie poleceń na podstawie kontekstu

Można wyświetlić lub ukryć polecenie pakietu w IDE bez ładowania samego pakietu. Aby to zrobić, zdefiniuj polecenie w pliku `DefaultDisabled`vsct pakietu `DefaultInvisible`za pomocą flag , i `DynamicVisibility` flagi polecenia i dodanie jednego lub więcej [elementów VisibilityItem](../../extensibility/visibilityitem-element.md) do sekcji [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Gdy kontekst `GUID` określonego polecenia staje się aktywny, polecenie jest wyświetlane bez ładowania pakietu.

### <a name="custom-context-guids"></a>Identyfikatory GUID kontekstu niestandardowego

Jeśli identyfikator GUID kontekstu polecenia nie jest jeszcze zdefiniowany, można zdefiniować go w programie VSPackage, a następnie zaprogramować go jako aktywny lub nieaktywny zgodnie z wymaganiami do kontrolowania widoczności poleceń. Skorzystaj <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> z usługi, aby:

- Zarejestruj identyfikatory GUID kontekstu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (wywołując metodę).

- Pobierz stan kontekstu `GUID` (wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodę).

- Włącz `GUID`i wyłącz kontekst (wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodę).

    > [!CAUTION]
    > Upewnij się, że vspackage nie wpływa na stan istniejącego identyfikatora GUID kontekstu, ponieważ inne VSPackages może zależeć od nich.

## <a name="example"></a>Przykład

Poniższy przykład polecenia VSPackage pokazuje dynamiczną widoczność polecenia, które jest zarządzane przez konteksty poleceń bez ładowania vspackage.

Polecenie jest ustawione do włączenia i wyświetlania, gdy istnieje rozwiązanie; oznacza to, że gdy jeden z następujących identyfikatorów GUID kontekstu polecenia jest aktywny:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

W przykładzie należy zauważyć, że każda flaga polecenia jest oddzielnym [elementem flaga polecenia.](../../extensibility/command-flag-element.md)

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Należy również zauważyć, że każdy kontekst `VisibilityItem` interfejsu użytkownika muszą być podane w oddzielnym elemencie, w następujący sposób.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Zobacz też

- [Dodawanie polecenia do paska narzędzi Eksploratora rozwiązań](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamiczne dodawanie elementów menu](../../extensibility/dynamically-adding-menu-items.md)
