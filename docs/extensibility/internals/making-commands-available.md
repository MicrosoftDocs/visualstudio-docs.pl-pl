---
title: Udostępnianie poleceń | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707331"
---
# <a name="making-commands-available"></a>Udostępnianie poleceń

Gdy wiele pakietów VSPackage jest dodawanych do programu Visual Studio, interfejs użytkownika może zostać nadmiarowy za pomocą poleceń. Możesz zaprogramować pakiet, aby pomóc w zmniejszeniu tego problemu w następujący sposób:

- Zaprogramowanie pakietu w taki sposób, aby był ładowany tylko wtedy, gdy użytkownik go wymaga.

- Zaprogramowanie pakietu tak, aby polecenia były wyświetlane tylko wtedy, gdy mogą być wymagane w kontekście bieżącego stanu zintegrowanego środowiska programistycznego (IDE).

## <a name="delayed-loading"></a>Opóźnione ładowanie

Typowym sposobem włączania opóźnionego ładowania jest zaprojektowanie pakietu VSPackage w taki sposób, aby polecenia były wyświetlane w interfejsie użytkownika, ale sam pakiet nie jest ładowany do momentu kliknięcia jednego z poleceń przez użytkownika. Aby to osiągnąć, w pliku VSCT Utwórz polecenia, które nie mają flag poleceń.

Poniższy przykład przedstawia definicję polecenia menu z pliku. vsct. Jest to polecenie generowane przez szablon pakietu programu Visual Studio w przypadku wybrania opcji **menu** w szablonie.

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

W przykładzie, jeśli grupa nadrzędna, `MyMenuGroup` jest elementem podrzędnym menu najwyższego poziomu, takim jak menu **Narzędzia** , polecenie będzie widoczne w tym menu, ale pakiet, który wykonuje polecenie nie zostanie załadowany, dopóki polecenie nie zostanie kliknięte przez użytkownika. Jednak przez programowanie polecenia w celu zaimplementowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, można włączyć ładowanie pakietu, gdy menu zawierające polecenie jest najpierw rozwinięte.

Należy zauważyć, że opóźnione ładowanie może również zwiększyć wydajność uruchamiania.

## <a name="current-context-and-the-visibility-of-commands"></a>Bieżący kontekst i widoczność poleceń

Polecenia pakietu VSPackage można wyświetlić lub ukryć, w zależności od bieżącego stanu danych pakietu VSPackage lub działań, które są obecnie odpowiednie. Można włączyć pakietu VSPackage, aby ustawić stan poleceń, zazwyczaj przy użyciu implementacji <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, ale wymaga załadowania pakietu VSPackage przed wykonaniem kodu. Zamiast tego zalecamy włączenie środowiska IDE w celu zarządzania widocznością poleceń bez ładowania pakietu. W tym celu w pliku VSCT Skojarz polecenia z co najmniej jednym kontekstem interfejsu użytkownika. Te konteksty interfejsu użytkownika są identyfikowane przez identyfikator GUID znany jako *Identyfikator GUID kontekstu polecenia*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoruje zmiany wynikające z akcji użytkownika, takich jak ładowanie projektu lub przechodzenie przez edytowanie do kompilowania. Po wystąpieniu zmian wygląd IDE jest automatycznie modyfikowany. W poniższej tabeli przedstawiono cztery główne konteksty zmiany środowiska IDE, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoruje.

| Typ kontekstu | Opis |
|-------------------------| - |
| Typ aktywnego projektu | W przypadku większości typów projektów ta `GUID` wartość jest taka sama jak identyfikator GUID pakietu VSPackage implementujący projekt. Jednak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty używają typu projektu `GUID` jako wartości. |
| Aktywne okno | Zwykle jest to ostatnie okno aktywnego dokumentu, które ustanawia bieżący kontekst interfejsu użytkownika dla powiązań kluczy. Jednak może to być również okno narzędzi, które ma tabelę powiązań kluczy przypominającą wewnętrzną przeglądarkę internetową. W przypadku okien dokumentów z wielodostępnymi, takimi jak edytor HTML, każda karta ma inny kontekst poleceń `GUID` . |
| Aktywna usługa języka | Usługa językowa, która jest skojarzona z plikiem, który jest aktualnie wyświetlany w edytorze tekstu. |
| Aktywne okno narzędzi | Otwarte okno narzędzi i ma fokus. |

Piąty obszar kontekstu głównego to stan interfejsu użytkownika IDE. Konteksty interfejsu użytkownika są identyfikowane przez aktywny kontekst poleceń `GUID` s w następujący sposób:

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

Identyfikatory GUID są oznaczone jako aktywne lub nieaktywne, w zależności od bieżącego stanu środowiska IDE. Jednocześnie może być aktywnych wiele kontekstów interfejsu użytkownika.

### <a name="hide-and-display-commands-based-on-context"></a>Ukrywanie i wyświetlanie poleceń opartych na kontekście

Możesz wyświetlić lub ukryć polecenie Package w środowisku IDE bez ładowania samego pakietu. Aby to zrobić, zdefiniuj polecenie w pliku. vsct pakietu przy użyciu `DefaultDisabled` `DefaultInvisible` flag, i i `DynamicVisibility` Dodaj jeden lub więcej elementów [VisibilityItem](../../extensibility/visibilityitem-element.md) do sekcji [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Gdy określony kontekst polecenia `GUID` zostanie uaktywniony, polecenie jest wyświetlane bez ładowania pakietu.

### <a name="custom-context-guids"></a>Identyfikatory GUID kontekstu niestandardowego

Jeśli odpowiedni identyfikator GUID kontekstu polecenia nie jest jeszcze zdefiniowany, można go zdefiniować w pakietu VSPackage, a następnie program powinien być aktywny lub nieaktywny, zgodnie z wymaganiami, aby kontrolować widoczność poleceń. Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi, aby:

- Zarejestruj identyfikatory GUID kontekstu (przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody).

- Pobierz stan kontekstu `GUID` (przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody).

- Włącz `GUID` i Wyłącz kontekst s (przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody).

    > [!CAUTION]
    > Upewnij się, że pakietu VSPackage nie ma wpływu na stan jakiegokolwiek istniejącego identyfikatora GUID kontekstu, ponieważ inne pakietów VSPackage mogą być od nich zależne.

## <a name="example"></a>Przykład

Poniższy przykład polecenia pakietu VSPackage demonstruje dynamiczną widoczność polecenia, które jest zarządzane przez konteksty poleceń bez ładowania pakietu VSPackage.

Polecenie jest ustawione do włączenia i wyświetlania za każdym razem, gdy istnieje rozwiązanie; oznacza to, że za każdym razem, gdy jeden z następujących identyfikatorów GUID kontekstu poleceń jest aktywny:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

W przykładzie należy zauważyć, że każda Flaga polecenia jest osobnym elementem [flagi polecenia](../../extensibility/command-flag-element.md) .

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

Zauważ również, że każdy kontekst interfejsu użytkownika musi być określony w osobnym `VisibilityItem` elemencie w następujący sposób.

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

- [Dodaj polecenie do paska narzędzi Eksplorator rozwiązań](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamiczne dodawanie elementów menu](../../extensibility/dynamically-adding-menu-items.md)
