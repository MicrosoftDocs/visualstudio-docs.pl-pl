---
title: Dynamiczne dodawanie elementów menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712066"
---
# <a name="dynamically-add-menu-items"></a>Dynamiczne dodawanie elementów menu
Elementy menu można dodawać w czasie `DynamicItemStart` wykonywania, określając flagę polecenia w definicji przycisku zastępczego w pliku polecenia tabela poleceń programu Visual Studio (*.vsct),* a następnie definiując (w kodzie) liczbę elementów menu do wyświetlenia i obsługi poleceń. Po załadowaniu vspackage, symbol zastępczy jest zastępowany elementami menu dynamicznego.

 Program Visual Studio używa list dynamicznych na liście **Ostatnio używane** (MRU), która wyświetla nazwy dokumentów, które zostały niedawno otwarte, oraz listy **systemu Windows,** która wyświetla nazwy okien, które są obecnie otwarte.   Flaga `DynamicItemStart` w definicji polecenia określa, że polecenie jest symbolem zastępczym, dopóki nie zostanie otwarty vspackage. Po otwarciu vspackage, symbol zastępczy jest zastępowany 0 lub więcej poleceń, które są tworzone w czasie wykonywania i dodaje się do listy dynamicznej. Być może nie można zobaczyć pozycji w menu, w którym pojawia się lista dynamiczna, dopóki nie zostanie otwarty vspackage.  Aby wypełnić listę dynamiczną, Visual Studio prosi VSPackage szukać polecenia o identyfikatorze, którego pierwsze znaki są takie same jak identyfikator symbolu zastępczego. Gdy program Visual Studio znajdzie pasujące polecenie, dodaje nazwę polecenia do listy dynamicznej. Następnie zwiększa identyfikator i wyszukuje inne pasujące polecenie, aby dodać je do listy dynamicznej, dopóki nie będzie więcej dynamicznych poleceń.

 W tym przewodniku pokazano, jak ustawić projekt uruchamiania w rozwiązaniu programu Visual Studio za pomocą polecenia na pasku narzędzi **Eksploratora rozwiązań.** Używa kontrolera menu, który ma dynamiczną listę rozwijaną projektów w aktywnym rozwiązaniu. Aby to polecenie nie pojawiało się, gdy żadne rozwiązanie nie jest otwarte lub gdy otwarte rozwiązanie ma tylko jeden projekt, vspackage jest ładowany tylko wtedy, gdy rozwiązanie ma wiele projektów.

 Aby uzyskać więcej informacji o plikach *vsct,* zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

1. Utwórz projekt VSIX o nazwie `DynamicMenuItems`.

2. Po otwarciu projektu dodaj niestandardowy szablon elementu polecenia i nadaj jego nazwę **DynamicMenu**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Konfigurowanie elementów w pliku *vsct*
 Aby utworzyć kontroler menu z dynamicznymi elementami menu na pasku narzędzi, należy określić następujące elementy:

- Dwie grupy poleceń, jedna zawierająca kontroler menu, a druga zawierająca elementy menu w menu rozwijanym

- Jeden element menu typu`MenuController`

- Dwa przyciski, jeden, który działa jako symbol zastępczy dla elementów menu, a drugi, który dostarcza ikonę i etykietkę narzędzia na pasku narzędzi.

1. W *pliku DynamicMenuPackage.vsct*zdefiniuj identyfikatory poleceń. Przejdź do sekcji Symbole i zastąp elementy IDSymbol w bloku **guidDynamicMenuPackageCmdSet** GuidSymbol. Należy zdefiniować elementy IDSymbol dla dwóch grup, kontrolera menu, polecenia zastępczego i polecenia zakotwiczenia.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. W sekcji Grupy usuń istniejące grupy i dodaj dwie zdefiniowane właśnie grupy:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Dodaj MenuController. Ustaw flagę polecenia DynamicVisibility, ponieważ nie zawsze jest ona widoczna. ButtonText nie jest wyświetlany.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Dodaj dwa przyciski, jeden jako symbol zastępczy dla dynamicznych elementów menu i jeden jako kotwicę dla MenuController.

     Elementem nadrzędnym przycisku zastępczego jest **MyMenuControllerGroup**. Dodaj flagi poleceń DynamicItemStart, DynamicVisibility i TextChanges do przycisku zastępczego. ButtonText nie jest wyświetlany.

     Przycisk zakotwiczenia zawiera ikonę i tekst etykietki narzędzia. Elementem nadrzędnym przycisku zakotwiczenia jest również **MyMenuControllerGroup**. Dodaj noShowOnMenuController flagi polecenia, aby upewnić się, że przycisk nie jest rzeczywiście pojawiają się w menu kontrolera listy rozwijanej i FixMenuController flagi polecenia, aby uczynić go stałą kotwicą.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Dodaj ikonę do projektu (w folderze *Zasoby),* a następnie dodaj odwołanie do niego w pliku *vsct.* W tym instruktażu używamy ikony Strzałki, która jest zawarta w szablonie projektu.

