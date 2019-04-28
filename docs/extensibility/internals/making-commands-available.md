---
title: Udostępnianie poleceń | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14998b8dca3c14bdae4f00f1940c19b696646ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909577"
---
# <a name="making-commands-available"></a>Udostępnianie poleceń

Gdy wiele pakietów VSPackage zostaną dodane do programu Visual Studio, interfejs użytkownika (UI) mogą stać się przepełniona za pomocą poleceń. Można programować pakietu w celu ograniczenia tego problemu w następujący sposób:

- Program pakiet tak, że jest załadowany, tylko wtedy, gdy użytkownik wymaga go.

- Program pakietu, tak aby jego polecenia są wyświetlane tylko wtedy, gdy może być wymagane w kontekście bieżącego stanu zintegrowanego środowiska programistycznego (IDE).

## <a name="delayed-loading"></a>Opóźnione ładowanie

Typowym sposobem, aby umożliwić opóźnione ładowanie jest projektować pakietu VSPackage, dzięki czemu polecenia są wyświetlane w interfejsie użytkownika, ale sam pakiet nie został załadowany, dopóki użytkownik kliknie jedno z poleceń. Aby to osiągnąć, w pliku vsct, Utwórz polecenia, które mają nie flag poleceń.

Poniższy przykład przedstawia definicję polecenia menu z pliku vsct. To polecenie, które są generowane przez szablon pakietu Visual Studio podczas **polecenia Menu** wybrano opcję w szablonie.

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

W przykładzie Jeśli grupy nadrzędnej `MyMenuGroup`, jest elementem podrzędnym menu najwyższego poziomu, takie jak **narzędzia** menu polecenie będzie widoczny w menu, ale pakiet, który wykonuje polecenie nie zostanie załadowany, kliknąć polecenie przez użytkownika. Jednak, Programując polecenie, aby zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, możesz włączyć pakiet, który ma być ładowany podczas najpierw rozwijane menu, który zawiera polecenie.

Należy zauważyć, że opóźnionego ładowania może również zwiększyć wydajność uruchamiania.

## <a name="current-context-and-the-visibility-of-commands"></a>Bieżący kontekst i widoczności poleceń

Można programować pakietu VSPackage polecenia ma być widoczny lub ukryty, w zależności od bieżącego stanu danych pakietu VSPackage lub akcje, które są aktualnie istotne. Możesz włączyć pakietu VSPackage ustawić stan jego poleceń zazwyczaj przy użyciu implementacji z <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, ale wymaga to pakietu VSPackage, należy załadować przed może on wykonać kod. Zamiast tego zaleca się włączenie zarządzania widocznością polecenia bez załadowania pakietu środowiska IDE. W tym celu w pliku vsct kojarzenie poleceń z jednego lub więcej specjalnych kontekstami interfejsu użytkownika. Tych kontekstach interfejsu użytkownika są identyfikowane przez identyfikator GUID znane jako *polecenia w kontekście identyfikatora GUID*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoruje zmiany, które wynikają z akcje użytkownika, takie jak ładowania projektu lub ruch do edycji do tworzenia. Wraz ze zmianami, wygląd IDE automatycznie zostanie zmodyfikowany. W poniższej tabeli przedstawiono cztery główne kontekstach IDE zmienimy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitorów.

| Typ kontekstu | Opis |
|-------------------------| - |
| Typ aktywnego projektu | Dla większości typów projektów to `GUID` wartość jest taka sama jak identyfikator GUID pakietu VSPackage, który implementuje projektu. Jednak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty korzystają z tego typu projektu `GUID` jako wartość. |
| Aktywne okno | Zazwyczaj są to okna dokumentów aktywnych ostatniego ustanawia bieżącego kontekstu interfejsu użytkownika dla powiązań klawiszy. Jednak może również być okna narzędzi, które zawiera tabelę powiązanie klucza, która przypomina wewnętrznej przeglądarki sieci Web. Dla systemu windows z wieloma kartami dokumentu, takich jak edytor HTML, każda karta ma innego polecenia kontekst `GUID`. |
| Usługa Active języka | Usługa języka, który jest skojarzony z pliku który jest aktualnie wyświetlany w edytorze tekstów. |
| Aktywnego okna narzędzi | Okna narzędzi, które jest otwarty i ma fokus. |

Piąty obszar głównych kontekstu jest stan interfejsu użytkownika IDE. Konteksty interfejsu użytkownika są identyfikowane za pomocą kontekstu aktywnego polecenia `GUID`s w następujący sposób:

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

Te identyfikatory GUID są oznaczone jako aktywną lub nieaktywną, w zależności od bieżącego stanu środowiska IDE. Wiele kontekstów interfejsu użytkownika może być aktywne w tym samym czasie.

### <a name="hide-and-display-commands-based-on-context"></a>Ukryj i wyświetlania poleceń na podstawie kontekstu

Można wyświetlić lub ukryć polecenia pakietu w środowisku IDE bez załadowania pakietu. W tym celu należy zdefiniować polecenia w pliku vsct pakietu przy użyciu `DefaultDisabled`, `DefaultInvisible`, i `DynamicVisibility` command flag i dodawania co najmniej jeden [VisibilityItem](../../extensibility/visibilityitem-element.md) elementów [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sekcji. Gdy w kontekście określonego polecenia `GUID` staje się aktywny, będzie ono wyświetlane bez ładowania pakietu.

### <a name="custom-context-guids"></a>Identyfikatory GUID kontekstowego

Jeśli kontekst odpowiednie polecenia, identyfikator GUID nie jest już zdefiniowany, można zdefiniować, w swojej pakietu VSPackage i Zaprogramuj się być aktywne lub nieaktywne zgodnie z potrzebami można kontrolować widoczność poleceń. Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi:

- Rejestrowanie identyfikatorów GUID w kontekście (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody).

- Pobieranie stanu kontekst `GUID` (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody).

- Włącz kontekstu `GUID`s włączać i wyłączać (przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody).

    > [!CAUTION]
    > Upewnij się, że Twoje pakietu VSPackage nie ma wpływu na stan dowolnego kontekstu istniejącego identyfikatora GUID ponieważ innych pakietów VSPackage może zależeć od ich.

## <a name="example"></a>Przykład

Poniższy przykład polecenia pakietu VSPackage pokazuje dynamiczne widoczność polecenia, który jest zarządzany przez kontekstów polecenia bez załadowania pakietu VSPackage.

Polecenie jest ustawiona na włączony i wyświetlany zawsze, gdy rozwiązanie istnieje; oznacza to, że zawsze, gdy jeden z następującym kontekstem polecenia identyfikatorów GUID jest aktywna:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

W tym przykładzie należy zauważyć, że flaga każdego polecenia jest oddzielny [flagi polecenia](../../extensibility/command-flag-element.md) elementu.

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

Zwróć również uwagę, które każdy kontekstu interfejsu użytkownika muszą być umieszczone w osobnym `VisibilityItem` elementu w następujący sposób.

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

## <a name="see-also"></a>Zobacz także

- [Dodaj polecenie do paska narzędzi Eksploratora rozwiązań](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [MenuCommands programu Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamiczne dodawanie elementów menu](../../extensibility/dynamically-adding-menu-items.md)
