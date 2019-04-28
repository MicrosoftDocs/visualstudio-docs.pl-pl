---
title: Dynamiczne dodawanie elementów Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18c2100341a62abd0f8f12bd4b459c7e271a15bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912523"
---
# <a name="dynamically-add-menu-items"></a>Dynamiczne dodawanie elementów menu
Można dodać elementów menu w czasie wykonywania, określając `DynamicItemStart` polecenia Flaga w definicji symbolu zastępczego przycisku w tabeli poleceń programu Visual Studio (*vsct*) plik, a następnie definiowanie (kod) liczba elementów menu do wyświetlenia i Obsługa polecenia. Po załadowaniu pakietu VSPackage, symbol zastępczy jest zastępowany elementów menu dynamiczne.

 Program Visual Studio używa dynamicznej listy w **ostatnio używane** listy (MRU), który wyświetla nazwy dokumentów, które zostały ostatnio otwarte, a **Windows** listę, która wyświetla nazwy systemu windows które są aktualnie otwarte.   `DynamicItemStart` Flaga w definicji polecenia określa, czy polecenie jest symbolem zastępczym, dopóki nie zostanie otwarty pakietu VSPackage. Po otwarciu pakietu VSPackage symbol zastępczy jest zastępowany 0 lub więcej poleceń, które są tworzone w czasie wykonywania i dodawane do listy dynamicznej. Nie można zobaczyć pozycję menu, gdzie lista dynamiczna pojawia się, dopóki nie zostanie otwarty pakietu VSPackage.  Do wypełniania listy dynamicznej, program Visual Studio pyta, czy pakietu VSPackage, aby wyszukać polecenia przy użyciu Identyfikatora, w której pierwsze znaki są takie same, jak identyfikator symbol zastępczy. Gdy program Visual Studio znajdzie pasujące polecenia, dodaje nazwę polecenia, do listy dynamicznej. Następnie zwiększa identyfikator i szuka innego polecenia pasujących do dodania do listy dynamicznej, aż nie wystąpią poleceń nie bardziej dynamiczne.

 W tym instruktażu przedstawiono sposób ustawiania projektem startowym w rozwiązaniu programu Visual Studio za pomocą polecenia na **Eksploratora rozwiązań** paska narzędzi. Używa kontrolera menu, który ma na liście rozwijanej dynamiczne projektów w aktywnym rozwiązaniu. Aby zapobiec tego polecenia pojawia się, gdy żadne rozwiązanie nie jest otwarty lub jeśli otwarte rozwiązanie ma tylko jeden projekt, pakietu VSPackage jest załadowany, tylko wtedy, gdy rozwiązanie zawiera wiele projektów.

 Aby uzyskać więcej informacji na temat *vsct* plików, zobacz [pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu

1. Utwórz projekt VSIX, o nazwie `DynamicMenuItems`.

2. Po otwarciu projektu dodania polecenia niestandardowego szablonu elementu i nadaj mu nazwę **wywołaniu zwrotnym**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Definiowanie elementów w *vsct* pliku
 Aby utworzyć kontroler menu przy użyciu dynamicznych elementów menu na pasku narzędzi, należy określić następujące elementy:

- Polecenie dwie grupy, zawierający kontroler menu i drugiego, który zawiera elementy menu w menu rozwijanym

- Element menu jednego typu `MenuController`

- Dwa przyciski o taki, który działa jako symbol zastępczy dla elementów menu, a drugi, który zawiera ikonę i etykietkę narzędzia na pasku narzędzi.

1. W *DynamicMenuPackage.vsct*, określ identyfikatory poleceń. Przejdź do sekcji symboli i Zastąp elementy IDSymbol w **guidDynamicMenuPackageCmdSet** GuidSymbol bloku. Musisz zdefiniować elementy IDSymbol na dwie grupy, kontroler menu, symbol zastępczy polecenia i polecenia zakotwiczenia.

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

2. W sekcji grupy Usuń istniejące grupy, a następnie dodaj dwie grupy, który został zdefiniowany:

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

     Dodaj MenuController. Ustawić flagę DynamicVisibility polecenia, ponieważ nie jest zawsze widoczny. ButtonText nie jest wyświetlana.

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

3. Dodaj dwa przyciski: jeden jako symbol zastępczy dla elementów menu dynamiczne, a drugi jako kotwica dla MenuController.

     Jest elementem nadrzędnym przycisk symbolu zastępczego **MyMenuControllerGroup**. Dodawanie flag poleceń DynamicItemStart DynamicVisibility i TextChanges do przycisku symbol zastępczy. ButtonText nie jest wyświetlana.

     Przycisk zakotwiczenia zawiera ikonę i tekst etykietki narzędzia. Element nadrzędny przycisk zakotwiczenia jest również **MyMenuControllerGroup**. Dodaj flagę polecenia NoShowOnMenuController, aby upewnić się, że przycisk faktycznie nie jest wyświetlane w menu rozwijanym kontrolera i Flaga polecenia FixMenuController umożliwiają stałe zakotwiczenia.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->
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

4. Dodaj ikonę do projektu (w *zasobów* folderu), a następnie dodaj odwołanie do niego w *vsct* pliku. W tym przewodniku używamy ikonę strzałki, który znajduje się w szablonie projektu.

5. Dodaj sekcję VisibilityConstraints poza sekcję polecenia tuż przed sekcji symboli. (Może być wyświetlone ostrzeżenie, jeśli zostanie dodany po symbole.) W tej sekcji gwarantuje, że kontroler menu pojawia się tylko po załadowaniu rozwiązania z wieloma projektami.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementowanie polecenia menu dynamiczne
 Tworzenie klasy polecenia menu dynamiczne, która dziedziczy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. W tej implementacji Konstruktor określa predykatu ma być używany do dopasowywania poleceń. Konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, aby użyć ten predykat, aby ustawić <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwości, które identyfikuje polecenie do wywołania.

1. Utwórz nowy plik języka C# klasy o nazwie *DynamicItemMenuCommand.cs*, i Dodaj klasę o nazwie **DynamicItemMenuCommand** tej, która dziedziczy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:

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

4. Dodaj Konstruktor, który dziedziczy z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Konstruktor i określa procedurę obsługi poleceń i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> programu obsługi. Dodaj predykat dopasowanie polecenia:

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

5. Zastąp <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodę, tak że wywołuje dopasowania predykat i zestawy <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> właściwości:

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
 Konstruktor wywołaniu zwrotnym jest skonfigurowanie poleceń menu, w tym elementy menu i menu dynamiczne.

1. W *DynamicMenuPackage.cs*, Dodaj identyfikator GUID zestawu poleceń i identyfikator polecenia:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. W *DynamicMenu.cs* plików, Dodaj następujące instrukcje using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. W `DynamicMenu` klasy, Dodaj pole prywatne **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Dodaj pole prywatne rootItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. W wywołaniu zwrotnym konstruktora należy dodać polecenie menu. W następnej sekcji zdefiniujemy program obsługi poleceń `BeforeQueryStatus` program obsługi zdarzeń, a predykat dopasowania.

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

## <a name="implement-the-handlers"></a>Implementowanie obsługi
 Aby wdrożyć elementy menu dynamiczne na kontrolerze menu, musi obsługiwać polecenia po kliknięciu elementu dynamicznego. Należy także zaimplementować logikę, która ustawia stan elementu menu. Dodawanie obsługi do `DynamicMenu` klasy.

1. Aby zaimplementować **Ustaw projekt startowy** polecenia, należy dodać **OnInvokedDynamicItem** programu obsługi zdarzeń. Szuka projektu, którego nazwa jest taka sama jak tekst polecenia, które zostało wywołane, a następnie ustawia go jako projekt startowy, ustawiając jego ścieżka bezwzględna w <xref:EnvDTE.SolutionBuild.StartupProjects%2A> właściwości.

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

2. Dodaj `OnBeforeQueryStatusDynamicItem` programu obsługi zdarzeń. To jest program obsługi, wywołana przed metodą `QueryStatus` zdarzeń. Określa, czy element menu jest elementem "członu real", oznacza to nie symbol zastępczy element, i czy element jest już zaznaczone pole wyboru (co oznacza, że projekt jest już ustawiony jako projekt startowy).

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

## <a name="implement-the-command-id-match-predicate"></a>Implementowanie predykatu dopasowania Identyfikatora polecenia

Teraz można wdrożyć predykatu dopasowania. Należy określić dwie rzeczy: po pierwsze, czy identyfikator polecenia jest prawidłowa (jest większe niż lub równa identyfikator zadeklarowany polecenia) i drugiego, czy określa możliwe projektu (jest on mniejszy niż liczba projektów w rozwiązaniu).

    ```csharp
    private bool IsValidDynamicItem(int commandId)
    {
        // The match is valid if the command ID is >= the id of our root dynamic start item
        // and the command ID minus the ID of our root dynamic start item
        // is less than or equal to the number of projects in the solution.
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
    }
    ```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Ustaw pakietu VSPackage załadować tylko wtedy, gdy rozwiązanie zawiera wiele projektów
 Ponieważ **Ustaw projekt startowy** polecenia nie ma sensu, chyba że aktywne rozwiązanie ma więcej niż jeden projekt, możesz ustawić Twojego pakietu VSPackage, można automatycznie załadować tylko w takim przypadku. Możesz użyć <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> wraz z kontekstu interfejsu użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. W *DynamicMenuPackage.cs* pliku Dodaj następujące atrybuty do klasy DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Polecenie Projekt uruchamiania zestawu testów
 Teraz można przetestować kod.

1. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.

2. W doświadczalnym wystąpieniu Otwórz rozwiązanie, które ma więcej niż jeden projekt.

     Ikona strzałki powinien zostać wyświetlony na **Eksploratora rozwiązań** paska narzędzi. Po rozwinięciu, powinna zostać wyświetlona elementy menu, które reprezentują różne projekty w rozwiązaniu.

3. Po zaznaczeniu projektów staje się projekt startowy.

4. Gdy Zamknij rozwiązanie lub Otwórz rozwiązanie, które ma tylko jeden projekt powinien zniknąć ikony paska narzędzi.

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)