5. Dodaj sekcję VisibilityConstraints poza sekcją Polecenia tuż przed sekcją Symbole. (Ostrzeżenie może zostać dodane po symbolach). W tej sekcji upewnij się, że kontroler menu pojawia się tylko wtedy, gdy rozwiązanie z wieloma projektami jest ładowane.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementowanie polecenia menu dynamicznego
 Tworzenie dynamicznej klasy polecenia menu, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>która dziedziczy po . W tej implementacji konstruktor określa predykatu, który ma być używany do pasowania poleceń. Należy zastąpić <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, aby użyć tego predykatu, aby ustawić <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwość, która identyfikuje polecenie, które ma zostać wywołane.

1. Utwórz nowy plik klasy C# o nazwie *DynamicItemMenuCommand.cs*i dodaj klasę o nazwie **DynamicItemMenuCommand,** która dziedziczy po: <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Dodaj następujące za pomocą dyrektyw:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Dodaj pole prywatne do przechowywania predykatu dopasowania:

    ```csharp
    private Predicate<int> matches;

    ```

4. Dodaj konstruktora, który <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dziedziczy z konstruktora <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> i określa program obsługi poleceń i program obsługi. Dodaj predykat do dopasowania polecenia:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Zastąp <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę tak, aby wywołuje predykatu dopasowania i ustawia <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwość:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Dodawanie polecenia
 Konstruktor DynamicMenu to miejsce, w którym można skonfigurować polecenia menu, w tym menu dynamiczne i elementy menu.

1. W *DynamicMenuPackage.cs*dodaj identyfikator GUID zestawu poleceń i identyfikator polecenia:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. W pliku *DynamicMenu.cs* dodaj następujące elementy za pomocą dyrektyw:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. W `DynamicMenu` klasie dodaj pole prywatne **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Dodaj pole private rootItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. W konstruktorze DynamicMenu dodaj polecenie menu. W następnej sekcji zdefiniujemy program `BeforeQueryStatus` obsługi poleceń, program obsługi zdarzeń i predykat dopasowania.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Zaimplementowanie programów obsługi
 Aby zaimplementować dynamiczne elementy menu na kontrolerze menu, należy obsługiwać polecenie po kliknięciu elementu dynamicznego. Należy również zaimplementować logikę, która ustawia stan elementu menu. Dodaj programy obsługi `DynamicMenu` do klasy.

1. Aby zaimplementować polecenie **Ustaw projekt uruchamiania,** dodaj program obsługi zdarzeń **OnInvokedDynamicItem.** Wyszukuje projekt, którego nazwa jest taka sama jak tekst polecenia, który został wywołany i ustawia <xref:EnvDTE.SolutionBuild.StartupProjects%2A> go jako projekt startowy, ustawiając jego ścieżkę bezwzględną we właściwości.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Dodaj `OnBeforeQueryStatusDynamicItem` program obsługi zdarzeń. Jest to program obsługi `QueryStatus` wywoływany przed zdarzeniem. Określa, czy element menu jest elementem "rzeczywistym", czyli nie elementem zastępczym i czy element jest już zaznaczony (co oznacza, że projekt jest już ustawiony jako projekt startowy).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Implementowanie predykatu dopasowywki identyfikatora polecenia

Teraz zaimplementuj predykat dopasowania. Musimy określić dwie rzeczy: po pierwsze, czy identyfikator polecenia jest prawidłowy (jest większy lub równy deklarowanego identyfikatora polecenia), a po drugie, czy określa możliwy projekt (jest mniejsza niż liczba projektów w rozwiązaniu).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Ustaw vspackage załadować tylko wtedy, gdy rozwiązanie ma wiele projektów
 Ponieważ **polecenie Ustaw projekt uruchamiania** nie ma sensu, chyba że aktywne rozwiązanie ma więcej niż jeden projekt, można ustawić vsPackage do automatycznego ładowania tylko w takim przypadku. Używasz <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> razem z kontekstem <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>interfejsu użytkownika . W pliku *DynamicMenuPackage.cs* dodaj następujące atrybuty do klasy DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testowanie polecenia projektu uruchamiania zestawu
 Teraz możesz przetestować swój kod.

1. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

2. W wystąpieniu eksperymentalnym otwórz rozwiązanie, które ma więcej niż jeden projekt.

     Na pasku narzędzi **Eksploratora rozwiązań** powinna zostać widoczna ikona strzałki. Po rozwinięciu powinien pojawić się elementy menu reprezentujące różne projekty w rozwiązaniu.

3. Po sprawdzeniu jednego z projektów staje się projektem startowym.

4. Po zamknięciu rozwiązania lub otwarciu rozwiązania, które ma tylko jeden projekt, ikona paska narzędzi powinna zniknąć.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak vspackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
