---
title: Dodawanie podmenu do Menu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32a69a260aff2163deb02a67fb011d50f138c601
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309869"
---
# <a name="add-a-submenu-to-a-menu"></a>Dodawanie podmenu do Menu
W tym przewodniku opiera się na pokaz w [dodać Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , przedstawiający sposób dodawanie podmenu do **TestMenu** menu.

 Podmenu jest dodatkowej menu, który pojawia się w innym menu. Podmenu można zidentyfikować strzałką, który następuje po jego nazwę. Kliknięcie nazwy powoduje, że podmenu i jego poleceń, które mają być wyświetlane.

 Ten przewodnik utworzy podmenu w menu na pasku menu programu Visual Studio i umieszcza nowe polecenie, w podmenu. Instruktaż implementuje również nowe polecenie.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Dodawanie podmenu do Menu

1. Postępuj zgodnie z instrukcjami w [dodać Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Tworzenie elementu projektu i menu. Kroki opisane w tym przewodniku przyjęto założenie, że nazwa projektu VSIX jest `TopLevelMenu`.

2. Otwórz *TestCommandPackage.vsct*. W `<Symbols>` Dodaj `<IDSymbol>` elementu podmenu: jeden dla grupy podmenu i jeden dla polecenia, w `<GuidSymbol>` węzeł o nazwie "guidTopLevelMenuCmdSet." Jest to ten sam węzeł, który zawiera `<IDSymbol>` element menu najwyższego poziomu.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Dodaj nowo utworzony podmenu `<Menus>` sekcji.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Para identyfikator GUID/element nadrzędny określa grupy menu, który został wygenerowany w [dodać Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), i jest elementem podrzędnym menu najwyższego poziomu.

4. Dodawanie grupy menu zdefiniowane w kroku 2, aby `<Groups>` sekcji i Uczyń elementem podrzędnym podmenu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Dodaj nową `<Button>` elementu `<Buttons>` sekcji, aby zdefiniować polecenia utworzony w kroku 2, jako element w podmenu.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Powinien zostać wyświetlony wystąpienie eksperymentalne.

7. Kliknij przycisk **TestMenu** aby zobaczyć nowe podmenu o nazwie **podmenu**. Kliknij przycisk **podmenu** można otworzyć podmenu i zobaczyć nowe polecenie **testu podpolecenie**. Należy zauważyć, że kliknięcie **testu podpolecenie** nic nie robi.

## <a name="add-a-command"></a>Dodawanie polecenia

1. Otwórz *TestCommand.cs* i Dodaj następujący identyfikator polecenia po wykonaniu istniejący identyfikator polecenia.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Dodaj polecenie podrzędnych. Znajdź Konstruktor polecenia. Dodaj następujące wiersze po wywołaniu `AddCommand` metody.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    `SubItemCallback` Program obsługi poleceń zostanie zdefiniowana później. Konstruktor powinien teraz wyglądać następująco:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Dodaj `SubItemCallback()`. Jest to metoda, która jest wywoływana po kliknięciu polecenia Nowy w podmenu.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.

5. Na **TestMenu** menu, kliknij przycisk **podmenu** a następnie kliknij przycisk **testu podpolecenie**. Okno komunikatu powinno wyświetlane, a następnie wyświetlić tekst "Test polecenia wewnątrz TestCommand.SubItemCallback()".

## <a name="see-also"></a>Zobacz także

- [Dodawanie menu na pasku menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
