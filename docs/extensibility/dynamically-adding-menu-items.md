---
title: Dynamiczne dodawanie elementów menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 136ee925f1ee7505e7058eb643d7bac3a9222c06
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252356"
---
# <a name="dynamically-add-menu-items"></a>Dynamicznie Dodaj elementy menu
Możesz dodać elementy menu w czasie wykonywania, określając `DynamicItemStart` flagę polecenia w definicji przycisku zastępczego w pliku tabeli programu Visual Studio ( *. vsct*), a następnie definiując (w kodzie) liczbę elementów menu do wyświetlenia i obsługi poleceń. Po załadowaniu pakietu VSPackage symbol zastępczy jest zastępowany dynamicznymi elementami menu.

 Program Visual Studio używa dynamicznych list na liście ostatnio **używanych** (MRU), która wyświetla ostatnio otwarte dokumenty i listę **systemu Windows** , w której są wyświetlane nazwy okien, które są aktualnie otwarte.   `DynamicItemStart` Flaga w definicji polecenia określa, że polecenie jest symbolem zastępczym do momentu otwarcia pakietu VSPackage. Po otwarciu pakietu VSPackage symbol zastępczy zostanie zastąpiony przez 0 lub więcej poleceń, które są tworzone w czasie wykonywania i dodawane do listy dynamicznej. Być może nie widzisz pozycji w menu, w którym pojawia się lista dynamiczna, dopóki nie zostanie otwarta pakietu VSPackage.  Aby wypełnić listę dynamiczną, program Visual Studio prosi pakietu VSPackage o wyszukanie polecenia o IDENTYFIKATORze, którego pierwsze znaki są takie same jak identyfikator symbolu zastępczego. Gdy program Visual Studio znajdzie pasujące polecenie, dodaje nazwę polecenia do listy dynamicznej. Następnie zwiększa identyfikator i wyszukuje inne pasujące polecenie do dodania do listy dynamicznej do momentu braku dodatkowych poleceń dynamicznych.

 W tym instruktażu pokazano, jak ustawić projekt startowy w rozwiązaniu programu Visual Studio za pomocą polecenia na pasku narzędzi **Eksplorator rozwiązań** . Używa kontrolera menu, który ma dynamiczną listę rozwijaną projektów w aktywnym rozwiązaniu. Aby zapobiec pojawianiu się tego polecenia, gdy żadne rozwiązanie nie jest otwarte lub gdy otwarte rozwiązanie ma tylko jeden projekt, pakietu VSPackage jest ładowany tylko wtedy, gdy rozwiązanie ma wiele projektów.

 Aby uzyskać więcej informacji na temat plików *. vsct* , zobacz [pliki programu Visual Studio Command Table (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

1. Utwórz projekt VSIX, o nazwie `DynamicMenuItems`.

2. Po otwarciu projektu Dodaj szablon niestandardowego elementu polecenia i nadaj mu nazwę **wywołaniu**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Konfigurowanie elementów w pliku *. vsct*
 Aby utworzyć kontroler menu z dynamicznymi elementami menu na pasku narzędzi, należy określić następujące elementy:

- Dwie grupy poleceń, takie, które zawiera kontroler menu i inny, który zawiera elementy menu na liście rozwijanej

- Jeden element menu typu`MenuController`

- Dwa przyciski, takie jak symbol zastępczy dla elementów menu i inne, które dostarczają ikonę i etykietkę narzędzia na pasku narzędzi.

1. W *DynamicMenuPackage. vsct*Zdefiniuj identyfikatory poleceń. Przejdź do sekcji symbole i Zastąp elementy IDSymbol w bloku **guidDynamicMenuPackageCmdSet** GuidSymbol. Należy zdefiniować elementy IDSymbol dla dwóch grup, kontrolera menu, polecenia PlaceHolder i polecenia zakotwiczenia.

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

2. W sekcji grupy Usuń istniejące grupy i Dodaj dwie zdefiniowane grupy:

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

     Dodaj MenuController. Ustaw flagę polecenia DynamicVisibility, ponieważ nie jest ona zawsze widoczna. ButtonText nie jest wyświetlana.

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

3. Dodaj dwa przyciski, jeden jako symbol zastępczy dla elementów menu dynamicznego i jeden jako zakotwiczenie dla MenuController.

     Elementem nadrzędnym przycisku symbolu zastępczego jest **MyMenuControllerGroup**. Dodaj flagi polecenia DynamicItemStart, DynamicVisibility i textchangs do przycisku symbolu zastępczego. ButtonText nie jest wyświetlana.

     Przycisk zakotwiczenia zawiera ikonę i tekst etykietki narzędzia. Elementem nadrzędnym przycisku zakotwiczenia jest również **MyMenuControllerGroup**. Dodaj flagę polecenia NoShowOnMenuController, aby upewnić się, że przycisk nie jest rzeczywiście wyświetlany na liście rozwijanej kontrolera menu, i Oflaguj polecenie FixMenuController, aby stała się zakotwiczeniem.

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

4. Dodaj ikonę do projektu (w folderze *zasoby* ), a następnie Dodaj odwołanie do niego w pliku *. vsct* . W tym instruktażu używamy ikony strzałek, która znajduje się w szablonie projektu.

5. Dodaj sekcję VisibilityConstraints poza sekcją poleceń tuż przed sekcją symbole. (Może pojawić się ostrzeżenie, jeśli dodasz ją po symbolach). Ta sekcja gwarantuje, że kontroler menu pojawia się tylko wtedy, gdy jest ładowany rozwiązanie z wieloma projektami.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementowanie polecenia menu dynamicznego
 Tworzysz klasę poleceń menu dynamicznego, która dziedziczy z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. W tej implementacji Konstruktor Określa predykat, który ma być używany do dopasowywania poleceń. Należy zastąpić <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, aby użyć tego predykatu do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> ustawienia właściwości, która identyfikuje polecenie, które ma być wywoływane.

1. Utwórz nowy C# plik klasy o nazwie *DynamicItemMenuCommand.cs*i Dodaj klasę o nazwie **DynamicItemMenuCommand** , która dziedziczy z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Dodaj następujące instrukcje using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Dodaj pole prywatne do przechowywania predykatu dopasowania:

    ```csharp
    private Predicate<int> matches;

    ```

4. Dodaj Konstruktor, który dziedziczy z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> konstruktora i określa procedurę obsługi poleceń <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> i procedurę obsługi. Dodaj predykat pasujący do polecenia:

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

5. Zastąp <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> metodę tak, aby wywołała predykat dopasowania i ustawił Właściwość: <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>

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

## <a name="add-the-command"></a>Dodaj polecenie
 Konstruktor wywołaniu to miejsce, w którym można skonfigurować polecenia menu, w tym dynamiczne menu i elementy menu.

1. W *DynamicMenuPackage.cs*Dodaj identyfikator GUID zestawu poleceń i identyfikator polecenia:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. W pliku *DynamicMenu.cs* Dodaj następujące instrukcje using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. W klasie Dodaj pole private **DTE2.** `DynamicMenu`

    ```csharp
    private DTE2 dte2;
    ```

4. Dodaj prywatne pole rootItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. W konstruktorze wywołaniu Dodaj polecenie menu. W następnej sekcji zdefiniujemy procedurę obsługi poleceń, `BeforeQueryStatus` procedurę obsługi zdarzeń i predykat dopasowania.

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

## <a name="implement-the-handlers"></a>Implementowanie programów obsługi
 Aby zaimplementować dynamiczne elementy menu na kontrolerze menu, należy obsłużyć polecenie po kliknięciu elementu dynamicznego. Należy również zaimplementować logikę, która ustawia stan elementu menu. Dodaj programy obsługi do `DynamicMenu` klasy.

1. Aby zaimplementować polecenie **Ustaw projekt startowy** , Dodaj program obsługi zdarzeń **OnInvokedDynamicItem** . Szuka projektu, którego nazwa jest taka sama jak tekst wywoływanego polecenia i ustawia go jako projekt startowy, ustawiając jego ścieżkę bezwzględną we <xref:EnvDTE.SolutionBuild.StartupProjects%2A> właściwości.

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

2. Dodaj program obsługi zdarzeń. `OnBeforeQueryStatusDynamicItem` Jest to procedura obsługi wywołana przed `QueryStatus` zdarzeniem. Określa, czy element menu jest elementem "Real", czyli nie elementem symbolu zastępczego, oraz czy element jest już zaznaczony (oznacza to, że projekt jest już ustawiony jako projekt startowy).

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

## <a name="implement-the-command-id-match-predicate"></a>Zaimplementuj predykat dopasowania identyfikatora polecenia

Teraz Zaimplementuj predykat Match. Musimy określić dwie rzeczy: najpierw, czy identyfikator polecenia jest prawidłowy (jest większy niż lub równy zadeklarowanemu IDENTYFIKATORowi polecenia), a drugi, czy określa możliwy projekt (jest mniejszy niż liczba projektów w rozwiązaniu).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Ustaw pakietu VSPackage do załadowania tylko wtedy, gdy rozwiązanie ma wiele projektów
 Ponieważ polecenie **Ustaw projekt startowy** nie ma sensu, chyba że aktywne rozwiązanie ma więcej niż jeden projekt, można ustawić pakietu VSPackage do ładowania automatyczne tylko w tym przypadku. Używasz razem z kontekstem <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>interfejsu użytkownika. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> W pliku *DynamicMenuPackage.cs* Dodaj następujące atrybuty do klasy DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testuj polecenie Ustaw projekt startowy
 Teraz można testować kod.

1. Skompiluj projekt, a następnie rozpocząć debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

2. W eksperymentalnym wystąpieniu Otwórz rozwiązanie, które ma więcej niż jeden projekt.

     Na pasku narzędzi **Eksplorator rozwiązań** powinna zostać wyświetlona ikona strzałki. Po jego rozszerzeniu należy wyświetlić elementy menu, które reprezentują różne projekty w rozwiązaniu.

3. Gdy sprawdzisz jeden z projektów, jego stan zmieni się na projekt startowy.

4. Po zamknięciu rozwiązania lub otwarciu rozwiązania, które ma tylko jeden projekt, ikona paska narzędzi powinna zniknąć.

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)